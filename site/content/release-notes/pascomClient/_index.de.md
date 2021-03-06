---
title: pascom Client
description: pascom bietet native Clients für Windows, MacOS, Linux, iOS und Android
weight: 990
---

{{% notice tip %}}
Für weitere Informationen zu unserem pascom Client finden Sie in unserer ausführliche [Client-Dokumentation]({{< ref "/clients" >}}).
{{%/notice%}}

## What's New
 
{{< youtube cnSuDvVzl5Q >}}

## Wichtige Änderungen

{{% notice changes %}}  
In diesem Abschnitt geben wir Ihnen einen Überblick aller wichtigen Änderungen im pascom Client
{{% /notice %}}

* Kompatibilität zu pascom 16 und älter wurde eingestellt. Ältere Client Versionen finden Sie in unserem [Release-Archiv](https://www.pascom.net/de/downloads/#release-archive).
* Der pascom macOS Client setzt jetzt mindestens macOS 10.12 voraus

## Bekannte Probleme

{{% notice issues %}}
Diese Probleme sind uns bekannt und wir arbeiten bereits an einer Lösung  
{{% /notice %}}

* [CL-1071] Plantronics Support ist auf einigen Systemen instabil. Falls im Zusammenspiel mit einem Plantronics Headset der Client oft abstürzt, in den Einstellungen Plantronics auf “ignorieren” stellen. Nur die Nutzung von Headset-Tasten funktioniert dann nicht mehr
* [CL-1165] Outlook Support ist auf einigen Systemen instabil und führt zu Abstürzen des pascom Clients
* [CL-1191] Manche Endpoint-Protection Software (z. B. Kaspersky) verhindert bestimmten Aktionen des pascom Clients, z. b. Autostart-Konfiguration oder Mikrofonzugriff
* [CL-1212] Unter macOS lässt sich die Unterstützung für Sennheiser Headsets derzeit nicht einrichten, da HeadSetup seitens EPOS / Sennheiser nicht zum Download zur Verfügung steht


## Release 62.R1061 (20.04.2020)

**Auf einen Blick**

* Unterstützung für Gäste via WebClient mit pascom 19.06R Server.
* Linux: Support für Jabra Headsets.
* Windows/macOS: Der pascom Client kann jetzt gleichzeitig mit Jabra Direct installiert sein.
* Windows/macOS: Stabilität der Jabra-Integration verbessert.
* macOS/Linux/Android/iOS: QOS / TOS Flags für SIP und SRTP werden nun korrekt gesetzt.
* Android: Der Client prüft nun ob die Energiespareinstellungen korrekt konfiguriert sind.
* Android/Xiaomi: Wenn die "Bildschirm-Aufwecken"-Berechtigung auf Xiaomi-Geräten mit MIUI nicht gesetzt ist, erscheint nun eine Warnungmeldung nach dem ersten fehlgeschlagenen Anruf.
* Audioqualität bei Gesprächen über das Softphone, auf allen Plattformen verbessert.
* Windows/macOS/Linux: "dynamisches Scrollen" kann nun deaktiviert werden.
* AEC ist standardmäßig deaktiviert, wenn ein unterstütztes Headset (Jabra, Sennheiser, Plantronics) verwendet wird.
* Acoustic Echo Cancellation (AEC) Einstellungen sind nun konfigurierbar.
* Sowohl pascom Client.exe als auch das Setup haben nun ein gültiges Codesign-Zertifikat.
* Wenn zwei Desktop Clients angemeldet sind, verbleibt die SIP-Registrierung beim zuletzt angemeldeten Client.
* Synchronisierung mit einem pascom19 Server ist schneller und blockiert den Client nicht mehr.
* Behoben: Wenn der pascom Client auf mehreren Geräten verwendet wurde, wurden bereits gelesene Chat-Nachrichten manchmal wieder als ungelesen angezeigt (mit pascom19 Server).

**ÄNDERUNGEN**

* [CL-22] - Hide headset configuration message during login
* [CL-114] - Improved Jabra Headset support (SDK v2)
* [CL-540] - Cursor stays in input mode
* [CL-542] - Implement QOS / TOS support in client
* [CL-583] - Disable background-clicking in settings
* [CL-629] - Apple Call Kit Overlay won't work for iOS client
* [CL-633] - Right click menu glitches
* [CL-643] - Show a hint if the android client is not on the "Battery Whitelist"
* [CL-762] - Support iOS13 SDK and Remote Notification pushes in iOS
* [CL-847] - Allow to disable / reduce scroll inertia
* [CL-1007] - Implement a "Detail overlay" for (error) toast messages on mobile
* [CL-1024] - Support Public Groups and Guests in pascom Client
* [CL-1054] - Remove unread messages of deleted user (sender)
* [CL-1059] - Scrolling glitches on mobile clients
* [CL-1082] - Disable tooltips on mobile client
* [CL-1085] - Content entered in the chat input is lost if you put the app into the background
* [CL-1093] - You can click through the resync screen
* [CL-1099] - Yellow stated user should also be visible if filter is 'online'
* [CL-1110] - App does not open if you tap on a missed call notification on android
* [CL-1111] - Android app doesn't handle vendor specific additional permissions correctly
* [CL-1115] - Sennheiser Headset treats forwarded calls incorrectly
* [CL-1134] - Follow me settings are out of box on mobile if config is blocked by admin
* [CL-1135] - Client does not notify me if i do not have a usable phone
* [CL-1144] - Show "audio only" users in group details and stream list
* [CL-1146] - Optimize AEC and Gain Parameters
* [CL-1156] - pascom Client sometimes crashes when rescanning video devices on Windows
* [CL-1162] - User entered content is not properly filtered, and will be treated as html
* [CL-1167] - pascom Client checks for updates too often
* [CL-1173] - Pickup to a queue with Jabra Headset results in a hangup of the picked call
* [CL-1174] - Can't change selected audio device after start up
* [CL-1180] - Client steals sip registration if two desktop clients are online
* [CL-1181] - Link buttons on blue background are hard to read
* [CL-1186] - Message ordering is wrong if you send a message in a group chat
* [CL-1188] - Handle aspect-ratio changes in the video stream correctly
* [CL-1191] - Additionally sign pascom Client.exe, not only setup
* [CL-1193] - Clean chat history on discardEvent
* [CL-1198] - Invalid Displayed marker is sent to server
* [CL-1203] - Group vanishes if you star and unstar it
* [CL-1204] - Sometimes, video is hidden in client for no apparent reason
* [CL-1206] - Missing camera device in settings after startup sometimes
* [CL-1208] - Better Interactivity with incremental handling of Events
* [CL-1213] - utf-8 error when loading gstreamer plugins
* [CL-1215] - Client shows "You need to assign a number to the device in order to dial" error
* [CL-1219] - Close video fullscreen mode if the last video stream stops
* [CL-1225] - Client crashes during datev import
* [CL-1231] - Client displays "login failed" before actually logging in
* [CL-1235] - iOS App doesn't play notification sound if a message is received via push
* [CL-1240] - Broken translation for HeadsetToast
* [CL-1242] - Client shows notifications for displayed or already acknowledged messages
* [CL-1255] - Message content is not visible in push notification


## Release 61.R919 (19.02.2020)

**Auf einen Blick**

- Im Betriebssystem konfigurierte Http-Proxies werden nun beim Update berücksichtigt.
- Automatische Updates können nun in den erweiterten Einstellungen deaktiviert werden.
- Filtern der Kontaktliste ist jetzt zuverlässiger, es werden keine Zeichen mehr doppelt eingegeben.
- Android: Eingehende Anrufe werden nun in einem optimierten Bildschirm dargestellt um Fehlbedienungen zu vermeiden.
- Android/iOS: Die Freisprech-Funktion ist nun zuverlässiger und “lauter”.
- Android: Die App wacht jetzt zuverlässiger auf, bei eingehenden Anrufen.
- Android: Umschalten auf Freisprechen funktioniert nun wieder.
- Lautstärke des Softphones auf allen Plattformen angehoben.
- Echo-Cancelling (AEC) bei Anrufen und Freisprechen verbessert.
- Automatische-Gain-Anpassung (AGC) abgeschaltet.
- SIP-Re-Registrierung auf Mobilgeräten beschleunigt.

**ÄNDERUNGEN:**

* [CL-94] - Proper http proxy support in pascom Client
* [CL-370] - Weird behaviour if recording stops
* [CL-534] - Disable menu buttons if we already are in the correct view
* [CL-564] - Always set MODE_IN_COMMUNICATION for AudioManager
* [CL-686] - Disable automatic updates via "Advanced Settings"
* [CL-693] - Improve logging of client proxy
* [CL-729] - Introduce chat inline notifications
* [CL-839] - Disable proxymity sensor when handsfree speaker is active
* [CL-879] - Correctly handle pushed messages on iOS and Android
* [CL-894] - Show group chat message origin in android and ios notification
* [CL-909] - Hide away (yellow) user state on pascom 19
* [CL-928] - Switching to handsfree speaker doesn't work
* [CL-971] - Prohibit to open empty settings on mobile during pairing process
* [CL-950] - Save outgoing message immediately to the database
* [CL-980] - pascom Client looses characters when typing into the roster filter
* [CL-994] - Bring back redial function on dial button
* [CL-998] - Resolve caller number of local (DATEV) phone book in pickup notifications
* [CL-1004] - Do not resynchronize on every server version change
* [CL-1006] - Implement a special incoming call screen on android
* [CL-1018] - Check for microphone access is broken on windows
* [CL-1019] - Re-Implement alert() / request attention feature in desktop client
* [CL-1031] - Client crashes on shutdown on macOS in pjsip libDestroy()
* [CL-1040] - Crash in WinnotificationController::findToastFromHistory()
* [CL-1044] - TAPI doesn't immediately use changed preferred device
* [CL-1047] - You can't use Escape to close the settings screen
* [CL-1061] - Switch NSIS installer to Unicode
* [CL-1068] - Hover for outlook settings button 'add' vanishes text
* [CL-1074] - Change status text after switching focus
* [CL-1078] - Fix macOS 10.15 notarization
* [CL-1079] - An active redirection is not shown in the roster anymore
* [CL-1080] - Don't change position of filtered roster (sorted by name) after presence change
* [CL-1081] - Crash in MdTonePlayer::stop() on android
* [CL-1084] - Back button does not work correctly on android
* [CL-1086] - User chat is opened instead of group chat when clicking on a group notification
* [CL-1089] - Mobile apps shows sip connection error message after wakeup
* [CL-1090] - Handsfree speaker is not correctly handled if gain increase is disabled
* [CL-1102] - android pascom Client sometimes does not wake up to calls
* [CL-1104] - Gain increase doesn't work on certain ios devices
* [CL-1106] - Use Connection Service Switch is missing from the Advanced Settings on android
* [CL-1114] - Changing roster sort broken
* [CL-1116] - libgstqtvideo is searched in wrong path on android armv7 (32bit)
* [CL-1120] - Improve echo cancellation and audio quality in pascom Client
* [CL-1140] - Client always shows resync screen after login
* [CL-1142] - WebCam stream leaks and crashes Client if usb monitor is restared while a stream is running


## Release 60.R872 (13.01.2020)

**Auf einen Blick**

- Wenn das Softphone die Verbindung verliert, registriert es sich wieder deutlich schneller.
- Die Kontaktliste kann nun wieder nach den Server konfigurierten Rollen gefiltert werden.
- Linux: Der Client verbraucht nicht mehr 100% CPU nach einem Telefonat auf Ubuntu ab 18.10. (Known Issue CL-1002)
- Linux: Die Auswahl von Audiogeräten zeigt nun leserliche Namen und funktioniert wieder. (Known Issue CL-491)
- Linux: Kompatibilität zu verschiedenen Linux Distributionen / Versionen verbessert.
- Windows: Native Benachrichtungen sind zuverlässiger. (Known Issues CL-1009)
- Windows: Der Client startet nun automatisch beim Systemstart. (Option in den Client Einstellungen und bei der Installation)
- Android: Connection-Service Implementation verbessert. (Known Issues CL-957)
- iOS: Amtspräfix wird nun nicht mehr vor der Rufnummer gezeigt, bei einem eingehenden Anruf. (Known Issues CL-800)

**ÄNDERUNGEN:**

* [CL-357] - Client doesn't remember pdf watcher folder after closing settings
* [CL-394] - Inconsistent behavior for adding a call
* [CL-426] - Speedup client installation time on windows
* [CL-431] - Improve registration of softphone after instance/xmpp restart
* [CL-491] - pascom Client shows wrong audio devices on Linux
* [CL-585] - Ask user if setup should create autostart link on windows
* [CL-676] - Client crashes on older Nvidia GPUs during QSGDefaultDistanceFieldGlyphCache creation
* [CL-677] - Client crashes on older ATI / AMD GPUs during QOpenGLContext destructor
* [CL-688] - Wrong device used for team pickup
* [CL-755] - Implement hardened runtime / sandboxing in pascom Client until 2020
* [CL-783] - Automate Upload to the iOS App Store
* [CL-793] - Speed up Settings Screen
* [CL-800] - iOS client shows trunk prefix in call push notification
* [CL-871] - Only show applicable Rendering Modes on MacOS/Linux Clients
* [CL-891] - Smart Filters, Milestone 1 - Filter Roles
* [CL-906] - Apple phonebook contact not populated after switching to settings
* [CL-911] - Open 'join group' info from group details
* [CL-917] - Mark phonebookentry as favorite broken
* [CL-919] - Store pin in groupparticipant table
* [CL-932] - Improve Android Connection Service Integration
* [CL-947] - Match different ringing icons
* [CL-951] - Impossible to invite newly created user into the group
* [CL-952] - Improve client resynchronisation logic
* [CL-957] - Sometimes, a connection service screen shows up despite self managed is enabled
* [CL-967] - Custom status not immediately visible
* [CL-972] - MdSoftphone::findCall(PhonecallPtr) breaks mute and handsfree feature
* [CL-978] - Client requests prohibited contacts
* [CL-982] - Can't copy phonebook contact to private phonebook if added to group before
* [CL-986] - Update to Qt 5.12.6
* [CL-987] - Include type in monitor init transfer
* [CL-991] - Call list layout broken
* [CL-992] - Details of favorite phone book contact not updated
* [CL-993] - Bring back details and chat in ringing screen
* [CL-995] - Message counter wrong in group edgecase
* [CL-1001] - Windows native notification shows group avatar
* [CL-1002] - Linux Client freeze/high-cpu after each call starting from ubuntu 18.10
* [CL-1003] - Fix phonebook UI glitches on mobile clients
* [CL-1005] - Fix fpic and other build problems on modern linux systems
* [CL-1009] - Problems with Windows Notification Center
* [CL-1012] - Roster not shown after new log in 
* [CL-1016] - Client settings partly broken
* [CL-1017] - Linux client crashes on startup
* [CL-1020] - Crash due to invalid read in winFileTransfer notification
* [CL-1023] - Linux: Check which system libraries should be used
* [CL-1028] - Chat view is broken if you put the app into background and bring it back again
* [CL-1032] - Windows native notification not shown for missed voicemail call
* [CL-1045] - Ringback tone during call on mobile
* [CL-1046] - Auto sending of fax setting disabled after client restart
* [CL-1053] - Can't add favorite contact to group 
* [CL-1055] - Client crashes when there is no matching ContactFactory
* [CL-1057] - Logout or restart causes problems with smart filter in roster
* [CL-1060] - NSIS 3.05 breaks pascom client setup script
* [CL-1066] - Name of phonebook contact missing in group overview
* [CL-1069] - Sound for incoming message is played multiple times in a row
* [CL-1070] - Client allows to add phonebook contacts to 'removed' groups 
* [CL-1075] - Open android phonebook entry is broken


## Release 59.R726 (26.11.2019)

**Auf einen Blick**

- Die Favoriten werden mit pascom 17 / 18 Servern wieder korrekt angezeigt
- Chat-Nachrichten werden bei pascom 17 / 18 Servern nicht mehr mehrfach angezeigt
- Der Client verbindet sich schneller zu pascom 17 und 18 Servern
- Die Telefonbuch Listenansicht enthält jetzt wieder Icons, um direkt eine Rufnummer zu wählen
- Chat-Nachrichten werden auf pascom 19 Servern nicht mehr mehrfach angezeigt
- Gruppenchats zeigen jetzt den Avatar des Absenders an

**ÄNDERUNGEN:**

* [CL-853] - Introduce a refresh button on the contactlist
* [CL-913] - Roster contacts slowly shown on mobiles with pascom 17 and pascom18
* [CL-925] - No phonebook details visible after adding phonebook contact to group
* [CL-933] - Improve contact search provider
* [CL-943] - "filtered" message not shown when text filter is active 
* [CL-944] - Active smart filter + click on message indicator makes strange things
* [CL-949] - Respect XDG Specification in linux create-starter.sh
* [CL-953] - Improve Toast Messages after login
* [CL-962] - Fax via phone book contact not correctly working
* [CL-964] - Improve Phonebook list view cells
* [CL-970] - Pascom 19: The same chat message is shown multiple times in a notification 
* [CL-973] - Missing call buttons  if renderer mode is 'software'
* [CL-976] - Avatar is missing in notification
* [CL-983] - The same chat message is shown multiple times in a notification on pascom 17 / 18 (again)
* [CL-984] - pascom Client crashes after startup


## Release 58.R676 (07.11.2019)

**Auf einen Blick**

- Die Icons in den Details eines Telefonbucheintrages können wieder zum Wählen angeklickt werden
- Avatare flackern nicht mehr, wenn ein Smart Filter gesetzt ist
- Chat-Nachrichten werden nicht mehr mehrfach angezeigt (pascom 17 / 18 Server)
- Seltenen Crash beim Empfangen einer Chat-Nachricht behoben
- Pickup Benachrichtigungen aus Teams zeigen wieder korrekte Informationen an

**ÄNDERUNGEN:** 

- [CL-905] - Wrong datev icon size 
- [CL-923] - Hide 'Add to group' button if phonebook entry is in edit mode
- [CL-934] - Do not show video buttons in a external 1:1 phonecall
- [CL-935] - Renaming a group is tricky
- [CL-936] - Group + Icon missing when starting with empty user directory 
- [CL-937] - You can't click on a phone number within phonebook entry details to dial it
- [CL-938] - Speed up Avatar Displaying, avoid flickering images
- [CL-939] - If you pair a mobile, your avatar is sometimes broken
- [CL-940] - Native windows notifications still flicker sometimes
- [CL-948] - Pickup notification doesn't show team information anymore and it's not possible to pickup a team
- [CL-955] - Integrate User Feedback 
- [CL-958] - Client crashes with a stackoverflow when receiving a chat message
- [CL-968] - Pascom 18: The same chat message is shown multiple times in a notification
- [CL-969] - pascom Client does not ring in background on android 10 (again)


## Release 57.R661 (30.10.2019)

{{% notice note %}}
Bei diesem Release gibt es keine eigene Client-Version, da die Änderungen nur die Mobile iOS-Applikation betrifft.
{{% /notice %}}

**Auf einen Blick**

- iOS Anruf Problem in Verbindung mit pascom 18 Server behoben.

**ÄNDERUNGEN:** 

- [CL-942] - iOS App can't phone with a pascom 18 server

## Release 56.R659 (29.10.2019)

**Auf einen Blick**
 
- Kontaktliste neu gestaltet
- Chat UI überarbeitet
- Suchbildschirm verbessert
- Android: Connection Service integriert, dies ermöglicht u. a. Anrufsteuerung via Headset und im Auto
- Android 10 kompatibilität
- Android 6.0 oder neuer erforderlich
 
**Im Zusammenspiel mit einem pascom19 Server außerdem:**  

- Video-Anrufe
- Flexible permanente Gruppenchats, Anrufe und Videokonferenzen
 
**ÄNDERUNGEN:**
 
- [CL-921] - Sometimes deleted contacts show up in the contactlist
- [CL-895] - Emoticon Keyboard is broken on iOS 13
- [CL-882] - Answer a call in a car does not work on android
- [CL-816] - Use native notifications by default on windows
- [CL-809] - iOS somtimes continues ringing after push
- [CL-807] -  Android client does not hang up softphone call if a gsm call is already running
- [CL-792] -  Auto update doesn't work sometimes on macOS
- [CL-763] -  Be compatible to Android 9 privacy settings
- [CL-751] -  pascom Client does not ring in background on android 10
- [CL-748] -  pascom Client compatibility to iOS 13
- [CL-728] -  Broken timestamp formatting on iOS/Android journal
- [CL-726] -  Wrong translation for "Hide System Calls in Journal"
- [CL-710] -  Implement workaround: Call Specific actions are broken for softphone calls
- [CL-647] -  Prevent connecting to server versions lower than 17
- [CL-567] -  CallKit on Lockscreen should have an icon for the "pascom" button
- [CL-508] -  Sennheiser keeps ringing after offhook on desktop phone

## Release 54.R534 (12.09.2019)

{{% notice note %}}
Bei diesem Release gibt es keine eigene Client-Version, da die Änderungen nur die Mobile iOS-Applikation betrifft.
{{% /notice %}}

**Auf einen Blick**

- Kompatibilität zu iOS 13

**ÄNDERUNGEN:**

- [CL-748] - pascom Client compatibility to iOS 13


## Release 53.R453 (03.07.2019)

**Auf einen Blick**

- Android: Anrufhandling bei gesperrtem Bildschirm verbessert
- iOS: Wenn der DND-Modus von iOS aktiv ist, wird der Anruf direkt abgelehnt
- Desktop: Ein Update wurde trotz gesetztem --noUpdate-Flag heruntergeladen, aber nicht installiert. Der Client gibt nun nur noch einen Hinweis, dass eine neue Version zur Verfügung steht
- Windows: Auf Systemen mit Intel-Grafikkarte wird nun standardmäßing Angle als Rendering-Backend verwendet

**ÄNDERUNGEN:**

- [CL-260] - Broken attended transfer with locked screen on android
- [CL-354] - Check iPhone "DND" mode *before* setting up an incoming call
- [CL-500] - Message badge is not reset on iOS if no Chats are opened
- [CL-515] - Prevent Screen Locking while phoning on android
- [CL-528] - Proximity Screen Turn Off is not handled correctly on android
- [CL-546] - Show unix path as example action app path on macOS/Linux 
- [CL-549] - Add a red background again to Buttonless iOS-Devices
- [CL-584] - Setup "Angle" as default rendering for all Intel GPUs
- [CL-605] - FindPhonebookEntry is sent for journal without phonebook entry 
- [CL-653] - pascom Client prevents screen locking on Android if no passcode or similar locking mechanism is defined
- [CL-657] - Volume too low on iOS handsfree speaker
- [CL-658] - Bump target api level to 28 on android client
- [CL-660] - pascom Client downloads update despite NO_UPDATE is set


## Release 52.R428 (18.06.2019)

**Auf einen Blick**

- Alle Plattformen: Die App sperrt die UI nicht mehr während Daten nachgeladen werden. Dies verbessert insbesondere auf Mobilgeräten die Reaktionszeit
- Windows: Das verwendete Renderbackend lässt sich nun direkt in den Client-Einstellungen umschalten
- Android: Die App ist jetzt als 32bit / 64bit "Universal APK" verfügbar
- Android / iOS: Notrufe an die 110 und 112 werden nun immer direkt über das Mobiltelefon (GSM) aufgebaut

**ÄNDERUNGEN:**

- [CL-11] - Wrong call state if second call via hardware phone
- [CL-31] - Remember selected journal filter in client
- [CL-84] - Ensure 64bit compatibility in android client for play store
- [CL-469] - Copy private phonebook entry to global company phonebook
- [CL-492] - Do not block the client UI by default if a cmd is sent
- [CL-511] - Switch the Rendering mode directly in the client
- [CL-531] - No popup notification if chattab is open in background on mobile
- [CL-533] - Close right click menu in phonebook details after click on different area
- [CL-544] - Convert capital letters to lower case in login mask
- [CL-554] - Force openglSoftware on Intel G41 express
- [CL-561] - Mute in 3 party conference causes missing audio for all participants
- [CL-569] - Get rid of "libpng warning: iCCP: known incorrect sRGB profile" warnings
- [CL-572] - Chat Notification does not immediately close if you click on it
- [CL-601] - Enforce mobile client emergency call via GSM
- [CL-602] - Update cocoasudo version in macOS client
- [CL-627] - pascom Client on iOS looses pairing after update
- [CL-631] - Phonebook entry details are not showing any details in the client
- [CL-649] - No chat notification sent if chat is already open
- [CL-650] - No chat notification sent if client was closed
- [CL-651] - Remove server version deprecated warning again


## Release 51.R365 (27.05.2019)

**Auf einen Blick**

- Es stehen jetzt mehr integrierte Klingeltöne zur Auswahl
- Benachrichtigungen zeigen nun wieder die Quelle (z. b. eine Warteschlange an)
- Diverse Performance und Stabilitätsverbesserungen

**ÄNDERUNGEN:**

- [CL-67] - Remove keyboard lowercase hints on android again
- [CL-286] - Sennheiser status LED stays busy and call control problems
- [CL-327] - Include more ringtones in pascom Client
- [CL-383] - Update opus codec to version 1.3
- [CL-403] - Select dark theme automatically if the main theme of macOS is dark
- [CL-407] - Open chat shortcut broken in normal and extended mode
- [CL-429] - You can select multiple messages in the chat room, but copy only one
- [CL-448] - No error message if password change in pascom Client fails
- [CL-450] - Implement ‘select all’ for group chats
- [CL-478] - Improve behavior of client if a call gets cancelled
- [CL-481] - Copy and paste via right click menu in login mask
- [CL-489] - Chat UI is broken after resizing
- [CL-495] - Show message that no journal entries are matching the filter
- [CL-502] - Introduce a toast message if the client is outdated and updates are disabled
- [CL-503] - Native notification avatar resolution is too low
- [CL-532] - Improve avatar handling for larger (> 50 User) installations with huge images
- [CL-539] - Client crashes after connecting to appliance without maintenance
- [CL-545] - Client doesn’t remember auto PDF faxing setting
- [CL-552] - Wrong shortcut appears after recording key press
- [CL-558] - Attended Transfer is broken on iOS
- [CL-565] - Display a warning if the client connects to a deprecated or outdated server version
- [CL-586] - Avatar in roster still gray if contact switches to available
- [CL-589] - Avatar Caching mechanism sometimes loops, consuming huge amounts of bandwith
- [CL-599] - Use “callDisplayName” property to show correct title for a phonecall in new call notifications
- [CL-614] Number shown twice instead of name


## Release 50.R318 (24.04.2019)

**Auf einen Blick**

- "Flackernde Anzeige" des Clients auf macOS 10.14.4 behoben
- Alle Benachrichtungen im Desktop-Client wurden neu gestaltet und verbessert
- Viele Absturzprobleme auf Android behoben
- Schnellerer Client-Start durch beschleunigtes Avatar-Rendering
- Bei wartenden Anrufern in einem Team werden nun die Labels des Anrufs angezeigt

**ÄNDERUNGEN:**

- [CL-127] - Upgrade Client to Qt 5.12
- [CL-151] - Show incoming file transfer requests also as toast
- [CL-244] - Mobile client crashes on Huawei and Android 6.x 
- [CL-310] - pascom Client crashes when Acessibility Support is enabled in Windows
- [CL-358] - Close open fax dialog if connection interrupts
- [CL-382] - Can't scroll via mouse wheel on non-primary screen
- [CL-404] - Improve custom notifications in client
- [CL-435] - Improve layout for "Edit" button of phone book entry in call details
- [CL-441] - Introduce Database migration during updates
- [CL-444] - Show labels in queue waiting calls
- [CL-464] - Autofocus in LoginPane
- [CL-465] - Use OpenGL fragmentShader for drawing avatar images
- [CL-470] - Deactivate call action buttons if device doesn't support remote control
- [CL-471] - Exception on registerSoftphone after selecting softphone as prefered device
- [CL-475] - Phonebook entry layout broken after incoming call on mobile client
- [CL-476] - Roster button schedules callback notification instead of calling destination of call forwarding
- [CL-479] - Mark text if you tab to input filed in login mask
- [CL-483] - Client Crash when displaying pickup notifications
- [CL-487] - Mobile pairing glitches
- [CL-494] - Client Freezes with ANGLE in an Windows Server 2012R2 Terminal Server Environment
- [CL-497] - Some database settings are read too early during client startup
- [CL-498] - Test client release 50
- [CL-501] - Client crashes on Windows and OSX if you initiate a call
- [CL-504] - Decline button on left side after take off on mobile
- [CL-509] - Copy from phonebook is broken
- [CL-513] - Client flickers when displaying notifications on macOS 10.14.4
- [CL-521] - Wrong avatar shown in roster
- [CL-522] - copy from a chat search result cell copies the wrong text
- [CL-523] - Client crash after receiving incoming chat message
- [CL-525] - Can't show more details to missed call notification with labels 
- [CL-527] - Inconsistent and too low call volume on android
- [CL-529] - Broken Menubar Layout for iPhone X devices with Qt 5.12
- [CL-530] - No default avatar shown in team overview
- [CL-537] - Android client sometimes crashes during first startup
- [CL-555] - Windows client shows both native and custom callback notification


## Release 49.R265 (21.03.2019)

**Auf einen Blick**
 
- Systemanrufe können nun aus dem Journal gefiltert werden
- Bei eingehenden Chat-Nachrichten wird nun ein Ton abgespielt
- Beim pascom Softphone kann nun eine Verstärkung für Mikrofon und Lautsprecher konfiguriert werden
 
**ÄNDERUNGEN:**
 
- [CL-14] - Switches changing color in client settings
- [CL-38] - Scroll loop in client journal
- [CL-100] - Save Settings (FollowMe) on pressing Home-Button
- [CL-281] - Chat room glitches
- [CL-299] - Simplify login forms for pascom.cloud users
- [CL-326] - Play a sound when receiving an incoming chat message
- [CL-345] - Improve tabbing through settings
- [CL-366] - Bright context menu in dark theme
- [CL-390] - Call volume is still to low on certain mobile devices
- [CL-395] - Pickup call clicking on phone icon
- [CL-396] - Preserve entered mobile number if the app goes to sleep
- [CL-401] - Remove deprecated logging window and model
- [CL-402] - Select dark theme automatically if the main theme of windows is dark
- [CL-405] - Callback notification shown twice
- [CL-415] - Headset not selected as speaker
- [CL-419] - Enhance “offline contact filter” - also filter out user that have a paired mobile but an offline phone presence
- [CL-422] - Introduce a switch to filter out system calls from journal
- [CL-442] - Missing activity after voicemailbox answers
- [CL-446] - Notifications has incorrect position on windows
- [CL-452] - pascom Client does not recognize eSim on a iPhone Xr/Xs
- [CL-453] - Phonecall duration is incorrect
- [CL-455] - Softphone not reacting on rejected call
- [CL-473] - Pairing not working

## Release 48.R196 (08.03.2019)

**Auf einen Blick**

- Automatischer Faxversand: Wenn ein PDF Steuerzeichen enthält und GhostScript installiert und konfiguriert ist, kann der pascom Client dieses nun automatisch an die Zielrufnummer faxen
- Der iOS Client zeigt nun eine Benachrichtigung bei verpassten Anrufen an
- Auch mit aktiviertem Jabra-Headset-Support können nun wieder 3er-Konferenzen erstellt werden

**ÄNDERUNGEN:**

* [CL-7] - You can open a grayed out dial pad 
* [CL-41] - Missed call notification is empty after moving it
* [CL-251] - Make search editable to correct typos
* [CL-252] - Buttons for creating phonebook entry layout broken
* [CL-258] - Reset changed phonebook entry after invalid input
* [CL-267] - Copy outlook/apple contacts to private and company phonebook
* [CL-289] - Show a missed call notification on iOS additionally
* [CL-302] - Multiple push notifications with same content are not displayed on android
* [CL-305] - Schedule call back notification if phone is offline
* [CL-313] - Mobile client shows no number after pairing
* [CL-331] - Additional timestamp of current date in journal
* [CL-338] - Improve Settings Dialog - Use a consistent layout for checkboxes / switches
* [CL-341] - Duration in call details overlapping with info button on iPod
* [CL-349] - Sending fax documents unattended
* [CL-355] - If you click on a native chat notification, the client is not moved to the foreground
* [CL-385] - Jabra Pro prohibits to add a call to a running one
* [CL-399] - Playing Voicemail in journal glitches
* [CL-411] - App-Icon Unread messages counter is not reset on iOS
* [CL-413] - Client crashes quite often on macOS
* [CL-416] - Client crashed when try to close all native notifications
* [CL-418] - Can't open settings screen on iPhone
* [CL-423] - Client UI freezes sometimes on macOS
* [CL-433] - Can't create phonebook entry without email address
* [CL-437] - Broken layout of the Chat Input Box on macOS
* [CL-457] - Chat input box does not reset correctly on mobile.


## Release 47.R161 (11.02.2019)

{{% notice note %}}
Bei diesem Release gibt es keine eigene Mobile-Version, da die Änderungen nur die Destop Applikation betreffen.
{{% /notice %}}

**Auf einen Blick**

Diese Version behebt ein Problem auf manchen älteren Windows-Systemen (z. B. Windows 2008 R2 Terminal Server), auf dem die Version v46 mit einer OpenGL-Fehlermeldung nicht mehr startet.

**ÄNDERUNGEN:**

- [CL-414] - Default ANGLE Renderer doesn't work on Windows Server 2008R2


## Release 46.R152 (06.02.2019)

**Auf einen Blick**

- Die UI-Darstellung unter Windows basiert nun auf OpenGL/Angle für mehr Stabilität und bessere Performance
- Die Mindestvorraussetzung ist nun macOS 10.12
- Die Startgeschwindigkeit auf iOS und Android wurde verbessert
- bessere Kompatibilität zu macOS 10.14 

**ÄNDERUNGEN:**

* [CL-16] - Don’t stack ‘configure headset’ messages
* [CL-78] - Status text not in default language
* [CL-116] - Switch back to OpenGL rendering on windows
* [CL-147] - Check client macOS 10.14 "Mojave" compatibility
* [CL-232] - Switch iOS App to iOS12-SDK (iPhone iOS 12)
* [CL-268] - Log in and contact list has slow performance on android
* [CL-285] - Client crashed when import outlook contacts
* [CL-280] - Add possibility to hide notifications of new group chat messages
* [CL-285] - Client crashed when import outlook contacts
* [CL-311] - Improve layout of device settings on mobile
* [CL-325] - Show “default” roster group in client with a nice translated name
* [CL-334] - Calls waiting list position is misleading
* [CL-335] - Crash when clicking on a letter in the phonebook view
* [CL-347] - Send number to dialpad if call is running
* [CL-352] - QR-Code is very big
* [CL-353] - Generate QR-Code in pairing information with long press
* [CL-362] - Client crash in MdSoftphone::muteAllCalls()
* [CL-368] - Labels in native call notifications
* [CL-377] - Regularly vacuum the client settings database
* [CL-379] - Show message that Qt requires macOS 10.12.0 or later
* [CL-397] - Mobile client shows different layout in pairing screen
* [CL-380] - Missing “Play” and “Upload” button for ringtones in client settings
* [CL-400] - No native missed call notification for calls with voicemail
* [CL-408] - Request microphone permissions for client on macOS Mojave


## Release 45.R93 (17.12.2018)

**Auf einen Blick**

- Windows Benutzer können nun optional Windows-Integrierte (Windows Info Center) Benachrichtigungen verwenden. Dies verbessert die Anzeige der Benachrichtigungen insbesondere auf Multi-Monitor-Systemen mit verschiedenen UI-Skalierungsfaktoren
- Der Client kann nun PDF-Dateien aus einem bestimmten überwachten Ordner automatisch zum Faxversand vorschlagen
- Der Android-Client zeigt nun bei einem verpassten Anruf eine Benachrichtigung an
- Wenn zwei Anrufe am pascom Softphone vorhanden sind, dann kann der aktive mit dem gehaltenen Anruf getauscht werden

**ÄNDERUNGEN:**

* [CL-55] - Use native notification systems on Windows
* [CL-70] - Number in journal search results is very small on tablet
* [CL-156] - Send PDF files as Fax by watching a folder
* [CL-237] - Show a persistent notification if a call is missed on android
* [CL-250] - Android client ignores phone locking state on android 9
* [CL-256] - Received invalid call data after *44 on location device
* [CL-261] - Prohibit multiple shortcuts in recording state
* [CL-273] - Improve multi-call handling ("Makeln") when using pascom Softphone
* [CL-274] - Call volume is too low on mobile
* [CL-277] - Cant mark chat message as seen because of incorrect autoaway db value
* [CL-279] - Touchable area for the phone number input field is too small on mobile
* [CL-284] - Proximity sensor not darken call screen after transfer
* [CL-288] - Handle incoming GSM call on android if softphone is already in call
* [CL-292] - Missing busy tone if softphone is unavailable
* [CL-303] - Generating new QR code by pressing enter
* [CL-306] - Client crash on Ubuntu 18.04.1 LTS 
* [CL-309] - Incorrect phone number matching in DATEV phonebook
* [CL-333] - Improve client starter entry on Ubuntu


## Release 44.R66 (27.11.2018)

**Auf einen Blick**

- Plantronics Headset Bibliothek auf die neueste Version aktualisiert
- Die iOS-App empfängt nun noch zuverlässiger Anrufe via Push
- Der GSM-Schalter behält seinen Zustand nun zuverlässig

**ÄNDERUNGEN:**

* [CL-10] - Adapt tooltip in client to current state
* [CL-15] - Do not acknowledge chat message if received in settings menu
* [CL-27] - Message counter broken with pascom client and LTS
* [CL-35] - Can’t close permanent group chat in macOS client
* [CL-53] - Update plantronics spokes sdk in client to the latest version
* [CL-62] - Pickup waiting callers via ‘Calls Waiting’ list
* [CL-64] - Do not allow Update Channel Switching if user has no permission to update client
* [CL-65] - Duplicate error message if voip is disabled on the proxy
* [CL-71] - pascom Client tel callto and sip uri handlers don’t work if the numbers have spaces
* [CL-92] - Audio doesn’t work on windows 10 after upgrade 1803
* [CL-95] - iOS App still misses some calls
* [CL-97] - Contact list / roster filter is not correctly restored on startup
* [CL-168] - Show Team Call names in iOS Client and improve name generation
* [CL-236] - Mobile application displays “Login failed” screen, but logs in sucessfully
* [CL-238] - GSM Switch is still unreliable and activates itself
* [CL-240] - Sort trunk dropdown in client
* [CL-255] - Make settings scrollable on whole width
* [CL-259] - Android client crashes very often with “Illegal State Exception”
* [CL-283] - Android has incorrect version name


## Release 42.R34 (17.10.2018)

**Auf einen Blick**

- Integration der Android Kontakte
- Integration der macOS und iOS Kontakte
- Verbesserte Sennheiser Headset Unterstützung
- Verbesserung der Anrufweiterleitung mit Rücksprache auf iOS

**ÄNDERUNGEN:**

* [CL-23] - Improve behavior of shortcut settings in client
* [CL-34] - Headset buttons on Plantronics D100 not working with macOS
* [CL-37] - Right click in chat binds menu to cursor
* [CL-42] - Multiple dials after long click-to-dial shortcut press
* [CL-43] - Improve input validation for phonebook editing in client
* [CL-47] - Inconsistent behavior of xmpp groups and teams in classic and pascom client
* [CL-86] - Client reconnects after sending special character
* [CL-88] - client crash in SingleChat::unreadMessages()
* [CL-104] - Client phonebook search provider should also search incomplete numbers
* [CL-108] - Sennheiser Headset stays in call if call is accepted simultaneously by another user
* [CL-121] - Include dump files during creation of Support Information in client
* [CL-125] - Check and upgrade to pjsip release 2.8
* [CL-133] - Detect and prevent installing on unsupported windows Versions
* [CL-145] - Integrate Apple macOS/iOS Address Book in Client
* [CL-149] - Show a toast if the device changes after switching the location
* [CL-152] - Message counter in close button on mobile
* [CL-163] - Android Phonebook Integration
* [CL-172] - Add "Load older messages" button to chat view
* [CL-220] - Multi-Line chat messages are not possible anymore in pascom client
* [CL-221] - Client tray icon translation sometimes doesn't work
* [CL-222] - Wrong contact details in chat history
* [CL-223] - Prohibit inconsistent phonebook entries of users
* [CL-224] - Improve fax dialog
* [CL-225] - No hint if softphone is not ready
* [CL-226] - "preferred device" toast is shown also on mobile
* [CL-227] - Create High-Resolution Versions for Phonebook Icons
* [CL-228] - Show hint that sennheiser activation failed
* [CL-245] - No audio after transfer of external call to ios mobile client

