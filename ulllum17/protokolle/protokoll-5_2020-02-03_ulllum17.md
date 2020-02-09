# 5. Protokoll | AHME17 
# Uller Lucas
-------------------------------------------------------------------------
* **Thema:** Versionsverwaltungssystem, Git-Befehle(Shell), Shell
* **Datum:** 03.02.2020
* **Gefehlt:** ---
* **Erstellt von:** ulllum17
* **Protokoll letzte Einheit:** [4.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ulllum17/ulllum17/protokolle/protokoll-4_2020_01_27_ulllum17.md)
--------------------------------------------------------------------------
## Inhaltsverzeichnis




--------------------------------------------------------------------------


## Autostart

In der letzten Einheit haben wir das Programm als Dienst verfügbar gemacht. Den Dienst können wir mit Folgendem Befehl Automatisch starten lassen.
````bash
stystemctl enable programm
````

## Logrotate
> In der Informationstechnologie ist die Protokollrotation ein automatisierter Prozess in der Systemverwaltung, bei dem Protokolldateien komprimiert, verschoben, umbenannt oder gelöscht werden, wenn sie zu alt oder zu groß sind.

Quelle: Übersetzt aus dem Englischen - [Wikipedia](https://en.wikipedia.org/wiki/Log_rotation)

### Logrotate erstellen
Der Logrotate ist im Verzeichnis **/etc/logrotate.d/** zu speichern.

Logrotate Beispiel:

````bash
  /var/log/programm.log {
    rotate 4
    weekly
    compress
    missingok
    notifempty
}
````

## Programm als System Account

1. System Account anlegen 
````bash
adduser --disabled-password --no-create-home --system programm
````
2. In der Service Datei den *System Account* hinzufügen.

````bash
nano /etc/systemd/system/programm.service
````
Hinzuzufügen ist **User=programm**.    
Die Service Datei sieht wie folgt aus. 

````service
[Unit]
Description=Labor Programm

[Service]
Type=simple
ExecStart=/home/ulllum17/programm/a.out
User=programm

[Install]
WantedBy=multi-user.target
````
### Überprüfen ob das Programm mit dem System Account läuft

Tool *Top*

````bash
top
````
benutze die *SHIFT-Taste* + *L* um im Tool *Top* das Suchfeld zu aktivieren und mithilfe der PID(=Process identifier) den Prozess zufinden.

### PID finden

Der PID vom Dienst kann mit folgendem Befehl gefunden werden

```bash
systemctl status programm
````

Ausgabe:

````bash

● programm.service - Labor Programm
   Loaded: loaded (/etc/systemd/system/programm.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2020-02-09 09:37:02 GMT; 3s ago
 Main PID: 1586 (a.out)
    Tasks: 1 (limit: 2200)
   Memory: 96.0K
   CGroup: /system.slice/programm.service
           └─1586 /home/ulllum17/programm/a.out

````
**Main PID: 1586 (a.out)** ==> PID = 1586

## SSH Schlüssel erstellen


