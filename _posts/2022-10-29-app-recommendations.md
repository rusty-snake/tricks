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
  app_id = "app.accrescent.client"
  url = "https://accrescent.app/"
  available_in = "Accrescent (Initial sideload from Website)"
  grant = "Install unknown apps;Battery usage: Unrestricted"
  %}

#### Settings

- Material You: On

### Play Store / Aurora Store

If you use Sandboxed Play Services and link your G-account, use the Play Store.
Otherwise you can use the Aurora Store.

{% include app.html
  name = "Aurora Store"
  app_id = "com.aurora.store"
  url = "https://gitlab.com/AuroraOSS/AuroraStore"
  available_in = "Obtainium, F-Droid"
  grant = "Install unknown apps with obb access;Enable Storage Scopes;Open links"
  %}

### Neo Store

{% include app.html
  name = "Neo Store"
  app_id = "com.machiav3lli.fdroid"
  url = "https://github.com/NeoApplications/Neo-Store"
  available_in = "IzzyOnDroid, F-Droid"
  grant = "Install unknown apps;Open links"
  %}

#### Settings

- Downloaded APK cache retention: 10
- Auto-sync interval (in minutes): 240
- Package sources:
  - F-Droid
  - IzzyOnDroid F-Droid Repo
  - NewPipe upstream repository

### Obtainium

{% include app.html
  name = "Obtainium"
  app_id = "dev.imranr.obtainium"
  url = "https://github.com/ImranR98/Obtainium"
  available_in = "Obtainium, IzzyOnDroid"
  grant = "Install unknown apps"
  %}

## Browser

### Vanadium

{% include app.html
  name = "Vanadium"
  app_id = ""
  url = ""
  available_in = "<i>Preinstalled in GrapheneOS</i>"
  revoke = "Nearby Devices"
  %}

#### Notifications

- Disable Ingocnito notification

#### Settings

- You can disable auto-complete if you don't need it.
  - Privacy and Security > Search and URL completion: Off
- Privacy and Security > Open external links in incognito: On
- `chrome://flags/#cct-incognito`: Enabled
- You can enable app preview in the recently used apps view.<br>
  `chrome://flags/#incognito-screenshot`: Enabled

### Brave

{% include app.html
  name = "Brave"
  app_id = "com.brave.browser"
  url = "https://github.com/brave/brave-browser"
  available_in = "Obtainium, FFUpdater"
  %}

#### Settings

Brave Schutz & Datenschutz > Tracker & Werbung blockieren: aggresiv
Brave Schutz & Datenschutz > Immer sichere Verbindungen verwenden: An
Brave Schutz & Datenschutz > Skripte blockieren: An
Brave Schutz & Datenschutz > Fingerprinting blockieren: streng
Brave Schutz & Datenschutz > Daten beim Beenden löschen: An
Brave Schutz & Datenschutz > Social Media Blocking: Alles abwählen
Brave Schutz & Datenschutz > WebRTC-IP-Nutzungsrichtlinien: Nicht-proxisiertes UDP deaktivieren
Brave Schutz & Datenschutz > Cookie-Einwilligungshinweise blockieren: An
Brave Schutz & Datenschutz > Registerkarten beim Beenden schließen: An
Brave Schutz & Datenschutz > Ping der täglichen Nutzung automatisch an Brave senden: Aus
Brave Schutz & Datenschutz > Wichtigste Websites in Autovervollständigung anzeigen: Aus
Startseite: Aus
Privatsphärebericht: An
Downloads > Benachrichtigung über den Download-Fortschritt anzeigen: An
Hintergrundwiedergabe: An
Darstellung > Brave-Belohnungen-Symbol in der Adressleite anzeigen: Aus
Neuer-Tab-Seite > Hintergrundbildanzeigen: Aus
Neuer-Tab-Seite > Gesponsorte Bilder anzeigen: Aus
Neuer-Tab-Seite > Die führenden Seiten anzeigen: Aus

### Tor Browser for Android

{% include app.html
  name = "Tor Browser for Android"
  app_id = "org.torproject.torbrowser"
  url = "https://www.torproject.org/download/#android"
  available_in = "Obtainium (HTML), FFUpdater, Website"
  %}

## Messenger

### Signal

{% include app.html
  name = "Signal"
  app_id = "org.thoughtcrime.securesms"
  url = "https://signal.org/android/apk/"
  available_in = "Website (self-updating apk)"
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
  app_id = "com.nononsenseapps.feeder"
  url = "https://f-droid.org/packages/com.nononsenseapps.feeder/"
  available_in = ""
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
  available_in = "Obtainium, F-Droid"
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
  app_id = "com.kunzisoft.keepass.free"
  url = "https://f-droid.org/packages/com.kunzisoft.keepass.libre/"
  %}

