---
title: DATEV Integration
description: Integrieren Sie DATEV in Ihre pascom.
weight: 50
---

{{< doctype "both"  >}}

{{< description >}}

## Konzept

Die DATEV-Schnittstelle ermöglicht es bei einem eingehenden Anruf die Anrufdaten in Ihre *DATEV Arbeitsplatz pro*-Software zu übertragen. Ebenso können Sie aus dem DATEV-Telefonbuch Gespräche starten. Voraussetzung ist die Verwendung von *DATEV Arbeitsplatz pro* mit dem *Telefoniemodul*

## Konfiguration

Zur Vorbereitung muss zunächst ein *Generisches Label* angelegt werden. Klicken Sie hierfür auf {{< ui-button "Anrufverteilung" >}} > {{< ui-button "Anruf Labels" >}} > {{< ui-button "Hinzufügen" >}}. Wählen Sie {{< ui-button "Generisches Label" >}} und tragen Sie als *Label Name* **DATEV** ein. *Im Client anzeigen* sollten Sie auf *NEIN* setzen.

Anschließend ist die DATEV-Schnittstelle automatisch aktiv sobald Sie neben *DATEV Arbeitsplatz pro* mit Telefoniemodul den [pascom Client]({{< relref "clients/desktop-installation">}}) installieren.

Sollte das Label nicht angelegt sein, erscheint bei Start des Classic Clients folgende Meldung:

![Kein DATEV-Label konfiguriert](no-label.de.png?width=250px)

## Bedienung

### Eingehender Anruf

Bei einem eingehenden Anruf werden die DATEV-Stammdaten abgefragt und Treffer in der Anruf-Notification angezeigt.

![DATEV Notification](notification.de.png)

Schon während des Läutens ist es möglich über den DATEV-Klick die Telefonie-Daten in die Telefonliste Ihres *DATEV Arbeitsplatz pro* zu übertragen.

Nach einem Anruf können die Daten über den DATEV-Klick aus dem Journal übertragen werden.

![DATEV Journal](journal.de.png)

Sollten zu einer Telefonnummer mehrere Einträge in den DATEV-Stammdaten zu finden sein, erscheint eine Liste mit den möglichen Treffern und Sie können den richtigen Kontakt für die Datenübertragung auswählen.

![DATEV Eintrag auswählen](select_entry.de.png)

**DATEV-Einstellungen im Classic Client**

Im Classic Client können unter {{< ui-button "Einstellungen" >}} > {{< ui-button "Adressbücher" >}} Einstellungen vorgenommen werden:

![DATEV Einstellungen](full-auto.de.png)

|Einstellungen|Beschreibung|
|---|---|
|Reihenfolge der Telefonbücher|Verwenden Sie den Classic Client auf einer Arbeitsstation auf dem auch *DATEV Arbeitsplatz pro* installiert ist, wird immer als erstes das DATEV-Telefonbuch abgefragt.|
|DATEV-Integration ist aktiviert|Hier kann die Verwendung der DATEV-Schnittstelle deaktiviert/aktiviert werden.|
|Bei Telefonbuch-Suche verwenden|Hier kann angegeben werden, ob bei einem einkommenden Anruf das DATEV-Telefonbuch durchsucht werden soll.|
|Cache aktualisieren|Wenn Sie in den DATEV-Stammdaten Änderungen vornehmen, kann es bis zu 2 Stunden dauern, bis diese synchronisiert werden. Möchten Sie die Änderungen sofort synchronisieren, klicken Sie hier auf {{< ui-button "Aktualisieren" >}}|
|Automatische Datenweitergabe|Hier können Sie einstellen, ob Anrufdaten erst nach dem DATEV-Klick oder automatisch in die DATEV-Stammdaten übertragen werden sollen.|


### Ausgehender Anruf

Bei Ausgehenden Anrufen werden folgende Funktionen unterstützt:

* Wird eine Nummer über den pascom Client oder einem Hardware-Telefon gestartet, erscheint in der Gesprächs-Notification der DATEV-Klick. Über den Klick können die Gesprächs-Daten an die DATEV-Software übertragen werden. Ist das Gespräch beendet, können die Daten über den DATEV-Klick aus dem Journal heraus übertragen werden.
* Wird im  Client-Telefonbuch nach einem Kontakt gesucht, wird auch das DATEV-Telefonbuch durchsucht.
* Aus der Kontaktliste in der *DATEV Arbeitsplatz pro* kann ebenfalls ein Kontakt angerufen werden.
