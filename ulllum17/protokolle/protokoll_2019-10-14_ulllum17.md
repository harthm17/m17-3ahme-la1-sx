# 2. Protokoll | AHME17 
# Uller Lucas
--------------------------------------------------------------------------
* **Thema:** Datenträger, Shell
* **Datum:** 14.10.2019
* **Gefehlt:** ---
* **Erstellt von:** ulllum17
* **Protokoll letzte Einheit:** [1.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ulllum17/ulllum17/protokolle/protokoll_2019-09-30_ulllum17.md) 
* **Protokoll nächste Einheit:** [2.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ulllum17/ulllum17/protokolle/protokoll_2020-01-20_ulllum17.md)
--------------------------------------------------------------------------
## Inhaltsverzeichnis
1. [Datenträger](#datenträger)
1. [Verzeichnisse unter Linux](#verzeichnisse-unter-linux)
1. [Dateisysteme einhängen](#dateisysteme-einhängen)
    1. [Manuell Gerät einhängen](#manuell-gerät-einhängen)
    1. [Manuell Gerät aushängen](#manuell-gerät-aushängen)
1. [Benutzer anlegen](#benutzer_anlegen)
1. [DLL](#dll)
    1. [DLL-Hölle](#dll-hölle)
1. [Rechte](#rechte)
    1. [Oktalverfahren](#oktaleverfahren)
    1. [symbolische Verfahren](#symbolische-verfahren)

--------------------------------------------------------------------------
## Datenträger

Ein Datenträger ist unter Partitionen unterteilt und auf den Partitionen befindet sich das Dateisystem(Linux ext4, Windows NTFS)
![Datenträger](https://user-images.githubusercontent.com/55395678/67149888-2d05d180-f2b1-11e9-9e4c-383a3caf429c.png)

## Verzeichnisse unter Linux
**/bin** Hier befinden sich wichtige Programme für den Benutzer z.B. Shell    
**/dev** Hier befinden sich die Gerätedatein    
**/etc** Hier befinde sich die Daten für die Systemsteuerung    
**/root** Dies ist das Heimatverzeichnis des Systemverwalters root    
**/lib** Hier sind wichtige Funktionsbibliotheken    
**/tmp** Hier werden Daten temporär gespeichtert. Bei einem neustart des Systems sind diese gelöscht    



## Dateisysteme einhängen
Mit dem Kommando ```mount``` werden alle eingehängten Datenträger angezeigt

```bash
ulllum17@ulllum17:~/Schreibtisch$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=2711196k,nr_inodes=677799,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=547016k,mode=755)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=25,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=12621)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
configfs on /sys/kernel/config type configfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
/var/lib/snapd/snaps/gnome-system-monitor_100.snap on /snap/gnome-system-monitor/100 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_81.snap on /snap/gnome-logs/81 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_67.snap on /snap/gnome-3-28-1804/67 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_406.snap on /snap/gnome-calculator/406 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_7270.snap on /snap/core/7270 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_317.snap on /snap/gnome-characters/317 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_1066.snap on /snap/core18/1066 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1353.snap on /snap/gtk-common-themes/1353 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-characters_296.snap on /snap/gnome-characters/296 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core18_1223.snap on /snap/core18/1223 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-3-28-1804_71.snap on /snap/gnome-3-28-1804/71 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gtk-common-themes_1313.snap on /snap/gtk-common-themes/1313 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/core_7917.snap on /snap/core/7917 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-logs_61.snap on /snap/gnome-logs/61 type squashfs (ro,nodev,relatime,x-gdu.hide)
/var/lib/snapd/snaps/gnome-calculator_501.snap on /snap/gnome-calculator/501 type squashfs (ro,nodev,relatime,x-gdu.hide)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=547012k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
/dev/sr0 on /media/mrrobot/VBox_GAs_5.2.26 type iso9660 (ro,nosuid,nodev,relatime,nojoliet,check=s,map=n,blocksize=2048,uid=1000,gid=1000,dmode=500,fmode=400,uhelper=udisks2)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)

```
*/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)* ist die **Hauptfestplatte**

### Manuell Gerät einhängen

**Hängt ein Gerät /dev/sdb1 ein und macht es unter /mnt/usbstick verfügrbar. Der Ordner /mnt/usbstick muss vorher erstellt werden**

```bash
mount /dev/sdb1 /mnt/usbstick
```

### Manuell Gerät aushängen
Mit dem Kommando ```umount``` wird das Gerät ausgehängt

```bash
umount /dev/sdb1
```

Früher mussten die USB-Stick manuell eingehängt bzw. ausgehängt werden.

----------


## Benutzer anlegen

Es gibt zwei möglichkeiten einen neuen Benutzer anzulegen:
* Mit dem Befehl ```adduser```
* Manuell

### Benutzer Manuell anlegen:

**Um in den Superuser(Root) zuwechseln**
```bash
sudo -i
```

**Öffne die passwd Datei im nano um den Benutzer hinzuzufügen**
```bash
nano /etc/passwd
```

```bash
benutzer:x:1000:1000:benutzer,,,:/home/benutzer:/bin/bash
```

**Öffne die group Datei im nano um die Gruppe des Benutzer hinzuzufügen**
```bash
nano /etc/group
```

```bash
benutzer:x:1000:
```

**Öffne die shadow Datei im nano um das Passwort für den Benutzer hinzuzufügen**
```bash
nano /etc/shadow
```

```bash
benutzer:$6$V3MJD/zs$OZ0kBdnquiE0olDFMldDA45Hh4XI.op.siyaQ7FNsU3bkGoBy3umBOPsC/Y$:::::
```
*Als passwort kann eine beliebige Passwortzeile kopiert werden.*

**Das Passwort ändern vom Benutzer**

```bash
sudo passwd benutzer
```
-----------------
### DLL
[Wikipedia](https://de.wikipedia.org/wiki/Dynamic_Link_Library)
> Dynamic Link Library (DLL) bezeichnet allgemein eine dynamische Programmbibliothek; meist bezieht sich der Begriff jedoch auf die für die Betriebssysteme Microsoft Windows und OS/2 verwendete Variante. 

#### DLL-Hölle
[Wikipedia](https://de.wikipedia.org/wiki/DLL-Konflikt)
> Der Ausdruck DLL-Konflikt (auch DLL Hell, deutsch: „DLL-Hölle“ genannt) bezeichnet ein Problem, das durch die Installation von Dynamic Link Library (DLLs) auf den Betriebssystemen der Windows-Reihe entstehen kann.

**Problem:**    
DLLs werden von verschiedenen Programmen in unterschiedlichen Versionen benötigt, welche in der Regel an einem zentralem Ort (im Windows- oder Systemverzeichnis) gespeichert. Das spart Speicherplatz und kann die Programmausführung deutlich beschleunigen, da das System weniger Zeit benötigt, um die für das Programm jeweils richtige DLL-Version zu finden. Andererseits kann die Installation eines neuen Programms dazu führen, dass eine neue DLL die alte Version überschreibt. Obwohl die noch von einem anderem Programm benötigt wird.

----------------------

### Rechte

Es wird unterschieden in Datei- und Verzeichnisrechte

**Datei:**    
* r...Inahlt lesen (read)    
* w...Inhalt modifizieren (write)
* x...Datei als Programm ausführen (execute)

**Verzeichnis:**    
* r...Inhalt des Verzeichnisses sehen (read)
* w...Inhalt des Verzeichnisses ändern (write)
* x...In das Verzeichniss wechseln (execute)


#### Rechte ändern
Es gibt drei Benutzerklassen, denen man unterschiedliche Rechte geben kann
* user (Eigentümer)
* group (Gruppe)
* others (alle anderen)

Es gibt zwei möglichkeiten Rechte zu ändern:
* Oktalverfahren
* Symbolischeverfahren
    
#### Oktaleverfahren    
Die Rechte werden in Form einer dreistelligen Oktal-Zahl angegeben, wobei jede Ziffer für die Rechte einer Gruppe steht.

rwxr-xr-x    
 7 - 5 - 3  (oktal)
  
 ```bash
ulllum17@MrRobotsPC:~/Schreibtisch$ ls -l
insgesamt 4
drwxr-xr-x 2 ulllum17 ulllum17 4096 Okt 19 19:32 Verzeichnis
ulllum17@ulllum17:~/Schreibtisch$ chmod 750 Verzeichnis/
ulllum17@ulllum17:~/Schreibtisch$ ls -l
insgesamt 4
drwxr-x--- 2 ulllum17 ulllum17 4096 Okt 19 19:32 Verzeichnis
 ```
#### symbolische Verfahren

u...user    
g...group    
o..others    

+...rechte geben    
-...rechte entziehen    

```bash
ulllum17@ulllum17:~/Schreibtisch$ ls -l
insgesamt 4
drwxr-xr-x 2 ulllum17 ulllum17 4096 Okt 19 20:00 Verzeichnis
ulllum17@ulllum17:~/Schreibtisch$ chmod o-rwx Verzeichnis/
ulllum17@ulllum17:~/Schreibtisch$ ls -l
insgesamt 4
drwxr-x--- 2 ulllum17 ulllum17 4096 Okt 19 20:00 Verzeichnis
```


