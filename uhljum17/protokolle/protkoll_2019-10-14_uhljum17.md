# 2. Protpkoll

------------------------------

* **Thema:** Datenträger, Shell
* **Datum:** 14.10.2019
* **Gefehlt:** -
* **Gruppe:** 4
* **Protkollverfasser:** Uhl Julian
* **Letztes Protokoll:** [1. Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/uhljum17/uhljum17/protokolle_2019-09-30_uhljum17.md)
* **Nächstes Protkoll:**

------------------------------

## Inhatlverzeichniss
1. [Datenträger](#datenträger)
   1. [Patitionen](#patitionen)
   1. [Verzeichnisse](#verzeichnisse)
1. [Einhängen von Dateisystemen](#Einhängen-von-Dateisystemen)
1. [Benutzer erstellen](#benutzer-erstellen)
1. [Dll](#dll)
1. [Rechte](#rechte)
   1. [Dateirechte](#dateirechte)
   1. [Verzeichnisrechte](#verzeichnisrechte)
   1. [Ändern von Besitzer und Gruppe](#Ändern-von-Besitzer-und-Gruppe)

-------------------------------

## Datenträger

---------------------

Ein Datenträger ist ein Speichermedium. Dieses Speichermedium kann entweder beschrieben oder ausgelesen werden. Ein Datenträger ist z.B. eine Festplatte oder Diskette. Es gibt tragbare oder fest eingebaute Datenträger. Ohne die Datenträger könnten keine Dokumente und Daten gespeichert werden. Die Datenträger sind ein sehr wichtiger Teil von einem Computersystem.

---------------------

### Patitionen

---------------------

Patitionen sind aufteilungen eines Datenträgers in unterschliedlich vielen und unterschiedlich großen Teilen. In diesen Teilen befindet sich jeweils ein Dateisystem. Bei Linux ist es ext4.

---------------------

### Verzeichnisse

---------------------
```

 Mit dem Befehl ls -l / lässt sicht der Verzeichnisbaum sichtbar machen.

Auf einem Raspberry Pi ergibt das:

root@pi:~# ls -l /

insgesamt 264

drwxr-xr-x   2 root root   4096 Sep  7 07:29 bin

drwxr-xr-x   3 root root  16384 Jän  1  1970 boot

drwxr-xr-x  12 root root   3200 Sep 25 12:38 dev

drwxr-xr-x 104 root root   4096 Sep 15 17:29 etc

drwxr-xr-x   4 root root   4096 Sep  7 07:25 home

drwxr-xr-x  14 root root   4096 Mai  7 01:15 lib

drwx------   2 root root  16384 Mai  7 00:10 lost+found

drwxr-xr-x   2 root root   4096 Mai  7 00:12 media

drwxr-xr-x   2 root root   4096 Jän 11  2015 mnt

drwxr-xr-x   6 root root   4096 Mai  7 01:24 opt

dr-xr-xr-x 104 root root      0 Jän  1  1970 proc

drwx------   3 root root   4096 Sep 21 11:56 root

drwxr-xr-x  15 root root    620 Sep 24 13:03 run

drwxr-xr-x   2 root root   4096 Sep  7 07:29 sbin

drwxr-xr-x   2 root root   4096 Jun 20  2012 selinux

drwxr-xr-x   2 root root   4096 Mai  7 00:12 srv

dr-xr-xr-x  11 root root      0 Sep 27 17:25 sys

drwxrwxrwt   5 root root   4096 Sep 27 17:17 tmp

drwxr-xr-x  10 root root   4096 Mai  7 00:12 usr

drwxr-xr-x  11 root root   4096 Mai  7 01:29 var

````

-------

Alle Zeilen, die mit einem "d" beginnen sind Verzeichnisse (directory). Danach folgen die Rechte. Die folgende Zahl gibt die Anzahl der Verwendungen (Referenzen) im Dateisystem (zum Beispiel durch Links) an. Danach kommen der Eigentümer (Owner) und die Gruppe (Group). Anschließend die Grüße in Byte, das Datum der letzten Veränderung und dann der Dateiname.

------

    /etc: Dateien für die Systemsteuerung
    /root: Home-Verzeichnis des Super-User root
    /home: Verzeichnis in dem die Home-Verzeichnisse aller Benutzer (außer root) liegen
    /boot: Dateien die den Boot-Vorgang steuern
    /dev: Gerätedateien (devices) über die der Zugriff auf Geräte erfolgt
    /media: Verzeichnis in das die Gerätedatei von Wechselmedien (DVD, USB-Stick,...) gelegt wird.
    /mnt: Verzeichnis an das ein Gerät manuell temporär eingebunden wird.
    /opt: Verzeichnis in dem optionale Software abgelegt wird (sollte unter Ubuntu nicht verwendet werden).
    /bin und /sbin: Verzeichniss in denen wichtige Systemprogramme zu finden sind. Auf /bin haben alle lesenden Zugriff, auf sbin teilweise nur der Super-User root.
    /lib: Kernel-Module und dynamische Blibiotheken
    /tmp: Temporäres Verzeichnis
    /srv: Daten, die von Diensten angeboten werden (zum Beispiel Web-Server)
    /run: ersetzt das ursprüngliche /var/run. Hier werden Dateien die für laufende Prozesse wichtig sind abgelegt.
 
---------------------------

### Einhängen von Dateisystemen

--------------------------------------

**Der Befehl mount**

Der aktuelle „Mount“-Zustand lässt sich mit dem Kommando mount feststellen:

```
schueler@pcxx:~$ mount
...
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
/dev/sdb1 on /media/816E-DD42 type vfat (rw,nosuid,nodev,uid=1000,gid=1000, ...)
/dev/sdc1 on /media/6F112B4136D46EAE type fuseblk (rw,nosuid, ...)
````

**Der Befehl umount**

Ein eingehängtes Dateisystem kann mit dem Befehl umount entfernt werden.

Hinter dem Kommando umount muss dabei entweder der Device-Name oder das mit dem Device verbundene Verzeichnis angegeben werden.

Beispiel: schueler@pcxx:~$ **sudo umount /dev/sdb1**

Ein solches Aushängen ist allerdings nur dann möglich, wenn das Gerät (Verzeichnis) nicht mehr verwendet wird. Das Systemlaufwerk / kann daher nicht ausgehängt werden.


--------------------

## Benutzer erstellen

------------------------

Um einen neuen Benutzer zu erstellen muss man fogendes machen:

zuerst zum superuser modus wechseln 

```
sudo -i

nano /etc/passwd

nano /etc/group        

nano /etc /shadow

nano /etc/passwd

pw eingeben: 

pw widerholen:


```
----------------------

## Dll  

-----------------------------

Dynamic Link Library (DLL) bezeichnet allgemein eine dynamische Programmbibliothek; meist bezieht sich der Begriff jedoch auf die für die Betriebssysteme Microsoft Windows und OS/2 verwendete Variante.

DLL-Dateien verwenden das auch für ausführbare EXE-Dateien gebräuchliche Dateiformat, das in 16-Bit-Programmen das New-Executable-Format (NE)[1] und in 32- und 64-Bit-Programmen das Portable-Executable-Format (PE) ist. Diese Dateien können Programmcode (Maschinencode), Daten und Ressourcen in beliebiger Kombination enthalten.

Die Windows-Dateinamenserweiterung für solche Bibliotheken ist gewöhnlich DLL, es können auch andere Dateiendungen wie OCX (für Bibliotheken mit ActiveX-Steuerelementen), DRV oder CPL (für die Systemsteuerung) sein. 

Quelle: https://de.wikipedia.org/wiki/Dynamic_Link_Library

-------------------------------

## Rechte

--------------------------

### Dateirechte

---------------------

Dateirechte regeln, welcher Benutzer was mit einer Datei darf. Dabei ist zu beachten, dass echter Schutz nur mit Verschlüsselung oder durch Platzierung des Rechners in einem unzugänglichen Raum gegeben ist!

 Angezeigt werden Dateityp und Eigenschaften in der Shell mit Hilfe des Kommandos ls unter Verwendung der Option -l (Line). Es ergibt sich dann folgende Anzeige:

-rwxr-x--- 1 besitzer gruppe 12345 Oct 14 10:54 test.dat

Die nächsten 9 Zeichnen regeln die Zugriffsrechte. Danach folgt die Anzahl der Verwendung im Dateisystem, der Besitzer (user), die Gruppe (group), die Dateigröße in Bytes, das Datum der letzten Änderung und der Dateiname.

Die 9 Buchstaben für die Zugriffsrechte teilen sich auf in:

    3 Buchstaben für die Rechte des Besitzers (user)
    3 Buchstaben für die Rechte von Mitgliedern der Gruppe (group) zu der die Datei gehört
    3 Buchstaben für alle anderen Benutzer (others)

Jeder der drei Buchstaben kennzeichnet (von links nach rechts):

    r  ... read
    Darf die die Datei gelesen werden?
    w  ... write
    Darf die Datei geändert werden?
    x  ... execute
    Darf die Datei als Programm ausgeführt werden?


 Im oberen Beispiel bedeutet daher rwxr-x--- ( ⇒  rwx  r-x  --- ):

    Der Besitzer hat die Rechte rwx, er darf daher die Datei lesen, ändern und als Programm ausführen.
    Mitglieder der Gruppe haben die Rechte r-x, sie dürfen die Datei lesen, als Programm ausführen, aber nicht verändern.
    Alle anderen Benutzer haben die Rechte ---, sie dürfen die Datei daher weder lesen, noch ändern oder als Programm ausführen.
    
---------------------

### Verzeichnisrechte

---------------------------

Im wesentlichen gelten die gleichen Prinzipien wie bei den Dateirechten (Verzeichnisse sind ja auch nur Dateien). Allerdings werden die read, write und execute Rechte anders interpretiert.

Die drei Buchstaben kennzeichnen (von links nach rechts):

    r  ... read
    Der Verzeichnisinhalt darf gelesen werden
    w  ... write
    Im Verzeichnis dürfen neue Dateien angelegt oder bestehende Dateien gelöscht werden.
    x  ... execute
    Es darf in den Verzeichnisse auf die Dateieigenschaften und auf Unterverzeichnisse zugegriffen werden.
    
-----------------------

### Ändern von Besitzer und Gruppe

-------------------------

Der Besitzer einer Datei (dazu zählen auch Verzeichnisse) kann mit Hilfe des Kommandos chown geändert werden.

Soll auch die Gruppe gleich mit geändert werden, kann hinter dem Namen ein Doppelpunkt und die neue Gruppe angegeben werden.

```
user@ubuntu:~$ sudo chown user text.txt

user@ubuntu:~$ sudo chown user:schueler text.txt
```

Die Gruppe einer Datei kann mit dem Kommando chgrp geändert werden:

````
user@ubuntu:~$ sudo chgrp schueler text.txt
````

