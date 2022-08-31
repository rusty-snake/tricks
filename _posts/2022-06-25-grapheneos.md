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

```bash
git clone https://github.com/M0Rf30/android-udev-rules.git
cd android-udev-rules

sudo install -Dm0644 51-android.rules /etc/udev/rules.d/51-android.rules
sudo install -Dm0644 android-udev.conf /etc/sysusers.d/android-udev.conf
sudo systemd-sysusers
sudo gpasswd -a "$(whoami)" adbusers
reboot
```

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
- Disable position services.
  - Position: Off
  - Position > Services > WLAN Search: Off
  - Position > Services > Bluetooth Search: Off
- Not security/privacy relevant but really handy.
  - System > Gestures and Moves > One hand mode: On
  - Notifications > Allow snooze for notifications: On
- Enable Material You if you want.
  - Styles & Wallpapers > Use wallpsper colors: On
- To catch "hidden" or short-living notifications, you should enable notifications
  histroy and review it.
  - Notifications > Notifications histroy: On
- Enable app pining.
  - Security > More Security settings > App pining: On
- System > user profiles: TODO
- Do not include private data in your device name.
  - About the Phone > Device name


## F-Droid

> _TODO: Use Neo Store here._

Go to <https://f-droid.org/>, download F-Droid, verify it using gpg¹,
transfer it to your phone, install it and update it.

¹ TODO: Add an explanation of how this is done.

### Additional Repositories

