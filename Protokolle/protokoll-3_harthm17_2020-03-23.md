# 3. Protokoll
---------------------------------------------
## Thema: Installation von Ubuntu
---------------------------------------------
* Datum:      23.03.2020
* Gruppe:     2  
* Abwesend:   keiner
* Verfasser:  Thomas Harrer 
* Klasse:     3AHME
* Schuljahr:  2019/20
---------------------------------------------
## Inhaltsverzeichnis

* [Download und Installation einer Virtual Box](#download-und-installation-einer-virtual-box)
  * [Herunterladen](#)
  * [](#)
* [Oracle VM VirtualBox Extension Pack installieren](#oracle-vm-virtualbox-extension-pack-installieren)
* [Virtuelle Maschine einrichten](#virtuelle-maschine-einrichten)
* [Ubuntu einrichten](#ubuntu-einrichten)
* [HTL Paket installieren](#htl-paket-installieren)
* [Lesezeichen in Firefox konfigurieren](#lesezeichen-in-firefox-konfigurieren)

---------------------------------------------
### Download und Installation einer Virtual Box
#### Herunterladen
Der erste Schritt ist, eine Virtual Box herunterzuladen. In meinen Fall musste ich eine Virtual Box für Windows herunterladen.
Um auf die Website zu kommen, klicken Sie [hier](https://www.virtualbox.org/wiki/Downloads)

#### Installation
Nachdem Sie die Installationsdatei heruntergeladen haben, müssen Sie diese dann ausführen und die Installationsschritte befolgen.

### Oracle VM VirtualBox Extension Pack installieren
Dannach muss das Oracle VM VirtualBox Extension Pack heruntergeladen werden. Dies wird dann auch automatisch installiert. Um das Pack herunterzuladen, klicken Sie [hier](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack)

### Virtuelle Maschine einrichten


### Ubuntu einrichten


### HTL Paket installieren
Anschließend muss das HTL Paket installiert werden.
Um das HTL Paket zu installieren, muss man zu allererst als Superuser einsteigen.
```
thomas@thomas-VirtualBox:~$ sudo -i
-> [sudo] Passwort für Thomas: 
```
Dannach müssen Sie die folgenden Befehle nach der vorgegeben Reihenfolge eingeben.
```
root@thomas-VirtualBox:~# wget -O - http://www.htl-mechatronik.at/ubuntu-htl/install | bash
root@thomas-VirtualBox:~# apt update
root@thomas-VirtualBox:~# apt dist-upgrade
root@thomas-VirtualBox:~# install htl
```

### Lesezeichen in Firefox konfigurieren

