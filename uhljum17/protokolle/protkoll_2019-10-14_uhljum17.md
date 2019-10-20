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

-------------------------------

## Datenträger

---------------------

Ein Datenträger ist ein Speichermedium. Dieses Speichermedium kann entweder beschrieben oder ausgelesen werden. Ein Datenträger ist z.B. eine Festplatte oder Diskette. Es gibt tragbare oder fest eingebaute Datenträger. Ohne die Datenträger könnten keine Dokumente und Daten gespeichert werden. Die Datenträger sind ein sehr wichtiger Teil von einem Computersystem.

---------------------

### Patrtitionen

---------------------

Patitionen sind aufteilungen eines Datenträgers in unterschliedlich vielen und unterschiedlich großen Teilen. In diesen Teilen befindet sich jeweils ein Dateisystem. Bei Linux ist es ext4.

---------------------

### Verzeichnisse

---------------------

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

Alle Zeilen, die mit einem "d" beginnen sind Verzeichnisse (directory). Danach folgen die Rechte. Die folgende Zahl gibt die Anzahl der Verwendungen (Referenzen) im Dateisystem (zum Beispiel durch Links) an. Danach kommen der Eigentümer (Owner) und die Gruppe (Group). Anschließend die Grüße in Byte, das Datum der letzten Veränderung und dann der Dateiname.

Welche Aufgabe haben die einzelnen Verzeichnisse:
(siehe auch https://de.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

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
-----------------------------