- Guardian Project Offical Releases
- [IzzyOnDroid F-Droid Repo](https://apt.izzysoft.de/fdroid/)
  ```
  https://apt.izzysoft.de/fdroid/repo/?fingerprint=3BF0D6ABFEAE2F401707B6D966BE743BF0EEE49C2561B9BA39073711F628937A
  ```
- [NewPipe upstream repository](https://newpipe.net/#download)
  ```
  https://archive.newpipe.net/fdroid/repo/?fingerprint=E2402C78F9B97C6C89E97DB914A2751FDA1D02FE2039CC0897A462BDB57E7501
  ```
- DivestOS Official

## Apps

Some apps to get started with.

### Vanadium

_Vanadium comes pre-installed with GrapheneOS._

#### Permissions

##### Remove

- Nearby Devices

#### Notifications

- Disable Ingocnito notification

#### Settings

- You can disable auto-complete if you don't need it.
  - Privacy and Security > Search and URL completion: Off
- Privacy and Security > Open external links in incognito: On
- You can enable app preview in the recently used apps view.<br>
  `chrome://flags/#incognito-screenshot`: Enabled

### Neo Store

<https://apt.izzysoft.de/fdroid/index/apk/com.machiav3lli.fdroid>

#### Permissions

##### Grant

- Install unknown apps
- Open links

#### Settings

- Downloaded APK cache retention: 10
- Auto-sync interval (in minutes): 240

### Aurora Store

<https://f-droid.org/packages/com.aurora.store/>

#### Permissions

- Install unknown apps with obb access
- Enable Storage Scopes
- Open links

### apps_Packages Info - Updated ApplicationsInfos (<sup>2</sup>

<https://f-droid.org/packages/com.oF2pks.applicationsinfo/>

### Exodus

<https://f-droid.org/packages/org.eu.exodus_privacy.exodusprivacy/>

### PCAPdroid

<https://f-droid.org/packages/com.emanuelef.remote_capture/>

### Signal

<https://signal.org/android/apk/>

#### Permissions

##### Grant

- Media files
- Microphone (or always ask if you're paranoid)
- Camera (or always ask if you're paranoid)
- Install unkonw apps
- Battery usage: Unrestricted

##### Remove

- WLAN control

#### Notifications

- Disable Background-connections notification
- Enable Bubbles if you want

### Aegis

<https://f-droid.org/packages/com.beemdevelopment.aegis>

### KeePassDX

<https://f-droid.org/packages/com.kunzisoft.keepass.libre/>

### Tor Browser for Android

<https://guardianproject.info/apps/org.torproject.torbrowser/>

#### Permissions

##### Remove

- Sensors

### Feeder

<https://f-droid.org/packages/com.nononsenseapps.feeder/>

### Etar

<https://f-droid.org/packages/ws.xsoh.etar/>

#### Permissions

##### Grant

- Calendar
- Battery usage: Unrestricted

### ICSx<sup>5</sup>

<https://f-droid.org/packages/at.bitfire.icsdroid/>

#### Permissions

##### Grant

- Calendar

### DAVx<sup>5</sup>

<https://f-droid.org/packages/at.bitfire.davdroid/>

#### Permissions

##### Grant

- Calendar

### OpenTasks

<https://f-droid.org/packages/org.dmfs.tasks/>

#### Permissions

##### Grant

- Battery usage: Unrestricted

### Quillnote

<https://f-droid.org/de/packages/org.qosp.notes/>

#### Permissions

##### Remove

- Network

### ExifEraser

<https://apt.izzysoft.de/fdroid/index/apk/com.none.tom.exiferaser>

### PrivacyBlur

<https://f-droid.org/de/packages/de.mathema.privacyblur/>

#### Permissions

##### Grant

- Media files

### OCR

<https://f-droid.org/de/packages/io.github.subhamtyagi.ocr/>

#### Permissions

##### Remove

- Network
  After initial downloading of traineddata files.

### NewPipe

<https://newpipe.net/#download>

#### Permissions

##### Grant

- Open links

### URL Radio

<https://apt.izzysoft.de/fdroid/index/apk/com.jamal2367.urlradio>

### VLC

<https://f-droid.org/packages/org.videolan.vlc>

#### Permission

##### Grant

- Media files

##### Remove

- Network
- Nearby devices

### Zapp

<https://f-droid.org/packages/de.christinecoenen.code.zapp/>

### Organic Maps

<https://f-droid.org/de/packages/app.organicmaps/>

#### Permissions

##### Grant

- Location

#### Settings

- 3D Buildings: Off
- Show on lockscreen: Off

### GMaps WV

<https://f-droid.org/de/packages/us.spotco.maps/>

### Compass

<https://f-droid.org/packages/com.bobek.compass/>

### CPU Info

<https://f-droid.org/packages/com.kgurgul.cpuinfo/>

#### Permissions

##### Remove

- Network

### Atomic

<https://apt.izzysoft.de/fdroid/index/apk/com.jlindemann.science>

#### Permissions

##### Remove

- Network

### Randomix - Decision Maker

<https://f-droid.org/packages/com.minar.randomix/>

### Simple Mobile Tools

- [Simple App Launcher](https://f-droid.org/packages/com.simplemobiletools.applauncher/)
- [Simple Calculator](https://f-droid.org/packages/com.simplemobiletools.calculator/)
- [Simple Calendar Pro](https://f-droid.org/packages/com.simplemobiletools.calendar.pro/)
- [Simple Camera](https://f-droid.org/packages/com.simplemobiletools.camera/)
- [Simple Clock](https://f-droid.org/packages/com.simplemobiletools.clock/)
- [Simple Contacts Pro](https://f-droid.org/packages/com.simplemobiletools.contacts.pro/)
- [Simple Dialer](https://f-droid.org/packages/com.simplemobiletools.dialer/)
- [Simple Draw Pro](https://f-droid.org/packages/com.simplemobiletools.draw.pro/)
- [Simple File Manager Pro](https://f-droid.org/packages/com.simplemobiletools.filemanager.pro/)
- [Simple Flashlight](https://f-droid.org/packages/com.simplemobiletools.flashlight/)
- [Simple Gallery Pro](https://f-droid.org/packages/com.simplemobiletools.gallery.pro/)
  <br> Note: I only see disadvantages compared to Secure Camera (the Camera app that comes with GrapheneOS).
- [Simple Keyboard](https://f-droid.org/packages/com.simplemobiletools.keyboard/)
  <br> Note: Keyboards are a very sensitive topic, it is best to stick with the AOSP keyboard.
- [Simple Music Player](https://f-droid.org/packages/com.simplemobiletools.musicplayer/)
- [Simple Notes Pro](https://f-droid.org/packages/com.simplemobiletools.notes.pro/)
- [Simple SMS Messenger](https://f-droid.org/packages/com.simplemobiletools.smsmessenger/)
- [Simple Voice Recorder](https://f-droid.org/packages/com.simplemobiletools.voicerecorder/)

### Clock

_Pre-installed_

#### Notifications

- Disable Upcomming alarms notification

### Telefon

_Pre-installed_

#### Permissions

_TODO_

### SMS/MMS

_Pre-installed_

#### Permissions

_TODO_

### More apps

- <https://android.izzysoft.de/articles/named/list-of-fdroid-repos>
- <https://android.izzysoft.de/applists.php>

---

_Last update: 2022-08-31_
