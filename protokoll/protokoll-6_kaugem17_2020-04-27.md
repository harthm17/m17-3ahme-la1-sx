# 6. Protokoll

-------------------------------------------------

## Thema: Debian Paket erzeugen

-------------------------------------------------

Übungsdatum:   Montag, 27.04.2020     
Übungszeit:    14:10 bis 16:30      
Übungsort:     St. Veit in der Südsteiermark, Home-Office    
Verfasser:     Georg Kaufmann    
Abwesend:      keiner      
Anwesend:      Felix Hamrle, Stefan Haring, Thomas Harrer, Georg Kaufmann, Andreas Kogler, Franz Lieleg, Simon Marcher

-------------------------------------------------

### Inhaltsverzeichnis
1) [Java Programm erstellen](#java-programm-erstellen) 
1) [Debian Paketverzeichnis erstellen](#debian-paketverzeichnis-erstellen)
1) [Datei DEBIAN/control](#datei-debiancontrol)
1) [Datei DEBIAN/postints und DEBIAN/postrm](#datei-debianpostints-und-debianpostrm)
1) [Java Programm einfügen](#java-programm-einfügen)
1) [Resümee](#resümee)

-------------------------------------------------

#### Java Programm erstellen
Es ist mit Netbeans ein Java Swing GUI Programm zu erstellen.
Dazu ist es ratsam sich folgendes [Video](https://cloud.htl-mechatronik.at/index.php/s/AlyXs7YglQDLZSP) anzuschauen.

Hier nochmals kurz zusammen gefasst. Hierbei muss man folgende Schritte beachten und umsetzen:
1) Java Projekt erzeugen
1) Java Paket gui erzeugen
1) Java Klasse abgeleitet von jFrame erzeugen
1) Titel und Mindestgröße konfigurieren, Fenster in der Bildschirmmitte öffnen lassen
1) "Flow Layout" setzen
1) Button "Press me..." einfügen
1) Im Button-Handler-Methode ein Dialogfenster öffnen und einen Text ausgeben
1) Projekt ausführen und testen
1) Projekt mit "Clean and Build" übersetzen
1) Aus dem Ordner dist die fertige Java Archiv Datei entnehmen

-------------------------------------------------

#### Debian Paketverzeichnis erstellen
Es ist ein Unterordner für das Debianpaket zu erstellen.
```
user@host:~$ mkdir kursname-guiapp_1.~1_all
user@host:~$ cd kursname-guiapp_1.~1_all
user@host:~/kursname-guiapp_1.~1_all
```
Es werden bereits drei Informationen bekannt gegeben.
1) Der Name des Pakets (kursname-guiapp).
2) Die Version des Pakets. In unserem Fall 1.0~1.
3) Die unterstützte Architektur. In unserem Fall **all**, was bedeutet das alle Architekturen unterstützt werden.

-------------------------------------------------

#### Datei DEBIAN/control


-------------------------------------------------

#### Datei DEBIAN/postints und DEBIAN/postrm

-------------------------------------------------

#### Java Programm einfügen

-------------------------------------------------

#### Resümee
