---
title: pascom Desktop Client installieren
description: Den pascom Desktop Client installieren und updaten
weight: 31

---


## Desktop-Client herunterladen

Die aktuelle Version des pascom Desktop Client für Windows, MacOS und Linux können Sie direkt von unserer [Homepage](https://www.pascom.net/de/mobydick-voip/) herunterladen. 


## Windows Installation

Die Windows Installation benötigt keine Administratorrechte und erfolgt automatisch in das Home-Directory des aktuell angemeldeten Benutzers:

 * Windows Desktop Client herunterladen
 * pascom-client-setup.exe ausführen
 * Installationanweisungen folgen

## Terminalserver Installation

Am Microsoft Terminal Server können Sie den pascom Desktop Client optional statt in das jeweilige Home-Directory der Benutzer direkt in das Programme Verzeichnis installieren. 

Der Nachteil dieser Installationsart ist, dass Sie sich selbst um das Update des Desktop Clients kümmern müssen da dieses Administrator Rechte Benötigt. Als Vorteil sparen Sie ca. 100 MB Plattenplatz pro Benutzer.

* Windows Desktop Client herunterladen
* Öffnen Sie die Eingabeaufforderung als Administrator
* Starten Sie das Setup und geben Sie das Zielverzeichnis an 

Beispiel

```
pascomClient-setup.exe /D=C:\Program Files (x86)\pascom Client
```

## MacOS Installation

* MacOS Desktop Client herunterladen
* pascom Client.dmg ausführen
* Schieben Sie das pascom Icon auf den Application Ordner
* Sobald der Kopiervorgang abgeschlossen ist, können Sie den Client starten

## Linux Installation

Unter Linux bringen wir keinen Installer mit:

* Linux Desktop Client herunterladen
* pascom_Client.tar.bz2 entpacken
* Client starten

Beispiel
```
tar xvjf pascom_Client-7.17.10.R.tar.bz2
./md_client/bin/md_client
```

## Windows Installer Kommandozeilen Parameter

|Parameter|Bedeutung|
|---------|---------|
|/S|Ermöglicht eine Installation im Hintergrund, ohne dass Dialogfenster angezeigt werden.|
|/D=PATH| Gibt einen Installationsordner an. Dieser Parameter muss immer der letzte in der Befehlszeile sein, darf keine Anführungzeichen enthalten und unterstützt nur absolute Dateipfade|


## Desktop Client Umgebungsvariablen und Kommandozeilen Parameter

Der pascom Desktop Client unterstützt auf allen Betriebsystemen zahlreiche Kommandozeilen Parameter und reagiert außerdem auf etliche Umgebungsvariablen. 

Welche Parameter und Umgebungsvariablen von Ihrer Version unterstützt werden können Sie durch den Parameter `--help` abfragen.

{{% notice tip %}}
Der Desktop Client darf nicht gestartet sein um die Hilfe auszugeben.
{{% /notice %}}

Beispielausgabe:

```
pascom Client 7.18.00.D3667_267a0cd
Environment variables without corresponding commandline parameter:
- PC_SCALE_FACTOR=<value>: Set this environment variable to override automatic DPI Scaling value. Useful if you have a Setup with multiple Monitors and non-integer scaling factors. Value is a real, e. g. 1, 0.75, 1.5, and applies as second factor to the Scaling Value QT Calculated. Example: Your screen is at 150% scaling, QT would calculate a factor of 2. So VALUE needs to be 0.75 to get to the correct real scaling of 1.5

- PC_SCENE_GRAPH_BACKEND=<value>: Set this environment variable to switch the backend used for rendering the ui. Useful if the default backend produces graphic errors on your setup. Do not set or leave empty to use automatic (Software on Windows, OpenGL on other platforms). Possible Values are: software, d3d12, openvg, opengl

- PC_QSG_RENDER_LOOP=<VALUE>: Change the used opengl render loop by setting `QSG_RENDER_LOOP` internally. Defaults to 'basic' if not set. Possible Values are: basic, windows, threaded



Options:
  --userDir <userDir>      Set user directory. Via Environment: Set PC_USERDIR
                           to desired value
  -h, --help               Displays this help.
  --exec                   Execute a command instead of starting a client
                           instance. Example: --exec dial,*104 (Calls your own
                           Voicemailbox)
  --debug                  Show debug window. Via Environment: Set
                           PC_DEBUG_WINDOW to any value.
  --noUpdate               Disable automatic update. Via Environment: Set
                           PC_NO_UPDATE to any value.
  --forceTouchMode         Show UI like touchscreen is enabled
  --disableHeadsetSupport  Set to true to disable automatic headset detection
                           and controls. Via Environment: Set
                           PC_HEADSET_SUPPORT_DISABLED to any value.
  --logSennheiserMessages  Log all communication from and to Sennheiser
                           HeadSetupApplication. Via Environment: Set
                           PC_LOG_SENNHEISER_MESSAGES to any value.
  --logXmppMessages        Log complete Xmpp Messages. Via Environment: Set
                           PC_LOG_XMPP_MESSAGES to any value.
  --logSipMessages         Log complete Sip Messages. Via Environment: Set
                           PC_LOG_SIP_MESSAGES to any value.
  --loglevel <loglevel>    Set Logging verbosity. values from 0-5. Via
                           Environment: Set PC_LOG_LEVEL to desired value.
  --minimized              Do not open the main window on startup. Via
                           Environment: Set PC_MINIMIZED to any value
  --user <user>            Override login username. Via Environment: Set
                           PC_USER to desired value.
  --password <password>    Override login password. Insecure, please use
                           PC_PASS environment variable instead
  --server <server>        Override login server. Via Environment: Set
                           PC_SERVER to desired value.
```
