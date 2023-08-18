---
layout: post
title:  "GrapheneOS"
author: "rusty-snake"
#tags:
---

## Installation

Just follow the official guide at <https://grapheneos.org/install/>.

If you use the Web installer use a classic installation of your browser instead
of flatpaks or the like.  Consider also to run it without an external sandbox
like firejail.

To enable non-root flashing with a distribution other than Arch Linux/Debian
based, you can directly install the source of the `android-udev` packet from
Arch Linux as long as your system isn't too exotic:

~~~ bash
git clone https://github.com/M0Rf30/android-udev-rules.git
cd android-udev-rules

sudo install -Dm0644 51-android.rules /etc/udev/rules.d/51-android.rules
sudo install -Dm0644 android-udev.conf /etc/sysusers.d/android-udev.conf
sudo systemd-sysusers
sudo gpasswd -a "$(whoami)" adbusers
reboot
~~~

## Settings

- Use a **secure PIN** (or password).
- You can easily setup system-wide ad-blocking by using an ad-blocking DNS.
  An overview of good DNS can be found at <https://www.privacyguides.org/dns/#recommended-providers>.
  - Network & Internet > Private DNS: _Server of your choice_
- If you don't need the connectivity check you can disable it.
  - Network & Internet > Internet connectivity check: Disable
- Wireless features are a security and privacy risk and consume energy so you're
  better off disabling them when they're not in use.
  Bluetooth and NFC are disabled by default in GrapheneOS.
  - Network & Internet > Internet > WLAN: Off
  - Connected Devices > Connection settings > Bluetooth: Off
  - Connected Devices > Connection settings > NFC: Off
  - Network & Internet > Internet > Network Settings > Turn off Wi-Fi automatically: 15sec
  - Connected Devices > Bluetooth timeout: 15sec
- Cellular network can be hardened.
  - Network & Internet > SIM-Card > Prefered Nettype: LTE-only
  - Network & Internet > SIM-Card > 2G: Off
- WiFi calling can be enabled (contract dependent).
  - Network & Internet > SIM-Card > WLAN-Telefonie
- If you want you can enable Auto reboot.
  - Security > Auto reboot: _duration_
- You can further hardening USB security by always denying USB accessories if
  you want.
  - Security > USB accessories: Deny
- Unless one of your apps requires it, you should disable native code debugging
  (ptrace).
  - Security > Enable native code debugging: Off
- Security > PIN scrambling: On
- Camera and Microphone can be disable by default, if an app wants to use them
  you will be asked to enable them.
  - Privacy > Camera: Off
  - Privacy > Microphone: Off
- There are not that much apps that require Sensors permission, using a whitelist
  rather than a blacklist managment for it makes really sense.
  - Privacy > Allow Sensors permission to apps by default: Off
- Disable position services.
  - Position: Off
  - Position > Services > WLAN Search: Off
  - Position > Services > Bluetooth Search: Off
  - Secure User Plane Location: Disabled
- Not security/privacy relevant but really handy.
  - System > Gestures and Moves > One hand mode: On
  - Notifications > Allow snooze for notifications: On
- Enable Material You if you want.
  - Styles & Wallpapers > Use wallpaper colors: On
- To catch "hidden" or short-living notifications, you should enable notifications
  histroy and review it.
  - Notifications > Notifications histroy: On
- Enable app pining.
  - Security > More Security settings > App pining: On
- Do not include private data in your device name.
  - About the Phone > Device name

### Settings in new user profiles

- Benachrichtigungen > Benachrichtigungsverlauf: On
- Display > Automatische Helligkeit: Off
- Display > Sperrbildschirm > Beim Hochheben Display aktivieren: Off
- Sicherheit > Scramble PIN input layout: On
- Datenschutz > Allow Sensors permission by default: Off
- Vanadium > Einstellungen > Datenschutz und Sicherheit > Open external links in incognito: On

## Apps

See [App Recommendations](/2022/10/29/app-recommendations.html).

---

_Last update: 2023-08-18_
