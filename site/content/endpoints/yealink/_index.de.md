---
title: Yealink Tischtelefone
description: Integrieren Sie Ihre Yealink IP-Tischtelefone in die pascom.
weight: 30
---


{{< doctype "both" >}}

{{< description >}}

![Yealink T46G](yealink-t4-series1.jpg?width=400px)

## Unterstützte Geräte

**[Liste der unterstützten Endgeräte, hier klicken!]({{<ref "/endpoints#yealink-ip-telefone" >}})**

## Provisionierung

{{% notice tip %}}
Für lokale Installationen des pascom Servers ist es möglich Endgeräte per DHCP-Server massenweise und vollautomatisch in Betrieb zu nehmen.
Details können Sie dem Howto [Telefon-Provisionierung via DHCP]({{< ref "/howto/dhcp-provisioning" >}}) entnehmen.
{{% /notice %}}

pascom ist in der Lage IP-Telefone des Herstellers Yealink automatisch und zentral zu konfigurieren. Diesen Vorgang nennt man Provisionierung. Dazu stellt pascom eine Basis-Konfiguration ({{< ui-button "Endgeräte" >}} > {{< ui-button "Basis-Konfigurationen" >}}) zur Verfügung. Diese ist ausreichend vorparametriert und muss nur in manchen Fällen angepasst werden.

## Neues Telefon hinzufügen

{{% notice tip %}}
Handelt es sich nicht um ein fabrikneues Telefon setzen Sie es in jedem
Fall auf **Werkseinstellungen** zurück. Drücken Sie die {{< ui-button "OK" >}}-Taste des Telefons,
im eingeschalteten Zustand, so lange bis **Factory Reset** im Display erscheint.
Bestätigen Sie nochmals mit der {{< ui-button "OK" >}}-Taste.
{{% /notice %}}

Stecken Sie das Yealink-Telefon an das Netzwerk. Das Telefon enthält einen eingebauten Switch, benutzen Sie den Ethernet-Port mit der Bezeichnung **Internet**. Falls Sie kein **PoE** (Power over Ethernet) verwenden, stecken Sie das Telefon an den Netzstrom.

Nach dem Boot-Vorgang drücken Sie die {{< ui-button "OK" >}}-Taste des Telefons und notieren Sie
sich die IP-Adresse.

### MAC-Adresse ermitteln

Die MAC-Adresse steht auf der Rückseite des Telefones.

Alternativ surfen Sie nun mit Ihrem Browser auf die zuvor notierte IP-Adresse des Telefones.
Loggen Sie sich mit Benutzer und Passwort **admin**, **admin** ein.
Unter {{< ui-button "Status" >}} > {{< ui-button "MAC Address" >}} notieren Sie sich die MAC-Adresse des
Telefons. 

### Endgerät anlegen

Loggen Sie sich in Ihrer Telefonanlage ein und fügen unter {{< ui-button "Endgeräte" >}} > {{< ui-button "Geräteliste" >}} ein
neues Gerät vom Typ **IP-Telefon: Hersteller Yealink** hinzu.

Tragen Sie im Feld **Mac-Adresse** die zuvor ermittelte MAC-Adresse des Telefons
ein.

### Jobs Anwenden

Nach dem Speichern von Änderungen erscheint in der Job-Box (oben) ein
entsprechender Eintrag die Telefonie anzuwenden. Starten Sie den Job durch
einen Klick auf den {{< ui-button "grünen Haken" >}}.

### Provisionierung-URL ermitteln

Haken Sie das Telefon in der Geräte-Liste an und wählen {{< ui-button "Aktion" >}} > {{< ui-button "Provisioning URL" >}}.
Für jeden verfügbaren Proxy erscheint ein Eintrag in der Liste. Kopieren Sie die
**URL** in die Zwischenablage.

### Provisionierung-URL eintragen

{{% notice tip %}}
Sollte Sie **kein offizielles Zertifikat** auf Ihrem Proxy installiert
haben müssen Sie auf der Web-UI des Telefons ***Only Accept Trusted Certificates***
unter {{< ui-button "Security" >}} > {{< ui-button "Trusted Certificates" >}} auf **Disabled** stellen
{{% /notice %}}

Zurück auf der Web-UI des Telefons tragen Sie unter {{< ui-button "Settings" >}} > {{< ui-button "Auto Provision" >}} > {{< ui-button "Server URL" >}}
die eben kopierte Provisionierung-URL ein.

Klicken Sie auf {{< ui-button "Confirm" >}} und anschließend auf {{< ui-button "Autprovision Now" >}}.

Das Telefon startet neu.

### Benutzer zuweisen

Nachdem das IP-Telefon neu gestartet ist kann es in der Geräteliste bearbeitet werden. Klicken Sie hierzu auf {{< ui-button "Bearbeiten" >}}. Im Tab {{< ui-button "Zuweisung" >}} kann dem Telefon ein [Benutzer]({{< ref "/user/user">}}) zugewiesen werden.

