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
  grant = "Install unknown apps"
  %}

### Play Store / Aurora Store

If you use Sandboxed Play Services and link your G-account, use the Play Store.
Otherwise you can use the Aurora Store.

{% include app.html
  name = "Aurora Store"
  app_id = "com.aurora.store"
  url = "https://gitlab.com/AuroraOSS/AuroraStore"
  available_in = "Obtainium"
  grant = "Install unknown apps with obb access;Enable Storage Scopes;Open links"
  %}

### Neo Store

{% include app.html
  name = "Neo Store"
  app_id = "com.machiav3lli.fdroid"
  url = "https://github.com/NeoApplications/Neo-Store"
  available_in = "Obtainium, IzzyOnDroid"
  grant = "Install unknown apps;Open links"
  %}

#### Settings

- Package sources:
  - F-Droid
    - I recommend against using Apps distributed via F-Droid,
      see https://privsec.dev/posts/android/f-droid-security-issues/.
      This source is used to discover apps. You can then install them with Obtainium.
  - IzzyOnDroid F-Droid Repo
  - NewPipe upstream repository
  - Collabora Office F-Droid Repo

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
Brave Schutz & Datenschutz > Verbindungen auf HTTPS upgraden: Alle Verbindungen müssen HTTPS verwenden (streng)
Brave Schutz & Datenschutz > Skripte blockieren: An
Brave Schutz & Datenschutz > Fingerprinting blockieren: streng
Brave Schutz & Datenschutz > Fingerprinting über die Spracheinstellungen verhindern: Aus
Brave Schutz & Datenschutz > Vergiss mich, wenn ich diese Seite schließe: An
Brave Schutz & Datenschutz > Daten beim Beenden löschen: An
Brave Schutz & Datenschutz > Social Media Blocking: Alles Aus
Brave Schutz & Datenschutz > YouTube: Alles An
Brave Schutz & Datenschutz > WebRTC-IP-Nutzungsrichtlinien: Nicht-proxisiertes UDP deaktivieren
Brave Schutz & Datenschutz > Websites die Abfrage gespeicherter Zahlungsinformationen erlauben: Aus
Brave Schutz & Datenschutz > Unaufhaltsame Domains: Aus
Brave Schutz & Datenschutz > Ethereum Name Service: Aus
Brave Schutz & Datenschutz > Solana Name Service: Aus
Brave Schutz & Datenschutz > IPFS-Gateway: Aus
Brave Schutz & Datenschutz > Cookie-Einwilligungshinweise blockieren: An
Brave Schutz & Datenschutz > Registerkarten beim Beenden schließen: An
Brave Schutz & Datenschutz > Ping der täglichen Nutzung automatisch an Brave senden: Aus
Brave Schutz & Datenschutz > Wichtigste Websites in Autovervollständigung anzeigen: Aus
Brave Wallet > Web3-Benachrichtigungen anzeigen: Aus
Startseite: Aus
Downloads > Benachrichtigung über den Download-Fortschritt anzeigen: An
Downloads > Wenn möglich automatisch öffnen: Aus
Hintergrundwiedergabe: An
Darstellung > Brave-Belohnungen-Symbol in der Adressleite anzeigen: Aus
*Alle standard verknüpfungen auf der Neuer-Tab-Seite löschen*
Neuer-Tab-Seite > Hintergrundbildanzeigen: Aus
Neuer-Tab-Seite > Gesponsorte Bilder anzeigen: Aus
Neuer-Tab-Seite > Die führenden Seiten anzeigen: Aus
Zahlungsmethoden > Zahlungsmethoden speichern und ausfüllen: Aus
Adressen > Adressen speichern und ausfüllen: Aus

{::comment}
TODO: Initial connections
{:/comment}

While brave has good defaults for privacy, it frequently fails in security on
basic things like 64bit builds, Site Isolation or disabling Javascript-JIT.
Site Isolation can be tweaked to match vanadiums settings

