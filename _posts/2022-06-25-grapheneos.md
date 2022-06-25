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
- Apps: TODO
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
- System > user profiles: TODO
- Do not include private data in your device name.
  - About the Phone > Device name

<p></p>

- You can disable auto-complete in Vanadium if you don't need it.
  - Privacy and Security > Search and URL completion: Off

## F-Droid

Go to <https://f-droid.org/>, download F-Droid, verify it using gpg¹,
transfer it to your phone, install it and update it.

¹ TODO: Add an explanation of how this is done.

### Additional Repositories

- [IzzyOnDroid F-Droid Repo](https://apt.izzysoft.de/fdroid/)
  ```
  https://apt.izzysoft.de/fdroid/repo/?fingerprint=3BF0D6ABFEAE2F401707B6D966BE743BF0EEE49C2561B9BA39073711F628937A
  ```
- [NewPipe upstream repository](https://newpipe.net/#download)
  ```
  https://archive.newpipe.net/fdroid/repo/?fingerprint=E2402C78F9B97C6C89E97DB914A2751FDA1D02FE2039CC0897A462BDB57E7501
  ```
- [Bromite official F-Droid repository](https://www.bromite.org/fdroid)
  ```
  https://fdroid.bromite.org/fdroid/repo/?fingerprint=E1EE5CD076D7B0DC84CB2B45FB78B86DF2EB39A3B6C56BA3DC292A5E0C3B9504
  ```

### Apps

Some apps to get started with.

#### NewPipe

<https://newpipe.net/#download>

#### Aegis

<https://f-droid.org/packages/com.beemdevelopment.aegis>

#### KeePassDX

<https://f-droid.org/packages/com.kunzisoft.keepass.libre/>

#### Bromite

<https://www.bromite.org/fdroid>

Suggested settings:

- Privacy and Security > Expire history days threshold: _duration_
- Privacy and Security > Incognito-mode > Always open links in incognito: On
- Privacy and Security > Open external links in incognito: On

#### Signal

<https://signal.org/android/apk/>

#### Aurora Store

<https://f-droid.org/packages/com.aurora.store/>

#### Exodus

<https://f-droid.org/packages/org.eu.exodus_privacy.exodusprivacy/>

#### Etar

<https://f-droid.org/packages/ws.xsoh.etar/>

#### OpenTasks

<https://f-droid.org/packages/org.dmfs.tasks/>

#### Joplin

<https://apt.izzysoft.de/fdroid/index/apk/net.cozic.joplin>

#### Simple Mobile Tools

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
