# Protokoll 5 La1/SX 3AHME (2019/20)

--------------

* **Thema:** Dienst bei Systemstart starten, Log-Dateien, Login mit Zertifikaten

  * **Datum:** 3.2.2020

  * **Gefehlt:** Niemand

  * **Erstellt von:** Michael Ully
  
  * **Letztes Protokoll:** [4. Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ullmim17/ullmim17/protokolle/protokoll-4_2020-01-27_ullmim17.md)
  
  * **Nächstes Protokoll:**

  --------------------------------------------------

  ## Inhaltsverzeichnis

  1.  [Dienst bei Systemstart automatisch starten lassen](#dienst-bei-systemstart-automatisch-starten-lassen)
      
  2. [Log-Dateien](#log-dateien)
     1. [Log-Rotate](#log-rotate)
  3. [Eigenen Benutzer für den Dienst anlegen](#eigenen-benutzer-für-den-dienst-anlegen)
  
  4. [Login mit Zertifikaten](#login-mit-zertifikaten)

  
 

  ---------------------------------------------------------------
  ## Dienst bei Systemstart automatisch starten lassen
  
  Mit dem Befehl systemctl und der Option enable können wir Dienste bei Systemstart automatisch starten lassen.
  Laut [Wikiubuntuusers](https://wiki.ubuntuusers.de/systemd/systemctl/)
  
  > enable UNITDATEI:	Aktiviert die Unit-Datei UNITDATEI. Danach kann die zugehörige Unit automatisch (z.B. beim Systemstart) gestartet werden.
  
 ``` bash
  michael@michael-GL752VW:/var/log$ systemctl enable programm
Created symlink /etc/systemd/system/multi-user.target.wants/programm.service → /etc/systemd/system/programm.service.
 ```
 ## Log-Dateien
 Laut [ip-insider](https://www.ip-insider.de/was-ist-eine-log-datei-a-794350/)
 
 > Eine Log-Datei ist eine Datei, in der IT-Systeme Ereignisse eintragen und protokollieren. Die Datei soll helfen, bestimmte Vorgänge nachzuvollziehen und kann beispielsweise für die Problemanalyse oder die Rekonstruktion von Transaktionen zum Einsatz kommen. Die Log-Datei ist in der Regel textbasiert.

Weil wir die count-Ausgabe im [journal](https://wiki.ubuntuusers.de/systemd/journald/) nicht gefunden haben, wollten wir die Ausgabe des Dienstes in eine Log-Datei schreiben.

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

```bash
michael@michael-GL752VW:~/programm$ tail -f /var/log/programm.log
cnt: 1
cnt: 2
cnt: 3
```
### Log-Rotate

logrotate ist dazu entworfen, die Verwaltung von Systemen zu vereinfachen, die eine große Anzahl von Log-Dateien generieren. Es erlaubt eine automatische Rotation, Kompression, Entfernung und Verschickung der Logdateien. Jede Logdatei kann täglich, wöchentlich, monatlich oder dann erfolgen, wenn sie zu groß geworden ist.

Log-Rotate-Datei erstellen: 

```bash
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
```bash
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

## Login mit Zertifikaten
Laut [Wikipedia](https://de.wikipedia.org/wiki/Public-Key-Authentifizierung)
> Die Public-Key-Authentifizierung ist eine Authentifizierungsmethode, die unter anderem von SSH und OpenSSH verwendet wird, um Benutzer mit Hilfe eines Schlüsselpaars, bestehend aus privatem und öffentlichem Schlüssel, an einem Server anzumelden. Ein solches Schlüsselpaar ist wesentlich schwerer zu kompromittieren als ein Kennwort.

>Bei einer Authentisierung mittels eines Kennworts wird dieses Kennwort, oder dessen Hash-Wert, auf einem Server gespeichert. Hat jemand Zugang zur Kennwortdatei auf diesem Server, gelangt er damit im ersten Fall auch in den Besitz des Kennworts. Im zweiten Fall kann er, mit Hilfe entsprechender Software, eine Zeichenkombination finden, die den gleichen Hash-Wert wie das Kennwort ergibt. Wird das gleiche Kennwort zur Anmeldung auf mehreren Systemen benutzt, so sind damit alle diese Systeme kompromittiert.

>Im Gegensatz dazu wird bei der Public-Key-Authentifizierung nur der öffentliche Schlüssel auf einem Server gespeichert. Der private Schlüssel wird auf dem eigenen Rechner gespeichert, kann damit geheim gehalten und zusätzlich mit einer Kennung verschlüsselt werden. Die Kennung kann aus mehreren Wörtern bestehen (im Englischen passphrase).

>Die Berechnung des privaten Schlüssels aus dem öffentlichen ist je nach Wahl der Länge des Schlüssels sehr aufwändig bis praktisch unmöglich.

1) Schlüssel erstellen
````bash
ssh-keygen
````
2) Öffentlicher Schlüssel
````bash
 cat .ssh/id-rsa.pub
````
3) Privater Schlüssel
````bash
 cat .ssh/id-rsa
````
4) Schlüssel auf den Raspberry kopieren
 ````
 ssh-copy-id ullmim1717@10.200.114.222
    
    root@pi22:~# mkdir.ssh
                 chmod 700.ssh
                 cp /home/ullmim17/.ssh/authrized_keys.ssh/
    rsync root@10.200.114.217 /home/tmp
 
 ````
