 # Protokoll Labor 3AHME (2019-10-14)

* Thema: Datenträger, Benutzer, Rechte
* Datum: 14.10.2019
* Gefehlt: -
* Erstellt von: strmam17
* Protokoll letzte Einheit: [1.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/strmam17/strmam17/protokolle/protokoll-1_strmam17_2019-09-30.md)
* Protokoll nächste Einheit: [3.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/strmam17/strmam17/protokolle/protokoll-3_strmam17_2020-01-20.md)
--------------------------------------------------------------------------------------------------------------------------------------
## Inhaltsverzeichnis
1. [Datenträger](#datenträger)
    * [Partitionstabellen](#partitionstabellen)
    * [Gerät einhängen](#gerät-einhängen)
    * [Gerät aushängen](#gerät-aushängen)
    * [Dateien für Systemsteuerung](#dateien-für-systemsteuerung)
2. [Benutzer erstellen](#benutzer-erstellen)
3. [Benutzer zu einer Gruppe hinzufügen](#benutzer-zu-einer-gruppe-hinzufügen)
4. [DLL](#dll)
5. [Rechte](#rechte) 
    * [Rechte ändern](#rechte-ändern)
6. [Eigentümerschaft verändern](#eigentümerschaft-verändern)
7. [Befehle](befehle)
-------------------------------------------------------------------------------------------------------------------------------------
## Datenträger
Ein Datenträger besteht aus Partitionen, Kleinere und Größere, in diesen Partitionen befindet sich das Dateisystem (bei Linux: ext4,
bei Microsoft: NTFS).
![Datenträger](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/strmam17/template/Datentr%C3%A4ger.png)
### Partitionstabellen
```
sudo -i                   // Man muss zuerst in den Superuser sonst hat man keinen Zugriff
fdisk /dev/sda            // Auflistung der Partitionstabellen
```
### Gerät einhängen
Früher musste man den USB-Stick immer ein- und aushängen.
```
mount                     // Zeigt an was alles im System eingehenkt ist (Hauptfestplatte: /dev/sda1 on
ll /mnt 
mount /dev/sda1/mnt
ls /mnt
```
### Gerät aushängen
```
umount /mnt
```
### Dateien für Systemsteuerung
```
/etc                      // steht für et cetera

less /etc/passwd
man passwd
nano /etc/group
id
who
```
--------------------------------------------------------------------------------------------------------------------------------
## Benutzer erstellen
```
nano /etc/passwd                                     // Seine eigenen Daten dazu schreiben
nano /etc/group                                      // Seine eigenen Daten dazu schreiben
nano /etc /shadow                                    // Seine eigenen Daten dazu schreiben
passwd <eigner Benutzer>                             // Sein Passwort ändern
nano /etc/shadow
chown <eigener Benutzer>: <eigener Benutzer> /home/<eigener Benutzer> 
```
------------------------------------------------------------------------------------------------------------------------------
## Benutzer zu einer Gruppe hinzufügen
Wenn man einen anderen Benutzer zu deiner Gruppe hinzufügen will, dann muss man in seinen eigenen Verzeichnis sein.
```
ll /etc/group 
```
Dann ganz unten muss man seinen Namen hinschreiben.

-----------------------------------------------------------------------------------------------------------------------------
## DLL
  Dynamic link libories <-> so-Datei(static object file)
  DLL Hölle:
  
  Es bezeichnet ein Problem, das durch die Installation von Dynamic Link Library auf 
  den Betriebssystemen der Windows-Reihe entstehen kann.
  
  Windows braucht 8-10 mal mehr Platz als Linux
  
-------------------------------------------------------------------------------------------------------------------------------
## Rechte
Rechte sind dafür da, damit nicht ein jeder auf alle Dateien und Verzeichnisse zugriff hat.

Es gibt: 
  * Eigentümer(user)                      
  * Gruppe(groupe)                       
  * Alle Anderen(other)
 
Diese bekommen rechte:
  * r(read
  * w(write)
  * x(ausführbar)
     
   1. Rechte bei Dateien: 
      * r...Inhalt zu lesen
      * w...Inhalt modifizierend
      * x...Datei als Programm ausführbar
      
   2. Rechte bei Verzeichnisse: 
       * r...Inhalt zu sehen
       * w...Inhalt veränderbar
       * x...In das Verzeichnis wechseln
       
 ### Rechte ändern
 Bsp.: rwxr-xr-x
 * Der Eigentümer kann lesen, schreiben und ausführen.
 * Die Gruppe kann lesen und ausführen.
 * Alle anderen können lesen und ausführen.

Es wird immer in oktal angegeben das heißt bei diesem Beispiel 755. Würde man es auf 750 umändern dann würde man alle Anderen 
alle Rechte entnehmen. Es gibt zwei arten die Rechte zu ändern.
1. Oktal
```
chmod 750 /home/schueler
```
2. Variable
```
chmod o-rwx                     // o steht für others (alle Anderen)
```
------------------------------------------------------------------------------------------------------------------------------
## Eigentümerschaft verändern
```
sudo chown schueler Datei1                  // Die Eigentümerschaft von Datei1 würde verändert
```
------------------------------------------------------------------------------------------------------------------------------
## Befehle
```
sudo -i                         // Superuser damit hat man alle Rechte
date                            // aktuelle Zeitausgabe
/lib                            // Bibliotheksdateien
/temp                           // Verzeichnisse die beim nächsten Mal gelöscht sind
find                            // zum finden von Dateien oder Verzeichnissen 
```
