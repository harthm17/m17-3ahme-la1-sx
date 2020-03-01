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

**Verbinden**              
    ssh flelum17@10.200.114.226 (benutzer@IPadresse)           
    
   







