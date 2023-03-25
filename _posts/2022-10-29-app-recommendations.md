---
layout: post
title: "App Recommendations"
author: "rusty-snake"
#tags:
---

In advance, this list assumes that you use [GrapheneOS](/2022/06/25/grapheneos.html).

- ToC
{:toc}

## App Stores

### Accrescent

{% include app.html
  name = "Accrescent"
  url = "https://accrescent.app/"
  grant = "Install unknown apps"
  %}

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
  url = "https://www.torproject.org/download/#android"
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
- Enable Message Backup

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

#### Settings

- Appearance > Theme: System default (AMOLED)
- Behaviour > Highlight token when tapped: On
- Behaviour > Freeze tokens when tapped: On
- Security > Tap to reveal: On
- Backups > Automatically back up vault: On
- Backups > Participate in Adnroid's backup system: On

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
  url = "https://f-droid.org/packages/de.mathema.privacyblur/"
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

### LibreTube

{% include app.html
  name = "LibreTube"
  url = "https://f-droid.org/packages/com.github.libretube/"
  anti_features = "Non-Free Network Services"
  grant = "Open links"
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

### Simple Calendar Pro

{% include app.html
  name = "Simple Calendar Pro"
  url = "https://f-droid.org/packages/com.simplemobiletools.calendar.pro/"
  grant = "Calendar"
  %}

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

| App | Notes | Task Lists | Reminders | Voice Notes | Markdown | Attachments | Material You | Dark Mode | Seedvault | Anti-Features & Permissions | Maintaince |
| --- | ----- | ---------- | --------- | ----------- | -------- | ----------- | ------------ | --------- | --------- | --------------------------- | ---------- |
| Another notes app<br><sup><code>com.maltaisn.notes.sync</code></sup> | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | - | only (critical) bugs *but got material you* |
| D Note<br><sup><code>com.mahmoudrh.roomxml</code></sup> | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | ✅ | - | n/a |
| Fokus<br><sup><code>com.isaiahvonrundstedt.fokus</code></sup> | ❌ | ✅ | ✅ | ❌ | ❌ | ✅ | ❌ | ✅ | ❌ | - | n/a |
| Ionic Notes<br><sup><code>kurxz.github.io</code></sup> | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | Always on | ✅ | - | n/a |
| Joplin<br><sup><code>net.cozic.joplin</code></sup> | ✅ | ✅ | ✅ | ❌ | ✅ | ✅ | ❌ | Experimental | ❌ | Location Permission | n/a |
| lists<br><sup><code>com.example.lists</code></sup> | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | - | n/a |
| Markor<br><sup><code>net.gsanter.markor</code></sup> | ✅ | ✅ | ❌ | ✅ | ✅ wb | ✅ | ❌ | ✅ | ✅ | storage TODO | n/a |
| My Brain<br><sup><code>com.mhss.app.mybrain</code></sup> | ✅ | ✅ | ✅ | ❌ | ✅ | ❌ | ❌ | ✅ | ✅ | - | n/a |
| NoNonsense Notes<br><sup><code>com.nononsenseapps.notepad</code></sup> | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ not synced with system; black | ✅ | - | n/a |
| Notally<br><sup><code>com.omgodse.notally</code></sup> | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | - | n/a |
| Note<br><sup><code>github.ck1412.noteApp</code></sup> | ❌ | ❌ | ❌ | ❌ | ✅ images only | ❌ | Always on | ✅ | - | n/a |
| Notely<br><sup><code>com.davenet.notely</code></sup> | ✅ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | - | n/a |
| Notes (PFA)<br><sup><code>org.secuso.privacyfriendlynotes</code></sup> | ✅ | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | - | n/a |
| Notesnook<br><sup><code>com.streetwriters.notesnook</code></sup> | ✅ | ❌ | ❌ | ❌ | ✅ wb | ✅ | ❌ | ✅ black | ❌ | Unfree dependencies | n/a |
| Noto<br><sup><code>com.noto</code></sup> | ✅ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | - | n/a |
| Orgzly<br><sup><code>com.orgzly</code></sup> | ✅ | ✅ | ✅ | ❌ | ✅ | ❌ | ✅ | ✅ black | ✅ | - | n/a |
| Pinnit<br><sup><code>dev.sasikanth.pinnit</code></sup> | ✅ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | - | n/a |
| PocketPlan<br><sup><code>com.pocket_plan.j7_003</code></sup> | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | - | n/a |
| Quillnote<br><sup><code>org.qosp.quillnote</code></sup> | ✅ | ✅ | ✅ | ✅ | ✅wb | ✅ | ❌ | ✅black | ✅ | - | dead |
| Quillpad<br><sup><code>io.github.quillpad</code></sup> | ✅ | ✅ | ✅ | ✅ | ✅wb | ✅ | ❌ | ✅black | ✅ | - | yes |
| Simple Material Notes<br><sup><code>com.rafapps.simplenotes</code></sup> | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | - | n/a |
| Simple Notes Pro<br><sup><code>com.simplemobiletools.notes.pro</code></sup> | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ✅ | ✅ | - | n/a |
| SimpleReminder<br><sup><code>felixwiemuth.simplereminder</code></sup> | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | - | n/a |
| Standard Notes<br><sup><code>com.standardnotes</code></sup> | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | - | n/a |
| Tasks.org<br><sup><code>org.tasks</code></sup> | ❌ | ✅ | ✅ | ❌ | ❌ | ✅ | ❌ | ✅ | ✅ | TODO | n/a |
| ToDark<br><sup><code>com.yoshi.todark</code></sup> | ❌ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | - | ✅ | - | n/a |
| To-Do<br><sup><code>com.samuel.todoapp</code></sup> | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | - | n/a |
| Todo List (PFA)<br><sup><code>org.secuso.privacyfriendlytodolist</code></sup> | ❌ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | - | n/a |
| ToDo Manager<br><sup><code>com.github.webierta.todo_manager</code></sup> | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ not synced with system | ✅ | - | n/a |
| Todopad<br><sup><code>com.example.flutter_riverpod_todo_app</code></sup> | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ not synced with system | ✅ | - | n/a |
| Note to Self<br><sup>Signal & Co.</sup> | ☑️ | ❌ | ❌ | ✅ | ❌ | ☑️ | ❌ | ✅ | ❌ | - | n/a |

There are a lot more features to consider that a note in the table like

- Available translation
- Support for Folders/Notebooks
- Pining of Notes
- Labels and Color for Notes
- Setting a priority
- Themed app icon support
- History for Notes
- ...

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

### FlashDim

{% include app.html
  name = "FlashDim"
  url = "https://f-droid.org/packages/com.cyb3rko.flashdim/"
  %}

### Flashlight Tiramisu

{% include app.html
  name = "Flashlight Tiramisu"
  url = "https://f-droid.org/packages/com.pdb82.flashlighttiramisu"
  %}

### Flashy

{% include app.html
  name = "Flashy"
  url = "https://f-droid.org/packages/rocks.poopjournal.flashy/"
  %}

### Exodus

{% include app.html
  name = "Exodus"
  url = "https://f-droid.org/packages/org.eu.exodus_privacy.exodusprivacy/"
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

<br>

Last update: 2023-03-25
