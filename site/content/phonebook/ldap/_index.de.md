---
title: Telefonbuch aus LDAP
description: Synchronisieren Sie Ihre Telefonbuch-Einträge gegen LDAP
weight: 40
---

{{< doctype "both" >}}

{{< description >}}


## Connector-Profil "Telefonbuch aus LDAP"

Erstellen Sie ein neues Connector-Profil indem Sie in der pascom Web-UI unter dem
Menüpunkt {{< ui-button "Erweitert" >}} > {{< ui-button "Connector" >}} auf {{< ui-button "Hinzufügen" >}} klicken.

Wählen Sie die Vorlage *Telefonbuch aus LDAP* und tragen Sie folgende Daten ein:

|Feld|Beschreibung|
|---|---|
|**Bezeichung**|Name des Connectors|
|**LDAP URI**|URL zum LDAP-Verzeichnis|
|**BaseDN**|BaseDN gibt die Position im LDAP-Verzeichnis an, die ausgelesen werden soll|
|**LDAP bindDN**|Benutzer mit Zugriff auf das LDAP-Verzeichnis|
|**Passwort**|Passwort zur Authentifizierung an LDAP|
|**Suchfilter**|Filter zur detaillierten Suche im LDAP-Verzeichnis|

Nach dem Speichern kann die Vorlage im Reiter {{< ui-button "Basisdaten" >}} bei Bedarf angepasst werden.

### Basisdaten

In den Basisdaten konfigurieren Sie die Verbindung zu Ihrem LDAP genauer oder können die zuerst konfigurierten Einstellungen ändern.

|Feld|Beschreibung|
|---|---|
|**Bezeichung**|Name des Connectors (*wird automatisch befüllt*)|
|**Modus**|**Neue Sätze importieren, geänderte abgleichen und früher importiere Datensätze entfernen**: (*Standardauswahl*) Importiert nur neue Telefonbucheinträge und gleicht geänderte Einträge ab, alte Einträge werden entfernt. <br/>**Neue Sätze importieren und geänderte abgleichen**: Importiert neue Telefoneinträge und gleicht geänderte ab. Es werden keine Einträge entfernt.|
|**URI**|Uri zum LDAP (*wird automatisch befüllt*)|
|**Basis DN**|Basis DN Einträge zum LDAP (*wird automatisch befüllt*)|
|**Benutzername** und **Passwort**|Zugangsdaten zum im LDAP angelegten pascom Benutzer zur Authentifizierung (*wird automatisch befüllt*)|
|**Suchfilter**|LDAP-Suchfilter zur Filterung des auszulesenen Telefonbuch-Ordners (*wird automatisch befüllt*)|
|**Dokumentation**|Dient zur Dokumentation/ Beschreibung des Connectors|

### Pre Filter

Im Standard importiert die Vorlage alle globalen Telefonbucheinträge aus dem LDAP. Über den Reiter {{< ui-button "Pre Filter" >}} können Sie den Import eines bestimmten Telefonbuchs, z. B. *company-phonebook*, einschränken. Fügen Sie dazu folgenden Code ein:

    if (strpos($row['memberOf'],'company-phonebook') !== false) {
    return true;
    }
    return false;

### Telefonbuchfelder aus LDAP

Über den Reiter {{< ui-button "Variablen" >}} können Sie in der Spalte **Quelle** definieren aus welchem Telefonbuchfeld in LDAP die Informationen ausgelesen werden können. Auf der linken Seite ist die **Variable** definiert, die zum Importieren der Daten in die pascom Telefonanlage gesetzt werden kann.

Die bereits gesetzten Felder sind lediglich ein Vorschlag der Vorlage. Sie können Felder hinzufügen und entfernen bzw. die gesamte Import-Struktur beliebig anpassen.

### Importlauf testen und aktivieren

Nachdem Sie die Konfiguration abgeschlossen haben, können Sie durch die Schaltfläche {{< ui-button "Speichern und Simulieren" >}} testen welche Datensätze importiert werden würden. Wenn Sie mit dem Ergebnis zufrieden sind können Sie den Import entweder einmalig unter {{< ui-button "Aktion" >}} > {{< ui-button "Import jetzt durchführen" >}} ausführen oder durch die Schaltfläche {{< ui-button "Automatisieren" >}} eine regelmäßige Durchführung des Importes einrichten.

### Optionale Einstellungen

#### Feldzuordnung anpassen

Im Connector Profil können Sie im Reiter {{< ui-button "Variablen" >}} und {{< ui-button "Struktur" >}} die Feldzuordnung LDAP > pascom Telefonbuch an Ihre Bedürfnisse anpassen.

Als Beispiel möchten wir Hinweise zu dem Kontakt im Notizfeld des pascom Telefonbuches speichern.
Fügen Sie hierzu im Reiter {{< ui-button "Variablen" >}} folgende Zeile durch {{< ui-button "Hinzufügen" >}} ein:

|Variable|Quelle|
|----|----|
|Notiz|return $row["info"];|

