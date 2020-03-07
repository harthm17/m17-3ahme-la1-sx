# Labor Protokoll 2020-03-03
         
**Lukas Fleischhacker**       
**3AHME**   

----------------------------
## Inhaltsverzeichnis    
1) [Nickname](#nickname)  
   * [Wofür](#wofür)  
   * [Erstellen](#erstellen)   
2) [C-Programm](#c-programm)
   * [Verzeichnis erstellen](#verzeichnis-erstellen)
   * [Quelltext schreiben](#quelltext-schreiben)
   * [Compilieren](#compilieren)             
         * [GNU Project](#gnu-project)
   * [Programm ausführen](#programm-ausführen)
   * [In Datei ausgeben](#in-datei-ausgeben)
   * [Datei beobachten](#datei-beobachten)
   * [Logrotate](#logrotate)                 
         * [Log-Datei erstellen](#log-datei-erstellen)
----------------------------
## Nickname
### Wofür
Mithilfe eines Nicknames kann man sich schneller und einfacher bei einem Raspberry einloggen.               
Ähnlich wie bei einem Alias verkürtzt man die Eingabe.                  
                  
Früher musste man **ssh flelum17@10.200.114.226** und das Passwort eingeben                                         
Jetzt geht es auch nur mit **ssh pi26**                    

### Erstellen

        nano /ssh/config (die Datei öffnen)
        
        (in die Datei schreiben:)
        
        Host pi26-root
        Hostname 10.200.114.226
        User root
        
        Host pi26-flelum17
        Hostname 10.200.114.226
        User flelum17

## C-Programm
### Verzeichnis erstellen

         flelum17@pi26:~ $ mkdir programm              

### Quelltext schreiben

         flelum17@pi26:~ $ /programm nano main.c
         
### Compilieren
Mithilfe des *GNU-Compilers*

         flelum17@pi26:~/programm $ gcc main.c

#### GNU Project
         
   >Das GNU-Projekt entwickelt das Betriebssystem GNU (Aussprache: [ɡnuː][1]),                
   das von Richard Stallman mit dem Ziel gegründet wurde, ein freies,               
   unixähnliches Betriebssystem zu schaffen, das sicherstellt,dass die              
   Endbenutzer die Freiheiten haben, es verwenden, untersuchen, verbreiten (kopieren)                 
   und verändern zu dürfen. Software, deren Lizenz diese Freiheiten garantiert, wird                  
   Freie Software (engl. Free Software) genannt, GNU ist in diesem Sinne frei.
 
laut [Wikipedia](https://de.wikipedia.org/wiki/GNU-Projekt)

![Richard Stallman](https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/Richard_Stallman_2005_%28chrys%29.jpg/220px-Richard_Stallman_2005_%28chrys%29.jpg)

Richard Stallman

### Programm ausführen

      flelum17@pi26:~/programm $ ./a.out
      
### In Datei ausgeben
Die Ausgabe des Programmes wird nicht in der Konsole angezeigt, sondern in einer Datei.
Dies geschied aber nur wenn auch der Quelltext des Programmes umgeändert wird.

         flelum17@pi26:~ $ ll /var/log
         flelum17@pi26:~ $ sudo touch /var/log/programm.log
         flelum17@pi26:~ $ sudo chmod 666/var/log/programm.log
         flelum17@pi26:~ $ ll /var/log/programm.log
         flelum17@pi26:~ $ gcc main.c
         flelum17@pi26:~ $ ./a.out
         
### Datei beobachten

         flelum17@pi26:~ $ watch ll /var/log/programm.log
         
### Logrotate 
>Logrotate wurde entwickelt, um die Verwaltung von Logdateien zu vereinfachen.            
Die Dateien können automatisch komprimiert, gelöscht oder per Mail verschickt             
werden. Logrotate kann dies täglich, wöchentlich, monatlich durchführen oder              
wenn eine Logdatei eine vorgegebene Größe überschreitet. Üblicherweise wird               
Logrotate einmal am Tag aktiv.
                  
Am Beispiel des "Syslogs" kann man sehen, wie logrotate arbeitet. Schaut man              
sich die Dateien in /var/log an, die den Namen "syslog" tragen:                  
                  
>-rw-r----- 1 root adm  82484 2006-10-15 00:29 syslog                                     
-rw-r----- 1 root adm  23503 2006-10-13 01:30 syslog.1               
-rw-r----- 1 root adm  36587 2006-10-12 11:18 syslog.2               
-rw-r----- 1 root adm  38361 2006-10-11 02:47 syslog.3

Laut [wiki.ubuntuusers.de](https://wiki.ubuntuusers.de/Logdateien/)

#### Log-Datei erstellen

         root@pi26:~# cd /etc/logrotate.d             (ins Verzeichnis wechseln)
         root@pi26:/etc/logrotate.d# nano programm    (Datei erstellen)
         
         (eingeben:)
         
         /var/log/programm.log
         { 
         rotate 4
         weekly
         }
         


      

