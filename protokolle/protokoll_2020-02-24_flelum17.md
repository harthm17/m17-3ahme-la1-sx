# Labor Protokoll 2020-02-24
         
**Lukas Fleischhacker**       
**3AHME**   

----------------------------
## Inhaltsverzeichnis    
1) [µC und Raspberry Pi](#µc-und-raspberry-pi)  
   * [µC Atmel 324P](#µc-atmel-324p)  
   * [Raspberrry Pi](#raspberry-pi)   
2) [Erste Schritte](#erste-schritte)
   * [Betriebssystem](#betriebssystem)
   * [SSH](#ssh)
   * [screen](#screen)
   * [Befehle](#befehle)
3) [Man in the middle](#man-in-the-middle)

----------------------------
## µC und Raspberry Pi
### µC Atmel 324P
* Single Chip Computer
* 32KiB Flash Programme
* 2KiB SRAM Arbeitsspeicher 
* Stromverbrauch 1mW-10mW
* ca. 1-2€
* [echtzeitfähig](https://de.wikipedia.org/wiki/Echtzeitsystem)


### Raspberry Pi
* Mini Computer mit Ethernet WLAN, USB und HDMI
* 1GiB/2GiB/GiB Arbeitsspeicher
* 32Bit/64Bit Leistungsfähige CPU
* 8GiB/16GiB/32GiB/... Flash MMC
* Stromverbrauch 1-2W bei Leerlauf
* ca. 30-40€ / Raspberry Zero ca. 12€
* nicht echtzeitfähig 

#### Ein µC ist mit einem Raspberry "verheiratbar"
-----------------------------
## Erste Schritte
### Betriebssystem 
* Standard Betriebssystem: [Linux Debian](https://de.wikipedia.org/wiki/Debian)
* frei von kommerziellen Interessen
* Ubuntu / Raspbian
* auf [raspberrypi.org](https://www.raspberrypi.org/) downloadbar 

 Dateien müssen mit einem Zip-file gepackt und danach wieder 1 zu 1 entpackt werden.       
 Bei Ubuntu kann das mit dem **dd** -tool gemacht werden.

### SSH
Mit der SSH (Secure Shell) kann man sich z.B. mit einem Raspberry über das Netzwerk verbinden.
Sie ist anfangs immer deaktiviert, um unbefugtes verbinden zu verhindern. 

### screen
Mit Hilfe eines screens kann man z.B. einen Download laufen lassen, auch wenn man sich auslogt. 

     apt install screen (screen installieren)
     screen (screen wird erstellt)
     screen schließen mit strg + a + d
     screen -r (screen wieder anzeigen)               

### Befehle

**Verbinden**  

    ssh flelum17@10.200.114.226 (benutzer@IPadresse)              
    passwort eingeben (y = z wegen amerikanischer Tastatur)             
    passwd (passwort ändern)  
       
**Konfigurieren**          

    sudo raspi-config (Einstellungen: Kammera einschalten, Zeitzone festlegen, usw.)               
    
**Updaten**                

    sudo -i
    apt update
    apt upgrade                       
    
**Installieren**           

    sudo -i
    apt search java (suche nach dem Programm z.B. java)
    apt install java ( installieren von z.B. java)
    
 **User hinzufügen**                
 
    adduser flelum17 (username)                  
    less/etc/group (benutzername bei sudo hinzufügen)          
    
**Hostname ändern**                 

    nano /etc/hostname
    nano /etc/hosts
    reboot
    
**SSH Schlüsselpaar erstellen**

    sshkeygen (es werden 2 Schlüssel erstellt, ein privater und ein öffentlicher)
    
-----------------------------------
## Man in the middle
         
         Ein Man-in-the-Middle-Angriff (MITM-Angriff), auch Janusangriff
         (nach dem doppelgesichtigen Janus der römischen Mythologie)genannt,
         ist eine Angriffsform, die in Rechnernetzen ihre Anwendung findet.
         Der Angreifer steht dabei entweder physisch oder – heute meist – 
         logisch zwischen den beiden Kommunikationspartnern, hat dabei mit
         seinem System vollständige Kontrolle über den Datenverkehr zwischen
         zwei oder mehreren Netzwerkteilnehmern und kann die Informationen
         nach Belieben einsehen und sogar manipulieren. Die Janusköpfigkeit
         des Angreifers besteht darin, dass er den Kommunikationspartnern
         vortäuscht, das jeweiligeGegenüber zu sein. 
         
aus Wikipedia: [Man in the Middle Angriff](https://de.wikipedia.org/wiki/Man-in-the-Middle-Angriff)



![Man in the Middle](https://phoenixnap.com/blog/wp-content/uploads/2019/03/example-of-mitm-attack-min.png)
[Bild](https://phoenixnap.com/blog/wp-content/uploads/2019/03/example-of-mitm-attack-min.png)

Um 100% sicher vor einem Man in the Middle Angriff zu sein, sollte man gleich direkt am Gerät abreiten.

    
 
 
    
    
    
    
    
    
   







