# Protokoll 3 Labor-SX (2019/20)

------------------------------------------------------------

* **Erstellt von:** Vanessa Plieschnegger
* **Datum:** 04.05. 2020
* **Thema:** Installation con Ubuntu in der Virtualbox
* **Fehlend:** keiner

------------------------------------------------------------

## Inhaltsverzeichnis
1. [Installation der Virtualbox](#instalaltion-der-virtualbox)
2. [Oracle VM VirtualBox Extension Pack](#oracle-vm-virtualbox-extension-pack)
3. [Virtuelle Maschine erstellen und einrichten](#virtuelle-maschine-erstellen-und-einrichten)
4. [Virtualbox Guest Additions installieren](#virtualbox-guest-additions-installieren)
5. [HTL Paket installieren](#htl-paket-installieren)

------------------------------------------------------------

### Installation der Virtualbox
Zuerst musste man die Installationsdatei herunterladen [hier](https://www.virtualbox.org/wiki/Downloads).
Sobald man dies erledigt hat, muss man nur noch die Installation fertigstellen.

### Oracle VM VirtualBox Extension Pack
Sobald man die Installation der Birtualbox erfolgreich abgeschlossen hat, muss man das Oracle VM VirtualBox Extension Pack herunterladen [hier](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack).
Dieses Pack wird dann automatisch installiert!

### Virtuelle Maschine erstellen und einrichten
Wir mussten ein Gastsystem in der Virtualbox erstellen, welches als Betriebssystem Ubuntu nutzt. Hierführ mussten wir Ubuntu 20.04 LTS [hier](https://ubuntu.com/download/desktop)
herunterladen und diese Datei dann anschließend in der Virtualbox installieren.

Wenn man eine neue Virtualebox erstellen möchte, muss man auf den Button **Neu** klicken.
Nun gibt man den Gewünschten Namen ein. In unserem Fall **Gastsystem** außerdem gibt man den Pfad ein, wo die Datei gespeichert wird.
Nun kann man den gewünschten Speicherplatz festlegen, welcher dem System zur Verfügung steht.
Jetzt muss man die iso Datei also Ubuntu 20.04 LTS installieren.
Nun kann man die Virtualbox starten.

### Virtualbox Guest Additions installieren
Um in der Virtualbox die Guest Additions installieren zu können, geht man zuerst einmal in den Terminal. Hier muss man nun 2 Befehle eingeben.
```
$ sudo add-apt-repository multiverse
$ sudo adp install virtualbox-guest-dkms virtualbox-guest-x11
```
Sobald man diese 2 Befehle ausgeführt hat, sind die Guest Additions installiert.

### HTL Paket installieren
Zuguterletzt habe ich noch das HTL Paket installiert hierführ muss man nur die folgenden Befehle eingeben.
```
$ sudo -i
$ wget -O - http://www.htl-mechatronik.at/ubuntu-htl/install | bash 
$ apt update
$ apt dist-upgrade
$ apt install htl
```
