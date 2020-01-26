# Protokoll 3 La1/SX 3AHME (2019/20)
--------------
 * **Thema:** Einführung Raspberry PI
  * **Datum:** 20.1.2020
  * **Gefehlt:** Richard Strohrigl
  * **Erstellt von:** Michael Ully 
  --------------------------------------------------
  ## Inhaltsverzeichnis
  1.  [Vergleich Arduino, Raspberry PI](#vergleich-arduino-raspberry-pi)
      * [Installation](#installation)
  2.  [SSH](#ssh)
  3.  [Raspberry Name und Passwort ändern und Benutzer erstellen](#raspberry-name-und-passwort-ändern-und-benutzer-erstellen)
  4.  [Man in the middle](#man-in-the-middle)
      
   ## Vergleich Arduino, Raspberry PI
   Ein Rasperry PI ist quasi ein vollwertiger PC. Bei einem Mykrocontroller mit 8 Bit ist es kaum möglich 
   ins Netzwerk zu gehen oder zu verschlüsseln.
   
   
   |      | Arduino Nano | Raspberry PI |
   |:----:|:------------:|:------------:|
   | CPU  | geringe Leistung | wesentlich Leistungsstärker(1000x größer im Vergleich zum Nano)|
   | Kosten | 1-3€ | Zero 12-14€ voller RPI 30€ |
   | Architektur | 8 Bit Architektur | 32 Bit Architektur |
   | Betriebssystem | keine Standardbetriebssysteme | Standard Betriebssysteme möglich |
   | Leistung | 2,5mW | 1W |
   | Echtzeitfähig | JA | NEIN |
   
   Unter Echtzeit versteht man die Anforderung an ein Rechensystem, innerhalb einer kürzesten definierten Zeitspanne korrekt zu reagieren.
   
   ## Betriebssysteme
   
   Betriebssysteme kann man auf der offiziellen Raspberry Pi Seite herunterladen. Wir arbeiten mit dem Devian Distribution Raspian. Es wäre sogar möglich 
   Windows zu installieren, weil neue Modelle sehr leistungsfähig sind.
   
   Es gibt drei Raspbian Varianten zum herunterladen.
   1) Raspbian Buster mit Desktop und vorgeschlagener Software
   2) Raspbian Buster mit Desktop
   3) Raspbian Buster Lite 
   
   ### Installation
   
   1) Herunterladen der [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) ZipDatei.
   2) Unter Linux können wir die ZIP-Datei mit folgendem Befehl auf der MMC entpacken.
   ````bash
michael@michael-GL752VW:~$ unzip-p Downloads/NamederZipDatei.zip | dd bs=4M of=/dev/nmcblk0
````
Laut 

[wiki.ubuntuuseres](https://wiki.ubuntuusers.de/dd/)

dd (disk dump) dient zum bit-genauen Kopieren von Festplatten, Partitionen oder Dateien. "Bit-genaues" Kopieren bedeutet, dass der Datenträger Bit-für-Bit bzw. Byte-für-Byte ausgelesen und beschrieben wird, unabhängig von dessen Inhalt und Belegung. dd ignoriert Dateisysteme und funktioniert mit allen blockorientierten Datenträgern, also auch mit Daten-CDs/DVDs.
  3) Aktivierung der SSH: Dazu muss man auf der SD-Karte in der Boot Partition eine leere Datei mit dem Namen SSH erstellen. Starten man nun Raspbian wird die SSH gestartet und die Datei gelöscht.
  
  ## SSH
  Laut [checkdomain.de](https://www.checkdomain.de/hosting/lexikon/ssh/)
  
> SSH ist die Abkürzung für Secure Shell. Mit Hilfe von Secure Shell lassen sich sichere Netzwerkverbindungen zu anderen Geräten herstellen, etwa von einem PC zu einem Webserver. SSH ermöglicht die gegenseitige Authentifizierung und eine verschlüsselte Datenübertragung, so dass sensible Daten wie Passwörter oder Benutzernamen nicht von Unberechtigten ausgespäht werden können. Secure Shell bietet dabei ein hohes Sicherheitsniveau.

Mit diesem Befehlm haben wir über SSH auf den Raspberry PI zugegriffen.

 ````bash
michael@michael-GL752VW:~$ ssh pi@10.200.114.222
````

## Raspberry Name und Passwort ändern und Benutzer erstellen

Hostname ändern

 ````bash
michael@michael-GL752VW:~$ sudo nano /etc/hostname
michael@michael-GL752VW:~$ sudo nano /etc/hosts
````
Passwort ändern

 ````bash
michael@michael-GL752VW:~$ sudo passwd
````
Benutzer erstellen

 ````bash
michael@michael-GL752VW:~$ sudo adduser <name>
````
Benutzer in die Sudo Gruppe hinzufügen:

````bash
michael@michael-GL752VW:~$ sudo usermod -G sudo <name>
````
## Man in the middle

Laut [Wikipedia](https://de.wikipedia.org/wiki/Man-in-the-Middle-Angriff)

>Ein Man-in-the-Middle-Angriff (MITM-Angriff), auch Janusangriff (nach dem doppelgesichtigen Janus der römischen Mythologie) genannt, ist eine Angriffsform, die in Rechnernetzen ihre Anwendung findet. Der Angreifer steht dabei entweder physisch oder – heute meist – logisch zwischen den beiden Kommunikationspartnern, hat dabei mit seinem System vollständige Kontrolle über den Datenverkehr zwischen zwei oder mehreren Netzwerkteilnehmern und kann die Informationen nach Belieben einsehen und sogar manipulieren. Die Janusköpfigkeit des Angreifers besteht darin, dass er den Kommunikationspartnern vortäuscht, das jeweilige Gegenüber zu sein.

![Man in the Middle](https://wiki.botfrei.de/images/7/73/Mitm.jpg)


   
