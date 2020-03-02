# Protokoll 24.02.2020
-----------------------------------------------------------------------
**Einführung Raspberry Pi**   
**Datum: 24.02.2020**   
**Protokollführer: Danko Sebastian** 

------------------------------------------------------------------------
## Inhaltsverzeichnis:
* [Microcontroler](#Microcontroler)  
* [Raspberry Pi](#Raspbrry-Pi)  
* [Raspberry über SSH steuern](#raspberry-über-ssh-steuern) 
* [Betriebssysteme Für den Raspberry Pi](#Betriebssysteme-auf-einen-Raspberry-Pi)   
* [Befehle](#befehle) 
------------------------------------------------------------------------------

## Microcontroler
* Leistungsschwache CPU 
* Verbrauch 1-10mW
* Flash Player 32KiB 
* SRAM Arbeitsspeicher 2 KiB 
* 8 Bit µC
* Kosten: 1-2€
* Echtzeitfähigkeit

## Raspberry Pi
* Leistungstarke CPU
* Verbrauch 1-2W
* Flash MMC 8,16,32,... GiB
* Arbeitsspeicher 1,2,4GiB
* 32/64 Bit 
* Kosten: 30-40€

## Raspberry über SSH Steuern
Um sich zu verbinden muss man mit der Schnittstelle des Raspberry Verbinden und aktievieren, weil es wegen Sichergründen nicht anders geht.
Danach geht es über die IP-Adresse mit dem Befehl: ssh
z.B.  ssh pi@10.200.114.227

## Betriebsystem Auf einen Raspberry Pi
* Raspbian Buster Lite
* Raspbian Buster mit Desktop 
* Raspbian Buster mit Desktop und recommended software

Um das betriebsystem zu instalieren muss man die ausgewählte datei herunterladen und dan mit dem dd Befehl entpacken und auf eine SD Karte kopieren.

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
