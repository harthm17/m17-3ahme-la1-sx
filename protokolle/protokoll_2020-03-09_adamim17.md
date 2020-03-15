# Protokoll 2020.03.09
--------------------------
**Kopieren von Daten von Raspberry Pi, automatisches ausführen von Programmen auf Raspberry Pi**   
Autor: **Mike Adam**  
Datum: **09.03.2020**   

----------------------
## Inhaltsverzeichnis:



## Kopieren von Daten von Raspberry Pi
* Als erstes muss man sich mit dem Raspberry Pi mit SSH verbinden, um an die Daten zugreifen zu können.
````bash
  schueler@pcxx:~$ ssh adamim17@10.200.114.229
````
Oder mit dem Nickname, der angelegt wurde. (Siehe  [Protokoll 2020.03.02](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/adamim17/protokolle/protokoll_2020-03-02_adamim17.md#anlegen-von-einem-nickname-f%C3%BCr-schnelleres-einloggen))
````bash
  schueler@pcxx:~$ ssh pi29
````
* Nun kann man mit dem folgendem Befehl daten vom Raspberry Pi auf den verbundenen PC kopieren
````bash
  schueler@pcxx:~$ rsync -aP pi29:/home/adamim17 ./
````
In diesem Fall wird der Inhalt vom Ordner (/home/adamim17) in das aktuelle Verzeichnis kopiert (./)   
   
Mit dem Zusatz `-aP` kann man sich den Fortschritt anzeigen lassen. Mit dem Zusatz `-aPn` kann man sich anzeigen lassen, was alles kopiert wird, ohne dass es direkt kopiert wird.

## Startup Systeme
Bei Unix findet man mittlerweile schon 3 Arten von Startup Systemen:
* systemd
* sys-V-init
* upstart
   
in unserem Fall haben wir systemd benutzt

## Systemd Kommandos
* Um eine Liste von dem Status vom Rechner auszugeben, wird folgendes Kommando benutzt
````bash
  schueler@pcxx:~$ systemctl status
````
* Um einen Status eines Programmes auszugeben muss der Datenamen angegeben werden
````bash
  schueler@pcxx:~$ systemctl status (Dateiname)
````
* Mit folgenden Befehlen kann man Programme starten und stoppen   
Um die Befehle zu benutzen, muss man als Superuser angemeldet sein
````bash
  schueler@pcxx:~$ sudo -i   
  schueler@pcxx:~$ systemctl start (Dateiname)
  schueler@pcxx:~$ systemctl stop (Dateiname)
````

## C- oder Java Programme am Raspberry Pi im Hintergrund laufen lassen 
### Kopieren:
* Wenn man ein Programm an einem anderen Rechner erstellt hat, muss man die Datei erst auf den Raspberry Pi kopieren
````bash
schueler@pcxx:~$ rsync -aP (Dateipfad am Rechner) (Zielordner am Raspberry Pi)
````
Beispiel: Java Programm vom Desktop am Rechner auf den Desktop vom Raspberry Pi kopieren
````bash
schueler@pcxx:~$ rsync -aP /Schreibtisch/Java_adamim17_3ahme.jar pi29:/Schreibtisch
````
### Service-Datei erstellen:
* Als erstes wird eine Service Datei erstellt:
````bash
root@pi29:~$ nano /home/adamim17/adamim17-programm.service
````
* In die Datei wird dann folgendes eingegeben:
````
[Unit]
Description=C-Programm mit Ausgabe (oder Java-Programm)

[Service]
ExecStart=/home/adamim17/(programmname)/a.out
````
* Nachdem wird das Programm gestartet:
````bash
root@pi29:~$ systemctl start adamim17-programm
````
* Man kann überprüfen ob das Programm aktiv ist:
````bash
root@pi29:~$ systemctl status adamim17-programm
````

