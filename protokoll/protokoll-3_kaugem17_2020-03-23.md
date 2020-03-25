# 3. Protokoll

-------------------------------------------------

## Thema: Installation von Ubuntu 18.04 mit Hilfe einer virtuellen Maschine

-------------------------------------------------

Übungsdatum:   Montag, 23.03.2020     
Übungszeit:    14:10 bis 16:30      
Übungsort:     St.Veit in der Südsteiermark, Home-Office    
Verfasser:     Georg Kaufmann    
Abwesend:      keiner      
Anwesend:      Felix Hamrle, Stefan Haring, Thomas Harrer, Georg Kaufmann, Andreas Kogler, Franz Lieleg, Simon Marcher

-------------------------------------------------

### Inhaltsverzeichnis
1) [Download von Virtualbox](#download-von-virtualbox) 
1) [Oracle VM VirtualBox Extension Pack installieren](#oracle-vm-virtualbox-extension-pack-installieren) 
1) [Erstellen der virtuellen Maschine](#erstellen-der-virtuellen-maschine)
1) [Installation von Ubuntu](#installation-von-ubuntu)   
1) [Virtualbox Guest Additions](#virtualbox-guest-additions)
1) [Verzeichnis zwischen dem Gastsystem und dem virtuellen System](#verzeichnis-zwischen-dem-gastsystem-und-dem-virtuellen-system)
1) [Installation des HTL-Paktettes](#installation-des-htl-paktettes)
1) [Lesezeichen Menüleiste im Browser konfigurieren](#lesezeichen-menüleiste-im-browser-konfigurieren)

-------------------------------------------------

### Download von Virtualbox
Zu aller erst muss man eine [Virtualbox](https://www.virtualbox.org/wiki/Downloads) installieren. Dies sollte zu keinem großen Problem führen, auf der Website einfach das Betriebsystem auswählen, dass man im Moment benutzt und man kann die Virtualbox installieren. 

-------------------------------------------------

### Oracle VM VirtualBox Extension Pack installieren    
Nachfolgend wird das [Oracle VM Virtual Extension Pack](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack) installiert. Dieses installiert sich voll automatisch und man muss nichts beachten.

-------------------------------------------------

### Erstellen der virtuellen Maschine
Anschließend erstellt man seine virtuelle Maschine. Dazu sind folgende Punkte zu beachten und durch zu führen.
* Es müssen die BIOS Hardware Visualisierungen aktiviert sein. 
* Zu aller erst muss man auf *NEU* klicken. 
* Nun muss man einen angemessenen Namen vergeben (Beispiel: Ubuntu-18.04-Kaufmann). Für die virtuellen Maschine einen Ordner auswählen und das Betriebssystem so wie die Version auswählen. In unserem Fall war dies *Linux* und *Ubuntu 64bit*
* Dann muss man die Speichergröße des Hauptspeichers vergeben. Empfohlen werden mindestens 4GiB. 
* Darauf muss man eine Festplatte erstellen. Diese sollte mindestens 50GiB haben.
* Hiernach muss man die [ISO-Datei](https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64) für Ubuntu auswählen.
* Sodann sollte man auf *Allgemein* und *Erweitert* klicken. Dort sollte man bei *Gemeinsame Zwischenablagen* und *Drag'n'Drop* bidirektional auswählen.

-------------------------------------------------

### Installation von Ubuntu
Wir haben [Ubuntu 18.04](https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64) installiert, hierbei ist zudem darauf zu achten, die Desktop Version und nicht die Server Version zu installieren. Sollte eigentlich klar sein. Hier einfach die ISO-Datei herunterladen und alles weitere ist im Punkt [Erstellen der virtuellen Maschine](#erstellen-der-virtuellen-maschine) erklärt. 

-------------------------------------------------

### Virtualbox Guest Additions
Im Normalfall sollte die Guest Addition schon installiert sein. Wenn dies aber nicht der Fall sein sollte, einfach den unteren Schritten folgen.    

Windows:
* Erstmals die virtuelle Maschine starten.
* Anschließend auf den Menüpunkt *Geräte* klicken und *Medium mit Gasterweiterung* auswählen.
* Zu guter letzt die *VBoxWindowsAddition.exe* ausführen. 

macOS:
* Erstmals die virtuelle Maschine starten. 
* Anschließend auf den Menüpunkt *Devices* klicken und *Insert Guest Addition CD image* auswählen.
* Zu guter letzte *VBox_GAs_6.1.4* auswählen.

-------------------------------------------------

### Verzeichnis zwischen dem Gastsystem und dem virtuellen System
Hier wird ein gemeinsamer Ordner erstellt. Dieser dient dazu einen transfer von Daten zwischen dem virtuellen und normalen Betriebsystem zu gewährleisten.
* Zu aller erst einen Ordner am Host-System erstellen.
* Anschließend in der VirtualBox das *Hauptmenü* und *Geräte* auswählen.
* Dannach bei *Gemeinsame Ordner* auf das grüne Plus klicken und den gemeinsamen Ordner ausführen. 

-------------------------------------------------

### Installation des HTL-Pakettes
Um das HTL-Pakett zu erhalten sollte man [folgendermaßen](http://www.htl-mechatronik.at/ubuntu-htl/readme) vorgehen. 

-------------------------------------------------

### Lesezeichen Menüleiste im Browser konfigurieren
Firefox:
* Erstmals muss man auf das *Bücherregal* klicken, anschließend muss man den *Stern* auswählen.
* Dort sollte man *Lesezeichen verwalten* auswählen. Im neuen Fenster auf *Importieren und Sichern* klicken. Hier kann man vier Punkte ausfrühen.    
  * *Daten aus einem Browser importieren* ... import aus beispielsweiße Chrome Browser möglich.    
  * *Wiederherstellen* ... wiederherstellung von vergangenen Datum möglich.
  * *Lesezeichen von HTML importieren* ... inform von einer HTML Datei die am Computer gespeichert ist das Format auf den Browser importieren.    
  * *Lesezeichen von HTML exportieren* ...  hiermit kann man seine Lesezeichen inform von einer HTML Datei am Computer speichern. 
  
Chrome:
* Man muss auf das Dreipunkt-Menü klicken.
* Anschließend muss man *Lesezeichen* und *Lesezeichen und Einstellungen importieren* auswählen.
* Nun das Programm auswählen das die gewünschten Lesezeichen enthält und auf *importieren* klicken.     
Für weitere Einstellungen einfach [hier](https://support.google.com/chrome/answer/96816?hl=de) klicken.
