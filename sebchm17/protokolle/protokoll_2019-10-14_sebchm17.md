# Protokoll Labor/SX 3AHME (2019/20)

* **Thema** : Shell; Datenträger
* **Datum** : 14.10.2019
* **Gruppe** : 4
* **Protokollverfasser** : Christoph Sebernegg
* **Protokoll letzte Einheit** : [1.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/sebchm17/sebchm17/protokolle/protokolle_2019-09-30sebchm17.md)

--------------------------------------------------------------------------------------------------------------------------------
## Inhaltsverzeichnis
1.  [Datenträger und Partitionen](#datenträger-und-partitionen)
1.  [Verzeichnisse](#verzeichnisse)
1.  [Mount](#mount)
      * [Gerät einloggen](#gerät-einloggen)
      * [Gerät ausloggen](#gerät-ausloggen)
1.  [Neuen Benutzer anlegen](#neuen-benutzer-anlegen)
1.  [Dll](#dll)
      * [Dll-Hölle](#dll-hölle)
1.  [Rechte](#rechte)
      * [Rechte ändern](#rechte-ändern)

--------------------------------------------------------------------------------------------------------------------------------
## Datenträger und Partitionen
[Datenträger][1]

Ein Datenträger muss mit einem Dateisystem formatiert sein damit darauf Dateien und Verzeichnisse gespeichert werden können.
Eine Partition ist ein Teil auf dem Datenträger, die von anderen Partitionen getrennt ist.
In Linux werden Partitionen als Block Device im verzeichniss /dev bereitgestellt. In Ubuntu können die Partitionstabellen mit dem Programm Gparted angezeigt werden.

--------------------------------------------------------------------------------------------------------------------------------
## Verzeichnisse

/etc: Im Ordner etc findet man Dateien für die Systemsteuerung.
/root: Das ist das "Home Verzeichnis" des Super Users.
/tmp: ist ein Temporäres-verzeichnis, dass bei einem reboot alle gespeicherten Dateien löscht.
/lib: Im Ornder lib sind die Bibliotheksdateinen enthalten.
/home: Hier befinden sich alle Verzeichnisse aller Benutzer
/boot: Das ist der Boot-ordner und hier liegen die datein die für den Bootvorgang zuständig sind.
/dev: enthält alle Gerätedateien, über die die Hardware im Betrieb angesprochen werden.
/var: enthält variable Dateien. 
/mnt: Im mnt Verzeichnis liegen Geräte, die manuell temporär eingebunden wurden.
/bin: Im dem Verzeichnis bin liegen wichtige Systemprogramme wie zum Beispiel die Shell.
/run: Hier liegen Dateien, die für laufende Programme wichtig sind.
/usr: enthält die meisten Systemtools, Bibliotheken und installierten Programme.
/proc und /sys: sind virtuelle Verzeichnisse, über die der Benutzer direkt mit dem Kernel komunizieren kann.

```bash
chris@chris:~$ ls /var/log
alternatives.log  	    dist-upgrade     	    installer           syslog.1
apt               	    dpkg.log         	    journal             syslog.2.gz
auth.log         	    faillog         	    kern.log            syslog.3.gz
auth.log.1        	    fontconfig.log   	    kern.log.1          tallylog
bootstrap.log     	    gdm3             	    lastlog             unattended-upgrades
btmp              	    gpu-manager.log  	    speech-dispatcher   wtmp
cups              	    hp               	    syslog

chris@chris:~$ ls /var/log/syslog
/var/log/syslog

chris@chris:~$ tail -f /var/log/syslog
Oct 17 21:19:00 chris gnome-software[2003]: message repeated 3 times: [ Failed to load snap icon: local snap has no icon]
Oct 17 21:19:19 chris libreoffice-writer.desktop[2102]: javaldx: Could not find a Java Runtime Environment!
Oct 17 21:19:19 chris libreoffice-writer.desktop[2102]: Please ensure that a JVM and the package libreoffice-java-common
Oct 17 21:19:19 chris libreoffice-writer.desktop[2102]: is installed.
Oct 17 21:19:19 chris libreoffice-writer.desktop[2102]: If it is already installed then try removing ~/.libreoffice/3/user/config/javasettings_Linux_*.xml
Oct 17 21:19:19 chris libreoffice-writer.desktop[2102]: Warning: failed to read path from javaldx
Oct 17 21:19:19 chris kernel: [  126.331911] kauditd_printk_skb: 28 callbacks suppressed
Oct 17 21:19:19 chris kernel: [  126.331912] audit: type=1400 audit(1571339959.616:39): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/usr/share/drirc.d/00-mesa-defaults.conf" pid=2122 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct 17 21:19:19 chris kernel: [  126.333132] audit: type=1400 audit(1571339959.620:40): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/usr/share/drirc.d/00-mesa-defaults.conf" pid=2122 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
Oct 17 21:19:53 chris PackageKit: get-updates transaction /136_edaaacdd from uid 1000 finished with success after 785ms

chris@chris:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 142
model name	: Intel(R) Core(TM) i7-8550U CPU @ 1.80GHz
stepping	: 10
cpu MHz		: 1991.999
cache size	: 8192 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 22
wp		: yes

```  
--------------------------------------------------------------------------------------------------------------------------------## Mount 

Der Befehl ``mount`` zeigt alle aktuelle gemounteten Dateisysteme an, die im System eingehängt sind.

```bash
chris@chris:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=2550532k,nr_inodes=637633,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=514880k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
```

In der letzten Zeile wird angezeigt, dass es sich um die Hauptfestplatte handelt und sie in ext4 formatiert ist.

### Gerät einloggen

Früher musste man einen Usb Stick immer einloggen und wieder aussloggen. Heute wird dies automatischdurchgeführt.
Mit dem Komando ```mount``` kann man ein man manuelles Einhängen durchführen.
 ```bash
 chris@chris:~$ sudo mount /dev/sdb1/mnt
 ```

### Gerät ausloggen

Ein eingehängtes Dateisystem kann mit dem Befehl umount wieder entfernt werden.
```bash
chris@chris:~$ sudo umount /dev/sdb1
```

--------------------------------------------------------------------------------------------------------------------------------
## Neuen Benutzer anlegen

Einen neuen Benutzer in der Shell anzulegen funktioniert mit dem Befehl ``adduser``  aber es funktioniert auch über eine etwas altmodischere Art quasi den Benutzer mit der Hand anzulegen. 

```bash
chris@chris:~# sudo-i
```
Dafür muss zuerst in den superuser mode (root) gewechselt werden.
```bash
root@chris:~# nano /etc/passwd
sebchm17:schueler:1000:1000::/home/sebchm17:/bin/bash
```
Um diese Datei anschauen zu können gibt man entweder cat oder nano ein. Hier werden alle Benutzer des Systems aufgelistet.
```bash
root@chris:~# nano /etc/group
sebchm17::1000:sebchm17
```
Hier sind die Benutzergruppen und ihre Mitglieder zu finden.
```bash
root@chris:~# nano /etc/shadow
```
In älteren Ubuntu-Versionen wurden die Passwörter in passwd Dateien gespeichert. Diese Methode um Passwörter zu speichern war sehr naiv, weil man die Passtwörter sehr leicht entschlüsseln und auslesen konnte. Deswegen gibt es etc/passwd, in der die Angaben über die Passwörter durch ein spezielles System besser geschützt werden.

--------------------------------------------------------------------------------------------------------------------------------
## Dll
[Wikipedia](https://de.wikipedia.org/wiki/Dynamic_Link_Library)

>Dynamic Link Library (DLL) bezeichnet allgemein eine dynamische Programmbibliothek; meist bezieht sich der Begriff jedoch auf die für die Betriebssysteme Microsoft Windows und OS/2 verwendete Variante. DLL-Dateien verwenden das auch für ausführbare EXE-Dateien gebräuchliche Dateiformat, das in 16-Bit-Programmen das New-Executable-Format (NE)[1] und in 32- und 64-Bit-Programmen das Portable-Executable-Format (PE) ist. Diese Dateien können Programmcode (Maschinencode), Daten und Ressourcen in beliebiger Kombination enthalten.

Windows braucht bei Updates 8-10 mal mehr GB als Linux.

### Dll Hölle

Der Ausdruck "Dll-Hölle" beschreibt ein Problem, das durch die Installation von Dynamic Link Library bei Betriebssystemen entstehen kann.

--------------------------------------------------------------------------------------------------------------------------------
## Rechte 

Datei :
        
        r .... Inhalt nur lesen
        
        w .... Inhalt modifizieren
        
        x .... Inhalt als programm ausfühern
 

Verzeichnis: 

        r .... Inhalt zu sehen
             
        w .... Inhalt verändern
             
        x .... In das Verzeichnis wechseln
     


### Rechte ändern

Rechte werden mit dem oktalsystemgerechnet, dh 111 entspircht 7.

```bash

chris@chris:~$ ls -l
insgesamt 76
drwxr-xr-x 2 chris chris 4096 Okt 12 19:47 Bilder
drwxr-xr-x 2 chris chris 4096 Okt 15 21:44 Dokumente
-rw-r--r-- 1 chris chris    7 Okt 13 15:17 test1.odt
-rw-r--r-- 1 chris chris   27 Okt 13 15:28 testdatei.odt
-rw-r--r-- 1 chris chris   20 Okt 13 15:13 test.odt
```

Die Zeilen, die mit einem d anfangen sind Verzeichnisse. Nach dem d kommen die ersten drei Rechte und diese beziehen sich auf den Besitzer (Owner). Die nächsten drei Rechte beziehen sich auf die Gruppe (group) und zum schluss kommen die Rechte für alle Anderen (others). Alle neu erstellten Dateien haben das Recht x noch nicht. Um den Inhalt als programm ausführen zu können ändert man es wie in deisem Beispiel.


```bash
chris@chris:~$ chmod 750 /home/Dokumente/test1.odt
-rwxr-x--- 1 chris chris    7 Okt 16 20:36  test1.odt
````
--------------------------------------------------------------------------------------------------------------------------------
[Protokoll]:https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/sebchm17/sebchm17/protokolle/protokolle_2019-09-30sebchm17.md

[1]:https://www.google.com/url?sa=i&rct=j&q=&esrc=s&source=images&cd=&ved=2ahUKEwiDguKV-6PlAhXECuwKHVEUALYQjRx6BAgBEAQ&url=https%3A%2F%2Faskubuntu.com%2Fquestions%2F738750%2Fcant-install-windows-10-alongside-ubuntu-mbr-error&psig=AOvVaw2vhHPiv5KrXulP44vjbXqN&ust=1571424375747436