- chrome://flags/#enable-site-pre-process
- chrome://flags/#strict-origin-isolation

### Tor Browser for Android

{% include app.html
  name = "Tor Browser for Android"
  app_id = "org.torproject.torbrowser"
  url = "https://www.torproject.org/download/#android"
  available_in = "Obtainium (HTML), FFUpdater"
  %}

Second URL (maybe better for Obtainium): <https://dist.torproject.org/torbrowser/>

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

### Nextcloud Talk

{% include app.html
  name = "Talk"
  app_id = "com.nextcloud.talk2"
  url = "https://github.com/nextcloud/talk-android"
  available_in = "Obtainium"
  %}

## Feed Reader

### Feeder

{% include app.html
  name = "Feeder"
  app_id = "com.nononsenseapps.feeder"
  url = "https://github.com/spacecowboy/Feeder"
  available_in = "Obtainium"
  %}

#### Settings

- Newslimit: 500

### Read You

{% include app.html
  name = "Read You"
  app_id = "me.ash.reader"
  url = "https://github.com/Ashinch/ReadYou"
  available_in = "Obtainium"
  %}

### News

{% include app.html
  name = "News"
  app_id = "co.appreactor.news"
  url = "https://github.com/bubelov/news"
  available_in = "Obtainium"
  %}

## Authentification

### Aegis

{% include app.html
  name = "Aegis"
  app_id = "com.beemdevelopment.aegis"
  url = "https://github.com/beemdevelopment/Aegis"
  available_in = "Obtainium"
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
  app_id = "com.kunzisoft.keepass.free OR com.kunzisoft.keepass.libre"
  url = "https://github.com/Kunzisoft/KeePassDX"
  available_in = "Obtainium"
  %}

## Gallery

### Aves

{% include app.html
  name = "Aves"
  url = "https://accrescent.app/app/deckers.thibault.aves"
  available_in = "Accrescent, Obtainium, IzzyOnDroid"
  grant = "Photos and Videos; Sensors"
  %}

### Gallery

{% include app.html
  name = "Gallery"
  app_id = "com.dot.gallery"
  url = "https://github.com/IacobIonut01/Gallery"
  available_in = "Obtainium"
  grant = "Photos and Videos;Enable Storage Scope"
  %}

## Photo Tools

### ExifEraser

{% include app.html
  name = "ExifEraser"
  app_id = "com.none.tom.exiferaser"
  url = "https://accrescent.app/app/com.none.tom.exiferaser"
  available_in = "Accrescent, Obtainium, IzzyOnDroid"
  %}

### Image Toolbox (Resizer)

{% include app.html
  name = "Image Toolbox (Resizer)"
  app_id = "ru.tech.imageresizershrinker"
  url = "https://github.com/T8RIN/ImageResizer"
  available_in = "Obtainium"
  %}

- Settings > About the App > Check for Updates: Off

### Watermarking

{% include app.html
  name = "Watermarking"
  app_id = "io.github.freewatermark.mobileapp"
  url = "https://github.com/free-watermark/mobile-app"
  available_in = "Obtainium"
  %}

## Media

### Auxio

Auxio isn't prefect like the Android Media API isn't either. However
it's still one of the better FOSS Audio player I know.

{% include app.html
  name = "Auxio"
  url = "https://github.com/OxygenCobalt/Auxio"
  available_in = "Obtainium"
  grant = "Music and Audio"
  %}

### InnerTune

{% include app.html
  name = "InnerTune"
  app_id = "com.zionhuang.music"
  url = "https://github.com/z-huang/InnerTune"
  available_in = "Obtainium"
  %}

### Just Player

{% include app.html
  name = "Just Player"
  app_id = "com.brouken.player"
  url = "https://github.com/moneytoo/Player"
  available_in = "Obtainium"
  %}

### LibreTube

{% include app.html
  name = "LibreTube"
  app_id = "com.github.libretube"
  url = "https://github.com/libre-tube/LibreTube"
  available_in = "Obtainium"
  grant = "Open links"
  %}

