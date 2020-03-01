# Protokoll m17-3ahme-la1

-----

**Name**: Andreas Augustin  
**Datum**: 17.02.2020  
**Klasse**: 3AHME  
**Gruppe**: 1  

-----

## Inhaltsverzeichniss

1) [ATmel 324P](#atmel324P)
1) [Raspberry PI](#raspberrypi)  
1) [Linux Debian System](#linuxdebiansystem)
1) [Kommandos](#kommandos)
   * [Sonstiges](#sonstiges)

-----

## ATmel 324P
```
• Bit µc
• single chip computer
• 32 KiB Flash (programme)
• 2 KiB SRAM
• Stromverbrauch: 1mW ~ 10 mW
```

* Ein wesentlicher vorteil dieser µc`s ist die Echtzeitfähigkeit!  

-----

## Raspberry PI

* Gerät 21 (ip: 10.200.114.21)
```
• 32 oder 64 Bit-System
• Stromverbrauch: 1W ~ 2W
• Preis: 30€ ~ 40€
• Leistungsstarke CPU
• Internetanschluss (ethernet, W-Lan)
• Flash MMC (8/16/32GiB)
• 10000 fach schneller als ATmel 324P
```

-----

## Linux Debian System

-> total freie Software...Raspian  
-> Ubuntu  

RPI...Fingerabdruck (sicherheit)  
-> man in the middle attack (passwort wird über das internet an den raspberry vermittelt und das will man verhindern)

-----

## Kommandos

* Neuen Benutzer erstellen (manuell)  
```
man adduser  
adduser *auganm17*  
nano /etc/group  
```  

* **mount** hängt ein Dateisystem ein. Ohne Optionen zeigt es alle grade eingehängten Dateisysteme an. Mount kann Lokale Systeme wie Festplatten, USB Sticks, DVDs etc.. sowie entferne NFS oder SMB Freigaben in das System einhängen (mounten).  
```
mount
->Datei anlegen SSH
unmount erste Partition
```
  
* Mit update wird überprüft ob es ein "**update**" gibt und mit "**upgrade**" wird es dann ausgeführt. Jedoch muss man dafür besondere Rechte besitzen (zb. Superuser).  
```
sudo -i
apt update
apt upgrade
```   
-----

## Sonstiges
  
* mit dem Programm "screen" kann man eine installation im Hintergrund weiterlaufen lassen auch wenn man ausgeloggt ist! Aufrufen kann man die installation wieder mit ```screen -r```.  
* Der raspberry geht beim ersten login vom falschen benutzer aus.  
-> ssh @pi10.200........  
* mit dem Programm "screen" kann man eine installation im Hintergrund weiterlaufen lassen auch wenn man ausgeloggt ist! Aufrufen kann man die installation wieder mit ```screen -r```.  
* SSH-Keygen:
*ist eine Standardkomponente der Secure Shell (SSH)-Protokollsuite, die auf Unix-, Unix-ähnlichen und Microsoft-Windows-Computersystemen zu finden ist und dazu dient, sichere Shell-Sitzungen zwischen entfernten Computern über unsichere Netzwerke durch den Einsatz verschiedener kryptographischer Techniken aufzubauen. Das Dienstprogramm ssh-keygen wird zur Erzeugung, Verwaltung und Konvertierung von Authentifizierungsschlüsseln verwendet.*  

*Quelle:* https://en.wikipedia.org/wiki/Ssh-keygen 
