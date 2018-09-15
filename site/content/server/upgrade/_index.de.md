---
title: Upgrade von pascom 17 und älter
description: Schritte für ein Upgrade von pascom 17 und älter
weight: 70
---

{{< doctype "self" >}}

{{< description >}}

## Lizenz Upgraden

{{% notice tip%}}
Ist eine Lizenz auf pascom 18 oder höher migriert kann diese nicht mehr für ältere Systeme verwendet werden. Möchte Sie für das alte System beispielsweise mehr Benutzer kaufen ist dies ohne ein gleichzeitiges Upgrade nicht mehr möglich.
{{% /notice %}}

Bevor Sie das Upgrade durchführen können **kontaktieren** Sie bitte unseren **Vertrieb** um Ihre Lizenz auf pascom 18 oder höher umzustellen. Dieser Vorgang ist selbstverständlich kostenlos.

Für die Migration **benötigen** Sie außerdem einen **my.pascom.net Zugang**. Sollten Sie noch keinen Zugriff auf my.pascom.net haben ist Ihnen unser Team gerne behilflich.


## Upgrade Checkliste

Bitte beachten Sie folgende Checkliste **BEVOR** Sie mit dem Upgrade beginnen

* [ ] Ich verwende keine Siemens Telefone
* [ ] Ich verwende keine Auerswald Telefone (Unterstützung noch in Arbeit)
* [ ] Ich verwende keine Aastra Tischtelefone (Unterstützung noch in Arbeit)
* [ ] Ich verwende keine Patton Gateways
* [ ] Ich verwende keinen pascom Classic Client oder FlexPanels
* [ ] Ich verwende kein Print To Fax
* [ ] Die Hardware oder Virtuelle Maschine die ich verwende hat min 2 GB RAM
* [ ] Ich verwende keine 32Bit Hardware oder 32Bit Virtuelle Maschine
* [ ] Mein Beronet Gateway hat mindestens Firmware Verison 16
* [ ] Ich verwende keinen pascom Cluster bzw. möchste diesen auflösen
* [ ] Ich verwende eine virtuelle Maschine und habe einen Snapshot erzeugt
* [ ] Ich habe meine Lizenz vom pascom Vertriebs Team upgraden lassen
* [ ] Ich habe einen mit meiner Firma verknüpften my.pascom.net Zugang

Weitere Details über wichtige Änderungen entnehmen Sie bitte den Release-Notes.

## Upgrade Schritte

pascom setzt ab Version 18 eine vollständig neue Basistechnologie ein. Daher kann das Upgrade nicht, wie gewohnt, "inplace" direkt auf dem laufenden Server ausgeführt werden sondern erfordert folgende Schritte.

### pascom / mobydick Version checken

Sie benötigen mindestens mobydick 7.11 (LTS) als Migrationsbasis. Falls Sie noch ein älteres System nutzen updaten Sie es bitte mindestens auf Version mobydick 7.11 (LTS). 

### Datenbank Backup erstellen

Erstellen Sie nun auf Ihrem vorhandenen System ein Datenbank Backup. Melden Sie sich hierzu an Ihren pascom / mobydick Server an und klicken unter
{{< ui-button "Appliance" >}}>{{< ui-button "Sicherung" >}}>{{< ui-button "Datenbanksicherung" >}} auf {{< ui-button "Erstellen" >}}.

Vergeben Sie einen Namen und schließen Sie ggf. Mitschnitte, Faxe und Voicemails in Ihr Backup mit ein.

Klicken Sie auf {{< ui-button "Ausführen" >}} und **laden** das so eben erstelle **Backup** 
**auf Ihren Computer herunter**.

### Backup Komplettsystem erstellen

{{% notice info %}}
Dieses Backup benötigen Sie im **Fehlerfall** um das ursprüngliche System **wiederherstellen** zu können. Bitte lassen Sie diesen Schritt in keinem Fall aus.
{{% /notice %}}

Klicken Sie auf {{< ui-button "Appliance" >}}>{{< ui-button "Sicherung" >}}>{{< ui-button "Komplettes System" >}} auf {{< ui-button "Erstellen" >}}.

