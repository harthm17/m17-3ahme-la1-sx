# Labor Protokoll 2020-03-09
         
**Lukas Fleischhacker**       
**3AHME**   

----------------------------
## Inhaltsverzeichnis    
1) [Kopie der Raspberry-Dateien](#kopie-der-raspberry-dateien)  
   * [tmp Verzeichnis](#tmp-verzeichnis)  
   * [rsync](#rsync)   
2) [Startup Systeme](#startup-systeme)
   * [systemd](#systemd)            
         * [Programm Status](#programm-status)                 
         * [Programm starten](#programm-starten)               
         * [Programm stoppen](#programm-stoppen)  
3) [Im Hintergrund laufendes C-Programm](#im-hintergrund-laufendes-c-programm)
   * [C-Servicedatei erstellen](#c-servicedatei-erstellen)
   * [automatisch starten](#automatisch-starten)               
4) [Im Hintergrund laufendes Java-programm](#im-hintergrund-laufendes-java-programm)
   * [Programm auf Raspberry kopieren](#programm-auf-raspberry-kopieren)
   * [Java-Servicedatei erstellen](#java-servicedatei-erstellen)
   * [automatisches Starten](#automatisches-starten)
5) [Wichtig](#wichtig)
----------------------------        

## Kopie der Raspberry-Dateien

### tmp Verzeichnis
Mit ````/tmp```` in das temporäre Verzeichnis wechseln.   
> im Verzeichnis /tmp werden jene Dateien abgelegt, die nach einem Neustart des Systems zweifelsfrei                 
nicht mehr benötigt werden und während des Systemstarts geleert werden können          
    
[laut Wikipedia](https://de.wikipedia.org/wiki/Temporäre_Datei)    

### rsync
Mit ````rsync```` werden die Daten am Computer gespeichert. 

    schueler@pcxx:~$ rsync -a pi26:/home/flelum17 ./
    
Man gibt ````rsync```` ein, dann eine Option wie z.B. ````-aP```` , ````-aPn```` oder ````-aP --delete````           
und dann die Quelle und das Ziel. 

> rsync ist ein Programm, um Dateien zwischen lokalen oder über das Netzwerk erreichbaren          
Pfaden abzugleichen. Dabei werden zunächst die Größe und die Änderungszeit der Dateien in          
Quelle und Ziel verglichen ("Quick Check"-Algorithmus), so dass nur die Dateien behandelt                   
werden müssen, bei denen es Änderungen gegeben hat.            
    
[laut wiki.ubuntuusers.de](https://wiki.ubuntuusers.de/rsync/)

## Startup Systeme
Es sind drei verschiedene Systeme zu finden:          

* **Sys-V-Init**
* **Upstart**
* **systemd**

### systemd

#### Programm Status

      root@pi26:~# systemctl status

#### Programm starten

      root@pi26:~# systemctl start [z.B. alsa-state]

#### Programm stoppen
    
      root@pi26:~# systemctl stop  [z.B. alsa-state]
      
Mehr zu **systemd** bei [LMS](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#155470713)
    
    
##   Im Hintergrund laufendes C-Programm 

### C-Servicedatei erstellen

      root@pi26:~# nano /etc/systemd/system/flelum17-programm.service
      
dort eingeben:

      [Unit]
         Description=C-Programm mit Ausgabe

      [Service]
         ExecStart=/home/flelum17/programm/a.out
         
      [Install]
         WantedBy=multi-user.target
          
### automatisch starten
Mit ````systemctl enable```` und dem Programmnamen starten              
     
     root@pi26:~# systemctl enable flelum17-programm
  
danach den Raspberry neustarten:

      root@pi26:~# reboot
      
## Im Hintergrund laufendes Java-Programm

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
### Programmm auf Raspberry kopieren 

    schueler@pcxx:~$ rsync -aP Schreibtisch/Java_flelum17_3ahme.jar pi26:/tmp/
    
### Java-Servicedatei erstellen

    root@pi26:~# nano /etc/systemd/system/flelum17-java-programm.service
    
dort eingeben:

    [Unit]
       Description=Java Programm mit Ausgabe

    [Service]
       ExecStart=java -jar /root/Java_flelum17_3ahme.jar

    [Install]
       WantedBy=multi-user.target
       
### automatisches Starten
Gleich wie früher mit ````systemctl enable```` und dem Programmnamen starten              
     
     root@pi26:~# systemctl enable flelum17-programm
  
danach den Raspberry neustarten:

      root@pi26:~# reboot
 
## Wichtig
Man sollte sich für jede Anwendung einen neuen und eigenen Benutzer anlegen,                 
**keinesfalls** den superuser, da Schadsoftware sonnst alle Rechte haben könnte.          
Im besten Fall nimmt man dem Benutzer alle Rechte, bis auf die notwendigen.               

