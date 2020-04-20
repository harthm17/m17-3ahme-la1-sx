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

----------------------------------------------------------------------------------------------

## Autostart

----------------------------------------------------------------------------------------------
