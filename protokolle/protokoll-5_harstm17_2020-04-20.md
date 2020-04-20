# Protokoll-5 LABOR/SX 3AHME (2019/20)

---------------------------------------------------------------------------------------------

* **Thema:** Dienste in Linux-Systemen 2
* **Datum:** 20.04.2020
* **Gefehlt:** -
* **Erstellt von:** Stefan Haring (harstm17)
* **Protokoll der letzten Einheit:** [Protokoll 4](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/edit/harstm17/protokolle/protokoll-4_harstm17_2020-03-30.md)

----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis  

1. [Arbeitsauftrag](#arbeitsauftrag)
1. [Systemdienst mit Syslogausgabe](#systemdienst-mit-syslogausgabe)
   * [Bereits erledigte Aufgabenstellungen](#bereits-erledigte-aufgabenstellungen)
   * [Systemd Service erstellen](#systemd-service-erstellen)
   * [Fund eines Fehlers während dem Beobachten des Dienstes](#fund-eines-fehlers-während-dem-beobachten-des-dienstes)
   * [Service starten, stoppen und beobachten](#service-starten,-stoppen-und-beobachten)
   * [Autostart](#autostart)
1. [Resümee](#resümee)
-------------------------------------------------------------------------------------------------------------------

### Arbeitsauftrag

Fertigstellen der Arbeitsaufträge von der letzten Einheit. Falls man damit fertig wird, soll man mit der Durcharbeitung des [Kapitels 2 (Scripting)](#https://lms.at/mybib/MjM3NDc1ODU5/bibs/dotlrn_class_instance/xolrn__381036830.symlink/9F2714A93B69A.symlink?resource_id=0-237477244-237484829-381037558-420357452&m=view#155470705) beginnen.

--------------------------------------------------------------------------------------------------------------------------

### Systemdienst mit Syslogausgabe

Folgende Punkte beschreiben diese [Aufgabenstellung](#https://lms.at/mybib/MjM3NDc1ODU5/bibs/dotlrn_class_instance/xolrn__381036830.symlink/9F2714A93B69A.symlink?resource_id=0-237477244-237484829-381037558-420357452&m=view#155470740) näher:

#### Bereits erledigte Aufgabenstellungen

Die Aufgabenstellungen * ***C-Programm,
                       * Programm übersetzen,
                       * Programm testen*** wurden bei der letzten Einheit schon erledigt.
                       
Jedoch hat beim Punkt ***Programm testen*** etwas nicht 100%ig funktioniert, deswegen habe ich diese Aufgabenstellung wiederholt.
Jetzt verlief der Test ohne Probleme.

#### Systemd Service erstellen

##### Erstellen der Datei
Zu galt es eine neue Datei *mydaemon.service* mit dem Befehl `nano mydaemon.service` zu erstellen. Der Speicherort sollte möglichst dem Speicherort der *mydaemon.c*-Datei gleichen, damit man leichter auf diese Datei zurückgreifen kann.  
In der neu erstellten Datei musste folgender Text eingefügt werden:  

```
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=/home/user/mydaemon/mydaemon
IgnoreSIGPIPE=false
KillMode=process
```

##### Link auf Servicedatei erstellen

Danach muss man einen Link auf die *mydaemon.service*-Datei erstellen. Das läuft wie folgt ab:

```
user@pi: ~/mydaemon$ sudo -i
root@pi: ~# cd /etc/systemd/system
root@pi: /etc/systemd/system# ln -s /home/user/mydaemon/mydaemon
root@pi: /etc/systemd/system# ls -l
...
lrwxrwxrwx 1 root root   40 Mär 29 15:23  mydaemon.service -> /home/user/mydaemon/mydaemon.service
...
root@pi: /etc/systemd/system# exit
user@pi: ~/mydaemon$ 
```

Wichtig ist es, hier genau auf den Dateipfad zu achten, da dort leicht ein Fehler unterlaufen kann (später beschrieben). *User* muss oft statt dem tatsächlichen User geändert werden.


##### Dienst starten

Anschließend wird der Dienst mit folgendem Kommando gestartet:

```
user@pi: ~/mydaemon$ sudo systemctl start mydaemon
user@pi: ~/mydaemon$ 
```


##### Dienst beobachten

Das wird wie folgt in einer paralell ausgeführten Shell gemacht:

```
user@pi: ~/mydaemon$ sudo journalctl -f -u mydaemon
user@pi: ~/mydaemon$ 
```
###### Kommandos und deren Bedeutung

In den man-pages kann man nachschauen, welche Bedeutung Kommandos haben. Die man-pages ruft man mit ***man "gewünschter Befehl"*** auf.
Zu journalctl und deren Erweiterungen habe ich folgendes gefunden:

```
       journalctl may be used to query the contents of the systemd(1) journal
       as written by systemd-journald.service(8).

       If called without parameters, it will show the full contents of the
       journal, starting with the oldest entry collected.

       -f, --follow
           Show only the most recent journal entries, and continuously print
           new entries as they are appended to the journal.

       -u, --unit=UNIT|PATTERN
           Show messages for the specified systemd unit UNIT (such as a
           service unit), or for any of the units matched by PATTERN. If a
           pattern is specified, a list of unit names found in the journal is
           compared with the specified pattern and all that match are used.
           For each unit name, a match is added for messages from the unit
           ("_SYSTEMD_UNIT=UNIT"), along with additional matches for messages
           from systemd and messages about coredumps for the specified unit.

           This parameter can be specified multiple times.

       -p, --priority=
           Filter output by message priorities or priority ranges. Takes
           either a single numeric or textual log level (i.e. between
           0/"emerg" and 7/"debug"), or a range of numeric/text log levels in
           the form FROM..TO. The log levels are the usual syslog log levels
           as documented in syslog(3), i.e.  "emerg" (0), "alert" (1),
           "crit" (2), "err" (3), "warning" (4), "notice" (5), "info" (6),
           "debug" (7). If a single log level is specified, all messages with
           this log level or a lower (hence more important) log level are
           shown. If a range is specified, all messages within the range are
           shown, including both the start and the end value of the range.
           This will add "PRIORITY=" matches for the specified priorities.
```


Anschließend kann man den Dienst erneut starten. 
Bei Änderungen in der Service-Datei muss mit dem Kommando ***sudo systemctl daemon-reload*** eine Aktualisierung durchgeführt werden.


#### Fund eines Fehlers während dem Beobachten des Dienstes

Die Ursache, das inkorrekte Auführen des Dienstes, ist darauf zurzückzuführen, dass ich beim Link erstellen auf der Service-Datei einen falschen Pfad verwendet habe. Sobald ich diesen mit Hilfe des Terminals wieder richtig gestellt habe, ist der Test reibungsfrei abgelaufen.


#### Autostart

Dienste sollen oft beim Systemstart automatisch zum richtigen Zeitpunkt gestartet werden. Bei systemd lässt sich das mit folgendem Kommando leicht realisieren:

```
user@pi: ~/mydaemon$ sudo systemctl enable mydaemon
```

Jedoch wird es jetzt zum Auftreten einer Fehlermeldung kommen, die wie folgt aussieht:

```
The unit files have no installation config (WantedBy=, RequiredBy=, Also=,
Alias= settings in the [Install] section, and DefaultInstance= for template
units). ...
```
Um diese zu beheben, muss folgender Text in die *mydaemon.service*-Datei eingefügt werden:

```
[Install]
WantedBy=multi-user.target
```

Damit drücken wir aus, dass wenn das System den Zustand Multi-User Fähigkeit erreichen sollte, auch unser Dienst mydaemon zu starten ist.   

Letztendlich werden noch folgende zwei Kommandos ausgeführt, die zu einem Neustart führen:    

```
user@pi: ~/mydaemon$ sudo systemctl enable mydaemon
user@pi: ~/mydaemon$ sudo reboot
```
Sobald das erledigt ist, soll man mit *journalctl* überprüfen ob alles funktioniert hat und ob der Dienst nun tatsächlich läuft.


### Resümee

Die Übung ist recht gut von der Hand gegangen. Es hat nur eine Schwierigkeit gegeben, die sich baldig beheben lassen hat.
