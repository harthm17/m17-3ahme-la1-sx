# Besprechung Rasperry (Mini-Computer)      
### Gerät 22
#### IP: 10.200.114.222 


Atmel 324P.... Single Chip Computer...8 Bit µC... 32Kib FlashProgramme... 2Kib SRAM Arbeitsspeicher... Stromverbrauch: 1mW - 10mW... 1-2 €... ECHTZEITFÄHIGKEIT

Raspery Pi... Mini-Computer mit Ethernet, WLAN, USB, HDMI.... 32Bit/64Bit Leistungsstarke CPU... Flash MMC (8/16/32GiB)... 1GiB/2GiB/4GiB Arbeitsspeicher... Stromverbrauch 1-2W bei Leerlauf... 30-40€

## Linux Debian
### Ubunto  
### Raspian

## SSH (Secure Shell)
Verbindung mit z.B. einem Raspberry Pi über ein Netzwerk (Internet/LAN)

SSH Schnittstelle ist standartmäßig aus Sicherheitsgründen deaktiviert. Um sie zu aktivieren muss mann eine Datei mit dem Namen 'ssh' auf der ersten Patition der MSD erstellen.

### Über SSH mit Raspberry verbinden:
* ssh benutzer@ipadresse
* standartpassword raspberry eingeben
* mit passwd password ändern

* mit sudo raspi-config kommt man in die Einstellungen

### Programme updaten
* sudo -i
* apt update
* apt upgrade

### programme installieren
* sudo -i
* apt search programm (z.B. apt search java)
* apt install programm (z.B. apt install screen; apt install default-jre)

### screen
Mit einem screen kann man Prozesse auch weiterlaufen lassen, wenn man sich ausloggt.
* screen .......... screen erstellen
* screen -r ....... screen wieder anzeigen

### User hinzufügen
* adduser username (z.B. adduser fucnim17)
* less etc/group........... bei sudo Benutzername hinzufügen
