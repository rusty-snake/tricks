---
layout: post
title: "Disable any resolv.conf handling of NetworkManager"
author: "rusty-snake"
#tags:
---

`/etc/NetworkManager/NetworkManager.conf`:

~~~ ini
[main]
# Do not mess with the global DNS Setup
dns=default
rc-manager=unmanaged
systemd-resolved=false
~~~
