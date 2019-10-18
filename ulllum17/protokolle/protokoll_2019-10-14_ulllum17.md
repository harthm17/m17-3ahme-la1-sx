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

Ein Datenträger ist unter Partitionen unterteilt und auf den Partitionen befindet sich das Dateisysteme(Linux ext4, Windows NTFS)

### Mount Gerät einhängen

Mit dem Kommando '''mount''' werden alle eingehängten Datenträger angezeigt

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
Um in den Superuser(Root) zuwechseln
```bash
sudo -i
```

Öffne die passwd Datei im nano um den Benutzer hinzuzufügen
```bash
nano /etc/passwd
```

```bash
benutzer:x:1000:1000:benutzer,,,:/home/benutzer:/bin/bash
```

Öffne die group Datei im nano um die Gruppe des Benutzer hinzuzufügen
```bash
nano /etc/group
```

```bash
benutzer:x:1000:
```

Öffne die shadow Datei im nano um das Passwort für den Benutzer hinzuzufügen
```bash
nano /etc/shadow
```

```bash
benutzer:$6$V3MJD/zs$OZ0kBdnquiE0olDFMldDA45Hh4XI.op.siyaQ7FNsU3bkGoBy3umBOPsC/Y$:::::
```

Das Passwort ändern vom Benutzer

```bash
nano passwd benutzer
```

