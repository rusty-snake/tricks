---
layout: post
title: "Local Nextcloud with podman"
author: "rusty-snake"
#tags:
---

- ToC
{:toc}

Architecture
------------

The overall architecture of this first concept contists of

1. A caddy webserver on the host started by a hardened systemd service.
   The rule of this caddy instance is to proper terminate the https connection
   and forward everything to the Nextcloud pod. This is a grown construct to
   workaround some problems and might get/should be replaced with something
   better in the future.
2. A caddy webserver in the Nextcloud pod which does static file servering and
   acts as the reverse proxy to php-fpm.
3. The Nextcloud php-fpm container in the Nextcloud pod.
4. A Nextcloud container for cron.

~~~ mermaid
flowchart LR
    caddy_host["Caddy (Host)"]---caddy
    subgraph Nextcloud Pod
        caddy("Caddy")---nextcloud
        nextcloud("Nextcloud")
        nextcloud_cron("Nextcloud (cron)")
    end
~~~

Caddy (Host)
------------

Install caddy and [harden caddy.service](https://github.com/rusty-snake/kyst/blob/main/systemd/caddy.service.d%2Boverride.conf).

### Configure caddy ###

#### `/etc/caddy/Caddyfile` ####

~~~ Caddyfile
# The Caddyfile is an easy way to configure your Caddy web server.
#
# https://caddyserver.com/docs/caddyfile

# Global Options
# https://caddyserver.com/docs/caddyfile/options
{
	# Enable debug mode
	#debug

	# Disable the admin endpoint
	admin off

	log {
		format filter {
			wrap console
			fields {
				request>headers>Requesttoken replace "*** REDACTED ***"
			}
		}
	}

	local_certs
	skip_install_trust
	ocsp_stapling off
}

# As an alternative to editing the above site block, you can add your own site
# block files in the Caddyfile.d directory, and they will be included as long
# as they use the .caddyfile extension.
import Caddyfile.d/*.caddyfile
~~~

#### `/etc/caddy/Caddyfile.d/nextcloud.caddyfile` ####

~~~ Caddyfile
# vim: set ft=caddyfile:

192.168.0.236:7777 {
	root * /tmp

	# TLS Options
	tls {
		# Increase minimal TLS version to 1.3.
		protocols tls1.3

		issuer internal {
			lifetime 365d
			sign_with_root
		}
	}

	# Enable HSTS with a duration of 1 year.
	header Strict-Transport-Security "max-age=31536000; includeSubDomains"

	# Restrict allowed ip ranges.
	@disallowed-ips not remote_ip 127.0.0.1 192.168.0.0/24
	abort @disallowed-ips

	encode gzip
	reverse_proxy 127.0.0.1:7867
}
~~~

### SELinux

[Because you use SELinux](https://stopdisablingselinux.com/), we have to adjust
the policy of caddy (`httpd_t`) for our usecase.

#### Allow caddy (`httpd_t`) to bind to port 7777 ###

~~~ bash
semanage port -a -t http_port_t -p tcp 7777
semanage port -a -t http_port_t -p udp 7777
~~~

#### Allow caddy (`httpd_t`) to connect to port 7867

~~~ bash
setsebool -P httpd_can_network_connect 1
~~~

> **TODO**: Replace this boolean with an module allowing something like
`reverse_proxy_upstream_port_t` and define port 7867 to be of this type.

### Start caddy ###

~~~ bash
systemctl enable --now caddy.service
~~~

### Add caddys root certificate to the system trust store[^adding-new-certificates] ###

~~~ bash
cp /var/lib/caddy/.local/share/caddy/pki/authorities/local/root.crt /etc/pki/ca-trust/source/anchors/caddy-root.pem
chmod 644 /etc/pki/ca-trust/source/anchors/caddy-root.pem
update-ca-trust extract
~~~

[^adding-new-certificates]: <https://docs.fedoraproject.org/en-US/quick-docs/using-shared-system-certificates/#proc_adding-new-certificates>

### View certificate fingerprint

~~~ bash
openssl x509 -noout -fingerprint -sha256 -inform pem -in /var/lib/caddy/.local/share/caddy/certificates/local/192.168.0.100/192.168.0.100.crt
~~~

### Open port 7777 in your firewall ###

~~~ bash
firewall-cmd --permanent --add-port=7777/tcp
~~~

Add new user for Nextcloud
--------------------------

~~~ bash
useradd --comment Nextcloud --no-create-home --home-dir /var/lib/nextcloud --shell /sbin/nologin --system --add-subids-for-system --user-group nextcloud
mkdir /var/lib/nextcloud
cp /etc/skel/.bash* /var/lib/nextcloud
chown -R nextcloud:nextcloud /var/lib/nextcloud
chmod 0700 /var/lib/nextcloud
loginctl enable-linger nextcloud
~~~

### tmux ###

To administrate the Nextcloud installation, we will run a tmux session in the
background that you can attach to.

~~~ bash
sudo -u nextcloud tmux attach-session -t nc-admin0
~~~

`/var/lib/nextcloud/.config/systemd/user/tmux.service`:

~~~ systemd
[Unit]
Description=Terminal multiplexer
Documentation=man:tmux(1)

[Service]
Type=forking
# TODO: Use socket activation once supported by tmux in Fedora (Fedora 38 will support it).
ExecStart=/usr/bin/tmux new-session -s nc-admin0 -d
ExecStop=/usr/bin/tmux kill-session -t nc-admin0
Restart=always

[Install]
WantedBy=default.target
~~~

~~~ bash
mkdir -p /var/lib/nextcloud/.config/systemd/user/default.target.wants
ln -s /var/lib/nextcloud/.config/systemd/user/tmux.service /var/lib/nextcloud/.config/systemd/user/default.target.wants/tmux.service
~~~

`/var/lib/nextcloud/.tmux.conf`:

~~~ bash
# Required because we configured /sbin/nologin as login shell.
set-option -g default-shell "/bin/bash"

#
## Optional, customizable to meet your own needs
#

bind-key c new-window -c "#{pane_current_path}"
bind-key % split-window -h -c "#{pane_current_path}"
bind-key '"' split-window -v -c "#{pane_current_path}"

set-option -g escape-time 0

bind-key -n M-w select-pane -U
bind-key -n M-a select-pane -L
bind-key -n M-s select-pane -D
bind-key -n M-d select-pane -R
~~~

`/var/lib/nextcloud/.bashrc` additions:

~~~ bash
alias systemctl="systemctl --user"
~~~

Installation
------------

### Volumes ###

~~~ bash
mkdir -p /var/lib/nextcloud/{app,data,caddy-data}
~~~

Because the space on my `/var` was a bit low I moved the data directory to a `/home`.

~~~ bash
mkdir /home/.nextcloud-data
chown nextcloud:nextcloud /home/.nextcloud-data
chmod 0700 /home/.nextcloud-data
ln -s /home/.nextcloud-data/data data
~~~

### Images ###

`caddy-rootless.containerfile`:

~~~ Containerfile
FROM caddy:2

RUN apk --no-cache upgrade \
	&& adduser --home /var/lib/caddy --gecos "Caddy web server" --shell /sbin/nologin --ingroup www-data --system --uid 443 caddy \
	&& chown -R caddy:www-data /config /data

USER caddy
~~~

~~~ bash
podman pull docker.io/library/caddy:2 docker.io/library/nextcloud:26-fpm-alpine
buildah bud -f caddy-rootless.containerfile -t caddy-rootless:2
~~~

### pod ###

~~~ bash
podman pod create --name=nextcloud --hostname=nextcloud --network=slirp4netns:port_handler=slirp4netns -p 7867:80
~~~

### caddy ###

~~~ bash
podman run --detach --replace --pod=nextcloud --name=nextcloud-caddy --log-driver=k8s-file --log-opt=path=/var/lib/nextcloud/logs/caddy.log -v /var/lib/nextcloud/Caddyfile:/etc/caddy/Caddyfile:Z,ro -v /var/lib/nextcloud/caddy-data:/data:Z,U,noexec -v /var/lib/nextcloud/app:/var/www/html:z,ro,noexec --read-only --read-only-tmpfs=false --security-opt=no-new-privileges --cap-drop=ALL --cap-add=CAP_NET_BIND_SERVICE localhost/caddy-rootless:2
~~~

#### Caddyfile ####

<details markdown="1"><summary>Caddyfile (click to expand)</summary>

~~~ Caddyfile
# Global Options
{
	# Uncomment the next line and restart/reload caddy to enable debug logging.
	#debug

	# Disable the admin endpoint.
	admin off

	log {
		format filter {
			wrap console
			fields {
				request>headers>Requesttoken replace "*** REDACTED ***"
			}
		}
	}

	auto_https off
	local_certs
	skip_install_trust
	ocsp_stapling off

	servers {
		trusted_proxies static 10.0.2.2
	}
}

:80 {
	root * /var/www/html

	# Ensure security related headers are always set.
	header {
		?Referrer-Policy no-referrer
		?X-Content-Type-Options nosniff
		?X-Frame-Options SAMEORIGIN
		# TODO: ?X-Permitted-Cross-Domain-Policies none
		?X-Robots-Tag "noindex, nofollow"
		?X-XSS-Protection "1; mode=block"
	}

	# Cache-Control
	@static-resources path *.css *.js *.mjs *.svg *.gif *.png *.jpg *.ico *.wasm *.tflite
	handle @static-resources {
		map {query.v} {immutable} {
			"" ""
			default "immutable"
		}
		header Cache-Control "max-age=15778463, {immutable}"
	}
	@woff path *.woff *.woff2
	header @woff Cache-Control "max-age=604800"

	# /.well-known/ redirects
	redir /.well-known/carddav /remote.php/dav 301
	redir /.well-known/caldav /remote.php/dav 301
	rewrite /.well-known/acme-challenge /index.php?{query}
	rewrite /.well-known/pki-validation /index.php?{query}
	@well-known {
		path /.well-known/*
		not path /.well-known/carddav
		not path /.well-known/caldav
		not path /.well-known/acme-challenge
		not path /.well-known/pki-validation
	}
	redir @well-known /index.php{path}?{query} 301

	@ms-dav {
		header User-Agent DavClnt*
		path /
	}
	redir @ms-dav /remote.php/webdav 302

	php_fastcgi 127.0.0.1:9000 {
		# Pretty URLs
		env front_controller_active true
		# Leaks php version
		header_down -X-Powered-By
	}
	@static-files path /core/* /apps/* /custom_apps/* /resources/* /themes/* /dist/* /index.html /robots.txt
	file_server @static-files
}
~~~

</details>
<br />

### Nextcloud ###

~~~ bash
podman run --detach --replace --pod=nextcloud --name=nextcloud-app --log-driver=k8s-file --log-opt=path=/var/lib/nextcloud/logs/nextcloud.log -v /var/lib/nextcloud/app:/var/www/html:z,noexec -v /var/lib/nextcloud/data:/srv/nextcloud/data:z,noexec --read-only --security-opt=no-new-privileges --cap-drop=all --cap-add=CAP_SETUID,CAP_SETGID,CAP_CHOWN,CAP_DAC_OVERRIDE,CAP_FOWNER docker.io/library/nextcloud:26-fpm-alpine
~~~

~~~ bash
podman exec nextcloud-app chown www-data:www-data /srv/nextcloud/data
~~~

Open `https://192.168.0.3:7777/` in a browser and install Nextcloud.
Use `/srv/nextcloud/data` as your data directory. Afterwards you must/can futher
via `occ`.

~~~ bash
podman exec -i -u www-data nextcloud-app sh <<EOF
php ./occ config:system:set trusted_proxies 0 --value=127.0.0.1

php ./occ config:system:set overwritehost --value=192.168.0.3:7777
php ./occ config:system:set overwriteprotocol --value=https
php ./occ config:system:set overwritewebroot --value=/
php ./occ config:system:set overwrite.cli.url --value=https://192.168.0.3:7777/

php ./occ config:system:set trusted_domains 0 --value=127.0.0.1:7867
php ./occ config:system:set trusted_domains 1 --value=127.0.0.1:7777
php ./occ config:system:set trusted_domains 2 --value=192.168.0.3:7777

# # # # #

php ./occ config:system:set default_phone_region --value=DE

php ./occ config:system:set default_language --value=de_DE
php ./occ config:system:set default_locale --value=de_DE

php ./occ config:app:set richdocuments disable_certificate_verification --value=yes
php ./occ config:app:set password_policy enforceHaveIBeenPwned --value=0
php ./occ config:app:set privacy readableLocation --value=de
php ./occ config:app:set privacy fullDiskEncryptionEnabled --value=1
EOF
~~~

More options can be found at <https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/config_sample_php_parameters.html>.

> The reverse proxy config can also be set from the environment:
>
> - TRUSTED_PROXIES=127.0.0.1
> - OVERWRITEHOST=192.168.0.3:7777
> - OVERWRITEPROTOCOL=https
> - OVERWRITEWEBROOT=/
> - OVERWRITECONDADDR=???
> - OVERWRITECLIURL=https://192.168.0.3:7777/

### Nextcloud (cron) ###

~~~ bash
podman run --detach --replace --pod=nextcloud --name=nextcloud-cron --log-driver=k8s-file --log-opt=path=/var/lib/nextcloud/logs/nextcloud-cron.log -v /var/lib/nextcloud/app:/var/www/html:z,noexec -v /var/lib/nextcloud/data:/srv/nextcloud/data:z,noexec --read-only --security-opt=no-new-privileges --cap-drop=all --cap-add=CAP_SETUID,CAP_SETGID --entrypoint=/cron.sh docker.io/library/nextcloud:26-fpm-alpine
~~~

systemd
-------

To start/restart the pod and containers we will use systemd.

~~~ bash
podman generate systemd --new --files --name nextcloud
mv *.service ~/.config/systemd/user/
systemctl --user daemon-reload
systemctl --user enable nextcloud-backup.service
systemctl --user enable pod-nextcloud.service
~~~

Backup
------

> TODO: This is a grown mess and should be replaced with something better.

`~/backup.sh`:

~~~ bash
#!/bin/bash
set -e

cd "${HOME:=$(getent passwd "$(id -u)" | cut -d: -f6)}"

NOW="$(date --utc --iso-8601=seconds)"


BACKUP_DIR="$HOME/backups"
BACKUP_FILE="$BACKUP_DIR/nextcloud-snapshot-$NOW.tar.zstd"
BACKUP_SOURCES=(./app/ ./Caddyfile ./caddy-data/)

mkdir -p "$BACKUP_DIR"
# TODO: --zstd vs. -I"zstd -T0" vs. -Izstdmt vs. -Ipzstd
podman unshare \
	tar -C"$HOME" --create --zstd --file "$BACKUP_FILE" "${BACKUP_SOURCES[@]}"


DATA_DIR="/home/.nextcloud-data/data"
SNAPSHOT_DIR="/home/.nextcloud-data/snapshots/$NOW"

mkdir -p "$SNAPSHOT_DIR"
podman unshare \
	cp --reflink=always -a "$DATA_DIR" "$SNAPSHOT_DIR"


ln -sTf "$(basename "$BACKUP_FILE")" "$BACKUP_DIR/latest"
ln -sTf "$(basename "$SNAPSHOT_DIR")" "$(dirname "$SNAPSHOT_DIR")/latest"
~~~

> TODO: Are permissions, SELinux labels, timestamps, ... backed up correctly?

`nextcloud-backup.service`:

~~~ systemd
[Unit]
Description=Backup Nextcloud
Wants=pod-nextcloud.service
Before=pod-nextcloud.service
RefuseManualStart=true

[Service]
Type=oneshot
ExecStart=/var/lib/nextcloud/backup.sh

[Install]
RequiredBy=pod-nextcloud.service
~~~

> TODO: Behaviour on `systemctl restart pod-nextcloud`.
> Is the script started? Is Nextcloud not running in that moment?

What's next?
------------

#### Maintainance

 * Keep installation up-to-date by pulling the newest images / rebuilding them.
 * Update Nextcloud image to newer major release before the old one becomes EOL.
 * Backups
 * Regularly check the admin page for new warnings like missing indicies which can be added using
   `podman exec -i -u www-data nextcloud-app php ./occ db:add-missing-indices`.
 * Automatic updates (except major updates)

#### Performance

 * [MariaDB](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#using-mariadb-mysql-instead-of-sqlite)
 * [APCu / Redis / Memcached](https://docs.nextcloud.com/server/latest/admin_manual/configuration_server/caching_configuration.html)
 * [Imaginary](https://docs.nextcloud.com/server/latest/admin_manual/installation/server_tuning.html#previews)

#### Hardening

 * [Disable preview image generation](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#disable-preview-image-generation)
 * [Ensure that your Nextcloud instance is installed in a DMZ](https://docs.nextcloud.com/server/latest/admin_manual/installation/harden_server.html#ensure-that-your-nextcloud-instance-is-installed-in-a-dmz)
 * Configure access logging
 * Customized seccomp profiles for caddy and nextcloud `--security-opt=seccomp=<profile>.json`
 * Limit resource usage by containers: `--cpu-*`, `--device-*`, `--memory`/`--memory-reservation`/`--memory-swap`, `--pids-limit`, experts:`--cgroup-conf=` and `--ulimit`
 * `--security-opt=proc-opts=subset=pid`

#### Features

 * Configure an Email server
 * Install more Apps
 * Setup Nextcloud Office with <abbr title="Collabora Online Development Edition">CODE</abbr> or ONLYOFFICE
 * Look at Nextcloud All-in-One and the stuff it provides like fulltextsearch

---
