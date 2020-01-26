# Protokoll 3 La1/SX 3AHME (2019/20)
--------------
 * **Thema:** Einführung Raspberry PI
  * **Datum:** 20.1.2020
  * **Gefehlt:** Richard Strohrigl
  * **Erstellt von:** Michael Ully 
  --------------------------------------------------
  ## Inhaltsverzeichnis
  1.  [Vergleich Arduino, Raspberry PI](#vergleich-arduino-raspberry-pi)
  2.  [Dateisysteme](#dateisysteme)
  3.  [Verzeichnisse unter Linux](#verzeichnisse-unter-linux)
  4.  [Einhängen von Dateisystemen](#einhängen-von-dateisystemen)
      * [Manuelles Einhängen von Geräten](#manuelles-einhängen-von-geräten)
      * [Manuelles Aushängen von Geräten](#manuelles-aushängen-von-geräten)
  5.  [Einen neuen Benutzer hinzufügen](#einen-neuen-benutzer-hinzufügen)
  6. [Dateirechte unter Linux](#dateirechte-unter-linux)
      * [Ändern von Rechten](#ändern-von-rechten)
      
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
unzip-p Downloads/NamederZipDatei.zip | dd bs=4M of=/dev/nmcblk0
````
Laut 

[wiki.ubuntuuseres](https://wiki.ubuntuusers.de/dd/)

dd (disk dump) dient zum bit-genauen Kopieren von Festplatten, Partitionen oder Dateien. "Bit-genaues" Kopieren bedeutet, dass der Datenträger Bit-für-Bit bzw. Byte-für-Byte ausgelesen und beschrieben wird, unabhängig von dessen Inhalt und Belegung. dd ignoriert Dateisysteme und funktioniert mit allen blockorientierten Datenträgern, also auch mit Daten-CDs/DVDs.


   