Durch diese Zeile speichert der Connector den Inhalt des LDAP Feldes "info" in der Variable "Notiz" ab.
Diese Variable muss nun unter {{< ui-button "Struktur" >}} dem Notiz pascom-Telefonbuch Feld zugeordnet werden.

Ergänzen Sie hierzu die Zeilen:

          "028pho_notes" :        "{{{Notiz}}}"

**in der Struktur:**

        {
          "phonebook": [{
            "028pho_bez" :  "{{{DisplayName}}}",
            "028pho_phone" : "{{{BusinessPhone}}}",
            "028pho_firstname" :  "{{{GivenName}}}",
            "028pho_lastname" : "{{{Surname}}}",
            "028pho_organisation" : "{{{CompanyName}}}",
            "028pho_email" :  "{{{EmailAddress}}}",
            "028pho_mobile" : "{{{MobilePhone}}}",
            "028pho_homephone" :  "{{{HomePhone}}}",
            "028pho_fax" :  "{{{BusinessFax}}}",
            "028pho_notes" :  "{{{Notiz}}}"
          }]
        }

Dadurch wird der Wert der Variablen Notiz dem **Notiz** pascom Telefonbuch Feld zugewiesen.

#### Labels nutzen

pascom Labels lassen sich auch dazu nutzen zusätzliche Informationen aus LDAP
mit im pascom Firmentelefonbuch anzuzeigen.

In diesem Beispiel möchten wir die Kundennummer des LDAP Kontakts im Label **Kundennummer**
abspeichern. Dieses Label ist dann nicht nur im Telefonbuch sondern auch in Journaleinträgen oder diversen Anruferinformationen sichtbar.

##### Label anlegen

Labels legen Sie im Menü {{< ui-button "Anrufverteilung" >}} > {{< ui-button "Anruf Labels" >}} durch Klicken auf die Schaltfläche {{< ui-button "Hinzufügen" >}} an.

Wählen Sie {{< ui-button "Generisches Label" >}}, vergeben Sie den Namen **Kundennummer** und klicken auf {{< ui-button "Speichern" >}}.

Wenden Sie ausstehende Jobs an um das Label anzulegen.

##### Connector Profil anpassen

Fügen Sie hierzu im Reiter {{< ui-button "Variablen" >}} folgende Zeile durch {{< ui-button "Hinzufügen" >}} ein:

|Variable|Quelle|
|---|---|
|Customernumber|return $row['Customernumber'];|

{{% notice info%}}
Im Gegensatz zu anderen Connector-Profilen muss der Name der Variablen und
der Name des Quellfeldes (hier "Customernumber") identisch sein.
{{% /notice  %}}

Durch diese Zeile speichert der Connector den Inhalt des LDAP Feldes "Customernumber" in der gleichnamigen Variable "Customernumber" ab.

Diese Variable muss nun unter {{< ui-button "Struktur" >}} dem Label **Kundennummer** pascom Feld zugeordnet werden.

Ergänzen Sie hierzu die Zeilen:

```
"post": {
            "phonebook.phonebooklabel": [
                {
                    "050lab_bez": "Kundennummer",
                    "028050pholab_value": "{{{Customernumber}}}"
                }
            ]
}
```

in der Struktur:

```
{
  "phonebook": [{
    "028pho_bez" :          "{{{DisplayName}}}",
    "028pho_phone" :        "{{{BusinessPhone}}}",
    "028pho_firstname" :    "{{{GivenName}}}",
    "028pho_lastname" :     "{{{Surname}}}",
    "028pho_organisation" : "{{{CompanyName}}}",
    "028pho_email" :        "{{{EmailAddress1}}}",
    "028pho_mobile" :       "{{{MobilePhone}}}",
    "028pho_homephone" :    "{{{HomePhone}}}",
    "028pho_fax" :          "{{{BusinessFax}}}",
    "post": {
            "phonebook.phonebooklabel": [
                {
                    "050lab_bez": "Kundennummer",
                    "028050pholab_value": "{{{Customernumber}}}"
                }
            ]
    }
  }]
}
```

Dadurch wird jedem Kontakt mit eingetragener Kundennummer das Label **Kundennummer** mit
dem entsprechenden Wert zugeteilt.

##### Ergebnis prüfen

{{% notice info%}}
Label-Zuordnungen werden NICHT unter "Speichern und Simulieren" mit angezeigt
{{% /notice  %}}

Prüfen Sie die erfolgreiche Zuordnung des Labels in der pascom Web-UI unter {{< ui-button "Benutzer" >}} > {{< ui-button "Telefonbuch" >}} indem Sie einen ensprechenden Kontakt {{< ui-button "Bearbeiten" >}} und die Zuordnung im Reiter {{< ui-button "Labels" >}} prüfen. Alternativ können Sie auch das Firmentelefonbuch im pascom Client einsehen.

{{% notice info %}}
Ggf. ist es notwendig den XMPP-Dienst unter {{< ui-button "Anwenden">}} > {{< ui-button "XMPP Server neu starten">}} neu zu starten, um alle mit der pascom verbundenen Clients neu zu starten und damit mit der Telefonanlage zu synchronisieren, damit alle konfigurierten Labels korrekt angezeigt werden.
{{% /notice %}}
