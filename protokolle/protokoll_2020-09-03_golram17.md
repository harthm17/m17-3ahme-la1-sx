# Protokoll 4 La1/SX 3AHME (2019/20)

-------------------------

* **Thema:** Erstellen und Starten von C -Programmen auf dem Raspberry PI
  * **Datum:** 09.03.2020
  * **Gefehlt:** Danko Sebastian
  * **Erstellt von:** Golser Raphael
  
  -------------------------------------------------------
  
## Inhaltsverzeichnis

1. [Kopieren von Daten vom Rapberry PI auf den Computer](#kopieren-von-daten-vom-rapberry-pi-auf-den-computer)
2. [Startup Systeme](#startup-systeme)
2. [systemd](#systemd)
3. [Automatisches Starten von C-Programmen](#automatisches-starten-von-c-programmen)
4. [Automatisches Starten von Java-Programmen](#automatisches-starten-von-java-programmen)

----------------------------------------------------------

## Kopieren von Daten vom Rapberry PI auf den Computer

Als aller erstes sind wir in das ````/tmp```` Verzeichnis gegangen, weil dort die Dateien täglich gelöscht werden und das in unserem Fall gut ist da nicht Speicher unnötig verbraucht wird.
````bash
  schueler@pcxx:~$ cd /tmp
  ````
Nun können wir mit dem Befehl ````rsync```` Daten vom Raspberry PI auf unseren Computer speichern:
````bash
  schueler@pcxx:~$ rsync -aP pi25:/home/golram17 ./
  ````
  mit dem Kommando ````-aP```` wird der Fortschritt vom Kopieren in Balken angezeigt. Der hintere Teil ````pi25:/home/golram17 ./```` sagt von wo ich die Daten die ich kopieren will her bekomme.
  Mit dem Kommando ````-aPn```` zeigt das Terminal nur die Daten an die mit dem ````rsync```` Befehl her kopiert werden würden. Doch will man diese kopierten Daten vom Computer löschen musss man nach dem ````-aP```` Kommando ein ````--delete```` Kommando anhängen.
  
  -----------------------------------------------------------
  
  ## Startup Systeme
  Laut: [LMS-Skriptum](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#155470713)
  > Mittlerweile sind drei unterschiedliche Systeme zu finden:
    Sys-V-Init
    Sys-V-Init ist das init-System des Unix-Betriebssystems System V. Die einzelnen Dienste werden hintereinander gestartet,      wodurch der Startup sehr überschaubar aber auch sehr langsam ist. Ein Nachbau wird in vielen Linux-Distributionen genutzt. So auch beim Debian System, also auch im Raspbian am Raspberry PI.
    Upstart
    Hier handelt es sich um ein Ubuntu-Projekt zur Beschleunigung des Systemstarts. Es verfügt über die Möglichkeit Prozesse mittels Events parallel zu starten. Upstart arbeitet nach dem Prinzip "greedy event-based". Alle Dienste die ein Start-Event erhalten werden so schnell wie möglich gestartet.
    Upstart kommt bis Ubuntu 14.10 zu Einsatz und eine Weiterentwicklung wurde eingestellt.
    systemd
    In Konkurrenz zu Upstart entstand systemd. Nachdem Debian auf systemd gewechselt hat, ist auch Ubuntu ab Version 15.10 auf systemd gewechselt. systemd arbeitet nach dem Prinzip "lazy dependency-based", das heisst, eine "Unit" wird nur dann gestartet wenn eine andere "Unit" davon abhängt.
    Aufgrund dieser historischen Entwicklung sind in einem Ubuntu 15.04 System alle drei Init-Systeme parallel im Einsatz. Langfristig wird ein Wechsel zu systemd erfolgen.
   
   Siehe auch: [wiki.ubuntuusers](https://wiki.ubuntuusers.de/Dienste/)
  
  -------------------------------------------------------------------
  
  ## systemd
  
  ````systemd```` ist ein System Dämon vor dem man keine Angst haben sollte, weil dieser freundlich ist.
  Mit dem Kommando ````systemctl```` ruft man diesen Dämon auf.
  Um Programme im ````sytemd```` die Programme in einer Liste anzuzeigen haben wir dieses Kommando genutzt:
  ````bash
  golram17@pi25:~$ systemctl status
  ````
  Diese Liste verlässt man wieder mit q.
  Nun haben wir uns das Programm ````alsa-state```` ausgesucht und wollten nur den status von ````alsa-state```` sehen:
  ````bash
  golram17@pi25:~$ systemctl status alsa-state
  ````
  Daher wir nicht genug Rechte hatten mussten wir wieder einmal in den Superuser um das Programm zu stoppen:
  ````
  root@pi25:~# systemctl stop alsa-state
  ````
  Da wir mit dem Programm weiter arbeiten wollten haben wir es wieder gestartet:
  ````
  root@pi25:~# systemctl start alsa-state
  ````
  Daher dass das Programm ````als-state```` verwendet und bzw. bearbeitet wurde kann man diese Änderungen sehen:
  ````
  root@pi25:~# journalctl -u /alsa-state
  ````
  Das ````-u```` steht für Unit und das bedeutet das man nur diese Date sehen will.
  Weil der Befehl ````journal```` dem Befehl ````tail```` Ähnlich ist kann man mit dem Kommando ````-f```` die gleiche Funktion nutzen:
  ````
  root@pi25:~# journal -f /alsa-state
 ````
 
 ---------------------------------------
 
 ## Automatisches Starten von C-Programmen
 
 Zuerst müssen wir eine Datei erstellen mit der wir das automatische Starten ausführen können:
 ````
 root@pi25:~# nano /etc/systemd/system/golram17-programm.service
 ````
 In dieser Datei steht:
 ````
 [Unit]
 Description=C-Programm mit Ausgabe
 
 [Service]
 ExecStart=/home/golram17/programm/a.out
 
 [Install]
 WantedBy=multi-user.target
 ````
 
 ---------------------------------------------------------
 
 Um den automatischen Start zu aktivieren, müssen wir zuerst erst ````systemctl````aktivieren und dann den Raspberry Neustarten:
 ````
 root@pi25:~# systemctl enable golram17-programm
 root@pi25:~# reboot
 ````
 
 -------------------------------------------------------------
 
 Als der Raspberry wieder gestartet wurde wollten wir sehen ob unsere Datei sich selbst gestartet hat:
 ````
 root@pi25:~# tail -f /var/log/programm.log
 ````
 
 --------------------------------------------------------
 
 ## Automatisches Starten von Java-Programmen
 
 Nachdem wir nicht wussten welche Java Version wir hatten haben wir zuerst die geprüft:
 ````
 root@pi25:~# java --version
 ````

--------------------------------------------------

Jetzt haben wir das Java-Programm unserer letzten Informatik Stunde in das ````/tmp/````Verzeichnis vom Raspberry kopiert:
````bash
schueler@pcxx:~$ rsync -aP /work/3AHME/golser/java_3ahme_golram17.tar.xz pi25 /tmp/
````

Dieses Java-Programm lautet:
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

--------------------------------------------------------------

Um auf das java Programm zugreifen zu können mussten wir zuerst in das ````/tmp````Verzeichnis um dann das Programm in das ````/home/````Verzeichis zu kopieren:
````
root@pi25:~# cd /tmp/
root@pi25:~/tmp # cp java_3ahme_golram17/dist/java_3ahme_golram17.jar ~
````

----------------------------------------------------------------

Nun haben wir wieder eine Datei angelegt in der wir wieder den automatischen Start aktivieren in der steht:
````
[Unit]
Description=Java Programm mit Ausgabe

[Service]
ExecStart=java -jar /root/java_3ahme_golram17/dist/java_3ahme_golram17.jar

[Install]
WantedBy=multi-user.target
````

------------------------------------------

Jetzt ist es gleich wie beim C-Programm, den atomatischen Start aktivieren und den Raspberry Neustarten:
````
root@pi25:~# systemctl enable golram17-java-programm
root@pi25:~# reboot
````

---------------------------------------------------------

Nun wurde das Programm wieder angezeigt diesmal aber mit ````journal````:
````
root@pi25:~# journal -u-golram17-java-programm
````
