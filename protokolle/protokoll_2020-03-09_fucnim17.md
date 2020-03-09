Kopie von Daten auf dem Raspberry machen:

schueler@pcxx:~$ rsync -a pi22:/home/fucnim17 ./

Startup Systeme ............... Linux 2 skript


systemctl status.......... status vom computer abfragen
mehr details: root@pi22:~# systemctl status [programmname]

Starten/stoppen: root@pi22:~# systemctl start [programmname]
                 root@pi22:~# systemctl stop [programmname]
                 
root@pi22:~# journalctl -u [alsa-state]
root@pi22:~# journalctl -f -u [alsa-state]  (wird aktualisiert)

Systemd servicedatei erstellen:

root@pi22:~# nano /etc/systemd/system/fucnim17-programm.service
flogendes eingeben: 
[Unit]
Description=C-Programm mit Ausgabe

[Service]
ExecStart=/home/fucnim17/programm/a.out

berprüfen ob es existiert: root@pi22:~# ls -la /home/fucnim17/programm/a.out
starten: root@pi22:~# systemctl start fucnim17-programm
status abrufen: root@pi22:~# systemctl status fucnim17-programm
programm stoppen root@pi22:~# systemctl stop fucnim17-programm

systemd servicedatei aktualisieren:

root@pi22:~# nano /etc/systemd/system/fucnim17-programm.service
folgendes eintragen:
[Unit]
Description=C-Programm mit Ausgabe

[Service]
ExecStart=/home/fucnim17/programm/a.out

[Install]
WantedBy=multi.user.target

progamm automatisch starten bei computer start: root@pi22:~# systemctl enable fucnim17-programm

java programm zum raspberry senden: schueler@pcxx:~$ rsync -aP Schreibtisch/Java_fucnim17_3ahme.jar pi22:/tmp/

Komprimieren: zip (Windows) | gnu-zip (Linux)


Java Programm am Raspberry laufen lassen:

systemd servicedatei erstellen:
root@pi22:~# nano /etc/systemd/system/fucnim17-java-programm.service

folgendes eintragen:
[Unit]
Description=Java Programm mit Ausgabe

[Service]
ExecStart=java -jar /root/Java_fucnim17_3ahme.jar

[Install]
WantedBy=multi-user.target

 root@pi22:~# systemctl start [programmname]
 root@pi22:~# systemctl stop [programmname]

progamm automatisch starten bei computer start: root@pi22:~# systemctl enable fucnim17-programm











