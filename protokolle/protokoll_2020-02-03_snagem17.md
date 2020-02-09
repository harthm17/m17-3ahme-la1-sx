# Protokoll Labor/SX 3AHME (2019/20)

* **Thema:** Raspberry Pi Programmieren
* **Datum:** 27.01.2020
* **Gefehlt:** keiner
* **Erstellt von:** Georg Schnabel
* **Protokoll letzte Einheit:** [Protokoll](protokoll_2020-01-27_snagem17.md)


## Inhaltsverzeichnis


  ## Dienst bei Systemstart automatisch starten lassen
  
Mit dem Befehl **systemctl** und der Option **enable** können wir das System automatisch starten lassen. Das macht man wenn man das System nicht immer selbst starten will.
  Quelle: [Wikiubuntuusers](https://wiki.ubuntuusers.de/systemd/systemctl/)
  
  > enable UNITDATEI:	Aktiviert die Unit-Datei UNITDATEI. Danach kann die zugehörige Unit automatisch (z.B. beim Systemstart) gestartet werden.
  
 ```
 systemctl enable programm
 ```
 ## Log-Dateien
 Laut [ip-insider](https://www.ip-insider.de/was-ist-eine-log-datei-a-794350/)
 
 > Eine Log-Datei ist eine Datei, in der IT-Systeme Ereignisse eintragen und protokollieren. Die Datei soll helfen, bestimmte Vorgänge nachzuvollziehen und kann beispielsweise für die Problemanalyse oder die Rekonstruktion von Transaktionen zum Einsatz kommen. Die Log-Datei ist in der Regel textbasiert.

Weil wir die count-Ausgabe im [journal](https://wiki.ubuntuusers.de/systemd/journald/) nicht gefunden haben, wollten wir die Ausgabe des Dienstes in eine Lod-Datei schreiben.

1) Zuerst haben wir unser Programm so verändert, dass es die Ausgabe in unsere Log-Datei speichert.
```C
#include <stdio.h>
#include <unistd.h>
int main()   

  { 

        int cnt = 0; 

//      for(int i = 0;i<10;i++) 

        while(1) 

        { 

                cnt++; 

                printf("cnt=%d\n",cnt); 

                FILE *f; 

                f = fopen("/var/log/programm.log","a"); 

                if(f!=NULL) 

                { 

                        fprintf(f, "cnt=%d\n",cnt); 

                        fclose(f); 

                        sleep(1); 

        //              delay(1); 

        } 

                } 
}





```
2) Mit dem Befehl [tail](https://wiki.ubuntuusers.de/tail/) können wir nun die letzten Zeilen der Datei ausgeben. Die Option -f folgt dem Ende der Datei, wenn sie wächst.

```
bash
michael@michael-GL752VW:~/programm$ tail -f /var/log/programm.log
cnt: 1
cnt: 2
cnt: 3
```
### Log-Rotate

logrotate ist dazu entworfen, die Verwaltung von Systemen zu vereinfachen, die eine große Anzahl von Log-Dateien generieren. Es erlaubt eine automatische Rotation, Kompression, Entfernung und Verschickung der Logdateien. Jede Logdatei kann täglich, wöchentlich, monatlich oder dann erfolgen, wenn sie zu groß geworden ist.

Log-Rotate-Datei erstellen: 

```
bash
sudo nano /etc/logrotate.d/programm

------------------------


/var/log/programm.log
{
        weekly
        rotate 4
        missingok
        notifempty
}

```
## Eigenen Benutzer für den Dienst anlegen

Wir wollten unserem Dienst auch einen eigenen Benutzer erstellen.

1) Benutzer erstellen:
```
bash
michael@michael-GL752VW:~/programm$ sudo adduser --disabled-password –system –no-create-home programm

```
2) Service-Datei ändern:
```
[Unit]
Description=Labor Programm

[Service]
Type=simple
ExecStart=/home/ullmim17/programm/a.out
User=programm

[Install]
WantedBy=multi-user.target
```
