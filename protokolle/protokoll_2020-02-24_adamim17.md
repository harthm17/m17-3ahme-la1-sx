# Protokoll 24.02.2020
------------------------------
**Einführung zum Raspberry Pi**   
**Datum: 24.02.2020**   
**Protokollführer: Mike Adam** 

------------------------------
## Inhaltsverzeichnis:
* [Microcontroler](#microcontroler)  
* [Raspberry Pi](#raspberry-pi)  
* [Betriebssysteme Für den Raspberry Pi](#betriebssysteme-für-den-raspberry-pi)  
* [Mit Raspberry über SSH verbinden](#mit-raspberry-über-ssh-verbinden)  
* [Befehle](#befehle) 
  * [Update](#update)  
  * [Konfiguration](#konfiguration)    
  * [Sicherheit und Benutzer](#sicherheit-und-benutzer) 
  * [Screen](#screen) 
  * [Installationen](#installationen)  
  * [SSH Schlüsselpaar](#ssh-schlüsselpaar)  

## Microcontroler:
  * Kosten 1-2€
  * Geringe CPU Leistung
  * Geringer Stromverbrauch 1 mW - 10 mW
  * 3kiB Abeitsspeicher
  * 8 bit - Architektur
  * Echtzeitfähig
  
## [Raspberry Pi](https://www.raspberrypi.org/products/):
  * Kosten 30 - 40€
  * CPU Leistung für kompliziertere Aufgaben
  * Stromverbrauch von 1 - 2 mW im Leerlauf
  * 1GiB, 2GiB, 4GiB Arbeitsspeicher
  * 32 (64) bit Architektur 
  
## Betriebssysteme für den Raspberry Pi:
  ### Es gibt verschieden arten von [Betriebssystemen](https://www.raspberrypi.org/downloads/raspbian/) für den Raspberry Pi
  * Raspbian Buster Lite
  * Raspbian Buster mit Desktop 
  * Raspbian Buster mit Desktop und Programmen
  
Um das Betriebssystem auf einen Raspberry Pi installieren zu können, muss man die ausgewählte Datei Herunterladen und mithilfe des dd Befehles (bei Ubuntu) entpacken und auf eine SD Karte kopieren.

## Mit Raspberry über SSH verbinden:
Um sich mit einem Raspberry Pi über SSH verbinden zu können muss man erst die SSH Schnittstelle aktivieren, weil sie aus Sicherheitsgründen standardmäßig deaktiviert ist. 

Nun kann man auf den Raspberry Pi mit der ip-Adresse vom Raspberry zugreifen:
````
bsp. SSH raspberrypi@10.200.114.229
````

## Befehle:

### Update:
* Um diese Befehle Benutzen zu können muss man als Superuser eingeloggt sein.
````
sudo -i
````

* Updates suchen (ohne sie zu installieren)
````
Befehl: apt update
````

* Updates installieren
````
Befehl: apt upgrade
````

### Konfiguration:
* Für den Raspberry Pi gibt es ein eigenes Konfigurations - Tool
````
Befehl: sudo raspi config
````

### Sicherheit und Benutzer:
* Neuen User erstellen:
 ````
Befehl: adduser adamim17
 ````
* Passwort ändern:
````
Befehl: passwd
````
* Superuser Rechte Hinzufügen
````
Befehl: nano /etc/group
````
### Screen:
Das ist eine Shell, sie auch beim verlassen weiter arbeitet.
* Screen installieren:
````
Befehl: apt install screen
````
* Aus dem Screen Fenster raus gehen:
````
Tastenkombination: strg + a + d
````
* In das Screen Fenster einsteigen (in dem Konsolenfenster vom Raspberry Pi:
````
Befehl: Screen -r
````

### Installationen:
Man kann über die Konsole auch Programme auf den Raspberry Pi installieren.
* Programm suchen:
````
Befehl: apt search
````
* Programm installieren:
````
Befehl: apt install
````
### SSH Schlüsselpaar:
Beim erstellen eines SSH - Schlüsselpaares hat man zwei Schlüssel, einen privaten und einen öffentlichen.
* Ein Schlüsselpaar erstellen:
````
ssh-keygen
````


