# Besprechung Rasperry (Mini-Computer)      
#### Gerät 22
#### IP: 10.200.114.222 
-----------------------------------------------------------
## Inhaltsverzeichniss

1. [µC versus Raspberry Pi](#µc-versus-raspberry-pi)
   1. [Atmel 324P](#atmel-324p)
   1. [Rasperry Pi](#raspberry-pi)
1. [Linux Debian](#linux-debian)
1. [Secure Shell](#ssh-secure-shell)

## µC versus Raspberry Pi
### Atmel 324P
* Single Chip Computer
* 8 Bit µC... 32Kib FlashProgramme
* 2Kib SRAM Arbeitsspeicher
* Stromverbrauch: 1mW - 10mW
* Kosten: 1-2 €
* ECHTZEITFÄHIGKEIT

![Bild1](http://www.hobbytronics.co.uk/image/cache/data/atmel/atmega32u4-500x500.jpg)

[Bild1](http://www.hobbytronics.co.uk/image/cache/data/atmel/atmega32u4-500x500.jpg)

### Raspberry Pi
* Mini-Computer mit Ethernet, WLAN, USB, HDMI
* 32Bit/64Bit Leistungsstarke CPU
* 1GiB/2GiB/4GiB Arbeitsspeicher
* Stromverbrauch 1-2W bei Leerlauf
* Kosten: 30-40€
* Flash MMC (8/16/32GiB)

![Bild2](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/Raspberry_Pi_4_Model_B_-_Side.jpg/1200px-Raspberry_Pi_4_Model_B_-_Side.jpg)

[Bild2](https://upload.wikimedia.org/wikipedia/commons/thumb/f/f1/Raspberry_Pi_4_Model_B_-_Side.jpg/1200px-Raspberry_Pi_4_Model_B_-_Side.jpg)

## Linux Debian
* Ubuntu
* Raspian

-->[weitere Informationen](https://www.debian.org)

## SSH (Secure Shell)
Verbindung mit z.B. einem Raspberry Pi über ein Netzwerk (Internet/LAN)

SSH Schnittstelle ist standartmäßig aus Sicherheitsgründen deaktiviert. Um sie zu aktivieren muss mann eine Datei mit dem Namen 'ssh' auf der ersten Patition der MCC erstellen.

### Über SSH mit Raspberry verbinden:
1. ssh ***benutzer*@*ipadresse*** (z.B. ssh fucnim17@10.200.114.222)
1. standartpassword von raspberry eingeben
1. mit **passwd** password ändern

* mit **sudo raspi-config** kommt man in die Einstellungen

### Programme updaten
* **sudo -i**
* **apt update**
* **apt upgrade**

### programme installieren
* **sudo -i**
* **apt search *programm*** (z.B. apt search java)
* **apt install *programm*** (z.B. apt install screen; apt install default-jre)

### screen
Mit einem screen kann man Prozesse auch weiterlaufen lassen, wenn man sich ausloggt.
* **screen** .......... screen erstellen
* **screen -r** ....... screen wieder anzeigen

### User hinzufügen
* **adduser *username*** (z.B. adduser fucnim17)
* **less /etc/group***........... bei sudo Benutzername hinzufügen

### Hostname ändern
* **nano /etc/hostname**
* **nano /etc/hosts**

### SSH Schlüssel
* **ssh-keygen**
* **ssh-copy-id *benutzer*@*ipadresse*** (z.B. ssh-copy-id fucnim17@10.200.114.222)
