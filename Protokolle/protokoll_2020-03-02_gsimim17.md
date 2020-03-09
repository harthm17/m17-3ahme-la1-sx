# 2. Protokoll Raspberry PI
         
-----

**Name**: Gschier Michael  
**Datum**: 02.03.2020  
**Klasse**: 3AHME  
**Gruppe**: 1  

-----

## Inhaltsverzeichnis    
1) [Nickname](#nickname)  
   * [Datei öffnen](#datei-öffnen)  
   * [Datei bearbeiten](#datei-bearbeiten)   
2) [C-Programm](#c-programm)
   * [Verzeichnis erstellen](#verzeichnis-erstellen)
   * [C-Programm schreiben](#c-programm-schreiben)
   * [Compilieren](#compilieren)            
   * [Programm starten](#programm-starten)
   * [In Datei ausgeben](#in-datei-ausgeben)
   * [Programm zusehen](#programm-zusehen)
   * [Logrotate](#logrotate)                 
   * [Log-Datei erstellen](#log-datei-erstellen)
3) [GNU-Project](#gnu-project)
----------------------------
## Nickname
Mithilfe eines Nicknames kann man sich schneller und einfacher bei einem Raspberry einloggen. Ähnlich wie bei einem Alias verkürtzt man die Eingabe.                                

### Datei öffnen

        nano /ssh/config 
        
### Datei bearbeiten
        
        Host pi24-root
        Hostname 10.200.114.224
        User root
        
        Host pi24-gsimim17
        Hostname 10.200.114.224
        User gsimim17
        
Früher musste man **ssh gsimim17@10.200.114.224** und das Passwort eingeben. Jetzt geht es auch nur mit **ssh pi24**.
        
--------------

## C-Programm
### Verzeichnis erstellen

         gsimim17@pi24:~ $ mkdir programm              

### C-Programm schreiben
Mithilfe des Editors *nano*

         gsimim17@pi24:~/programm $ nano main.c
         
Einfaches C-Programm schreiben, welches eine Ganzzahl *i* immer weiterzählt.

         #include <stdio.h>
         #include <unistd.h>

         int main () {
               int i = 100 x 10 +27;
                
               printf("i = %d", i);
               
               for(long l = 0; l < 100000; l++) {
                     /* i++;
                     printf("i = %d", i);
                     schlechte Lösung weil der Raspberry PI auf dauer belastet wird*/
               
                     i++;
                     printf("i = %d", i);
                     sleep(1);//Bessere Lösung weil Raspberry nicht auf dauer Belastet wird
               }
               
               return 0;
          }

### Compilieren
Mithilfe des *GNU-Compilers*

         gsimim17@pi24:~/programm $ gcc main.c

### Programm starten

         gsimim17@pi24:~/programm $ ./a.out
      
### In Datei ausgeben
Die Ausgabe des Programmes wird nicht in der Konsole angezeigt, sondern in einer Datei. Dies geschieht aber nur wenn auch der Quelltext des Programmes umgeändert wird.

         gsimim17@pi24:~ $ ll /var/log
         gsimim17@pi24:~ $ sudo touch /var/log/programm.log
         gsimim17@pi24:~ $ sudo chmod 666/var/log/programm.log
         gsimim17@pi24:~ $ ll /var/log/programm.log
         gsimim17@pi24:~ $ gcc main.c
         gsimim17@pi24:~ $ ./a.out
         
### Programm zusehen

         gsimim17@pi24:~ $ watch ll /var/log/programm.log

### Logrotate
Mit diesem Feature kann man automatisch nach einer bestimmten Zeit Backups erstellen lassen.

>"logrotate" ist ein Werkzeug um Logdateien zu verwalten. Wird Logdateien
keine Beachtung geschenkt, so werden sie immer größer und belegen am Ende den
gesamten verfügbaren Plattenplatz. Weiterhin ist das Durchsuchen vieler/großer
Logdateien zeitaufwendig. Um dies zu verhindern und Platz auf der Festplatte
zu sparen, ist "logrotate" entwickelt worden.
Mit "logrotate" kann man Logdateien ab einer bestimmten Größe (z.B. 1 MByte)
und/oder einem bestimmten Alter (z.B. 1 Tag, 1 Woche, 1 Monat, 1 Jahr) rotieren
lassen. Mit "Rotieren" ist gemeint, dass die aktuelle Logdatei und frühere
Versionen von ihr umbenannt/verschoben und dabei evtl. komprimiert werden. Die
aktuelle Logdatei wird geleert. Frühere Versionen der Logdatei werden dabei
durchnumeriert und ggf. auch gelöscht, sobald sie ein gewisses Alter oder eine
gewisse Anzahl erreichen.

[Logrotate](https://www.ostc.de/howtos/logrotate-HOWTO.html)

Quelle: [wiki.ubuntuusers.de](https://wiki.ubuntuusers.de/Logdateien/)

### Log-Datei erstellen

         root@pi24:~# cd /etc/logrotate.d             
         root@pi24:/etc/logrotate.d# nano programm   
         
         /var/log/programm.log
         { 
         rotate 4
         weekly
         }
         
       
------------

## GNU-Project
         
   >Das GNU-Projekt entwickelt das Betriebssystem GNU (Aussprache: [ɡnuː][1]),                
   das von Richard Stallman mit dem Ziel gegründet wurde, ein freies,               
   unixähnliches Betriebssystem zu schaffen, das sicherstellt,dass die              
   Endbenutzer die Freiheiten haben, es verwenden, untersuchen, verbreiten (kopieren)                 
   und verändern zu dürfen. Software, deren Lizenz diese Freiheiten garantiert, wird                  
   Freie Software (engl. Free Software) genannt, GNU ist in diesem Sinne frei.
 
Quelle: [Wikipedia](https://de.wikipedia.org/wiki/GNU-Projekt)

![Richard Stallman](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a8/Richard_Stallman_at_CommonsFest_Athens_2015_2.JPG/295px-Richard_Stallman_at_CommonsFest_Athens_2015_2.JPG)

*Richard Stallman*

--------------
