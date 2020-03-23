# Protokoll LA2/SX 3AHME (2019/20)

* **Thema:** Installation von Ubuntu 18.04 in einer virtuellen Maschine
* **Datum:** 23.03.2020
* **Erstellt von:** Felix Hamrle
* **Protokoll nächste Einheit:** --

## Inhaltsverzeichnis
1. [Installation der VirtualBox](#installation-der-virtualbox)    
2. [Download des Oracle VM VirtualBox Extension Packs](#download-des-oracle-vm-virtualbox-extension-packs)  
3. [Virtuelle Maschine erstellen](#virtuelle-maschine-erstellen)   
4. [Installieren von Ubuntu](#installieren-von-ubuntu)  
5. [VirtualBox Guest Additions installieren](#virtualbox-guest-additions-installieren)  
5. [Gemeinsamer Ordner](#gemeinsamer-ordner) 
5. [Installation des HTL-Packetes](#installation-des-htl-packetes)  
5. [Lesezeichen-Menüleisete konfigurieren](#lesezeichen-menüleisete-konfigurieren)  

## Installation der VirtualBox

Als erster Schritt wurde die [VirtualBox](https://download.virtualbox.org/virtualbox/6.1.4/VirtualBox-6.1.4-136177-Win.exe) (Dieser Link fürt direkt zur Installation von der VirtualBox 6.1.4 für Windows. Für andere Betriebssysteme benutzen Sie diesen [Link](https://www.virtualbox.org/wiki/Downloads)) installiert, dies geschah ohne Probleme  

## Download des Oracle VM VirtualBox Extension Packs

In diesem Schritt mussten wir [Oracle VM VirtualBox Extension Pack](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack) installieren.  
Da diese Installation automatisch abgelaufen ist, hatte ich keine Probleme.

## Virtuelle Maschine erstellen

Als erstes muss mann die Hardwarevisualisierung aktivieren. Das kann von BIOS zu BIOS unterschiedlich sein. Danach macht mann mit dem Menüpunkt **Neu** ein neue Virtuelle Maschine, wo abgefragt wird, wie sie benannt werden soll und wo sie gespeichert werden soll. Beim Punkt **Typ** sind mehrere Auswahlmöglichkeiten vorhanden. Für Ununtu muss man **Linux** auswählen und darunter bei **Version** wählt man **Ubuntu(64-bit)**. Damit man einstellen kann wie viel Speicher und welche Festplatte benuzt wird muss mann auf **Experten-Modus** klicken. Bei **Speichergröße** stelt man 4 MB ein und bei **Plate** last mann eine Festplatte erzeugen. Dann klickt mann auf **Erzeugen** und kommt zu den Einstellungen für die Festplatte wenn mann eine Virtuelle Festplatte anlegt. Dort stelt mann bei Dateigröße ein 50 GB und klickt dan nochmal auf **Erzeugen**.

## Installieren von Ubuntu

Einfach die virtuelle Maschine starten und den Anweisungen folgen.

## VirtualBox Guest Additions installieren

1) Virtuelle Maschine starten
1) Auf den Menüpunkt **Geräte** klicken
1) Auf **Medium mit Gasterweiterungen einlegen** klicken
1) Auf **VBoxWindowsAdditions.exe ausführen** klicken

## Gemeinsamer Ordner 

1) Ordner am Haupt-System erstellen
1) In der VirtualBox bevor mann sie startet auf der rechten odern Ecke auf **Ändern** klicken
1) Dort dann auf **Gemeinsame Ordner** klicken
1) Dann dort einen Ordner hinzufügen, indem man auf der rechten Seite auf einen **blauen Ordner mit einen Plus** klickt

## Installation des HTL-Packetes

Bei der Installation des HTL-Paketes geht man laut [dieser](http://www.htl-mechatronik.at/ubuntu-htl/readme) Anleitung vor.

## Lesezeichen-Menüleisete konfigurieren

Da sich Firefox und Chrome ständig ändern, finde ich es am besten wenn mann bei den aktuellen Anleitungen nachsieht.  
[Firefox](https://support.mozilla.org/de/kb/Lesezeichen-sichern-und-wiederherstellen)  
[Chrome](https://support.google.com/chrome/answer/96816?hl=de)

