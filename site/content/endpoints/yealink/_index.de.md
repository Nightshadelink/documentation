---
title: Yealink Tischtelefone T4-Serie
description: Integrieren Sie Ihre Yealink IP-Tischtelefone in die pascom.
weight: 30
---

![Yealink T46G](yealink-t4-series1.jpg?width=400px)


## Kompatibilität

|Provisionierung|Firmware-Verwaltung|Fernsteuerung über Desktop-Client|pascom Menü|
|---|---|---|---|
|ja|ja|ja|ja|

**Provisionierung**: Das IP-Telefon wird über die pascom verwaltet.<br>
**Firmware-Verwaltung**: Die Firmware kann über pascom aktualisiert werden.<br>
**Fernsteuerung über Desktop-Client**: Gespräche können über den Desktop-Client gestartet werden.<br>
**pascom Menü**: An einer Taste am Telefon wird das pascom Menü hinterlegt.


## Konfiguration

pascom ist in der Lage IP-Telefone des Herstellers Yealink automatisch und zentral zu konfigurieren. Diesen Vorgang nennt man Provisionierung. Dazu stellt pascom eine Basis-Konfiguration (`Endgeräte` > `Basis-Konfigurationen`) zur Verfügung. Diese ist ausreichend vorparametriert und muss nur in manchen Fällen angepasst werden.

{{% notice tip%}}
Bei Neuinstallationen sollten Sie den Provisionierungsvorgang zuerst mit einem Telefon testen. War dies erfolgreich können Sie alle weiteren IP-Telefone in Betrieb nehmen.
{{% /notice %}}

### Vorbereitung

Für die automatische Inbetriebnahme ist ein funktionierender DHCP-Server zwingend erforderlich.

### Inbetriebnahme

Stecken Sie das IP-Telefon an das Netzwerk. Das Telefon enthält einen eingebauten Switch, benutzen Sie den Ethernet-Port mit der Bezeichnung **Internet**. Falls Sie kein **PoE** (Power over Ethernet) verwenden, stecken Sie das Telefon an den Netzstrom.

Das IP-Telefon bootet nun, zieht sich vom DHCP-Server eine IP-Adresse und die passende Basis-Konfiguration. Nach diesem Vorgang trägt pascom das IP-Telefon automatisch in die Geräteliste unter `Endgeräte` > `Geräteliste` ein und legt ein entsprechendes SIP-Peer an.

Das SIP-Peer wird automatisch angelegt. Benutzername und Passwort werden automatisch generiert. Der Benutzername besteht aus einer zufälligen Zeichenfolge und den letzten sechs Stellen der Geräte-MAC-Adresse und hat insgesamt 15 Stellen. Das Passwort ist ebenfalls 15-stellig. Da die IP-Telefone automatisch provisioniert werden, müssen Sie die Daten niemals manuell eingeben. Es ist auch nicht möglich die Benutzerdaten zu ändern. Dies erhöht die Sicherheit gegen SIP-Brute-Force-Attacken beträchtlich.

Als Bezeichnung des Telefons wird automatisch die Herstellerbezeichnung gefolgt von der MAC-Adresse vergeben. Da auf dem Telefongehäuse die MAC-Adresse vermerkt ist, lässt sich vor Ort das IP-Telefon einfach zuordnen.

Nach der erfolgreichen Provisionierung sollte das IP-Telefon am Display die richtige Sprache, die richtige Zeit und den Text *Nur Notrufe* (oder *Emergency only*) anzeigen.

{{% notice info%}}
Nach der Provisionierung des IP-Telefons wird von pascom der Admin-User neu gesetzt.
<br>Username: *admin*
<br>Passwort: *0000*
{{% /notice  %}}

Das Passwort des Admin-Users am IP-Telefon kann über die Systemeinstellungen im Web-UI geändert werden. Suchen Sie in dem Suchfeld nach dem Parameter *sys.peripherals.access.password*. Geben Sie Ihren gewünschten Wert ein. Anschließend müssen Sie manuell die Telefonie-Konfiguration anwenden und die Endgeräte neustarten.

