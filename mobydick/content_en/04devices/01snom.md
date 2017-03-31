---
title: Snom VoIP Phones
keywords: 
    - Snom 
    - Desktop Phones
    - provisioning
    - 300, 320, 360, 370, 710,715, 720, 760
    - D705, D715, D725, D765
    - Snom BLF Key
    - Busy Lamp Field
    - Snom Firmware
description: All Snom IP telephone models are supported by mobydick and here is how to integrate your Snom VoIP Desktop Phone.
url:  /endpoints/snom-ip-telephones-300-700-series/
linkde: /endgeraete/snom-tischtelefone-300-700-serie/
prev: /endpoints/
next: /endpoints/grandstream-ip-telephones-gxp-gxv-series/
weight: 41
toc: true
---

![snom 300/700 series](/snom-series.png)

## Compatability

|Provisioning|Firmware Management|Desktop Client CTI Control|pascom Menu|
|---|---|---|---|
|yes|yes|yes|yes|

**Provisioning**: The IP phone is manageable via the PBX web UI.<br>
**Firmware Management**: Firmware can be managed and updated via the PBX web UI.<br>
**Desktop Client CTI Control**: The desktop UC client can remotely control the phone, i.e. to start calls.<br>
**pascom Menu**: A phone touch key will be assigned to access the pascom Menu.

{{% notice warning%}}
Necessary Requirements  
In order to automatically deploy (AutoProvision) Snom IP Telephones, a functioning DHCP server is required.
{{% /notice %}}

## Configuration

