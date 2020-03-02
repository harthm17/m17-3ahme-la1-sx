# Protokoll 24.02.2020
-----------------------------------------------------------------------
**Einführung Microcontroller und Raspberry Pi**   
**Datum: 24.02.2020**   
**Protokollführer: Danko Sebastian** 

------------------------------------------------------------------------
## Inhaltsverzeichnis:
* [µ controler](#µ-controler)  
* [Raspberry Pi](#Raspberry-Pi)  
* [Raspberry über SSH steuern](#raspberry-über-ssh-steuern) 
* [Betriebssysteme Für den Raspberry Pi](#Betriebssysteme-auf-einen-Raspberry-Pi)   
* [Befehle](#befehle) 
------------------------------------------------------------------------------

## µ controler
* Leistungsschwache CPU 
* Verbrauch: 1-10mW
* Flash Player 32KiB 
* SRAM Arbeitsspeicher 2 KiB 
* 8 Bit µC
* Kosten: 1-2€
* Echtzeitfähigkeit

![Bild](https://cdn.prod.www.spiegel.de/images/48a41de2-0001-0004-0000-000001028706_w948_r1.77_fpx61.3_fpy50.jpg)


## Raspberry Pi
* Leistungstarke CPU
* Verbrauch: 1-2W
* Flash MMC 8,16,32,... GiB
* Arbeitsspeicher 1,2,4GiB
* 32/64 Bit 
* Kosten: 30-40€

![Bild](https://images-na.ssl-images-amazon.com/images/I/91zSu44%2B34L._AC_SX466_.jpg)
## Raspberry über SSH Steuern
Um sich zu verbinden muss man mit der Schnittstelle des Raspberry Verbinden und aktivieren, weil es wegen Sichergründen nicht anders funktioniert.
Danach geht es über die IP-Adresse mit dem Befehl: ssh
z.B.  ssh pi@10.200.114.227

## Betriebsystem auf einen Raspberry Pi
* Raspbian Buster Lite
* Raspbian Buster mit Desktop 
* Raspbian Buster mit Desktop und recommended software

Um das betriebsystem zu instalieren muss man die ausgewählte datei herunterladen und dan mit dem dd Befehl entpacken und auf eine SD Karte kopieren.

## Befehle
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