### NewPipe

{% include app.html
  name = "NewPipe"
  url = "https://newpipe.net/#download"
  available_in = "NewPipe upstream repository"
  grant = "Open links"
  %}

### URL Radio

{% include app.html
  name = "URL Radio"
  app_id = "com.jamal2367.urlradio"
  url = "https://github.com/jamal2362/URL-Radio"
  available_in = "Obtainium"
  %}

### Seal

{% include app.html
  name = "Seal"
  url = "https://github.com/JunkFood02/Seal"
  %}

- Settings > About > Automatic updates: Off

### ViMusic

{% include app.html
  name = "ViMusic"
  app_id = "it.vfsfitvnm.vimusic"
  url = "https://github.com/vfsfitvnm/ViMusic"
  available_in = "Obtainium"
  %}

### VLC

{% include app.html
  name = "VLC"
  app_id = "org.videolan.vlc"
  url = "https://www.videolan.org/vlc/download-android.html"
  available_in = "Obtainium (VLC)"
  grant = "Enable Storage Scope"
  %}

### Zapp

{% include app.html
  name = "Zapp"
  app_id = "de.christinecoenen.code.zapp"
  url = "https://github.com/mediathekview/zapp"
  available_in = "Obtainium"
  %}

## Office / Documents

### Collabora Office

{% include app.html
  name = "Collabora Office"
  app_id = "com.collabora.libreoffice"
  url = "https://www.collaboraoffice.com/collabora-office-android-ios/"
  available_in = "Collabora Office F-Droid Repo"
  grant = "Enable Storage Scope"
  %}

### PDF Doc Scan

{% include app.html
  name = "PDF Doc Scan"
  app_id = "com.littletrickster.scanner"
  url = "https://github.com/LittleTrickster/PDF-Doc-Scan"
  available_in = "Obtainium"
  %}

## File-Sharing

### Nextcloud

{% include app.html
  name = "Nextcloud"
  app_id = "com.nextcloud.client"
  url = "https://github.com/nextcloud/android"
  available_in = "Obtainium"
  grant = "Enable Storage Scope"
  %}

### QRServ

{% include app.html
  name = "QRServ"
  app_id = "dev.uint.qrserv"
  url = "https://github.com/uintdev/qrserv"
  available_in = "Obtainium"
  %}

## Calendar

### Fossify Calendar

{% include app.html
  name = "Calendar"
  app_id = "org.fossify.calendar"
  url = "https://github.com/FossifyOrg/Calendar"
  available_in = "Obtainium"
  grant = "Calendar"
  %}

### ICSx<sup>5</sup>

{% include app.html
  name = "ICSx<sup>5</sup>"
  app_id = "at.bitfire.icsdroid"
  url = "https://github.com/bitfireAT/icsx5"
  available_in = "Obtainium"
  grant = "Calendar"
  %}

### DAVx<sup>5</sup>

{% include app.html
  name = "DAVx<sup>5</sup>"
  app_id = "at.bitfire.davdroid"
  url = "https://github.com/bitfireAT/davx5-ose"
  available_in = "Obtainium"
  grant = "Calendar"
  %}

## Notes, Tasks and Reminders

There are hundreds with different features, usage, UI, ...

### Doable

{% include app.html
  name = "Doable"
  app_id = "at.flobii.doable"
  url = "https://codeberg.org/florian-obernberger/flutter-doable"
  available_in = "Obtainium"
  %}

## Maps

### Organic Maps

{% include app.html
  name = "Organic Maps"
  app_id = "app.organicmaps"
  url = "https://github.com/organicmaps/organicmaps"
  available_in = "Obtainium"
  grant = "Location"
  %}

#### Settings

- Show on lockscreen: Off

## Utils

### BeauTyXT

{% include app.html
  name = "BeauTyXT"
  app_id = "dev.soupslurpr.beautyxt"
  url = "https://beautyxt.soupslurpr.dev/"
  available_in = "Accrescent, Obtainium"
  %}

