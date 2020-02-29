# Protokoll LA1/sx AHME17
-------------------------
* **Thema:** Einführung Raspberry PI
  * **Datum:** 24.02.2020
  * **Gefehlt:** ---
  * **Erstellt von:** Golser Raphael
--------------------------------------------------
 ## Inhaltsverzeichnis
 1. [Vergleich µc, Raspberry PI](#vergleich-µc-raspberry-pi)
  2. [SSH](#ssh)
  3. [Man in the middle](#man-in-the-middle)
  4. [Übungsbeispiele](#übungsbeispiele)
  
  ## Vergleich µc, Raspberry PI
  Ein Raspberry PI ist ein vollwertiger mini Computer der alle Funktionen hat die ein normaler Computer hat. 
  Doch ein einfacher µc hat jedoch eine Fähigkeit die der Raspberry nicht hat, nämlich die Echtzeitfähigkeit.
  |       | Gewöhnlicher µc | Raspberry PI |
  |:----:|:------------:|:------------:|
  | CPU | geringe Leistung | wesentlich mehr Leistung (ca. 1000 x größer als der µc) |
  | Kosten | 1 - 3€ | 30 - 40€ |
  | Architektur | 8 Bit Architektur | 32 Bit Architektur |
  | Stromverbrauch | 1mW ~/ 10mW | bei Leerlauf 1 -2mW |
  | Arbeitsspeicher | 3KiB | 1GiB / 2 GiB / 4 GiB |
  
  ## Betriebssysteme
  Betriebssysteme kann man auf der offiziellen Raspberry Pi Seite herunterladen. 
  Wir arbeiten mit dem Debian Distribution Raspian. 
  Es wäre sogar möglich Windows zu installieren, weil neue Modelle sehr leistungsfähig sind.
   
   Es gibt drei Raspbian Varianten zum herunterladen.
   1) Raspbian Buster mit Desktop und vorgeschlagener Software
   2) Raspbian Buster mit Desktop
   3) Raspbian Buster Lite
   
 Die Raspbian Variante die im Unterricht verwendet wird ist die Raspbian Buster Lite Version.
 
  ### Installation
   
   1) Herunterladen der [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) ZipDatei.
   2) Unter Linux können wir die ZIP-Datei mit folgendem Befehl auf der MMC entpacken.
  
  ````bash
schueler@pcxx:~$ unzip-p Downloads/NamederZipDatei.zip | dd bs=4M of=/dev/nmcblk0
````

Laut 

[wiki.ubuntuuseres](https://wiki.ubuntuusers.de/dd/)

>dd (disk dump) dient zum bit-genauen Kopieren von Festplatten, Partitionen oder Dateien. 
"Bit-genaues" Kopieren bedeutet, dass der Datenträger Bit-für-Bit bzw. Byte-für-Byte ausgelesen und beschrieben wird, unabhängig von dessen Inhalt und Belegung. 
dd ignoriert Dateisysteme und funktioniert mit allen blockorientierten Datenträgern, also auch mit Daten-CDs/DVDs. 3) Aktivierung der SSH: Dazu muss man auf der SD-Karte in der Boot Partition eine leere Datei mit dem Namen SSH erstellen. 
  Starten man nun Raspbian wird die SSH gestartet und die Datei gelöscht.
  
