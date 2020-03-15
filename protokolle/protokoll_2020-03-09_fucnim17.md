# Raspberry PI #3
         
**Name**: Fuchshofer Niklas  
**Datum**: 09.03.2020  
**Klasse**: 3AHME  
**Gruppe**: 1  
------
------

## Inhaltsverzeichniss
1) [rsync](#kopie-von-daten-auf-dem-raspberry-machen)
     * [Syntax](#syntax)
     * [Anwendung](#anwendung)
2) [Linux - Startup Systeme](#startup-systeme)
     * [systemd](#systemd)
          * [Status abfragen](#status-vom-computer-abfragen)
          * [Starten/Stoppen](#starten-und-stoppen-von-programmen)
3) [C-Programm auf Raspberry laufen lassen](#c-programm-auf-raspberry-laufen-lassen)
      * [Systemd Servicedatei erstellen](#systemd-servicedatei-für-c-programm-erstellen)
4) [C-Programm auf Raspberry im Hintergrund laufen lassen](#c-programm-auf-raspberry-im-hintergrund-laufen-lassen)
      * [Systemd Servicedatei aktualisieren](#systemd-servicedatei-aktualisieren)
5) [Java-Programm auf Raspberry im Hintergrund laufen lassen](#java-programm-auf-raspberry-im-hintergrund-laufen-lassen)
      * [Systemd Servicedatei erstellen](#systemd-servicedatei-für-java-programm-erstellen)
      * [Systemd Servicedatei aktualisieren](#systemd-servicedatei-für-java-programm-aktualisieren)
6) [Komprimieren von Verzeichnissen](#komprimieren)

## Kopie von Daten auf dem Raspberry machen
#### Syntax:
```
rsync [optionen] quelle ziel
```
#### Anwendung:
```
schueler@pcxx:~$ rsync -a pi22:/home/fucnim17 ./
```
> rsync gleicht Dateien und Ordner zwischen Lokalen oder Remote Systemen ab. die Synchronisation findet von der Quelle zum Ziel statt. Ist die Quelle oder das Ziel ein Remote System findet der Datenabgleich via SSH oder einen rsync-daemon statt. Rsync wird oft in Backupscripten verwendet oder zum kopieren (sichern) Großer Datenmengen. Es kann bei einem Abbruch jederzeit neu starten und macht an der „letzten stelle einfach weiter“. Rsync kopiert dabei auch nur neue oder geänderte Daten, was es wirklich gut für Backups macht. Wir behandeln hier nur die gängigsten Optionen!
         
--> [rsync](https://www.shellbefehle.de/befehle/rsync/)


## Startup Systeme 
* Sys-V-Init
* Upstart
* systemd

--> [Startup Systeme](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#155470713)

Heutzutage verwendet man nur mehr systemd!

### systemd
#### Status vom Computer abfragen
```
root@pcxx:~# systemctl status
```
##### Mehr details: 
```
root@pcxx:~# systemctl status [programmname]
```
#### Starten und Stoppen von Programmen
```
root@pcxx:~# systemctl start [programmname]

root@pcxx:~# systemctl stop [programmname]
```                
## C-Programm auf Raspberry laufen lassen
```c
int main ()
{
    int counter = 0;
    for (int i = 0; i < 10; i++)
    {
        counter += i;
        printf("%d\n", counter);
    }
    
    return 0;
}
```
### Systemd Servicedatei für C- Programm erstellen
```
root@pi22:~# nano /etc/systemd/system/fucnim17-programm.service
``` 
#### flogendes eingeben:
```
[Unit]
Description=C-Programm mit Ausgabe

[Service]
ExecStart=/home/fucnim17/programm/a.out
```
### überprüfen ob die Datei nun existiert
```
root@pi22:~# ls -la /home/fucnim17/programm/a.out
``` 
### starten
``` 
root@pi22:~# systemctl start fucnim17-programm
```
### Status abrufen
```
root@pi22:~# systemctl status fucnim17-programm
```
### Programm stoppen
```
root@pi22:~# systemctl stop fucnim17-programm
``` 
## C-Programm auf Raspberry im Hintergrunf laufen lassen

### Systemd Servicedatei aktualisieren
```
root@pi22:~# nano /etc/systemd/system/fucnim17-programm.service
```
#### folgendes eintragen:
``` 
[Unit]
Description=C-Programm mit Ausgabe

[Service]
ExecStart=/home/fucnim17/programm/a.out

[Install]
WantedBy=multi.user.target
```
Um das C-Progamm nun automatisch bei Computerstart zu starten folgendes in das Terminal eingeben: 
```
root@pi22:~# systemctl enable fucnim17-programm
```
## Java-Programm auf Raspberry im Hintergrunf laufen lassen
```java
public class Main {
    
    private static int counter; //Zählereigenschaft
    
    public static void main (String[] args) { //psvm \t
        for (int i = 0; i < 10; i++) {
            counter += i;
            System.out.println(counter); //sout \t
        }
    }
}
```
### Java programm zum raspberry senden
```
schueler@pcxx:~$ rsync -aP Schreibtisch/Java_fucnim17_3ahme.jar pi22:/tmp/
```
### Systemd Servicedatei für Java-Programm erstellen:
```
root@pi22:~# nano /etc/systemd/system/fucnim17-java-programm.service
```
#### folgendes eintragen:
```
[Unit]
Description=Java Programm mit Ausgabe

[Service]
ExecStart=java -jar /root/Java_fucnim17_3ahme.jar

[Install]
WantedBy=multi-user.target
``` 
### Starten/Stoppen
```
root@pi22:~# systemctl start [programmname]
root@pi22:~# systemctl stop [programmname]
```
Um das C-Progamm nun automatisch bei Computerstart zu starten folgendes in das Terminal eingeben: 
```
root@pi22:~# systemctl enable fucnim17-programm
```
### Systemd Servicedatei für Java-Programm aktualisieren:
Für jeden Service sollte man einen eigenen Benutzer erstellen!
```
root@pi22:~# nano /etc/systemd/system/fucnim17-java-programm.service
```
#### folgendes eintragen:
```
[Unit]
Description=Java Programm mit Ausgabe

[Service]
ExecStart=java -jar /root/Java_fucnim17_3ahme.jar
User=java

[Install]
WantedBy=multi-user.target
```

## Komprimieren:
* zip (Windows) 
* gnu-zip (Linux)

gnu-zip ist die bessere Variante, da man ganau das kriegt was man auch haben will und an den Dateiendung perfekt erkennt wie diese Datei/dieses Verzeichnis komprimiert wurde.









