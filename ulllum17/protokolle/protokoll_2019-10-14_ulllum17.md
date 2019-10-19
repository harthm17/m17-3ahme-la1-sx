# 2. Protokoll | AHME17 
# Uller Lucas
--------------------------------------------------------------------------
* **Thema:** Datenträger, Shell
* **Datum:** 14.10.2019
* **Gefehlt:** ---
* **Erstellt von:** ulllum17
* **Protokoll letzte Einheit:** [1.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ulllum17/ulllum17/protokolle/protokoll_2019-09-30_ulllum17.md) 
* **Protokoll nächste Einheit:**
--------------------------------------------------------------------------
## Inhaltsverzeichnis

--------------------------------------------------------------------------
## Datenträger

Ein Datenträger ist unter Partitionen unterteilt und auf den Partitionen befindet sich das Dateisystem(Linux ext4, Windows NTFS)
![Datenträger](https://user-images.githubusercontent.com/55395678/67149888-2d05d180-f2b1-11e9-9e4c-383a3caf429c.png)


### Mount Gerät einhängen

Mit dem Kommando ```mount``` werden alle eingehängten Datenträger angezeigt

```bash
mount
```

```bash
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=2099000k,nr_inodes=524750,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=425096k,mode=755)
/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=12345)
mqueue on /dev/mqueue type mqueue (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=425092k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
```

#### Mount Gerät aushängen
Mit dem Kommando ```umount``` wird der Datenträger ausgehängt

```bash
umount /mnt
```

Früher musste jeder USB-Stick manuell eingehängt bzw. ausgehängt werden.

----------

Dateien für Systemsteuerung werden in ```etc``` gespeichert

### Benutzer anlegen

Es gibt zwei möglichkeiten einen neuen Benutzer anzulegen:
* Mit dem Befehl *adduser*
* Manuell

Benutzer Manuell anlegen:

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
* r...Inhalt des Verzeichnises sehen (read)
* w...Inhalt des Verzeicnises ändern (write)
* x...In das Verzeichnis wechseln (execute)


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
 
 **Verzeichnis hat die Rechte *rwxr-xr-x*, wir möchten sie ändern auf *drwxr-x-wx***
 
 ```bash
ulllum17@MrRobotsPC:~/Schreibtisch$ ls -l
insgesamt 4
drwxr-x--- 2 ulllum17 ulllum17 4096 Okt 19 19:32 Verzeichnis
ulllum17@ulllum17:~/Schreibtisch$ chmod 753 Verzeichnis/
ulllum17@ulllum17:~/Schreibtisch$ ls -l
insgesamt 4
drwxr-x-wx 2 ulllum17 ulllum17 4096 Okt 19 19:32 Verzeichnis
 ```
#### Simbolischeverfahren

u...user    
g...group    
o..others    

+...rechte geben    
-...rechte entziehen    


**Wir möchten der group, write und execute rechte geben**
```bash
ulllum17@ulllum17:~/Schreibtisch$ ls -l
insgesamt 4
drwx---r-x 2 ulllum17 ulllum17 4096 Okt 19 20:00 Verzeichnis
ulllum17@ulllum17:~/Schreibtisch$ chmod g+wx Verzeichnis/
ulllum17@ulllum17:~/Schreibtisch$ ls -l
insgesamt 4
drwx-wxr-x 2 ulllum17 ulllum17 4096 Okt 19 20:00 Verzeichnis
```


