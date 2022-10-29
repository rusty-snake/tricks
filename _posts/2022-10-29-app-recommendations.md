---
layout: post
title:  "App Recommendations"
author: "rusty-snake"
#tags:
---

In advance, this list assumes that you use [GrapheneOS](/2022/06/25/grapheneos.html).

- ToC
{:toc}

## App Stores

### Play Store / Aurora Store

If you use Sandboxed Play Services and link your G-account, use the Play Store.
Otherwise you can use the Aurora Store.

{% include app.html
  name = "Aurora Store"
  url = "https://f-droid.org/packages/com.aurora.store/"
  anti_features = "Non-Free Network Services"
  grant = "Install unknown apps with obb access;Enable Storage Scopes;Open links"
  %}

### Neo Store

{% include app.html
  name = "Neo Store"
  url = "https://apt.izzysoft.de/fdroid/index/apk/com.machiav3lli.fdroid"
  grant = "Install unknown apps;Open links"
  %}


#### Settings

- Downloaded APK cache retention: 10
- Auto-sync interval (in minutes): 240
- Package sources:
  - F-Droid
  - Guardian Project Offical Releases
  - IzzyOnDroid F-Droid Repo
  - NewPipe upstream repository

## Browser

### Vanadium

{% include app.html
  name = "Vanadium"
  url = ""
  revoke = "Nearby Devices"
  %}

_Vanadium comes pre-installed with GrapheneOS._

#### Notifications

- Disable Ingocnito notification

#### Settings

- You can disable auto-complete if you don't need it.
  - Privacy and Security > Search and URL completion: Off
- Privacy and Security > Open external links in incognito: On
- `chrome://flags/#cct-incognito`: Enabled
- You can enable app preview in the recently used apps view.<br>
  `chrome://flags/#incognito-screenshot`: Enabled

### Tor Browser for Android

{% include app.html
  name = "Tor Browser for Android"
  url = "https://guardianproject.info/apps/org.torproject.torbrowser/"
  anti_features = "Non-Free Dependencies;Non-Free Network Services"
  %}

## Messenger

### Signal

{% include app.html
  name = "Signal"
  url = "https://signal.org/android/apk/"
  grant = "Media files;Microphone;Camera;Install unkonw apps;Battery usage: Unrestricted"
  revoke = "WLAN control"
  %}

#### Notifications

- Disable Background-connections notification
- Enable Bubbles if you want

#### Settings

- If you saved your PIN in a password-manager, you can disable
  PIN notifications.
- Enable Registration Lock

## Feed Reader

### Feeder

{% include app.html
  name = "Feeder"
  url = "https://f-droid.org/packages/com.nononsenseapps.feeder/"
  %}

#### Settings

- Newslimit: 500

### Read You

{% include app.html
  name = "Read You"
  url = "https://f-droid.org/packages/me.ash.reader/"
  %}

## Authentification

### Aegis

{% include app.html
  name = "Aegis"
  url = "https://f-droid.org/packages/com.beemdevelopment.aegis"
  %}

### KeePassDX

{% include app.html
  name = "KeePassDX"
  url = "https://f-droid.org/packages/com.kunzisoft.keepass.libre/"
  %}

## Gallery

### Aves

{% include app.html
  name = "Aves"
  url = "https://apt.izzysoft.de/fdroid/index/apk/deckers.thibault.aves"
  anti_features = "Non-Free Dependencies;Non-Free Network Services"
  grant = "Photos and Videos"
  %}

### Simple Gallery Pro

I prefer Aves as my gallery, however Simple Gallery Pro has a much better image editor.

{% include app.html
  name = "Simple Gallery Pro"
  url = "https://f-droid.org/packages/com.simplemobiletools.gallery.pro"
  grant = "Photos and Videos"
  %}

## Photo Tools

### ExifEraser

{% include app.html
  name = "ExifEraser"
  url = "https://apt.izzysoft.de/fdroid/index/apk/com.none.tom.exiferaser"
  %}

### PrivacyBlur

{% include app.html
  name = "PrivacyBlur"
  url = "https://f-droid.org/de/packages/de.mathema.privacyblur/"
  grant = "Media files"
  %}

### OCR

{% include app.html
  name = "OCR"
  url = "https://f-droid.org/de/packages/io.github.subhamtyagi.ocr/"
  revoke = "Network"
  %}

Network permission should be remove after initial downloading of
traineddata files.

## Media

### Auxio

Auxio isn't prefect like the Android Media API isn't either. However
it's still one of the better FOSS Audio player I know.

{% include app.html
  name = "Auxio"
  url = "https://f-droid.org/packages/org.oxycblt.auxio/"
  grant = "Music and Audio"
  %}

### NewPipe

{% include app.html
  name = "NewPipe"
  url = "https://newpipe.net/#download"
  anti_features = "Non-Free Network Services"
  grant = "Open links"
  %}

### URL Radio

Actually URL Radio is very buggy and I need to find a better app for radio streaming.

{% include app.html
  name = "URL Radio"
  url = "https://apt.izzysoft.de/fdroid/index/apk/com.jamal2367.urlradio"
  %}

