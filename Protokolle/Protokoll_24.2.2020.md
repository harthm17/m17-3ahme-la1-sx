# Protokoll 24.02.2020
-----------------------------------------------------------------------
**Einführung Raspberry Pi**   
**Datum: 24.02.2020**   
**Protokollführer: Danko Sebastian** 

------------------------------------------------------------------------
## Inhaltsverzeichnis:
* [Microcontroler](#microcontroler)  
* [Raspberry Pi](#raspberry-pi)  
* [Betriebssysteme Für den Raspberry Pi](#betriebssysteme-für-den-raspberry-pi)  
* [Mit Raspberry über SSH verbinden](#mit-raspberry-über-ssh-verbinden)  
* [Befehle](#befehle) 
------------------------------------------------------------------------------

## Microcontroler
* Kosten: 1-2€
* Geringer Stromverbrauch
* geringen CPU Leistung 1-10mW
* 32KiB Flash Player
* 2 KiB SRAM Arbeitsspeicher
* 8 Bit µC
* Echtzeitfähigkeit

## Raspberry Pi
* Kosten: 30-40€
* Leistungstarke CPU
* Verbrauch 1-2W
* 8,16,32,... GiB Flash MMC 
* 1,2,4GiB Arbeitsspeicher
* 32/64 Bit 

## Betriebsystem Auf einen Raspberry Pi
* Raspbian Buster Lite
* Raspbian Buster mit Desktop 
* Raspbian Buster mit Desktop und recommended software

Um das betriebsystem zu instalieren muss man die ausgewählte datei herunterladen und dan mit dem dd Befehl entpacken und auf eine SD Karte kopieren.

## Raspberry über SSH Steuern
Um sich zu verbinden muss man mit der Schnittstelle des Raspberry Verbinden und aktievieren, weil es wegen Sichergründen nicht anders geht.
Danach geht es über die IP-Adresse:
z.B.  ssh pi@10.200.114.227

## Befehle:
Befehl   | Bedeutung                | Erklärung<br>
--------|--------------------------|---------------------------------------------------
 dd      | duplicate data          |        Daten 1:1 kopieren (auch auf Geräte anwendbar)<br> 
  sudo    |     super-user do      |        in den Super-User Mode (root) wechseln<br>
  apt-get  |     get data from repository |  Daten/Files herunterladen<br>
  apt-get update        |     apt-get update        |   -> Lokale Software-Datenbank aktualisieren <br>
  apt-get upgrade         |     apt-get upgrade      |    -> Software aktualisieren<br>
mount   |        mount a filesystem |              Partition einbinden<br>
umount   |       unmount a filesystem      Eingebundene Partition trennen<br>
mkdir     |      make directory     |       Verzeichnis erstellen<br>
screen |<br>
exit      |      exit               |       Ende der Sitzung<br>
reboot     |                       |        Rechner neu starten<br>
chomd      |      change mod        |        Benutzer rechte verändern<br>
