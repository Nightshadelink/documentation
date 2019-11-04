---
title: pascom Server 19 beta
description: Mit dem pascom Release 19 stehen Ihnen eine Vielzahl an neuen Funktionen zur Verfügung.
weight: 995
---

![Highlights](pascom19_highlights.jpg)

{{% notice tip %}}
Folgen Sie bitte unserer detaillierten [Upgrade-Anleitung]({{< ref "/server/upgrade" >}}).
{{%/notice%}}

{{% notice warning %}}  
**Wichtige Hinweise zu diesem Update:**     
1. Trunk Failover (Ämterketten) ersatzlos gelöscht. Keine Migration und keine direkte Problemumgehung. Der Support kann bei Bedarf mit einem ausgehenden Skript helfen.  
2. IAX-Amtsleitungen ersatzlos gelöscht.  
3. Beronet wird in pascom 19 "BETA" noch nicht unterstützt, wird in der nächsten Bugfix-Version folgen.  
4. Swap ist jetzt standardmäßig deaktiviert. Dadurch können virtualisierte Setups mit weniger als 1 GB Arbeitsspeicher beschädigt werden. Konfigurieren Sie in diesem Fall mehr Arbeitsspeicher.  
5. Anrufgruppen werden automatisch in Teams umgewandelt. Die Anrufgruppenfunktion wurde entfernt, und stattdessen sollten Teams konfiguriert werden.  
6. Das Durchsagesystem funktioniert nicht.  
7. Portforwarding für UDP 3478 ist Voraussetzung, andernfalls funktioniert Video nicht.
{{% /notice %}}

## Highlights



### pascom Video Konferenzen 

55% der Kommunikation erfolgt visuell. Mit der nativen Videointegration von pascom ist das Starten einer Konferenz auf Ihrem Desktop oder Mobilgerät nur einen Klick entfernt. Sie benötigen weder zusätzliche Software noch können Probleme mit inkompatiblen Browsern auftreten.

![Video Konferenz](pascom-19-video-desktop-conference.png)

### Screensharing

Ein Bild sagt mehr als tausend Worte. Die neue Screensharing Funktion steht auf allen Geräten und Plattformen zur Verfügung und stellt sicher, dass auch Außendienstmitarbeiter jederzeit Dokumente und Präsentationen mit Ihren Kollegen teilen können.

![Screensharing](pascom-screen-sharing.png)

### pascom Gruppen mit Audio, Video und Chat

Verbessern Sie die Teamzusammenarbeit mithilfe von Gruppen. Aufbauend auf unserem “on the fly” Gruppen-Chat ist es mit pascom 19 jetzt jedem Benutzer möglich, permanente Gruppen zu erstellen. Ermöglichen Sie Ihren Mitarbeitern sich mühelos per Chat, Audio oder Video austauschen.

![pasocm Gruppen](pascom-team-chat.png)




## Release 19.00 (04.11.2019)

**Auf einen Blick**

- Kontakte/Kontaktliste überarbeitet
- Neue Suchfunktion mit Smartfilter
- Interaktive Anrufobjekte während einem Telefonat
- Video und Screensharing Funktion
- pascom Gruppen. Permanente Audio,- Video und Screensharing Gruppen
- Asterisk Update auf Version 16 LTS
- Zugriff auf RTP Statistiken
- Ämtertemplates geändert auf die pjsip Syntax



