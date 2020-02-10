# Protokoll Labor/SX 3AHME (2019/20)

* **Thema:** Autostart, Log-Dateien, SSH-Schlüssel
* **Datum:** 27.01.2020
* **Gefehlt:** keiner
* **Erstellt von:** Georg Schnabel
* **Protokoll letzte Einheit:** [Protokoll](protokoll_2020-01-27_snagem17.md)


## Inhaltsverzeichnis
1. System automatisch starten lassen
2. [Log-Dateien](https://de.wikipedia.org/wiki/Logdatei)
3. Programm als System-Account laufen lassen
4. [SSH-Schlüssel](https://www.zdv.uni-mainz.de/ssh-schluessel/)
* Schlüssel erzeugen
* Schlüssel kopieren
5. Ein Programm installieren

  ## System automatisch starten lassen
  
Mit dem Befehl **systemctl** und der Option **enable** können wir das System automatisch starten lassen. Das macht man wenn man das System nicht immer selbst starten will.
  
 ```
 systemctl enable programm
 ```
## Log-Dateien

Quelle: [Wikipedia](https://de.wikipedia.org/wiki/Logdatei)
>Eine Logdatei (auch Protokolldatei, Ereignisprotokolldatei) enthält das automatisch geführte Protokoll aller oder bestimmter Aktionen von Prozessen auf einem Computersystem.<

**In das Verzeichnis wechseln um ein Logrotate festzulegen**
```
cd /etc/logrotate.d
```
**Programm erstellen:**
```
nano programm
```
**Unser Programm sah folgendermaßen aus:**
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
## Programm als System Account laufen lassen

1. Account anlegen 
```
adduser --disabled-password --no-create-home --system programm
```
2. In der Service Datei den **System Account** hinzufügen.

```
nano /etc/systemd/system/programm.service
```

**Unsere Service-Datei sah so aus:**
```
[Unit]
Description=Labor Programm

[Service]
Type=simple
ExecStart=/home/pi/programm/a.out
User=programm

[Install]
WantedBy=multi-user.target
```

## Kontrollieren ob der System-Account läuft
Das funktioniert mit dem Befehl **top**. Mit der PID kann man im Tool **top** checken ob der System-Account läuft.
```
top
```


## SSH Schlüssel

Es gibt einen **öffentlichen Schlüssel**und einen **privaten Schlüssel**.

### Schlüssel erzeugen
Der Schlüssel kann mit dem Befehl **keygen** erzeugt werden.
```
ssh-keygen
```
Unter Windows werden Zusatzprogramme benötigt um einen Schlüssel zu erzeugen.


### Schlüssel kopieren

Mit **copy** kann der Schlüssel kopiert werden.

```
ssh-copy-id snagem17@10.200.114.226
```

Man kann den Schlüssel aber auch manuell hinzufügen.

```
sudo nano .ssh/authorized_keys
```
## Ein Programm installieren
Mit dem System APT(Advanced Packaging Tool) kann man sehr leicht Programmpakete suchen, instellieren und noch dazu das ganze System auf den neuesten Stand bringen,

```
apt update
apt install <Programm_name>
```
