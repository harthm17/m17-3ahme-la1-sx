# Protokoll Labor/SX 3AHME (2019/20)

* **Thema:** Raspberry Pi Programmieren
* **Datum:** 27.01.2020
* **Gefehlt:** keiner
* **Erstellt von:** Georg Schnabel
* **Protokoll letzte Einheit:** [Protokoll](protokoll_2020-01-27_snagem17.md)


## Inhaltsverzeichnis
1. System automatisch starten lassen
2. [Log-Dateien](https://de.wikipedia.org/wiki/Logdatei)

  ## System automatisch starten lassen
  
Mit dem Befehl **systemctl** und der Option **enable** können wir das System automatisch starten lassen. Das macht man wenn man das System nicht immer selbst starten will.
  
 ```
 systemctl enable programm
 ```
## Log-Dateien

**In das Verzeichnis wechseln:**
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
