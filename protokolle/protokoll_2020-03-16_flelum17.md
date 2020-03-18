# Labor Protokoll 2020-03-16
         
**Lukas Fleischhacker**       
**3AHME**   

----------------------------
## Inhaltsverzeichnis    
1) [Installieren von VirtualBox](#installieren-von-virtualbox)  
2) [Installieren von Oracle VM VirtualBox Extension Pack](#installieren-von-oracle-vm-virtualbox-extension-pack)    
3) [Erstellen einer virtuellen Maschine](#erstellen-einer-virtuellen-maschine)
      * [Erstellen](#erstellen)     
      * [Weitere Einstellungen](#weitere-einstellungen)                 
4) [Installieren von VirtualBox Guest Additions](#installieren-von-virtualbox-guest-additions)
5) [Verzeichnis zwischen gast- und virtuellen System](#verzeichnis-zwischen-gast--und-virtuellen-system)    
6) [Installieren von HTL-Paket](#installieren-von-htl-paket)
7) [Lesezeichen Menüleiste konfigurieren](#lesezeichen-menüleiste-konfigurieren)
----------------------------        

## Installieren von VirtualBox
Der erste Schritt ist VirtualBox zu installieren, mit Hilfe des Links: [(VirtualBox)](https://www.virtualbox.org/wiki/Downloads).    
Dort muss man nur das richtige Betriebssystem auswählen.

## Installieren von Oracle VM VirtualBox Extension Pack
Danach muss das Oracle VM VirtualBox Extension Pack installiert werden,     
auch hier der Link: [(Extension Pack)](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack)   
Da der Rest von selbst passiert, braucht man in diesem Schritt nichts mehr tun.

## Erstellen einer virtuellen Maschine 
### Erstellen 
Zuerst geht man in den Oracle VM VirtualBox Manager und erstellt mit ````neu```` eine neue virtuelle Maschine,    
dann muss man den gewünschten *Namen* und *Ordner* eigeben. Weiters muss man bei **Typ** *Linux* und bei **Version**    
*Ubuntu(64bit)* auswählen.    
    
Danach die richtige RAM größe zuweißen, bei uns sind das min. *4GiB*      
    
Weiters ````Festplatte erzeugen```` anklicken, dann ````VDI VirtualBox Disc Image````  und auch    
````dynamisch alloziert```` wählen. Nachdem kann man sich die virtuelle Festplattengröße auswählen,   
es wird min *50GiB* empfohlen. 

### Weitere Einstellungen
Unter ````Ändern```` - Allgemein -erweitert sollte man bei:   
"Gemeinsame Zwischenablage" und "Drag 'n' Drop" beidesmal *bidirektional* auswählen.    
                  
Danach wieder bei ````Ändern```` -Massenspeicher und dann sollte unter "Controller: IDE"             
"leer" stehen, dort raufklicken und mit der blauen CD an der Seite die vorher heruntergeladene              
Ubuntu ISO-Datei auswählen. Link: [Ubuntu ISO-Datei](https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64)                                                  
                  
Falls sich die virtuelle Maschine nicht starten lässt, kann es daran liegen, dass man im BIOS die           
Hardwarevisualisierung aktivieren muss.               

## Installieren von VirtulBox Guest Additions
Entwerder ist es schon installiert, wie bei den neueren Ubuntu-Versionen, oder man                 
muss es selbst installieren.                 
                  
Zuerst geht man in die virtuelle Maschine, dann geht man im Fenster auf ````Geräte```` -           
````Medium mit Gasterweiterung einlegen```` um die Guest Additions zu installieren.                

## Verzeichnis zwischen gast- und virtuellen System
Als erstes erstellt man sich einen Ordner am Gastsystem z.B. am Desktop.                  
Dann geht man wieder auf ````Ändern```` - ````Gemeinsame Ordner```` und dort                 
klickt man auf das *grüne Plus* und wählt den früher angelegten Ordner aus.               

## Installieren von HTL-Paket
Am besten richtet man sich bei der Installation des HTL-Pakets nach dieser Beschreibung.           
Link: [HTL Paket](http://www.htl-mechatronik.at/ubuntu-htl/readme)               

## Lesezeichen Menüleiste konfigurieren
Diesen Punkt habe ich leider noch nicht geschafft, werde ihn aber natürlich nachholen.             
Mit dem Link, der mir Niklas Fuchshofer gezeigt hat, sollte es kein Problem sein.
Link: [Konfigurieren](https://support.mozilla.org/de/kb/Lesezeichen-sichern-und-wiederherstellen)


