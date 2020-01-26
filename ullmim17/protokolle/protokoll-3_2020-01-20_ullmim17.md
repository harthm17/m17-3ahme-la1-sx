# Protokoll 3 La1/SX 3AHME (2019/20)
--------------
 * **Thema:** Einführung Raspberry PI
  * **Datum:** 20.1.2020
  * **Gefehlt:** Richard Strohrigl
  * **Erstellt von:** Michael Ully 
  --------------------------------------------------
  ## Inhaltsverzeichnis
  1.  [Paritionen](#partitionen)
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
   
   