Klicken Sie auf {{< ui-button "Sicherung starten" >}} und **laden** das so eben erstelle **Backup** 
**auf Ihren Computer herunter**.


### Neuinstallation pascom Server

Installieren Sie nun pascom Server Version 18 oder neuer. 

Falls Sie eine virtuelle Maschine verwenden empfiehlt es sich eine neue VM zu erstellen und das alte System vorest nur abzuschalten.

Nutzen Sie die pascom Appliance, SOHO oder SMB Server installieren Sie das System bitte neu.

Folgen Sie hierzu, je nach verwendetem System, einer unserer [Server Installations Anleitungen]({{< ref "server" >}}).

### Einspielen des Backups

Während des Installationsprozesses bietet Ihnen der Setup Wizard die Möglichkeit das zuvor erstellte **Backup** als Basis für die Neuinstallation zu nutzen.

### (Optional) pascom DHCP-Server aktivieren

Den DHCP Server wurde von der Telefonanlagen Oberfläche in die Management Oberfläche verschoben. Somit ist die Konfiguration des DHCP-Servers auch nicht Bestandteil des von Ihnen zuvor eingespielten Backups.

Falls Sie den pascom DHCP Server in der Vergangenheit genutzt haben müssen Sie diesen im Management wieder aktivieren und konfigurieren. Details können Sie dem Howto [Telefon-Provisionierung via DHCP]({{< ref "/howto/dhcp-provisioning" >}}) entnehmen.

### (Optional) Ihren DHCP Server anpassen

Verweden Sie Ihren eigenen DHCP-Server für das Provisioning müssen Sie nun die DHCP-Option 66 anpassen da sich diese für das Provisioning geringfügig geändert hat. Details können Sie dem Howto [Telefon-Provisionierung via DHCP]({{< ref "/howto/dhcp-provisioning" >}}) entnehmen.

### Neuprovisionierung aller Telefone

{{% notice tip %}}
Versorgen Sie alle Hardwaretelefone zentral über POE genügt es Ihren POE Switch einmal vom Stromnetz zu nehmen um alle Telefone neu zu starten.
{{% /notice %}}

Alle Hardware Telefone müssen nun von SIP-UDP und RTP auf SIP-TLS und SRTP (Verschlüsselung) umgestellt werden. Wenn Sie den DHCP-Server vorbereitet haben müssen Sie nun nur mehr alle Telefone neu starten. Diesen Vorgang müssen Sie manuell ausführen, da ein Reboot über den pascom Server ohne eine vorherige Umstellung der Provisionierung nicht möglich ist. 

### Neuprovisionierung Beronet PCI-Karte


### Neuprovisionierung Beronet Box


### pascom Desktop Client updaten

Nutzen Sie den pascom Desktop Client < 17.10 müssen Sie den Desktop Client manuell neu installieren.

Folgen Sie hierzu der Anleitung [pascom Dekstop Client Installation]({{< ref "/clients/desktop-installation" >}})

Der Grund hierfür: pascom Desktop Clients < 17.10 updaten sich über den pascom Server. Ab pascom 18 macht der Server keine Client-Updates mehr. Hierzu haben wir nun einen zentralen Updateservice etabliert.

### Änderungen am Fax-Server

Der pascom Server unterstützt kein Print-To-Fax mehr.

Zusätzlich hat sich die Nutzung von Fax-To-Mail verändert. Der pascom Server holt die Faxe jetzt von einem POP/IMAP Postfach ab anstatt die E-Mail direkt via SMTP entgegen zu nehmen.

Passen Sie hierzu Ihre Konfiguration entsprechend an.

### Änderungen Queuemetrics

Die Queuemetrics Schnittstelle überträgt die Daten zwischen pascom Server und Queuemetrics nun via Uniloader. Uniloader ersetzt den bisherigen Qloader. Der Uniloader ist auch in der Lage Befehle von Queuemetrics via HTTPS entgegen zu nehmen und diese an die Asterisk AMI weiter zu geben.

Weitere Informationen finden Sie in der [Uniloader Dokumentation](http://manuals.loway.ch/Uniloader-chunked/)

