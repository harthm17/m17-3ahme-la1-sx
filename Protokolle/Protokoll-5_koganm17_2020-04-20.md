# Protokoll-5 LABOR/SX 3AHME (2019/20)

* **Thema:** Dienste
* **Datum:** 30.03.2020
* **Gefehlt:** Keiner
* **Erstellt von:** koganm17
* **Protokoll letzte Einheit:** [30.03.2020](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/koganm17/Protokolle/Protokoll-4_koganm17_2020-03-30.md)

----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis
1) [Fehlerbehebung](#fehlerbehebung)
1) [systemd Service erstellen](#systemd-service-erstellen)
1) [Service starten, stoppen und beobachten](#service-starten-stoppen-und-beobachten)
1) [Autostart](#autostart)  
         
----------------------------------------------------------------------------------------------

## Fehlerbehebung

In der letzten Einheit bin ich nur bis zum Punkt Systemd Service erstellen gekommen.  

Mit der Hilfe meiner Mitschüler und von Herrn Steiner konnte ich das Problem lösen. 

Das Problem war, dass ich in der mydaemon.service Datei user statt andreas geschrieben habe. 


----------------------------------------------------------------------------------------------
## systemd Service erstellen

Zuerst erstellt man die mydaemon.service Datei mit nano. In dieses Fenster schreibt man dann den folgenden, vorgegebenen Text:
```
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=/home/user/mydaemon/mydaemon
IgnoreSIGPIPE=false
KillMode=process
```
Jetzt erstellen wir einen Link auf die system-Datei.
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
Danach starten wir den Dienst.
```
user@pi: ~/mydaemon$ sudo systemctl start mydaemon
user@pi: ~/mydaemon$
```
Den Dienst kann man mit diesem befehl beobachten:
```
sudo journalctl -f -u mydaemon
```
Wenn man einen Fehler in der service - Datei gemacht hat und ihn ausgebessert hat, kann man den daemon mit dem folgenden befehl aktualisieren.
```
sudo systemctl daemon-reload 
```

----------------------------------------------------------------------------------------------

## Service starten stoppen und beobachten
Ein Service kann mit dem Kommando systemctl gestartet und beobachtet werden.
Die nachfolgenden Befehle wurden zum starten, restarten, stoppen und Status anzeigen eingegeben.
```
root@pi:~# systemctl start mydaemon
root@pi:~# systemctl restart mydaemon
root@pi:~# systemctl stop mydaemon
root@pi:~# systemctl status mydaemon
```
 Mit den folgenden weiteren Befehlen kann man die Ausgabe verschieden ausgeben lassen. 
 ```
 journalctl -u mydaemon
 journalctl -u mydaemon -p warning
 ```
----------------------------------------------------------------------------------------------

## Autostart
Dienste sollen oft beim Systemstart automatisch zum richtigen Zeitpunkt gestartet werden. Bei systemd lässt sich das mit folgendem Kommando leicht realisieren:
```
sudo systemctl enable mydaemon
```
Dann kommt jedoch eine Fehlermeldung.
Der Fehler erscheint, da das System noch nicht weiß, wann der Dienst beim Hochfahren gestartet werden soll. Um diesen Fehler zu beseitigen, hängen wir einfach Folgendes an unsere mydaemon.service Datei an.
```
[Install]
WantedBy=multi-user.target
```
Damit sagen wir dem System, dass wenn das System den Zustand Multi-User Fähigkeit erreichen soll, auch unser Dienst mydaemon zu starten ist.

Nun aktivieren wir den Daemon noch einmal und rebooten das System. Danach checken wir, ob alles geklappt hat. Dafür benötigen wir folgende Befehle:
```
sudo systemctl enable mydaemon
sudo reboot
journalctl
```

----------------------------------------------------------------------------------------------
