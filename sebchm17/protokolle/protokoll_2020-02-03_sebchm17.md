 # Protokoll Labor/SX 3AHME (2019/20) 


* **Thema** : Raspberry PI 
* **Datum** : 03.02.2020 
* **Gruppe** : 4 
* **Protokollverfasser** : Christoph Sebernegg 
* **Protokoll letzte Einheit** : [4.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/sebchm17/sebchm17/protokolle/protokoll_2020-01-27_sebchm17.md) 

-------------------------------------------------------------------------------------------------------------------------------- 

## Inhaltsverzeichnis 
1.  [Programmeigenschaften](#programmeigenschaften)
1.  [Standardinput,Standardoutput,Standarderror](#standardinput-standardoutput-standarderror)
1.  [Autostart](#autostart)
1.  [LOG-Datei](#log-datei) 

---------------------------------------------------------------------------------------------------------------------------------
## Programmeigenschaften


    systemctl status programm

abfragen ob das Programm läuft

    systemctl start programm
    
startet das Programm

    systemctl stop programm
    
stopt das Programm

    journalctl -f -u programm

zeigt laufend an was das Programm macht

    root@pi16 tail -f /var/log/programm.log

--------------------------------------------------------------------------------------------------------------------------------------------

## Standardinput,Standardoutput,Standarderror

 ![Bild](https://www.linuxunit.com/io-redirection-stdin-stdout-stderr-streams/)

--------------------------------------------------------------------------------------------------------------------------------------------

## Autostart

Wir haben das Programm als Dienst verfügbar gemacht. Den Dienst können wir mit folgendem Befehl automatisch starten.

    systemctl enable programm
    
--------------------------------------------------------------------------------------------------------------------------------------------

## LOG-Datei

>Eine Logdatei (auch Protokolldatei, Ereignisprotokolldatei; englisch log file) enthält das automatisch geführte Protokoll aller oder bestimmter Aktionen von Prozessen auf einem Computersystem. Wichtige Anwendungen finden sich vor allem bei der Prozesskontrolle und Automatisierung.

[Wikipedia](https://de.wikipedia.org/wiki/Logdatei)
   
    logrotate


eigentliche LOG-Datei kern.log

Nach einer Woche wird die kern.log kommpremiert und zur kern.log.1 überschrieben

Nach zwei Wochen wird die kern.log.1 kommpremiert und zur kern.log.2 überschrieben

Das wiederholt sich bis zur 4.ten kompremierten Version, weil ab dann löscht er die Log-Datein


Eigene LOG-Datei erstellen

``` bash
     /var/log/programm.log
     {
       rotate 4
       weekly
       missingok
       notifempty
     }
```

--------------------------------------------------------------------------------------------------------------------------------------------

    sebchm@pi16:~/programm $ nano main.c 

```C  
      #include  <stdio.h>
      #include  <unistd.h>
      
      int main()
      {
        int cnt=0;
        
        for(int i=0; i<10; i++)
        {
          cnt++;
          printf("cnt=%d\n", cnt);
          FILE *f;
          f=fopen("/var/log/programm.log","a");
          if(f!= NULL){
          fprintf(f, "cnt=%d\n",cnt);
          fclose(f);
          }
          sleep(1); 
         
         }
         return 0;
```
