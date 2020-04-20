# 5. Protokoll

-------------------------------------------------

## Thema: Dienste in Linux Systemen 2

-------------------------------------------------

Übungsdatum:   Montag, 20.04.2020     
Übungszeit:    14:10 bis 16:30      
Übungsort:     St. Veit in der Südsteiermark, Home-Office    
Verfasser:     Georg Kaufmann    
Abwesend:      keiner      
Anwesend:      Felix Hamrle, Stefan Haring, Thomas Harrer, Georg Kaufmann, Andreas Kogler, Franz Lieleg, Simon Marcher

-------------------------------------------------

### Inhaltsverzeichnis
1) [Auftrag](#auftrag) 
1) [Erledigte Punkte](#erledigte-punkte)
1) [systemd Service erstellen](#systemd-service-erstellen)
1) [Autostart](#autostart)
1) [Resümee](#resümee)

-------------------------------------------------

#### Auftrag
Fertigstellen der Arbeitsaufträge von der letzten Einheit. Die dort erledigten Aufträge sind im [Protokoll vom 30.03.2020](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/kaugem17/protokoll/protokoll-4_kaugem17_2020-03-30.md).

-------------------------------------------------

#### Erledigte Punkte
Aufgabe war es einen Dienst zu erstellen.
In der letzten Einheit schaffte ich folgende Punkte.
* Programm übersetzen
* Programm testen

-------------------------------------------------

#### systemd Service erstellen
Zu aller erst muss man eine neue Datei *mydaemon.service* mit dem Befehl `nano mydaemon.service` erstellen.   
Dort mussten wir folgenden Text einfügen.   
    

```
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=/home/user/mydaemon/mydaemon
IgnoreSIGPIPE=false
KillMode=process
```
    
Nun müssen wir eine Link auf unsere Service-Datei legen. Dazu werden folgende Befehle verwendet.    
    

| Befehl |    |
| ------ | -- |
| `sudo -i` | wechsel in Super-User root, Passwort erforderlich |
| `cd /etc/systemd/system` | wechseln in /etc/systemd/system Verzeichnis |
| `ln -s /home/user/mydaemon/mydaemon` | erstellen eines Links |
| `ls -l`| Line-Mode, mehr Infos anzeigen | 
| `exit`| verlassen der Super-User root |   
    

![Bild](https://cdn.discordapp.com/attachments/692288920716705812/701839797219622997/service_erstellen.png)   
    

Wie bei dem Bild gut zu erkennen ist, muss der `user`, auf in meinem Fall `georg` geändert werden. Ansonsten funktioniert es nicht.   
    

Anschließend wird der Dienst gestartet.     
    

| Befehl |    |
| ------ | -- |
| `sudo systemctl start mydaemon` | starten des Dienstes |    
    

Mit dem Befehl `sudo journalctl -f -u mydaemon` kann man den Dienst in einer anderen Shell beobachten. Anschließend muss man den Dienst erneut starten. 
    

Wenn man Änderungen in der Service-Datei vornimmt muss man folgenden Befehl zur Aktualisierung durchführen.   
    

| Befehl |    |
| ------ | -- |
| `sudo systemctl daemon-reload` | aktualisierung eines Dienstes |    
    

-------------------------------------------------

#### Autostart
Mit folgenden Befehlen kann man einen Dienst automatisch starten lassen. Dies ist oft beim Systemstart automatisch zum richtigen Zeitpunkt erwünscht.

Zu aller erst muss man den Befehl `sudo systemctl enable mydaemon` anwenden. Anschließend wird eine Fehlermeldung angezeigt. Um diese weg zu bekommen muss man `nano mydaemon.service` eingeben und folgenden Text hinzufügen. 

```
[Install]
WantedBy=multi-user.target
```

Damit drücken wir aus, dass wenn das System den Zustand Multi-User Fähigkeit erreichen sollte, auch unser Dienst mydaemon zu starten ist.   
    
Anschließend werden noch folgende Befehle ausgeführt.

| Befehl |    |
| ------ | -- |
| `sudo systemctl enable mydaemon` | | 
| `sudo reboot` | reboot des Systems |

![Bild](https://cdn.discordapp.com/attachments/692288920716705812/701843132437889074/auto.png)

-------------------------------------------------

#### Resümee
Es hat teilweise Schwierigkeiten gegeben. Beispielsweiße bei den Befehlen `journalctl -f`, `journalctl -f -p 4`, `journalctl -f -v verbose` und `tail -f /var/log/syslog`. Aber zum Schluss hat alles funktioniert. 