Nach dem Speichern und Anwenden der Telefoniekonfiguration werden die neu zugewiesenen IP-Telefone neugestartet.

### Funktion testen

Am einfachsten kann man die erfolgreiche Inbetriebnahme testen, indem man mit **\*100** die eigene Voicemailbox anruft. Daraufhin sollte die Ansage Ihrer Voicemailbox zu hören sein.

## pascom Menütaste

Nach der Provisionierung ist auf der zweiten Funktionstaste am Display das pascom Menü zu finden. Hier sind pascom Funktionen hinterlegt:

|Funktion|Beschreibung|
|---|---|
|Telefonbuch|Ruft das pascom Telefonbuch auf.|
|Journal|Zeigt verpasste, angenommene und gewählte Anrufe an|
|Rufumleitung|Setzt eine Rufumleitung, aktiviert/ändert eine schon gesetzte Rufumleitung oder deaktiviert eine aktive Rufumleitung.|
|Voicmailbox|Voicemailbox-Menü zum Einschalten/Ausschalten und Abhören der eigenen Voicemailbox|
|Anmelden|Hier kann ein Benutzer sich an dem Arbeitsplatz anmelden.|
|Abmelden [*benutzername*]|Der bereits angemeldete Benutzer kann sich an dem Arbeitsplatz abmelden.|
|Warteschlangen|Dient zur Verwaltung der Warteschlangen (anmelden, abmelden, pausieren...), je nach Konfiguration der Warteschlangen.|


{{% notice tip%}}
Setzen Sie Rufumleitungen nur über das pascom Menü, da diese Rufumleitungen über die pascom verwaltet werden können.
{{% /notice %}}

{{% notice info%}}
Die Verwendung der DND-Taste (*do not disturb*) oder Ruhe-Taste am Yealink hat zur Folge, dass die Durchwahl am Telefon nicht erreichbar ist. Der DND-Hinweis erscheint nur am Telefon und hat für die pascom (z. B. Desktop Client) keine weitere Bedeutung.
{{% /notice %}}

## Auf die Yealink-Weboberfläche zugreifen

Um auf die Weboberfläche Ihres IP-Telefons zu gelangen benötigen Sie die IP-Adresse. Im Folgenden sind Möglichkeiten beschrieben, um diese in Erfahrung zu bringen:

### IP-Adresse am Telefon anzeigen

Drücken Sie die **OK**-Taste auf Ihrem Yealink IP-Telefon. Nun können Sie die IPv4-Adresse des Telefons ablesen.


### IP-Adresse über die Geräteliste ermitteln

Loggen Sie sich in das Web-UI der pascom ein. Klicken Sie auf {{< ui-button "Endgeräte" >}} > {{< ui-button "Geräteliste" >}}. Nun sehen Sie eine Übersicht über alle verfügbaren Geräte. Links von jedem Eintrag finden Sie ein *Info*-Symbol. Klicken Sie es an, erhalten Sie eine Übersicht über das provisionierte Telefon, unter anderem auch die IP-Adresse.

### Funktionstasten

Die Funktionstasten rechts und links vom Display sind dreifach belegbar. Ist die erste Seite vollständig belegt, wird die letzte Taste am Display zum "umblättern" verwendet.

### Andere Benutzer (Nebenstellen) überwachen

Zur Überwachung anderer Benutzer oder Nebenstellen können Funktionstasten eingerichtet werden. Dazu eignen sich BLF-Tasten (Besetztlampenfeld oder Busy Lamp Field). Diese geben Informationen über den Status der überwachten Durchwahl. Überwachen bedeutet in diesem Fall zu sehen ob ein Benutzer telefoniert, angerufen wird und ggf. sein Gespräch heranzuholen (Pickup).

Tasten können auf verschiedenen Wegen konfiguriert werden.

### Tasten belegen direkt am Telefon

Drücken Sie auf Ihrem Telefon ca. 5 Sekunden lang auf die Taste die Sie belegen möchten. Nun können Sie Ihre Taste (z. B. BLF-Taste) belegen.

|Einstellungen|Belegung|
|---|---|
|Typ|BLF|
|Konto ID|Leitung 1|
|Kontoname|Geben Sie hier eine Bezeichnung für die Taste an.|
|Wert|Die zu überwachende Durchwahl, z. B. 123 für die Durchwahl 123|

Drücken Sie zum Bestätigen auf *Speichern*.

### Tasten belegen über das Web-UI

Im Tab {{< ui-button "Speicher-Tasten" >}} können die verschiedenen Tasten, z. B. BLF-Tasten am Telefon belegt werden:

