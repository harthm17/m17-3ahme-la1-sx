# Protokoll 5 Labor-SX (2019/20)

------------------------------------------------

* **Erstellt von:** Vanessa Plieschnegger
* **Datum:** 18.05.2020
* **Thema:** Ausarbeitung der Aufgabenstellung
* **Fehlend:** keiner

------------------------------------------------

## Inhaltsverzeichnis
1. [Datenbank PostgreSQL installieren](#datenbank-postgresql-installieren)
2. [Erstellung eines Dienstes (Dämon)](#erstellung-eines-dienstes-(dämon))
3. [C-Programm erstellen](#c-programm-erstellen)
4. [Programm übersetzen](#programm-übersetzen)
5. [Programm testen](#programm-testen)
6. [systemd Service erstellen](#systemd-service-erstellen)
7. [Service starten, stoppen und beobachten](#service-starten,-stoppen-und-beobachten)
8. [Autostart](#autostart)

------------------------------------------------

### Datenbank PostgreSQL installieren
Um die Dantenbank PostgreSQL installieren zu können muss man nur folgenden Befehl eingeben.
```
apt install postgresql htl-pgadmin4
```

## Erstellung eines Dienstes (Dämon)
### C-Programm erstellen
Zunerst muss man eine Datei namens mydaemon.c mit folgendem Inhalt (für unser Beispiel erstellen):
```
#include <stdio.h>
#include <stdlib.h>
#include <syslog.h>
#include <unistd.h>

int main () {
    openlog ("mydaemon", LOG_PID, LOG_DAEMON);

    syslog (LOG_NOTICE, "mydaemon started.");
    printf("Hello 1\n"); fflush(stdout);
    sleep (2);
    printf("Hello 2\n"); fflush(stdout);
    sleep (2);
    printf("Hello 3\n"); fflush(stdout);
    sleep (2);
    syslog(LOG_WARNING, "bin bei der letzten Ausgabe...");
    printf("Hello 4\n"); fflush(stdout);

    usleep(1000);
    syslog (LOG_NOTICE, "mydaemon terminated.");
    closelog();
    usleep(1000);

    return 0;
}
### Programm übersetzen
```
Um das Programm zu übersetzen, muss man folgende Befehle ausführen:
```
mkdir mydaemon
cd mydaemon
nano mydaemon.c
gcc -o mydaemon mydaemon.c
ls -l
```
### Programm testen
Jetzt kann man das Programm mit dem folgenden Befehl testen:
```
./mydaemon 
```
In weiteren Shells kann man nun die Ausgaeb dazu anzeigen:
```
journalctl -f
```
```
journalctl -f -p 4
```
```
journalctl -f -v verbose
```
```
tail -f /var/log/syslog
```
### systemd Service erstellen
Nun wir ein systempd Service erstellt, welcher mydaemon.service heißt und folgenden Inhalt hat:
```
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=/home/vani/mydaemon/mydaemon
IgnoreSIGPIPE=false
KillMode=process
```

Nun erstellen wir in /etc/systemd/system einen Link auf die Service-Datei mydaemon.service:
```
sudo -i
cd /etc/systemd/system
ln -s /home/vani/mydaemon/mydaemon
ls -l
exit
```
Jetzt kann man den Dienst starten:
```
sudo systemctl start mydaemon
```
Wenn man möchte kann man in einer anderen Shell den Dienst beobachten, mit folgendem Befel:
```
sudo journalctl -f -u mydaemon
```
### Service starten, stoppen und beobachten
Mit folgeden Befehelen kann man nun einen Service starten, stoppen und beobachten:
```
systemctl start mydaemon
systemctl restart mydaemon
systemctl stop mydaemon
systemctl status mydaemon
```
## Autostart
Um einen Dienst automatich starten zulassen, kann man dies mit folgenden Befehlen leicht realisieren:
```
sudo systemctl enable mydaemon
```
Nun erscheint eine Fehlermeldung, die wiefolgt aussieht:
```
The unit files have no installation config (WantedBy=, RequiredBy=, Also=,
Alias= settings in the [Install] section, and DefaultInstance= for template
units). ...
```
Man muss in der mydaemon.service Datei nun noch einen zusätzlichen Eintrag [install] hinzufügen:
```
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=/home/user/mydaemon/mydaemon
IgnoreSIGPIPE=false
KillMode=process

[Install]
WantedBy=multi-user.target
```

Als letztes muss man noch zwei Befehle ausfrühren und dann sollte alles funktionieren:
```
sudo systemctl enable mydaemon
sudo reboot
```
Nun startet das System neu und nun kann man noch mit folgendem Befehl überprüfen, ob alles funktioniert hat:
```
sudo journalctl -f -u mydaemon
```