## Gallery

### Aves

{% include app.html
  name = "Aves"
  url = "https://accrescent.app/app/deckers.thibault.aves"
  available_in = "Accrescent, Obtainium, IzzyOnDroid, F-Droid"
  grant = "Photos and Videos"
  %}

### Simple Gallery Pro

I prefer Aves as my gallery, however Simple Gallery Pro has a much better image editor.

{% include app.html
  name = "Simple Gallery Pro"
  url = "https://f-droid.org/packages/com.simplemobiletools.gallery.pro"
  available_in = "F-Droid"
  grant = "Photos and Videos"
  %}

## Photo Tools

### ExifEraser

{% include app.html
  name = "ExifEraser"
  app_id = "com.none.tom.exiferaser"
  url = "https://accrescent.app/app/com.none.tom.exiferaser"
  available_in = "Accrescent, IzzyOnDroid"
  %}

### PrivacyBlur

> XXX TODO maintaince

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

### SuperImage

{% include app.html
  name = "SuperImage"
  app_id = "com.zhenxiang.superimage"
  url = "https://github.com/Lucchetto/SuperImage"
  available_in = "Obtainium, F-Droid"
  %}

### Image Resizer

{% include app.html
  name = "Image Resizer"
  app_id = "ru.tech.imageresizershrinker"
  url = "https://github.com/T8RIN/ImageResizer"
  available_in = "Obtainium, F-Droid"
  %}

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
  app_id = "com.github.libretube"
  url = "https://f-droid.org/packages/com.github.libretube/"
  grant = "Open links"
  available_in = "Obtainium, F-Droid"
  %}

### NewPipe

{% include app.html
  name = "NewPipe"
  url = "https://newpipe.net/#download"
  grant = "Open links"
  available_in = "NewPipe upstream repository"
  %}

### URL Radio

Actually URL Radio is very buggy and I need to find a better app for radio streaming.

{% include app.html
  name = "URL Radio"
  app_id = "com.jamal2367.urlradio"
  url = "https://github.com/jamal2362/URL-Radio"
  available_in = "Obtainium"
  %}

### Seal

{% include app.html
  name = "Seal"
  url = "https://f-droid.org/packages/com.junkfood.seal/"
  %}

### VLC

{% include app.html
  name = "VLC"
  app_id = "org.videolan.vlc"
  url = "https://f-droid.org/packages/org.videolan.vlc"
  available_in = "F-Droid"
  grant = "Media files"
  revoke = "Network;Nearby devices"
  %}

### Zapp

{% include app.html
  name = "Zapp"
  app_id = "de.christinecoenen.code.zapp"
  url = "https://f-droid.org/packages/de.christinecoenen.code.zapp/"
  available_in = "Obtainium, F-Droid"
  %}

## File-Sharing

### Nextcloud

{% include app.html
  name = "Nextcloud"
  app_id = "com.nextcloud.client"
  url = "https://github.com/nextcloud/android"
  available_in = "Obtainium, F-Droid, Website"
  grant = "Enable Storage Scope"
  %}

## Calendar

### Simple Calendar Pro

{% include app.html
  name = "Simple Calendar Pro"
  app_id = "com.simplemobiletools.calendar.pro"
  url = "https://f-droid.org/packages/com.simplemobiletools.calendar.pro/"
  available_in = "F-Droid"
  grant = "Calendar"
  %}

### Etar

{% include app.html
  name = "Etar"
  app_id = "ws.xsoh.etar"
  url = "https://f-droid.org/packages/ws.xsoh.etar/"
  grant = "Calendar;Battery usage: Unrestricted"
  %}

### ICSx<sup>5</sup>

{% include app.html
  name = "ICSx<sup>5</sup>"
  app_id = "at.bitfire.icsdroid"
  url = "https://f-droid.org/packages/at.bitfire.icsdroid/"
  grant = "Calendar"
  %}

### DAVx<sup>5</sup>

{% include app.html
  name = "DAVx<sup>5</sup>"
  app_id = "at.bitfire.davdroid"
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

- Tasky (com.thatsmanmeet.tasky)
- sNotz (com.sunilpaulmathew.snotz)

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
  app_id = "app.organicmaps"
  url = "https://f-droid.org/packages/app.organicmaps/"
  grant = "Location"
  %}

#### Settings

- 3D Buildings: Off
- Show on lockscreen: Off

### GMaps WV

{% include app.html
  name = "GMaps WV"
  app_id = "us.spotco.maps"
  url = "https://f-droid.org/packages/us.spotco.maps/"
  available_in = "F-Droid"
  %}

## Utils

