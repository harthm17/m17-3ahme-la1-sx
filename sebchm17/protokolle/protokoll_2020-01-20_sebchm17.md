# Protokoll Labor/SX 3AHME (2019/20)

* **Thema** : Einführung Raspberry PI
* **Datum** : 20.01.2020
* **Gruppe** : 4
* **Gefehlt** : Richard Strohrigel
* **Protokollverfasser** : Christoph Sebernegg
* **Protokoll letzte Einheit** : [2.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/sebchm17/sebchm17/protokolle/protokoll_2019-10-14_sebchm17.md)
--------------------------------------------------------------------------------------------------------------------------------
## Inhaltsverzeichnis
1.  [Vorteile und Nachteile des Raspberry PI und Arduino Nano](#vorteile-und-nachteile-des-raspberry-pi-und-arduino-nano)
1.  [Betriebssysteme am Raspberry](#Betriebssysteme-am-raspberry)
1.  [Installation](#installation)
1.  [Name und Passwort Ändern](#name-und-passwort-ändern)
1.  [Man in the Middle](#man-in-the-middle)

--------------------------------------------------------------------------------------------------------------------------------
## Vorteile und Nachteile des Raspberry PI und Arduino Nano
Ein Microcontroller kann für seinen Preis sehr viel aber es ist nicht möglich ihn in ein Netzwerk einzubinden, weil er keine Daten verschlüsseln kann.
Der Raspberry hat mehr Rechenleistung und ist größer weil die CPU mehr Pins hat.


|     | Arduino Nano | Raspberry PI | 
|-----|--------------|--------------|
| CPU |geringe Leistungsfähigkeit| wesentlich leistungsfähiger (um das 1000-fache als ein Arduino Nano)|
|Architektur|8-Bit Architektur|32-Bit Architektur|
|Preis| 1-3€ |  Raspberry Zero: 12-14€  , Voller PI: 30€|
|Betriebssystem| kein Standard Betriebssystem| Standard Betriebssystem möglich|
| | |- Raspian(Linux, Debian)|
|Leistung|~0,022kWh(auf ein Jahr)|~8,70kWh(auf ein Jahr)|
|Echtzeitfähig|Ja|Nein|


*Anwendung des Arduino:*
Überwachungssysteme, Sensoren, ...

*Anwendung des Raspberry PI's:*
Home Server & Mediacenter, ...

Echtzeit bedeuted, wenn eine Aufgabe mit einer Zeitschranke zeitnah erfüllt wird.

--------------------------------------------------------------------------------------------------------------------------------------------

# Betriebssysteme am Raspberry

Es gibt drei verschiedene Varianten vom Raspain-Betriebssystem.

* Raspbian Buster with desktop and recommended software
* Raspbian Buster with desktop
* Raspbian Buster Lite

[Download Raspbain](https://www.raspberrypi.org/downloads/raspbian/)

Für die den Gebrauch in der Schule benutzten wir das Raspbian Buster Lite.

Auf den neuesten Modelle des Raspberry PI ist es sogar möglich Windows darauf laufen zu lassen, weil sie so leistungsfähig sind.

--------------------------------------------------------------------------------------------------------------------------------------------

## Installation

1. Gewünschtes Betriebssystem downloaden als Zip-Datei.
2. Bei Linux braucht man kein Zusatzt Tool. Die Zip-Datei kann direkt auf die MMC-Karte kopiert werden.

          unzip-p Downloads/2019-09-26-raspain-buster-lite.zip | dd bs=4M of=/dev/nmcblk0

3. Windows benötigt ein zusätzliches Tool. Windows braucht ein Dateisystem.

4. Secure Shell aktivieren
   Den Raspberry Pi sollte man wenn möglich per Bildschirm, Tastatur und Maus in Betrieb nehemen, weil dann ist es möglich auf der MMC Karte                                                  in der Boot Partition eine Datei mit dem Namen ssh anzulegen. Bei Windows darf man keine Dateiendung dazuschreiben weil dann beim boot die datei von der ssh gelöscht wird.
   



## Secure Shell 

Die Secure Shell kann verschlüsselte Netzwerkverbindung mit einem entfernten Gerät herstellen.


Früher war die Secure Shell standardmäßig aktiviert, aber das wurde zum Problem, da der Standarbenutzer und das Passwort auf jedem Raspberry PI gleich ist. Wenn das Passwort nicht wird kann ein jeder auf den PI zugreifen und möglicherweise eine Schaden anrichten.

          mount /dev/mmcblk0p1
          touch /media/schueler/boot/ssh
          unmount /dev/mmcblk0p1
          unmount /dev/mmcblk0p2
 
 Über SSH auf dem Gerät einsteigen
 Ip-Adresse des Raspberry PI's: 10.200.114.216
          sshpi@10.200.114.216
          passwort: raspberry

Nun überprüft man ob man auf seinem eigenen Gerät ist mit dem Komando 'ip a'.

--------------------------------------------------------------------------------------------------------------------------------------------

## Name und Paswort Ändern

Name ändern:

          sudo /nano/etc/hostname

Aussteigen:

          sudo reboot

Passwort ändern:
         
         passwd
         
Man ändert den Namen und das Passwort, weil der Standard Login bei jedem Raspberry PI gleich ist und nachdem der Login geändert wurde kann kein anderer mehr auf den Raspberry PI zugreifen.

--------------------------------------------------------------------------------------------------------------------------------------------

## Man in the Middle

Man in the Middle: 

Login name und passwort werden über das Netzwerk transportiert. Ein "*Man in the Middle*" ist ein Angreifer der logisch zwischen den kommunizierenden Geräten steht und hat dabei mit seinem System vollständige Kontrolle über den Datenverkehr zwischen zwei oder mehreren Netzwerkteilnehmern und kann die Informationen nach Belieben einsehen und sogar manipulieren.

![MIA](http://wiki.cas.mcmaster.ca/images/3/38/Man_in_the_Middle.jpg)

Hostkeys:
>Mithilfe des Netzwerkprotokolls SSH können Sie eine sichere und verschlüsselte Netzwerkverbindung zu einem entfernten Gerät wie z. B. einem Server herstellen. Mit einer solchen SSH-Verbindung warten Sie den Server von Ihrem lokalen Computer aus oder bedienen ihn per Kommandozeile. Abhängig von der genutzten Version des Protokolls kommen dabei verschiedene Verschlüsselungsalgorithmen zum Einsatz – SSH-2 greift beispielsweise standardmäßig auf AES zurück. Der Verschlüsselung der Verbindung muss allerdings zunächst eine erfolgreiche Authentifizierung vorausgehen. Während der Server sich gegenüber dem Client mit einem Sicherheitszertifikat identifiziert, gibt es verschiedene Varianten zur Anmeldung des Clients auf dem Server. Neben der bekannten klassischen Variante mit Benutzername und Passwort können Sie unter anderem auch Schlüsselpaare nutzen, die aus einem privaten und einem öffentlichen SSH-Schlüssel bestehen.

[Ionos](https://www.ionos.de/digitalguide/server/sicherheit/ssh-keys-fuer-ihre-netzwerkverbindung-nutzen/)

--------------------------------------------------------------------------------------------------------------------------------------------

