# Protokoll 04.05.2020 Pfanner
* **Thema:** Installation, Inbetriebnahme und Arbeit mit einer virtuellen Maschine mit Ubuntu 20.04
* **Datum:** 04.05.2020
* **Gefehlt:** -
* **Erstellt von:** Pfanner Jan

## Inhaltsverzeichnis
* [Vorbereitung](#vorbereitung-und-beschaffung-der-nötigen-dateien)
* [Installation und Inbetriebnahme der VM](Installation-und-Inbetriebnahme-der-VM)
* [Einlegen der virtuellen Disk](Einlegen-der-virtuellen-Disk)
* [Anfang mit Ubuntu](Von-0-bis-Ubuntu)
* [Arbeiten mit dem virtuellen System](Arbeiten-mit-dem-virtuellen-System)
* [Ändern der Lesezeichen in Firefox/Chrome](Ändern-der-Lesezeichen-in-Firefox/Chrome)


## Vorbereitung und Beschaffung der nötigen Dateien
Um eine virtuelle Maschine auf dem eigenen Rechner laufen zu lassen, verwenden wir die Software [Oracle VM VirtualBox](https://www.virtualbox.org/). Diese stellt die virtuelle Maschine bereit. Um darauf dann ein BEtriebssystem laufen zu lassen, benötigt man noch eine iso-Datei, die man im Internet finden kann. Für Ubuntu 20.04 ist das [hier](https://ubuntu.com/download/desktop) (die file ist recht groß, der download kann also etwas dauern).

Hat man beide Dateien parat, ist die Vorbereitung so gut wie abgeschlossen. Durch das Warten auf den Download der iso-Datei ist man bereits bestens gewappnet gegen etwaige kommende Ladebalken.

## Installation und Inbetriebnahme der VM
Die Installation von Oracle VM geht nicht über die Grundkenntnisse des Dateiinstallierens hinaus. Für unsere Zwecke haben wir auch noch ein [Extension Pack](https://download.virtualbox.org/virtualbox/6.1.6/Oracle_VM_VirtualBox_Extension_Pack-6.1.6.vbox-extpack) für die VM installiert. Hat man dies betriebsbereit, folgt die Erstellung der eigentlichen virtuellen Maschine. Dafür unter dem Menüpunkt "Maschine" *Neu* auswählen und die gewünschten Konfigurationen auswählen. Vorsicht: Der gewählte Speicherort sollte als grober Richtwert etwa 50Gib besitzen. Außerdem benötigen heutige Betriebssysteme für PCs mindestens 4 GiB RAM. Auch beim der virtuellen Maschine zugewiesenen Grafikspeicher sollte man nicht geizen, da sonst Abstürze auftreten können. Zuletzt ist es essenziell, im BIOS Hardwarevisualisierung aktiviert zu haben. 

Hat man alle Einstellungen vorgenommen, ist der virtuelle Rechner bereit. Allerdings noch ohne jegliches Betriebssystem.

## Einlegen der virtuellen Disk
Hier kommt nun die iso-Datei ins Spiel. Der button *Ändern* öffnet die Einstellungen der VM. Im Menüpunkt *Massenspeicher* legt man nun im virtuellen Laufwerk die virtuelle Installationsdisk ein. Damit ist alles bereit um Ubuntu zu starten. Dies passiert mit dem button *Starten*.

## Von 0 bis Ubuntu
Nun da der virtuelle Rechner betriebsbereit, mit einem Betriebssystem versorgt und aktiviert ist, folgt die Installation von Ubuntu. Diese ist wenig spannend und weitestgehend selbsterklärend. Hat man alle Übungen in Geduld gemeistert, steht man nun vor einem vollwertigen, einsatzbereiten Betriebssystem. Dieses wird als Gastsystem bezeichnet, während das darüberliegende außerhalb der VM Hostsystem genannt wird (von engl. Host = Gastgeber).

## Arbeiten mit dem virtuellen System
Als guter Gastgeber ist es wichtig, sein virtuelles Betriebssystem ordentlich auszustatten. Erstens gibt es dafür die *Virtualbox Guest Additions*, die als iso-Datei im Installationsordner der Oracle VM zu finden ist. Da auch diese Datei eine virtuelle disk ist, wird sie wie gehabt in das virtuelle Laufwerk außerhalb der VM eingelegt. 
Falls dieses Vorgehen keine Wirkung zeigt, wie es bei mir der Fall war, besteht die Möglichkeit der Installation durch zwei einfache Kommandos im Terminal des Gastsystems.

`sudo add-apt-repository multiverse`

`sudo apt install virtualbox-guest-dkms virtualbox-guest-x11`

Erfolgreiche Installation zeigt sich sofort dadurch, dass die VM nicht mehr auf ein kleines Fenster beschränkt ist. Für angenehmes Arbeiten unerlässlich.

Für Arnfelser HTL-Schüler wie uns gibt es das praktische HTL-Paket, erhältlich von unserem hauseigenen Server. Alle wichtigen Infos dazu [hier]( http://www.htl-mechatronik.at/ubuntu-htl/readme). Auch Installationskommandos für Qucs und PostgreSQL sind hier auffindbar.

## Ändern der Lesezeichen in Firefox/Chrome
Der Webbrowser Mozilla Firefox kommt standardmäßig mit dem Betriebssytem, während Chrome zum selber Installieren ist. Als Reihenfolge für die Änderung der Lesezeichen empfehle ich erst Firefox und dann Chrome. In Firefox ist es möglich, unter dem Reiter *Lesezeichen* diese zu verwalten. Die Auswahl von *Importieren und sichern* erlaubt, eine vorhandene Liste von Lesezeichen einzubinden (wiederherstellen). Da solch eine im HTL-Paket inbegriffen ist, haben wir gleich alle wichtigen Links parat.
Chrome erlaubt es einem, die Lesezeichen von Firefox zu importieren, was weitere Einstellungen überflüssig macht. 


Somit hat man nun eine funktionierende virtuelle Maschine mit der zum gegenwärtigen Stand neuesten Ubuntu-Version, dem HTL-Paket und maßgeschneiderten Browser-Lesezeichen.