## SSH

 Laut [Wikipedia](https://de.wikipedia.org/wiki/Secure_Shell)
  
> Secure Shell oder SSH bezeichnet sowohl ein Netzwerkprotokoll als auch entsprechende Programme, mit deren Hilfe man auf eine sichere Art und Weise eine verschlüsselte Netzwerkverbindung mit einem entfernten Gerät herstellen kann. Häufig wird diese Methode verwendet, um lokal eine entfernte Kommandozeile verfügbar zu machen, das heißt, auf einer lokalen Konsole werden die Ausgaben der entfernten Konsole ausgegeben und die lokalen Tastatureingaben werden an den entfernten Rechner gesendet. Genutzt werden kann dies beispielsweise zur Fernwartung eines in einem entfernten Rechenzentrum stehenden Servers. Die neuere Protokoll-Version SSH-2 bietet weitere Funktionen wie Datenübertragung per SFTP. 

Mit diesem Befehl haben wir über SSH auf den Raspberry PI zugegriffen.

 ````bash
schueler@pcxx:~$ ssh pi@10.200.114.222
````


## Man in the middle
Laut [Kaspersky](https://www.kaspersky.de/blog/was-ist-eine-man-in-the-middle-attacke/905/)

>Das Konzept hinter der MITM-Attacke ist erstaunlich einfach und ist nicht auf die Computersicherheit oder Online-Bereiche beschränkt. In seiner einfachsten Form braucht sich der Angreifer nur zwischen zwei Parteien zu schalten, die miteinander kommunizieren, und muss dann nur die gesendeten Nachrichten abhören und sich zumindest als eine der beiden Parteien ausgeben. In der realen Welt kann so ein Angreifer zum Beispiel gefälschte Rechnungen an ein Opfer senden und dann einfach die von ihm zurückgeschickten Schecks abfangen. In der Online-Welt sind die Angriffe etwas komplexer, die Grundlagen sind aber die gleichen. Der Angreifer schaltet sich zwischen sein Opfer und eine Ressource ein, die das Opfer versucht zu erreichen. Um erfolgreich zu sein, muss dabei die Anwesenheit des Angreifers sowohl für das Opfer als auch für die andere Ressource unentdeckt bleiben.

![Man in the Middle](https://wiki.botfrei.de/images/7/73/Mitm.jpg)

## Übungsbeispiele

**Passwort von pi25 ändern mit Befehl:**

````bash
pi@raspberrypi:~$ passwd
````
--------------
**Konfigurations - Tool öffnen:**

````bash
pi@raspberrypi:~$ sudo raspi-config
````
--------------
**Software zuerst auflisten und dann updaten:**

````bash
pi@raspberrypi:~$ apt update
pi@raspberrypi:~$ apt upgrade
````
---------------
**screen:**

screen ist ein Programm womit der Raspberry PI wenn ein update/ eine Installation mit screen geöffnet gestartet wird, weiter arbeitet, wenn man die Konsole verlässt.

*screen installieren:*

````bash
pi@raspberrypi:~$ apt install screen
````

*screen schließen* mit strg + a + d

*zum aktiven screen wieder einloggen:*

````bash
pi@raspberrypi:~$ screen -r
````

*neuen screen erstellen mit anderen Namen:*

````bash
pi@raspberrypi:~$ screen -s backup(Beispiel Name)
````
---------------------------------------------------------------------------   
**Eine java-version suchen diese Suche im viewer öffnen und die dann installieren und dann anzeigen:**

````bash
pi@raspberrypi:~$ apt search java
pi@raspberrypi:~$ apt search java | less
pi@raspberrypi:~$ apt install java2516(nur Beispiel)
pi@raspberrypi:~$ java-version
````
--------------------------------------------------
**Neuen User erstellen:**

````bash
pi@raspberrypi:~$ adduser golram17
````
----------------------
**Superuserrechte bekommen:**

````bash
pi@raspberrypi:~$ nano /etc/group
````
Um Superuserrechte zu bekommen muss man sich neu einloggen.

---------------------------
**Hostname ändern:**

````bash
pi@raspberrypi:~$ nano /etc/hostname
pi@raspberrypi:~$ nano /etc/hosts
pi@raspberrypi:~$ reboot
````

nach reboot hat pi@raspberrypi jetzt den hostname pi@pi25.

-----------------------
**SSH - Schüsselpaar erstellen:**

````bash
schueler@pcxx:~$ ssh - keygen
````

nach der Erstellung  des Schlüsselpaars hat man zwei Dateien erstens id_rsa, das ist der private Schlüssel und zweitens id_rsa.pub, das ist der öffentliche Schlüssel.
  