### Seal

{% include app.html
  name = "Seal"
  url = "https://f-droid.org/packages/com.junkfood.seal/"
  %}

### VLC

{% include app.html
  name = "VLC"
  url = "https://f-droid.org/packages/org.videolan.vlc"
  grant = "Media files"
  revoke = "Network;Nearby devices"
  %}

### Zapp

{% include app.html
  name = "Zapp"
  url = "https://f-droid.org/packages/de.christinecoenen.code.zapp/"
  %}

## Calendar

### Etar

{% include app.html
  name = "Etar"
  url = "https://f-droid.org/packages/ws.xsoh.etar/"
  grant = "Calendar;Battery usage: Unrestricted"
  %}

### ICSx<sup>5</sup>

{% include app.html
  name = "ICSx<sup>5</sup>"
  url = "https://f-droid.org/packages/at.bitfire.icsdroid/"
  grant = "Calendar"
  %}

### DAVx<sup>5</sup>

{% include app.html
  name = "DAVx<sup>5</sup>"
  url = "https://f-droid.org/packages/at.bitfire.davdroid/"
  grant = "Calendar"
  %}

### Simple Calendar Pro

There are no good FOSS Android Calendar Apps, so you have to use Etar or Simple Calendar Pro.

{% include app.html
  name = "Simple Calendar Pro"
  url = "https://f-droid.org/packages/com.simplemobiletools.calendar.pro/"
  grant = "Calendar"
  %}

## Notes, Tasks and Reminders

Other Notes/Tasks/Reminder apps worth looking at:

- Notally
- Simple Notes Pro
- Joplin
- Standart Notes
- Pocket Plan
- Fokus
- lists
- Notes (PFA)
- Todo List (PFA)
- Pinnit

### Quillnote

{% include app.html
  name = "Quillnote"
  url = "https://f-droid.org/de/packages/org.qosp.notes/"
  revoke = "Network"
  %}

Unmaintained, so sad.

## Maps

### Organic Maps

{% include app.html
  name = "Organic Maps"
  url = "https://f-droid.org/de/packages/app.organicmaps/"
  grant = "Location"
  %}

#### Settings

- 3D Buildings: Off
- Show on lockscreen: Off

### GMaps WV

{% include app.html
  name = "GMaps WV"
  url = "https://f-droid.org/de/packages/us.spotco.maps/"
  anti_features = "Non-Free Network Services"
  %}

## Utils

### apps_Packages Info - Updated ApplicationsInfos (<sup>2</sup>

Not really needed anymore.

{% include app.html
  name = "apps_Packages Info - Updated ApplicationsInfos (<sup>2</sup>"
  url = "https://f-droid.org/packages/com.oF2pks.applicationsinfo/"
  %}

### Atomic

{% include app.html
  name = "Atomic"
  url = "https://apt.izzysoft.de/fdroid/index/apk/com.jlindemann.science"
  revoke = "Network"
  %}

### Bubble

{% include app.html
  name = "Bubble"
  url = "https://f-droid.org/packages/org.woheller69.level/"
  grant = "Sensors"
  %}

### Compass

{% include app.html
  name = "Compass"
  url = "https://f-droid.org/packages/com.bobek.compass/"
  grant = "Sensors"
  %}

### CPU Info

{% include app.html
  name = "CPU Info"
  url = "https://f-droid.org/packages/com.kgurgul.cpuinfo/"
  grant = "Sensors"
  revoke = "Network"
  %}

### Flashy

{% include app.html
  name = "Flashy"
  url = "https://f-droid.org/packages/rocks.poopjournal.flashy/"
  %}

### PCAPdroid

{% include app.html
  name = "PCAPdroid"
  url = "https://f-droid.org/packages/com.emanuelef.remote_capture/"
  %}

### Port Authority

{% include app.html
  name = "Port Authority"
  url = "https://f-droid.org/packages/com.aaronjwood.portauthority/"
  grant = ""
  revoke = ""
  %}

### Randomix - Decision Maker

{% include app.html
  name = "Randomix - Decision Maker"
  url = "https://f-droid.org/packages/com.minar.randomix/"
  %}

### Saber

{% include app.html
  name = "Saber"
  url = "https://f-droid.org/packages/com.adilhanney.saber/"
  revoke = "Network"
  %}

### Sky Map

{% include app.html
  name = "Sky Map"
  url = "https://f-droid.org/packages/com.google.android.stardroid/"
  grant = "Sensors"
  revoke = "Network"
  %}

### WiFiAnalyzer

{% include app.html
  name = "WiFiAnalyzer"
  url = "https://f-droid.org/packages/com.vrem.wifianalyzer/"
  grant = "Location"
  %}

{::comment}
Add it back when they fixed the F-Droid build.
### Exodus
<https://f-droid.org/packages/org.eu.exodus_privacy.exodusprivacy/>
{:/comment}

### More apps

- <https://android.izzysoft.de/articles/named/list-of-fdroid-repos>
- <https://android.izzysoft.de/applists.php>