### Benutzer zuweisen

Nachdem das IP-Telefon in der Geräteliste erscheint kann es bearbeitet werden. Klicken Sie hierzu auf `Bearbeiten`. Im Tab `Zuweisung` kann dem Telefon ein [Benutzer (oder Arbeitsplatz)]({{< ref "/user/user">}}) zugewiesen werden.

Nach dem Speichern und Anwenden der Telefoniekonfiguration werden die neu zugewiesenen IP-Telefone neugestartet.

### Funktion testen

Am einfachsten kann man die erfolgreiche Inbetriebnahme testen, indem man mit **\*100** die eigene Voicemailbox anruft. Daraufhin sollte die Ansage Ihrer Voicemailbox zu hören sein.

### pascom Menütaste

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

### Auf die Yealink-Weboberfläche zugreifen

Um auf die Weboberfläche Ihres IP-Telefons zu gelangen benötigen Sie die IP-Adresse. Im Folgenden sind Möglichkeiten beschrieben, um diese in Erfahrung zu bringen:

#### IP-Adresse am Telefon anzeigen

Drücken Sie die **OK**-Taste auf Ihrem Yealink IP-Telefon. Nun können Sie die IPv4-Adresse des Telefons ablesen.


#### IP-Adresse über die Geräteliste ermitteln

Loggen Sie sich in das Web-UI der pascom ein. Klicken Sie auf `Endgeräte` > `Geräteliste`. Nun sehen Sie eine Übersicht über alle verfügbaren Geräte. Links von jedem Eintrag finden Sie ein *Info*-Symbol. Klicken Sie es an, erhalten Sie eine Übersicht über das provisionierte Telefon, unter anderem auch die IP-Adresse.

### Funktionstasten

Die Funktionstasten rechts und links vom Display sind dreifach belegbar. Ist die erste Seite vollständig belegt, wird die letzte Taste am Display zum "umblättern" verwendet.

#### Andere Benutzer (Nebenstellen) überwachen

Zur Überwachung anderer Benutzer oder Nebenstellen können Funktionstasten eingerichtet werden. Dazu eignen sich BLF-Tasten (Besetztlampenfeld oder Busy Lamp Field). Diese geben Informationen über den Status der überwachten Durchwahl. Überwachen bedeutet in diesem Fall zu sehen ob ein Benutzer telefoniert, angerufen wird und ggf. sein Gespräch heranzuholen (Pickup).

Tasten können auf verschiedenen Wegen konfiguriert werden.

#### Tasten belegen direkt am Telefon

Drücken Sie auf Ihrem Telefon ca. 5 Sekunden lang auf die Taste die Sie belegen möchten. Nun können Sie Ihre Taste (z. B. BLF-Taste) belegen.

|Einstellungen|Belegung|
|---|---|
|Typ|BLF|
|Konto ID|Leitung 1|
|Kontoname|Geben Sie hier eine Bezeichnung für die Taste an.|
|Wert|Die zu überwachende Durchwahl, z. B. 123 für die Durchwahl 123|

Drücken Sie zum Bestätigen auf *Speichern*.

#### Tasten belegen über das Web-UI

Im Tab `Speicher-Tasten` können die verschiedenen Tasten, z. B. BLF-Tasten am Telefon belegt werden:

|Typ|Wert|Name|Konto|
|---|---|---|---|
|BLF|Die zu überwachende Durchwahl, z. B. 123 für die Durchwahl 123|Geben Sie hier eine Bezeichnung für die Taste an.|Leitung 1|

Neben Benutzer-Durchwahlen können auch Einbuchcodes für Warteschlangen oder Durchwahlschalter konfiguriert werden.

#### Weitere nützliche Funktionstasten

|Funktionstaste|Beschreibung|
|---|---|
|**Speed Dial**|Hier kann eine Telefonnummer hinterlegt werden.|
|**DTMF**|Hier können DTMF-Zeichen hinterlegt werden.| -->

### Basis-Konfiguration

