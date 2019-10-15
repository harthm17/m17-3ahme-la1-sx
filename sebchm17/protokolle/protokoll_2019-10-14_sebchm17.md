# Protokoll Labor/SX 3AHME (2019/20)

* **Thema** Shell
* **Datum** 14.10.2019
* **Gruppe** 4
* **Protokoll letzte Einheit** : [Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/sebchm17/sebchm17/protokolle/protokolle_2019-09-30sebchm17.md)

--------------------------------------------------------------------------------------------------------------------------------------

## Inhaltsverzeichnis
1. [Datenträger und Partitionen] (#datenträger-und-partitionen)
2. [Verzeichnisse] (#verzeichnisse)
3. [Mount] (#mount)
    * [Gerät einloggen/ausloggen] (#gerät einloggen/ausloggen)
4. [Neuen Benutzer anlegen] (#neuen benutzer anlegen)
5. [Rechte vergeben und ändern in der Shell] (#rechte vergeben und ändern in der shell)







--------------------------------------------------------------------------------------------------------------------------------------

## Datenträger und Partitionen
! [Datenträger] [Datenträger]
Quelle: https://www.google.com/url?sa=i&rct=j&q=&esrc=s&source=images&cd=&cad=rja&uact=8&ved=2ahUKEwjmv8a5q5zlAhUQsKQKHWowAnQQjB16BAgBEAM&url=https%3A%2F%2Fwww.chip.de%2Fdownloads%2FGParted-Live-64-Bit-ZIP-Version_66494949.html&psig=AOvVaw2abJxzhW5nvtWy66sY54JW&ust=1571160995931674

Ein Datenträger muss mit einem Dateisystem(ext4) formatiert sein damit darauf Dateien und Verzeichnisse gespeichert werden können.
Eine Partition ist ein Teil auf dem Datenträger, die von anderen Partitionen getrennt ist.
In Linux werden Partitionen als Block Device im verzeichniss /dev bereitgestellt. In Ubuntu können die Partitionstabellen mit dem Programm Gparted angezeigt werden.

--------------------------------------------------------------------------------------------------------------------------------------

## Verzeichnisse

--------------------------------------------------------------------------------------------------------------------------------------

## Mount 

Der Befehl ``mount`` zeigt an was alles im System eingehängt ist.

      ``bash
      chris@chris:~$ mount
      sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
      proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
      udev on /dev type devtmpfs (rw,nosuid,relatime,size=2550532k,nr_inodes=637633,mode=755)
      devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
      tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=514880k,mode=755)
      /dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
      ``

In der letzten Zeile wird angezeigt, dass es sich um die Hauptfestplatte handelt und sie in ext4 formatiert ist.




--------------------------------------------------------------------------------------------------------------------------------------
## Neuen Benutzer anlegen

Einen neuen Benutzer in der Shell anzulegen funktioniert mit dem Befehl ``adduser``  aber es funktioniert auch über eine etwas altmodischere Art quasi den Benutzer mit der Hand anzulegen. Dafür muss zuerst in den superuser mode (root) gewechselt werden.

```bash

chris@chris:~# sudo-i

root@chris:~# nano /etc/passwd
chris:x:1000:1000:chris,,,:/home/chris:/bin/bash#

root@chris:~# nano /etc/group
chris:x:1000:

root@chris:~# nano /etc/shadow

```
--------------------------------------------------------------------------------------------------------------------------------------

























--------------------------------------------------------------------------------------------------------------------------------------
[Protokoll]:https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/sebchm17/sebchm17/protokolle/protokolle_2019-09-30sebchm17.md

[Datenträger]:https://www.google.com/url?sa=i&rct=j&q=&esrc=s&source=images&cd=&cad=rja&uact=8&ved=2ahUKEwjmv8a5q5zlAhUQsKQKHWowAnQQjB16BAgBEAM&url=https%3A%2F%2Fwww.chip.de%2Fdownloads%2FGParted-Live-64-Bit-ZIP-Version_66494949.html&psig=AOvVaw2abJxzhW5nvtWy66sY54JW&ust=1571160995931674
