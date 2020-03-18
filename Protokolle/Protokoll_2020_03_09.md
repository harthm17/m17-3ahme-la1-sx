# 5 LA Protokoll dansem16

-------------------------
##Kopieren von Daten/Dateien und automatischer Start von C/Java-Programmen
---------------------------------------------------------------------------
  * **Datum:** 09.03.2020
  * **Gefehlt:** Danko Sebastian
  * **Erstellt von:** Danko Sebastian
  
  -------------------------------------------------------
  
## Inhaltsverzeichnis    
1. [tmp Verzeichnis](#tmp-verzeichnis)  
1. [rsync](#rsync)   
2. [Startup Systeme](#startup-systeme)            
    3,1. [Programm Status](#programm-status)                 
    3,2. [Programm starten](#programm-starten)               
    3,3. [Programm stoppen](#programm-stoppen)  
3. [Im Hintergrund laufendes C-Programm](#im-hintergrund-laufendes-c-programm)<br>
    4,1. [C-Servicedatei erstellen](#c-servicedatei-erstellen)<br>
    4,2. [automatisch starten](#automatisch-starten)              <br> 
4. [Im Hintergrund laufendes Java-programm](#im-hintergrund-laufendes-java-programm)<br>
    5,1. [Programm auf Raspberry kopieren](#programm-auf-raspberry-kopieren)<br>
    5,2. [Java-Servicedatei erstellen](#java-servicedatei-erstellen)<br>
    5,3. [automatisches Starten](#automatisches-starten)<br>

----------------------------        



### tmp Verzeichnis
Als erstes ins ````/tmp````  temporäre Verzeichnis wechseln. 

Im ````/tmp```` werden alle Daten gelöscht die da gespeichert wurden, um Speicher zu sparen.
   
[Kurze Beschreibung](http://www.64-bit.de/dokumentationen/linux/002/node19.html)    

--------------------------------------------------------------------------------------

### rsync

Mit ````rsync```` werden die Daten am Computer gespeichert. 

    schueler@pcxx:~$ rsync -a pi27:/home/dansem19 ./
 
>rsync gleicht Dateien und Ordner zwischen Lokalen oder Remote Systemen ab. die Synchronisation findet von der Quelle zum Ziel statt.

Ist die Quelle oder das Ziel ein Remote System findet der Datenabgleich via SSH oder einen rsync-daemon statt. Rsync wird oft in Backupscripten verwendet oder zum kopieren (sichern) Großer Datenmengen. Es kann bei einem Abbruch jederzeit neu starten und macht an der „letzten stelle einfach weiter“.

Rsync kopiert dabei auch nur neue oder geänderte Daten, was es wirklich gut für Backups macht. Wir behandeln hier nur die gängigsten Optionen!

[Quelle](https://www.shellbefehle.de/befehle/rsync/)

-----------------------------------------------------------------------------------------------------

## Startup Systeme

Es sind drei verschiedene Systeme zu finden:          

1. Sys-V-Init
>Sys-V-Init ist das init-System des Unix-Betriebssystems System V. Die einzelnen Dienste werden hintereinander gestartet, wodurch der Startup sehr überschaubar aber auch sehr langsam ist. Ein Nachbau wird in vielen Linux-Distributionen genutzt. So auch beim Debian System, also auch im Raspbian am Raspberry PI.
2. Upstart
>Hier handelt es sich um ein Ubuntu-Projekt zur Beschleunigung des Systemstarts. Es verfügt über die Möglichkeit Prozesse mittels Events parallel zu starten. Upstart arbeitet nach dem Prinzip "greedy event-based". Alle Dienste die ein Start-Event erhalten werden so schnell wie möglich gestartet.
Upstart kommt bis Ubuntu 14.10 zu Einsatz und eine Weiterentwicklung wurde eingestellt.
3. systemd
>In Konkurrenz zu Upstart entstand systemd. Nachdem Debian auf systemd gewechselt hat, ist auch Ubuntu ab Version 15.10 auf systemd gewechselt. systemd arbeitet nach dem Prinzip "lazy dependency-based", das heisst, eine "Unit" wird nur dann gestartet wenn eine andere "Unit" davon abhängt.

[Quelle LMS](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#155470713)
----------------------------------------------------------------

#### Status

      root@pi27:~# systemctl status

####  Starten

      root@pi27:~# systemctl start

####  Stoppen
    
      root@pi27:~# systemctl stop
      
Mehr Info auf[LMS](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#155470713)

---------------------------------------------------
    
##   Im Hintergrund C-Programm laufen lasen

#### C-Servicedatei erstellen

      root@pi27:~# nano /etc/systemd/system/dansem16-programm.service
      
          
### automatisch starten
                   
  Program starten 
      
      root@pi27:~# systemctl enable dansem16-programm
  
  Raspberry Neustarten 
      
      root@pi26:~# reboot
 
----------------------------------------------
## Im Hintergrund Java-Programm laufen lasen

### BeispielProgram
````java
public class Main {
    
    private static int counter; //Zählereigenschaft
    
    public static void main (String[] args) { //psvm \t
        for (int i = 0; i < 10; i++) {
            counter += i;
            System.out.println(counter); //sout \t
        }
    }
}
````

1. Programmm auf Raspberry kopieren 

    schueler@pcxx:~$ rsync -aP Schreibtisch/Java_dansem16_3ahme.jar pi26:/tmp/
    

2. Java-Servicedatei erstellen

    root@pi27:~# nano /etc/systemd/system/dansem16-java-programm.service
    
------------------------------------------------------------------------------------
       
### automatisches Starten              
     
Program starten wie vorher 
    
    root@pi27:~# systemctl enable dansem16-programm
  
Rapberry Neustarten 

     root@pi27:~# reboot
 
