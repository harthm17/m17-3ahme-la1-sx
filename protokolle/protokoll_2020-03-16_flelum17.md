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



