---
title: Univention (UCS)
keywords:
    - univention
    - ucs
description: Integrieren Sie Univention Corporate Server in Ihre pascom.
prev: /integrationen/microsoft-active-directory-integration/
url: /integrationen/univention-integration/
weight: 106
toc: true
---

![microsoft exchange](/connector-ucs.png?width=10%)

## Konzept

Univention Corporate Server (kurz UCS) ist ein auf Debian basierender Server, mit integriertem Managementsystem für zentrale und plattformübergreifende Verwaltung von Servern, Diensten, Desktops und Benutzern. Weitere Informationen finden Sie [hier](https://www.univention.de/).

Mit dem pascom Connector für UCS können Sie Benutzer importieren und synchronisieren. Zusätzlich kann die Authentifizierung der pascom Benutzer gegen UCS aktivieren werden.

## Konfiguration

### Vorbereitung

#### Installation der pascom App auf dem UCS

Bevor Benutzer aus dem UCS in die pascom importiert werden können, müssen auf dem UCS eine App installiert werden und ein paar Einstellungen vorgenommen werden. Loggen Sie sich hierfür auf die Weboberfläche Ihres UCS-Servers ein.
Apps können über das App Center heruntergeladen und installiert werden. Das App Center findet man unter dem Menüpunkt `Software` -> `App Center`.
Suchen Sie über die Suchfunktion nach der gewünschten App , in unserem Fall *mobydick*. Die App kann nun ausgewählt installiert werden.

#### UCS Rechner für pascom anlegen

Ist die *mobydick* App erfolgreich installiert, muss der pascom Server als Rechner im UCS hinzugefügt werden.
Über `Geräte` -> `Rechner` kann der pascom Server hinzugefügt werden.
Anschließend erscheint ein Popup-Fenster, wählen Sie unter dem Punkt *Rechner: Windows Workstation/Server* den Typ *Rechner:Linux* und klicken Sie weiter. Im nächsten Fenster müssen Sie nur einen Rechnernamen vergeben (z. B. pascom), die anderen Felder sind ortional. Diesen Namen wird die pascom nachher verwenden um sich beim UCS zu authentifizieren.

Wählen Sie nun in der Rechnerliste den neu angelegten Server aus und vergeben Sie unter `Erweiterte Einstellungen` ein Passwort. Dieses Passwort wird die pascom nachher verwenden um sich beim UCS zu authentifizieren.

#### UCS Benutzer für pascom frei schalten

Benutzer die im UCS angelegt sind werden nicht automatisch von der pascom importiert. In den Benutzereinstellungen unter `Erweiterte Einstellungen` muss bei jedem Benutzer der imporiert werden soll bei *MobyDick* ein Häkchen gesetzt werden für *Mobydick erlaubt*.


### Connector-Profil für UCS anlegen

Erstellen Sie ein neues Connector-Profil indem Sie in der pascom Web-UI unter dem
Menüpunkt `Erweitert` > `Connector` auf `Hinzufügen` klicken.

Wählen Sie die Vorlage *Benutzer aus UCS* und tragen Sie folgende Daten ein:

|Feld|Beschreibung|
|---|---|
|**Bezeichung**|Name des Connectors|
|**AD Domäne**|UCS Domain z.B. mydomain.intranet|
|**AD Server**|Server IP oder DNS-Name des Hosts|
|**Benutzername** und **Passwort**|Der zuvor angelegte mobydick Rechner und das dazugehörige Passwort|
|**Authentifizierung konfigurieren**|**NEIN**: Benutzer werden nur importiert und authentifizieren sich gegen die pascom<br>**JA**: Benutzer werden importiert und können sich gegen USC authentifizieren. In diesem Fall wird die Authentifizierung eingerichtet und Sie können unter `Appliance` > `Dienste` im Reiter `Authentifizierung` bei Bedarf anpassen.|

Nach dem Speichern kann die Vorlage im Reiter `Basisdaten` bei Bedarf angepasst werden.

#### Benutzerfelder im UCS

|UCS|pascom|Bescheibung|
|---|---|---|
|Allgemein > Benutzeranmeldename|Anmeldename|Der Anmeldename wird für sämtliche Anmeldung verwendet und darf nur Kleinbuchstaben enthalten. Pflichtfeld.|
|Allgemein > Anzeigename|Anzeigename |Der Anzeigename erscheint auf allen Telefondisplays und im pascom Client. Pflichtfeld.|
|Allgemein > Vorname|Vorname|Vorname des Benutzers für den pascom Telefonbucheintrag.|
|Allgemein > Nachname|Nachname|Nachname des Benutzers für den pascom Telefonbucheintrag.|
|Allgemein > Primäre E-Mail-Adresse|EMail|E-Mail Adresse des Benutzers. Wird für den Versand von Voicemails und Faxen benötigt.|
|Kontakt > Telefonnummer|Durchwahl|Die interne Durchwahl des Benutzers. Wird diese nicht im AD gepflegt, vergibt pascom automatisch die nächste freie Durchwahl aus dem Telefonnummernpool.|
|Kontakt > Telefonnummer Festnetz|Telefon privat|Private Telefonnummer des Benutzers für den pascom Telefonbucheintrag.|
|Kontakt > Telefonnummer Mobil|Handy|Mobilnummer des Benutzers für den pascom Telefonbucheintrag.|

Die Felder sind lediglich ein Vorschlag der Vorlage. Sie können Felder hinzufügen und entfernen bzw. die gesamte Import-Struktur beliebig anpassen.

#### Importlauf testen und aktivieren

Nachdem Sie die Konfiguration abgeschlossen haben, können Sie durch die Schaltfläche `Speichern und Simulieren` testen welche Datensätze importiert werden würden. Wenn Sie mit dem Ergebnis zufrieden sind können Sie den Import entweder einmalig unter `Aktion` > `Import jetzt durchführen` ausführen oder durch die Schaltfläche `Automatisieren` eine regelmäßige Durchführung des Importes einrichten.

#### Authentifizierung testen

Haben Sie in der Vorlage *Authentifizierung konfigurieren* auf *JA* gesetzt können Sie nun unter `Appliance` > `Dienste`
im Reiter `Authentifizierung` mit der Schaltfläche `Anmeldung Testen` testen ob die Authentifizierung Ihrer Benutzer funktioniert.