### apps_Packages Info - Updated ApplicationsInfos (<sup>2</sup>

Not really needed anymore.

{% include app.html
  name = "apps_Packages Info - Updated ApplicationsInfos (<sup>2</sup>"
  app_id = "com.oF2pks.applicationsinfo"
  url = "https://f-droid.org/packages/com.oF2pks.applicationsinfo/"
  available_in = "F-Droid"
  %}

### Atomic

{% include app.html
  name = "Atomic"
  app_id = "com.jlindemann.science"
  url = "https://apt.izzysoft.de/fdroid/index/apk/com.jlindemann.science"
  available_in = "IzzyOnDroid"
  revoke = "Network"
  %}

### Bubble

{% include app.html
  name = "Bubble"
  app_id = "org.woheller69.level"
  url = "https://f-droid.org/packages/org.woheller69.level/"
  available_in = "F-Droid"
  grant = "Sensors"
  %}

### Compass

{% include app.html
  name = "Compass"
  app_id = "com.bobek.compass"
  url = "https://f-droid.org/packages/com.bobek.compass/"
  available_in = "F-Droid"
  grant = "Sensors"
  %}

### Compass

{% include app.html
  name = "Compass"
  app_id = "dev.synapsetech.compass"
  url = "https://github.com/SynapseTech/Compass"
  available_in = "IzzyOnDroid"
  grant = "Sensors"
  %}

### CPU Info

{% include app.html
  name = "CPU Info"
  app_id = "com.kgurgul.cpuinfo"
  url = "https://github.com/kamgurgul/cpu-info"
  available_in = "Obtainium, F-Droid"
  grant = "Sensors"
  revoke = "Network"
  %}

### FlashDim

{% include app.html
  name = "FlashDim"
  app_id = "com.cyb3rko.flashdim"
  url = "https://f-droid.org/packages/com.cyb3rko.flashdim/"
  %}

### Flashlight Tiramisu

{% include app.html
  name = "Flashlight Tiramisu"
  app_id = "com.pdb82.flashlighttiramisu"
  url = "https://f-droid.org/packages/com.pdb82.flashlighttiramisu"
  %}

### Flashy

{% include app.html
  name = "Flashy"
  app_id = "rocks.poopjournal.flashy"
  url = "https://f-droid.org/packages/rocks.poopjournal.flashy/"
  %}

### Exodus

{% include app.html
  name = "Exodus"
  app_id = "org.eu.exodus_privacy.exodusprivacy"
  url = "https://f-droid.org/packages/org.eu.exodus_privacy.exodusprivacy/"
  %}

### PCAPdroid

{% include app.html
  name = "PCAPdroid"
  app_id = "com.emanuelef.remote_capture"
  url = "https://f-droid.org/packages/com.emanuelef.remote_capture/"
  %}

### Port Authority

{% include app.html
  name = "Port Authority"
  app_id = "com.aaronjwood.portauthority"
  url = "https://f-droid.org/packages/com.aaronjwood.portauthority/"
  %}

### Randomix - Decision Maker

{% include app.html
  name = "Randomix - Decision Maker"
  app_id = "com.minar.randomix"
  url = "https://f-droid.org/packages/com.minar.randomix/"
  %}

### Saber

{% include app.html
  name = "Saber"
  app_id = "com.adilhanney.saber"
  url = "https://f-droid.org/packages/com.adilhanney.saber/"
  revoke = "Network"
  %}

### Sky Map

{% include app.html
  name = "Sky Map"
  app_id = "com.google.android.stardroid"
  url = "https://f-droid.org/packages/com.google.android.stardroid/"
  grant = "Sensors"
  revoke = "Network"
  %}

### WiFiAnalyzer

{% include app.html
  name = "WiFiAnalyzer"
  app_id = "com.vrem.wifianalyzer"
  url = "https://f-droid.org/packages/com.vrem.wifianalyzer/"
  grant = "Location"
  %}

### Watermarking

{% include app.html
  name = "Watermarking"
  app_id = "io.github.freewatermark.mobileapp"
  url = "https://github.com/free-watermark/mobile-app"
  available_in = "Obtainium"
  %}

## Calculator

XXX TODO GrapheneOS

### OpenCalc

{% include app.html
  name = "OpenCalc"
  app_id = "com.darkempire78.opencalculator"
  url = "https://github.com/Darkempire78/OpenCalc"
  available_in = "Obtainium, F-Droid"
  %}

### Calculator-inator

{% include app.html
  name = "Calculator-inator"
  app_id = "com.inator.calculator"
  url = "https://github.com/prathameshmm02/calculator-inator"
  available_in = "Obtainium, F-Droid"
  revoke = "Network"
  %}

<br>

Last update: 2023-03-25