Wie bereits erwähnt, werden Yealink IP-Telefone  mit Hilfe der Basis-Konfiguration provisioniert. Die Basis-Konfiguration ist unter `Endgeräte` > `Basis-Konfigurationen` zu finden.

{{% notice note %}}
Bevor Sie die Basis-Konfiguration ändern, müssen Sie diese `Duplizieren`.
{{% /notice %}}

Ebenfalls können Sie eine schon bearbeitete Basis-Konfiguration als `Standard setzten`. Somit erhalten neu angelegte IP-Telefone automatisch die angepasste Basis-Konfiguration.

#### Zuweisung einer Basis-Konfiguration

Eine Basis-Konfiguration kann auf mehreren Wegen zugewiesen werden:

+ Über `Endgeräte` > `Basis-Konfigurationen` > Basis-Konfiguration auswählen und Bearbeiten, im Tab `Geräte` können gleich mehrere IP-Telefone hinzugefügt werden.
+ Über `Endgeräte` > `Geräteliste` > IP-Telefon auswählen und Bearbeiten im Tab `Basisdaten`.

#### BLF-Tasten konfigurieren über die Basis-Konfiguration

Im Tab `Konfiguration` können Sie die vorhandene Basis-Konfiguration anpassen. Im Bereich **keys** finden Sie bereits vorkonfigurierte Funktionstasten, an denen Sie sich orientieren können.

BLF-Tasten lassen sich wie folgt einrichten:

    {{!-- keys --}}
    linekey.3.type = 16
    linekey.3.value = 123
    linekey.3.label = Max

Die belegte Taste (in diesem Fall Linekey 3) besteht aus drei Parametern:

+ *type*: der Typ der Taste, 16 steht für BLF,
+ *value*: der Wert, das ist hier die Nebenstelle,
+ *label*: das Label, das ist die Bezeichnung, die am Display angezeigt wird.

Weisen Sie diese Basis-Konfiguration über den Tab `Geräte` den IP-Telefonen zu, die diese Taste auch in der Weise belegt haben sollen und speichern Sie. Nach dem Neustart der IP-Telefone werden die Änderungen auf diesen übernommen.


### Firmwareupdate

Ab der mobydick Version 7.14 wird die Firmware für IP-Endgeräte nicht mehr mitgeliefert. Sollte eine andere als auf dem IP-Endgerät installierte Firmware benötigt werden, muss diese selber heruntergeladen und in die pascom Firmware-Verwaltung hochgeladen werden.

#### Firmware hinzufügen

Die gewünschte Firmware kann hinzugefügt werden unter `Endgeräte` > `Firmware`:

|Einstellung|Beschreibung|
|---|---|
|Firmware-Datei|Laden Sie hier die Firware hoch. Diese finden Sie auf der [Download-Seite von Yealink](http://support.yealink.com/documentFront/forwardToDocumentFrontDisplayPage).|
|Model|Modellbezeichnung des Yealink-Telefons|
|Version|Firmware-Version|
|Dokumentation|Optionales Feld für Notizen|

#### Firmware ausrollen

Die Firmware kann über `Endgeräte` > `Geräteliste` aktualisiert werden. Wählen Sie die Zielgeräte in der Geräteliste mit Häkchen aus und klicken Sie auf `Aktion` > `Firmware ausrollen`. Nun erhalten Sie eine Übersicht der gewählen Geräte, in der Sie die Zielfirmware auswählen können. Anschließend klicken Sie auf `Firmware update` um die gewählte Firmware auszurollen.

#### Empfohlene Firmware

Da es für die verschiedenen IP-Telefone eine Vielzahl von Firmwares gibt ist es uns leider nicht möglich jede zu testen, so dass es sein kann, dass manche Firmware-Versionen pascom Funktionen nicht unterstützen. Daher finden Sie hier eine Liste der Firmwares die von uns bereits getestet wurden:

|Modell|Firmware|
|---|---|
|T41P|36.81.0.110|
|T46G|28.81.0.110, 28.73.0.50|
|T46S|66.81.0.20, 66.81.0.110|
