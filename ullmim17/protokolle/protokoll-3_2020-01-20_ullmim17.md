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
   Ein Rasperry PI ist quasi ein vollwertiger PC. Bei einem Mykrocontroller wie dem Arduino Nano mit 8 Bit ist es kaum möglich ins Netzwerk zu gehen oder zu verschlüsseln.
   
   
   |      | Arduino Nano | Raspberry PI |
   |:----:|:------------:|:------------:|
   | CPU  | geringe Leistung | wesentlich mehr Leistung(1000x größer im Vergleich zum Nano)|
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
  Laut [Wikipedia](https://de.wikipedia.org/wiki/Secure_Shell)
  
> Secure Shell oder SSH bezeichnet sowohl ein Netzwerkprotokoll als auch entsprechende Programme, mit deren Hilfe man auf eine sichere Art und Weise eine verschlüsselte Netzwerkverbindung mit einem entfernten Gerät herstellen kann. Häufig wird diese Methode verwendet, um lokal eine entfernte Kommandozeile verfügbar zu machen, das heißt, auf einer lokalen Konsole werden die Ausgaben der entfernten Konsole ausgegeben und die lokalen Tastatureingaben werden an den entfernten Rechner gesendet. Genutzt werden kann dies beispielsweise zur Fernwartung eines in einem entfernten Rechenzentrum stehenden Servers. Die neuere Protokoll-Version SSH-2 bietet weitere Funktionen wie Datenübertragung per SFTP. 

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

Laut [Kaspersky](https://www.kaspersky.de/blog/was-ist-eine-man-in-the-middle-attacke/905/)

>Das Konzept hinter der MITM-Attacke ist erstaunlich einfach und ist nicht auf die Computersicherheit oder Online-Bereiche beschränkt. In seiner einfachsten Form braucht sich der Angreifer nur zwischen zwei Parteien zu schalten, die miteinander kommunizieren, und muss dann nur die gesendeten Nachrichten abhören und sich zumindest als eine der beiden Parteien ausgeben. In der realen Welt kann so ein Angreifer zum Beispiel gefälschte Rechnungen an ein Opfer senden und dann einfach die von ihm zurückgeschickten Schecks abfangen. In der Online-Welt sind die Angriffe etwas komplexer, die Grundlagen sind aber die gleichen. Der Angreifer schaltet sich zwischen sein Opfer und eine Ressource ein, die das Opfer versucht zu erreichen. Um erfolgreich zu sein, muss dabei die Anwesenheit des Angreifers sowohl für das Opfer als auch für die andere Ressource unentdeckt bleiben.

![Man in the Middle](https://wiki.botfrei.de/images/7/73/Mitm.jpg)


   