With [our VoIP Software] (https://www.pascom.net/en/mobydick-voip/ "pascom VoIP phone systems") it is possible to centrally and automatically configure Snom IP Telephones, both 3xx and 7xx series. This process is know as `Provisioning`. For this purpose, pascom phone systems include a Default Configuration (`Devices > Basic Configuration`). For most deployment scenarios, these standard settings provide a sufficient set of parameters. However, in some cases, the settings may need to be modified.

{{% notice tip%}}
When modifying the default configuration settings, ensure you make a copy of the original and edit only the copy. 
{{% /notice %}}

{{% notice tip%}}
By new installations, you should first test the provisioning process with a telephone. Should this be successful then you will be able to deploy further telephones.
{{% /notice %}}

### Preparation

In order to automatically deploy (AutoProvision) Yealink Telephones, a functioning DHCP server is required.
[Network Planning and Configuration](../../server/network-configuration/).

### Device Commissioning

Connect the phone to your network. Yealink IP phones come with a built in switch, allowing you to connect the phone directly via the Ethernet port labelled as **Internet**. Should you not have a **PoE** option available, connect the phone to a power supply.

The IP phone will now boot and will be The phone will now boot and acquires an IP address and the corresponding Basic Configurations via **DHCP**. After this process is completed, the PBX will **automatically** add the device to the `device list as well as adding the appropriate SIP peer.

As mentioned above, for every device mobydick will also automatically add a SIP peer. In addition, the device username and password will also be automatically generated. The username consists of a randomly generated string followed by the last six digits of the device’s MAC address (15 digits in total). As the IP phones are automatically provisioned, you will not be required to enter this data manually and it is not possible to modifiy the user data. This is designed to considerably increase security against SIP Brute Force attacks.

The Device Name will be automatically added as signified by the vendor (Snom) and the MAC Address. On most IP phones, the MAC address is noted on the device housing, allowing phones to be more simply deployed on site in the correct locations.

After a successful provisioning, the IP phone display should show to correct language and time as well as the text `Emergency Only`

{{% notice info%}}
After the successful phone provisioning, the admin user will be reset by the PBX with the following credentials:  
<br>Username: *admin*
<br>Password: *0000*
{{% /notice  %}}

The Telephone Admin User Password can be changed within the Web UI under system settings. Use the search box and search for the parameter *sys.peripherals.access.password* and enter your desired password. Finally, you will be required to manually apply the Telephony Configurations and restart the endpoint.

### Assigning Users

As soon as the IP phone has appeared in the Device List, it can be edited via the `Edit` button. Under the `Assign` tab, the phone can be assigned to a [user (or location)](../../users/users-and-locations/). 

After saving your assignments and reapplying the telephony configurations, all affected IP phones will restart.

### Function Testing

The simplest method of testing whether a device has been successfully deployed is to call ones Voicemail box via **\*100**. On successfully provisioned phones, you should now hear your Voicemail box prompts.

### pascom Menu Key

After the provisioning process, the **Menu** button on Snom phones is no longer assigned to the Telephone Menu, but rather to a telephone specific pascom Menu making the following pascom phone system functions available:

|Function|Description|
|---|---|
|Telephone Book|Opens up the central PBX phonebook.|
|Journal|Displays answered, dialled and missed calls|
|Call Forwarding|Sets a call forwarding, activates / updates a previously configured call forwarding or deactivates an active call forwarding.|
|Voicmail Box|Voicemail box menu for activating/deactivating your mail box, plus message play backs|
|Login|Enables a user to log into the location where the phone is (Hotdesking / roaming users).|
|Logout [*username*]|Logs out the current user from this location.|
|Teams (Queues)<!--FIXME-->|Is used for agent management within a queue (login, logout, pause..) according the configuration of the queue.|

Should the Snom IP telephone not have a menu key (i.e. Snom 300, 710 or D715), then the second functions key be assigned with the pascom menu function.

{{% notice tip%}}
Only set Call Forwardings via the pascom menu as they can then be managed by the PBX and reflected within the desktop UC client etc.
{{% /notice %}}

{{% notice info%}}
 Using the DND key (*do not disturb*) directly on your Snom phone, ensures that the assigned user extension cannot be reached on the phone. The DND notice will appear only on the telephone itself and will have no impact on other endpoints or the Desktop UC client (softphone).
{{% /notice %}}

### Accessing the Snom Telephone Web UI

In order to access your telephone's web UI, you will need to know the phone's IP address. The following outlines the different methods of discovering the phone IP Address:

**Finding the IP-Address on the Telephone**

Press the **?** (i.e. the **help**) in order to call up the phone IP address.

**Finding the IP-Address via the Web UI Device List**

Log into the PBX Web UI and select the `Devices` > `Device list`, which provides you an overview of all available devices. To the left of each entry is an *Info* symbol which when clicked will open an overview of the provisioned telephone including the IP address.

**Admin Rights** 

In order to access certain menu options with the Snom Telephone web UI, you will require admin rights. To do this simply go the **Advanced** menu point and now enter the Admin Password. 

### Assigning Function Keys via the Phone Web UI.

In the menu of the left, click on the `Function Keys` option.

**User / Extension Monitoring with BLF Keys**

Using the function keys, it is possible to monitor other extensions (i.e. users). The BLF keys (Busy Lamp Field) can be used to provide status information relating to the monitored extension. In this scenario, monitoring means watching the extension to see if the user is currently on the phone, being called or to answer calls intended for this extension (call pickup). 

|Context|Type|Number|Short Text|
|---|---|---|---|
|Select Account / Identity|**Extension**|The extension to be monitored (e.g. 123) in the following format <sip:123@192.168.100.1>|Should the telephone have a second display for paperless keys, then the keys labels can be entered here.|

Alongside user extension, it is also possible to to configure keys as login / out codes for [queues](../../users/add-teams/) or to configure them as an [extension switch](../../call-distribution/business-hours/#using-extension-switches).

**Additional Useful Function Keys**

|Function Key|Description|
|---|---|
|**Speed Dial**| Can be assigned with a telephone number.|
|**DTMF**|Can be assigned with DTMF characters.|

### Default Configuration

As previously stated, Snom IP phones are provisioned using the default configurations which can be found under `Devices`> `Basic Configurations`.

{{% notice tip%}}
When modifying the default configuration settings, ensure you make a duplicate copy of the original using the `Duplicate`tool. 
{{% /notice %}}

In addition, you can set an already edited default configurations as the `standard settings`. Doing so ensures that all newly added IP telephones will automatically be provisioned with these default configurations.

**Assigning a Default Configuration**

A default configuration can be assigned using multiple methods:

+ Via `Devices`> `Basic Configurations` > Choose your Basic configuration set and press `Edit` Under the `Devices` tab, it is possible to add multiple IP telephones.
+ Via `Devices`> `Device list` > Select and edit the IP Telephone and under the tab `Basic Data` choose the correct **Basic configuration** option. 

**Automatic BLF Key Configuration via Basic Configurations**

Under the `Configuration` tab, it is possible to modify the existing basic configuration. Under the **Keys** section you will find the already pre-configured function keys which provide a useful guideline to work with.

Surfen Sie auf das Web-UI Ihres Snom Telefons und belegen Sie unter *Funktionstasten* als Beispiel die Taste **P1**. Wählen Sie als Typ **Nebenstelle**, als Nummer **123** und als Label **Musterbenutzer**. Übernehmen Sie die Einstellungen.

Klicken Sie auf den Menüpunkt *Einstellungen*. Falls Sie den Menüpunkt noch nicht sehen, benötigen Sie [Admin-Rechte](../snom-tischtelefone-300-700-serie/#auf-die-snom-weboberfläche-zugreifen).<br>
Suchen Sie nach *fkey0* und *fkey_label0*. Die gefundenen Zeilen tragen Sie anschließend in der Basis-Konfiguration über das Web-UI der mobydick ein:

    {{!-- keys --}}
    fkey0: dest <sip:123@192.168.100.1>
    fkey_label0: Zentrale

Weisen Sie diese Basis-Konfiguration über den Tab `Geräte` den IP-Telefonen zu, die diese Taste auch in der Weise belegt haben sollen und Speichern Sie nach dem Neustart der IP-Telefone werden die Änderungen auf diesen übernommen.

### Firmwareupdate

Ab der mobydick Version 7.14 wird die Firmware für IP-Endgeräte nicht mehr mitgeliefert. Sollte eine andere als auf dem IP-Endgerät installierte Firmware benötigt werden, muss diese selber heruntergeladen und in die mobydick Firware-Verwaltung hochgeladen werden.

**Firmware hinzufügen**

Die gewünschte Firmware kann hinzugefügt werden unter `Endgeräte` > `Firmware`:

|Einstellung|Beschreibung|
|---|---|
|Firmware-Datei|Laden Sie hier die Firware hoch. Diese finden Sie auf der [Wiki-Seite von Snom](http://wiki.snom.com/Category:Firmware).|
|Model|Modellbezeichung des Snom-Telefons|
|Version|Firmware-Version|
|Dokumentation|Optionales Feld für Notizen|

**Firmware ausrollen**

Die Firmware kann über `Endgeräte` > `Geräteliste` aktualisiert werden. Wählen Sie die Zielgeräte in der Geräteliste mit Häkchen aus und klicken Sie auf `Aktion` > `Firmware ausrollen`. Nun erhalten Sie eine Übersicht der gewählen Geräte, in der Sie die Zielfirmware auswählen können. Anschließend klicken Sie auf `Firmware update` um die gewählte Firmware auszurollen.

**Empfohlene Firmware**

Da es für die verschiedenen IP-Telefone eine Vielzahl von Firmwares gibt ist es uns leider nicht möglich jede zu testen, so dass es sein kann, dass manche Firmware-Versionen mobydick Funktionen nicht unterstützen. Daher finden Sie hier eine Liste der Firmwares die von uns bereits getestet wurde:

|Modell|Firmware|
|---|---|
|Snom 300|8.7.3.25.5|
|Snom 320|8.7.3.25.5|
|Snom 360|8.7.3.25.5|
|Snom 370|8.7.3.25.5|
|Snom 710|8.7.3.25.5|
|Snom 715|8.7.8.8.2|
|Snom 720|8.7.3.25.5|
|Snom 760|8.7.3.25.5|