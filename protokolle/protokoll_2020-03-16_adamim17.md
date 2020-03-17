# Protokoll 2020.03.16
--------------------------
**Erstellen und einrichten einer Virtual-Box mit Ubuntu**  
Autor: **Mike Adam**  
Datum: **16.02.2020**

--------------------------

## Inhaltsverzeichnis

## Herunterladen und installieren der Virtual-Box
### Herunterladen:
Als erstes wird die [Installationsdatei](https://www.virtualbox.org/wiki/Downloads) für die Virtual-Box Heruntergeladen.
### Installation:
Nachdem die Installationsdatei heruntergeladen ist, muss man sie ausführen und den Installatonsschritten folgen.

## Installation des Oracle VM VirtualBox Extension Packs
Die [Installationsdatei](https://www.virtualbox.org/wiki/Downloads) Herunterladen und Installieren. Die Installation verläuft komplett automatisch.

## Virtuelle Maschine Starten und einrichten
Herunterladen einer .iso Datei des ausgewählten Betriebssystems. In unserem Fall haben wir eine [Ubuntu 18.04 Datei](https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64) heruntergeladen. 

## Einrichten der Virtual-Box
* Als erstes wird eine neue Virtual-Box erstellt   
![](https://cdn.discordapp.com/attachments/420277853033332736/689397168708124684/Bild_1.PNG)

* Dannach muss man den gewünschten Namen der Virtual-Box eingeben, den Dateipfad, wo die Dateien gespeichert werden sollen und das gewünschte Betriebssystem mit der Distribution.   
![](https://cdn.discordapp.com/attachments/420277853033332736/689399639647977520/Bild_2dasdasdasd.png)

* Als nächsten schritt muss man der Virtuellen Maschine Arbeitsspeicher zuweisen
![](https://cdn.discordapp.com/attachments/420277853033332736/689397174659973122/Bild_3.PNG)

* Bei dem nächsten Fenster muss man eine Festplatte erstellen und die Größe der Festplatte Festlegen. (in unserem Fall min. 50gb)   
![](https://cdn.discordapp.com/attachments/420277853033332736/689397176694341650/Bild_4.PNG)

* Wenn alles ausgewählt ist, kommt man wieder zum Anfang. In diesem Moment sollte man die Virtuelle Maschine noch nicht starten, weil sie noch kein Betriebssystem hat. Als nächsten Schritt muss man die .iso Datei, die man schon heruntergeladen hat in die Virtuelle Maschine einfügen, dazu muss man die Virtuelle Maschine auswählen und auf "ändern" drücken.   
![](https://cdn.discordapp.com/attachments/420277853033332736/689397168708124684/Bild_1.PNG)

* Im Fester, das aufgemacht wurde, kann man unter "Massenspeicher", bei dem Symbol, das wie eine CD ausschaut die .iso Datei auswählen   
![](https://cdn.discordapp.com/attachments/420277853033332736/689397181127458826/Bild_7.PNG)

* Nun kann man die Virtuelle Maschine starten und Ubuntu installieren.
* Wenn die Virtuelle Maschine hochgefahren ist, kann man unter "Geräte", "Gästerweiterungen einlegen" die Virtualbox Guest Additions installieren.   
![](https://cdn.discordapp.com/attachments/420277853033332736/689409868079300639/Unbenanntsadasd.PNG)

 * Unter "ändern", wo man die .iso Datei ausgewählt hat kann man auch einen gemeinsamen Ordner erstellen      
 ![](https://cdn.discordapp.com/attachments/420277853033332736/689412325056315430/ydsfysdfy.PNG)
 
 ## HTL-Paket installieren
 * Um das HTL-Paket zu installieren muss man sich in der Shell als Superuser anmelden.
````bash
  adamim17@Mike-Virtual-Box:~$ sudo -i
````
* Um das HTL-Paket zu installieren braucht man folgende Befehle:
````bash
  root@Mike-Virtual-Box:~$ wget -O - http://www.htl-mechatronik.at/ubuntu-htl/install | bash
  root@Mike-Virtual-Box:~$ apt update
  root@Mike-Virtual-Box:~$ apt dist-upgrade
  root@Mike-Virtual-Box:~$ apt install htl
````
* Die Lesezeichen im Firefox und Chrome zu konfigurieren habe ich nicht geschafft.