### FlashDim

{% include app.html
  name = "FlashDim"
  app_id = "com.cyb3rko.flashdim"
  url = "https://github.com/cyb3rko/flashdim"
  available_in = "Obtainium"
  %}

### Flashlight Tiramisu

{% include app.html
  name = "Flashlight Tiramisu"
  app_id = "com.pdb82.flashlighttiramisu"
  url = "https://github.com/polodarb/Flashlight-Tiramisu"
  available_in = "Obtainium"
  %}

### Flashy

{% include app.html
  name = "Flashy"
  app_id = "rocks.poopjournal.flashy"
  url = "https://github.com/Crazy-Marvin/Flashy"
  available_in = "Obtainium"
  %}

### Kompass

{% include app.html
  name = "Kompass"
  app_id = "com.bobek.compass"
  url = "https://github.com/Kr0oked/Compass"
  available_in = "Obtainium"
  grant = "Sensors"
  %}

### Randomix - Decision Maker

{% include app.html
  name = "Randomix - Decision Maker"
  app_id = "com.minar.randomix"
  url = "https://github.com/m-i-n-a-r/randomix"
  available_in = "Obtainium"
  %}

### Record You

{% include app.html
  name = "Record You"
  app_id = "com.bnyro.recorder"
  url = "https://github.com/Bnyro/RecordYou"
  available_in = "Obtainium"
  grant = "Microphone"
  %}

### Sayboard

{% include app.html
  name = "Sayboard"
  app_id = "com.elishaazaria.sayboard"
  url = "https://github.com/ElishaAz/Sayboard"
  available_in = "Obtainium"
  grant = "Microphone"
  %}

## Nerd utils

### Alga

{% include app.html
  name = "Alga"
  app_id = "tech.laihz.alga.arm64"
  url = "https://github.com/laiiihz/alga"
  available_in = "Obtainium"
  %}

### apps_Packages Info - Updated ApplicationsInfos (<sup>2</sup>

{% include app.html
  name = "apps_Packages Info - Updated ApplicationsInfos (<sup>2</sup>"
  app_id = "com.oF2pks.applicationsinfo"
  url = "https://f-droid.org/packages/com.oF2pks.applicationsinfo/"
  available_in = "F-Droid"
  %}

### Exodus

{% include app.html
  name = "Exodus"
  app_id = "org.eu.exodus_privacy.exodusprivacy"
  url = "https://github.com/Exodus-Privacy/exodus-android-app"
  %}

### PCAPdroid

{% include app.html
  name = "PCAPdroid"
  app_id = "com.emanuelef.remote_capture"
  url = "https://github.com/emanuele-f/PCAPdroid"
  available_in = "Obtainium"
  %}

### WiFiAnalyzer

{% include app.html
  name = "WiFiAnalyzer"
  app_id = "com.vrem.wifianalyzer"
  url = "https://github.com/VREMSoftwareDevelopment/WifiAnalyzer"
  available_in = "Obtainium"
  grant = "Location"
  %}

## Calculator

The calculator app that comes with GrapheneOS is fine unless you need a more
fancy looking one or one that can convert units.

### Calculator-inator

{% include app.html
  name = "Calculator-inator"
  app_id = "com.inator.calculator"
  url = "https://github.com/prathameshmm02/calculator-inator"
  available_in = "Obtainium"
  revoke = "Network"
  %}

### Mint Calculator

{% include app.html
  name = "Mint Calculator"
  app_id = "bored.codebyk.mintcalc"
  url = "https://github.com/boredcodebyk/mintcalc"
  available_in = "Obtainium"
  %}

### Unitto

{% include app.html
  name = "Unitto"
  app_id = "com.sadellie.unitto"
  url = "https://github.com/sadellie/unitto"
  available_in = "Obtainium"
  %}

<br>

Last update: 2024-01-06
