# Protokoll 6 La1/SX 3AHME (2019/20)

-------------------------

* **Thema:** Installation von Ubuntu 18.04 LTS und Software in einer virtuellen Maschine
  * **Datum:** 16.03.2020
  * **Gefehlt:** Gschier Michael, Augustin Andreas (im moodle Chat)
  * **Erstellt von:** Golser Raphael
  
  -------------------------------------------------------
  
## Inhaltsverzeichnis

1. [Download der Virtualbox](#download-der-virtualbox)
2. [Installation von Oracle VM VirtualBox Extension Pack](#installation-von-oracle-vm-virtualbox-extension-pack)
3. [Erstellen einer virtuellen Maschine](#erstellen-einer-virtuellen-maschine)
4. [Installieren von Ubuntu in der virtuellen Maschine](#installieren-von-ubuntu-in-der-virtuellen-maschine)
5. [Virtualbox Guest Additions in Ubuntu installieren](#virtualbox-guest-additions-in-ubuntu-installieren)
6. [Ein Verzeichnis zwischen dem Gastsystem und dem virtuellen System teilen](#ein-verzeichnis-zwischen-dem-gastsystem-und-dem-virtuellen-system-teilen)
7. [HTL Paket installieren](#htl-paket-installieren)
8. [Im Firefox und im Chrome Browser die Lesezeichen Menüleiste konfigurieren](#im-firefox-und-im-chrome-browser-die-lesezeichen-menüleiste-konfigurieren)

----------------------------------------------------------

## Download der Virtualbox

Um die [Virtualbox](https://www.virtualbox.org/wiki/Downloads) zu  installieren muss man auf der Website sein Betriebssystem auswählen und man bekommt ein Programm dass die endgültige [Virtualbox](https://www.virtualbox.org/wiki/Downloads) installiert.
In diesem Programm kommt ein Fenster in dem man die weiteren Einstellungen der Installation machen kann.

![Oracle_VirtualBox](https://atechtown.b-cdn.net/wp-content/uploads/2018/03/install-virtualbox-1.png)

---------------------------------------------

## Installation von Oracle VM VirtualBox Extension Pack

Falls die installierte Virtualbox nicht die neueste/gewünschte Version besitzt, kann man ein [VirtualBox Extension Pack](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack) installieren. Wir bennötigen die Version 6.1.4 weshalb wir dazu ein [Extension Pack](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack) installieren mussten. Da man das [Extension Pack](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack) direkt in der Virtualbox öffnen kann wird dies, wenn man es direkt in der Virtualbox öffnet, auch die Virtualbox direkt updaten.

1.
![How_to_Install_VirtualBox_Extension_Pack-TecAdmin](https://tecadmin.net/wp-content/uploads/2018/02/virtualbox-extension-pack-installation.png)

2.
![How_To_Install_Virtualbox_Extension_Pack_Correctly](https://www.dev2qa.com/wp-content/uploads/2019/06/clidk-install-button-to-install-virtualbox-extensions.png)

-----------------------------------------------------------

## Erstellen einer virtuellen Maschine

Der erste Schritt ist den Menüpunkt ````neu```` auszuwählen um überhaupt ein virtuelles System zu erstellen. Danach kommt ein Fenster worin man das Betriebssystem und den Speicherort wählt.

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://digitalstartup.co.uk/uploads/default/original/1X/93e3a2544dd096efaf4fc92ccc380177b854b858.png)

Dann wählt man die Speichergröße des Arbeitsspeichers. 

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://digitalstartup.co.uk/uploads/default/original/1X/ff92edb93dadec861644d5d413a477496ce00407.png)

Im nächsten Schritt wird nach einer Festplatte gefragt.

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://digitalstartup.co.uk/uploads/default/original/1X/2df739486631829652da57dd785aa2bd11e54002.png)


Wenn man eine Festplatte kann man sich entsscheiden zwischen *VDI(VirtualBox Disk Image), VHD(Virtual Hard Disk) und VMDK(Virtual Machine Disk).*  

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://digitalstartup.co.uk/uploads/default/original/1X/74c3fcf977e8936ba393354971437a41120d16a0.png)


Als nächstes kann man entweder eine *dynamisch alloziert* oder einer mit *fester Größe*. Die dynamisch allozierte Festplatte speichert nur dann Daten auf die physische Platte des Hosts, wenn der Gast auch Daten schreibt. Hingegen die mit fester Größe eine bessere Performance bietet, aber dafür kann das Erzeugen dieser Festplatte länger dauern. 

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://digitalstartup.co.uk/uploads/default/original/1X/40b56d1a2f7a7005c3eabb9928ab977908e7f7c4.png)


Als nächstes wählt man die Größe und den Speicherort der Festplatte. 

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://digitalstartup.co.uk/uploads/default/original/1X/76f1411042b1eb3fa47a4e65c431d5b6bb9160eb.png)

Hat man dies geschafft hat man dann eine virtuelle Maschine erstellt.

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://digitalstartup.co.uk/uploads/default/original/1X/a1d04d3018ed45d396fe562dc3c22e03a3da7833.png)

------------------------------------------------

## Installieren von Ubuntu in der virtuellen Maschine

Zuerst müssen noch ein parr Einstellungen gemacht werden bevor das Installieren im virtuellen System beginnt.
Dafür gehen wir in den Menüpunkt ````Ändern```` und wählen die Größe von unserer CPU beim Punkt ````System````. Man sollte die Größe der CPU nicht zu groß und auch nicht zu klein wählen denn bei beiden Option kommt man dann nicht in Ubuntu hinein.

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://www.ease2code.com/wp-content/uploads/2017/10/ease2code-VM-properties.jpg)

Danach geht man zum Punkt ````Massenspeicher````, dort ist ein blaues CD Zeichen. Dort ist dann rechts eine weitere blaue CD, auf die man dann clickt und ````Virtuelles optisches Medium auswählen/erzeugen...```` auswählt

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://www.techmespot.com/wp-content/uploads/2016/12/Install-Ubuntu-16.04-On-Virtualbox-11-1024x519.png)

Hat man dies ausgewählt kann man oben links ````Hinzufügen```` auswählen um den Speicher zu kommen und dort dann die  installierte [Ubuntu Version](https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64) auszuwählen und das virtuelle System einbinden.

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://www.techmespot.com/wp-content/uploads/2016/12/Install-Ubuntu-16.04-On-Virtualbox-12.png)

Nun speichert man nur noch die Änderungen wenn man unten auf ````OK```` drückt.
Als nächstes Startet man das virtuelle System mit dem Menüpunkt ````Starten````.

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://www.techmespot.com/wp-content/uploads/2016/12/Install-Ubuntu-16.04-On-Virtualbox-14.png)

Jetzt startet sich das virtuelle System mit Ubuntu und wir kommen in ein Fenster in dem wir unsere gewünschte Sprache auswählen und Ubuntu installieren können.

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://1.bp.blogspot.com/-8lgZbL3mlAo/V0tMlhi85gI/AAAAAAAABbw/hX8ayE0V4kIwAOvMmSvcK9L2MFE7BCNbACLcB/s640/VirtualBox_Ubuntu1604try_29_05_2016_04_00_21.png)

Als nächstes kommt die Tastaturbelegung. Dann fängt installation erst so richtig an,  denn jetzt kann man auswählen ob man es Normal installiert haben will oder nur eine minimale Installation und unter ````anderen Option```` hat man die Option ob Ubuntu sich während der Installation auch updates herunterladen darf oder nicht und dann noch Einstellung mit bestimmten Lizenzbedienungen die Ubuntu unterliegt.

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://1.bp.blogspot.com/-JyIdtXj70nI/V0tNfv9gQzI/AAAAAAAABb4/JV-LCjo0SCsOmJIRRGR1naXuQoqPIkM8ACLcB/s640/VirtualBox_Ubuntu1604try_30_05_2016_01_41_38.png)
(Ich habe leider keine Grafik gefunden die die auswahl der Installationen zeigt.)

Nun wenn man dies erledigt hat kann man entweder die Daten von der erstellten Festplatte löschen und so Ubuntu installieren oder eine Partition selbst anlegen. Wenn man das obere Feld auswählt hat man noch die OPtion Ubuntu zu verschlüsseln und LVM für die Installation verwenden. LVM ist ein Programm die die Erstellung von Abbildern erlaubt und erleichtert die Größenänderung von der Partition.

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://1.bp.blogspot.com/-iFXbSKOUz2Y/V0tN9yFNWMI/AAAAAAAABb8/OWAKPt8Vsw0pSlV8ub1HIJFaIeSeYKm2QCLcB/s640/VirtualBox_Ubuntu1604try_30_05_2016_01_42_06.png)

Nun für die Installation braucht man einen Sicherheitsschüssel für das vituelle System und den erstellt man im nächsten Schritt.  Ubuntu fragt jetzt nach dem Standort, dann nach den Namen bzw. auch dem Benutzernamen und als letztes muss man nur mehr ein Passwort für den Benutzer anlegen.

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://4.bp.blogspot.com/-Qt0QT34VDow/V0tO28lWc_I/AAAAAAAABcQ/BgW6uslavN4yiJ_KaKUlnWKmZn1ehJquQCLcB/s640/VirtualBox_Ubuntu1604try_30_05_2016_01_43_31.png)

Jetzt wird Ubuntu auf die virtuelle Festplatte installiert. Nun muss sich das System nur noch rebooten und man kann sich in Ubuntu einloggen.

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://3.bp.blogspot.com/-DzfH1C__0UM/V0tP8l75OpI/AAAAAAAABcg/2crl8Ra7CbMgcEi26EDooj5s6zI4FGlUQCLcB/s640/VirtualBox_Ubuntu-16.04_30_05_2016_01_53_17.png)

-------------------------------------------

## Virtualbox Guest Additions in Ubuntu installieren

Wenn wir in unserer virtuellen Maschine drinnen sind müssen wir den Menüpunkt ````Geräte```` auswählen und dort dann den Punkt ````Gasterweiterungen einlegen...````.

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](https://lh3.googleusercontent.com/proxy/a3KiqEepXBZuryXWFiS4M_0wGt4HWQdshJuzHbdPUajXYX0NNGUPSDydhlESUNyHEFTno_S7KEwlGJI78UhiE-6ep-NdaomCcGdAiYiTpctiRaJRnBMq3Jm2kHQNy8v9Y-51ByEBX16ruw)

Ist diese Option gedrückt worden kommt ein Fenster ob wir uns sicher sind eine automatische Software von unserem zu starten und dort clickt man nur die Option Starten.

![How_to_install_Ubuntu_Server_18.04_on_Windows_10](http://www.misfitgeek.com/wp-content/uploads/2017/09/VB_Guest_add_1-768x578.png)

Es wird das Terminal geöffnet und es werden die Guest Assitions installiert:
````bash
Verifying archive integrity... All good.
Uncompressing VirtualBox 6.1.4 Guest Additions for Linux........
VirtualBox Guest Additions installer
Copying additional installer modules ...
Installing additional modules ...
VirtualBox Guest Additions: Starting.
VirtualBox Guest Additions: Building the VirtualBox Guest Additions kernel 
modules.  This may take a while.
VirtualBox Guest Additions: To build modules for other installed kernels, run
VirtualBox Guest Additions:   /sbin/rcvboxadd quicksetup <version>
VirtualBox Guest Additions: or
VirtualBox Guest Additions:   /sbin/rcvboxadd quicksetup all
VirtualBox Guest Additions: Building the modules for kernel 5.3.0-28-generic.

This system is currently not set up to build kernel modules.
Please install the gcc make perl packages from your distribution.
VirtualBox Guest Additions: Running kernel modules will not be replaced until 
the system is restarted
Press Return to close this window...
````

Wenn man jetzt wieder beim Menüpunkt ````Ändern```` wieder unter ````Massenspeicher```` geht kann man sehen, dass statt dem alten System jetzt eine ````VBoxGuestAdditions.iso```` drinnen ist.

----------------------------------------------------