|Typ|Wert|Name|Konto|
|---|---|---|---|
|BLF|Die zu überwachende Durchwahl, z. B. 123 für die Durchwahl 123|Geben Sie hier eine Bezeichnung für die Taste an.|Leitung 1|

Neben Benutzer-Durchwahlen können auch Einbuchcodes für Warteschlangen oder Durchwahlschalter konfiguriert werden.

### Weitere nützliche Funktionstasten

|Funktionstaste|Beschreibung|
|---|---|
|**Speed Dial**|Hier kann eine Telefonnummer hinterlegt werden.|
|**DTMF**|Hier können DTMF-Zeichen hinterlegt werden.| -->

## Basis-Konfiguration

Wie bereits erwähnt, werden Yealink IP-Telefone  mit Hilfe der Basis-Konfiguration provisioniert. Die Basis-Konfiguration ist unter {{< ui-button "Endgeräte" >}} > {{< ui-button "Basis-Konfigurationen" >}} zu finden.

{{% notice note %}}
Bevor Sie die Basis-Konfiguration ändern, müssen Sie diese {{< ui-button "Duplizieren" >}}.
{{% /notice %}}

Ebenfalls können Sie eine schon bearbeitete Basis-Konfiguration als {{< ui-button "Standard setzten" >}}. Somit erhalten neu angelegte IP-Telefone automatisch die angepasste Basis-Konfiguration.

### Zuweisung einer Basis-Konfiguration

Eine Basis-Konfiguration kann auf mehreren Wegen zugewiesen werden:

+ Über {{< ui-button "Endgeräte" >}} > {{< ui-button "Basis-Konfigurationen" >}} > Basis-Konfiguration auswählen und Bearbeiten, im Tab {{< ui-button "Geräte" >}} können gleich mehrere IP-Telefone hinzugefügt werden.
+ Über {{< ui-button "Endgeräte" >}} > {{< ui-button "Geräteliste" >}} > IP-Telefon auswählen und Bearbeiten im Tab {{< ui-button "Basisdaten" >}}.

### BLF-Tasten konfigurieren über die Basis-Konfiguration

Im Tab {{< ui-button "Konfiguration" >}} können Sie die vorhandene Basis-Konfiguration anpassen. Im Bereich **keys** finden Sie bereits vorkonfigurierte Funktionstasten, an denen Sie sich orientieren können.

BLF-Tasten lassen sich wie folgt einrichten:

    {{!-- keys --}}
    linekey.3.type = 16
    linekey.3.value = 123
    linekey.3.label = Max
    linekey.3.line = 1

Die belegte Taste (in diesem Fall Linekey 3) besteht aus drei Parametern:

+ *type*: der Typ der Taste, 16 steht für BLF,
+ *value*: der Wert, das ist hier die Nebenstelle,
+ *label*: das Label, das ist die Bezeichnung, die am Display angezeigt wird.
+ *line*: das Konto des Benutzers, der am Telefon angemeldet ist und die Konfiguration ausführt. *(Muss immer 1 sein)*

Weisen Sie diese Basis-Konfiguration über den Tab {{< ui-button "Geräte" >}} den IP-Telefonen zu, die diese Taste auch in der Weise belegt haben sollen und speichern Sie. Nach dem Neustart der IP-Telefone werden die Änderungen auf diesen übernommen.


## Firmwareupdate

Ab der mobydick Version 7.14 wird die Firmware für IP-Endgeräte nicht mehr mitgeliefert. Sollte eine andere als auf dem IP-Endgerät installierte Firmware benötigt werden, muss diese selber heruntergeladen und in die pascom Firmware-Verwaltung hochgeladen werden.

### Firmware hinzufügen

Die gewünschte Firmware kann hinzugefügt werden unter {{< ui-button "Endgeräte" >}} > {{< ui-button "Firmware" >}}:

|Einstellung|Beschreibung|
|---|---|
|Firmware-Datei|Laden Sie hier die Firware hoch. Diese finden Sie auf der [Download-Seite von Yealink](http://support.yealink.com/documentFront/forwardToDocumentFrontDisplayPage).|
|Model|Modellbezeichnung des Yealink-Telefons|
|Version|Firmware-Version|
|Dokumentation|Optionales Feld für Notizen|

### Firmware ausrollen

Die Firmware kann über {{< ui-button "Endgeräte" >}} > {{< ui-button "Geräteliste" >}} aktualisiert werden. Wählen Sie die Zielgeräte in der Geräteliste mit Häkchen aus und klicken Sie auf {{< ui-button "Aktion" >}} > {{< ui-button "Firmware ausrollen" >}}. Nun erhalten Sie eine Übersicht der gewählen Geräte, in der Sie die Zielfirmware auswählen können. Anschließend klicken Sie auf {{< ui-button "Firmware update" >}} um die gewählte Firmware auszurollen.


