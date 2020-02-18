# 5. Protokoll | AHME17 
# Uller Lucas
-------------------------------------------------------------------------
* **Thema:** Raspberry PI, SSH-Verbindungen
* **Datum:** 03.02.2020
* **Gefehlt:** ---
* **Erstellt von:** ulllum17
* **Protokoll letzte Einheit:** [4.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ulllum17/ulllum17/protokolle/protokoll-4_2020_01_27_ulllum17.md)
* **Protokoll nächste Einheit:*** [6.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/ulllum17/ulllum17/protokolle/protokoll-6_2020-02-10_ulllum17.md)
--------------------------------------------------------------------------
## Inhaltsverzeichnis

1. [Autostart](#autostart)   
1. [Logrotate](#logrotate)   
    1. [Logrotate erstellen](#logrotate-erstellen)
1. [Programm als System Account laufen](#programm-als-system-account-laufen)
1. [SSH Schlüssel](#ssh-schlüssel)
    1. [Schlüssel erzeugen](#schlüssel-erzeugen)
    1. [Schlüssel kopieren](#schlüssel-kopieren)
1. [Programm installieren](#programm-installieren)

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

## Programm als System Account laufen

1. System Account anlegen 
````bash
adduser --disabled-password --no-create-home --system programm
````
2. In der Service Datei den *System Account* hinzufügen.

````bash
nano /etc/systemd/system/programm.service
````
Hinzuzufügen ist **User=programm**.    
Die Service Datei sieht danach wie folgt aus. 

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

Mit dem Tool *Top*

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

## SSH Schlüssel

![ssh_verbindung](https://user-images.githubusercontent.com/55395678/74107695-10005180-4b73-11ea-86e9-6675ade9e493.png)



Es gibt ein Asymetrisches Schlüsselpaar
* Öffentlicher Schlüssel
* Privater Schlüssel

### Schlüssel erzeugen
Auf dem PC muss unter Linux Folgender Befehl ausgeführt werden um ein Schlüsselpaar zuerzeugen.

````bash
ssh-keygen
````

Unter windows wird ein Zusatzprogramm benötigt Putty und Puttygen, um eine Schlüsselpaar zu erzeugen


### Schlüssel kopieren

Mit Folgendem Befehl kann der öffentliche Schlüssel automatisch auf dem PI kopiert werden.

````bash
ssh-copy-id ulllum17@10.200.114.226
````

oder man fügt den Schlüssel manuel hinzu.

````bash
sudo nano .ssh/authorized_keys
````
und kopiert den Schlüssel hinein.

## Programm installieren
APT(Advanced Packaging Tool) ist ein Paketmanagement-System, das im Bereich des Betriebssystems Debian GNU/Linux entstanden ist. Mittels APT ist es sehr einfach, Programmpakete zu suchen, zu installieren oder auch das ganze System auf den neuesten Stand zu bringen.
````bash
apt uptdate
apt install <Programm_name>
````
Mehr Informationen auf [Ubuntuusers](https://wiki.ubuntuusers.de/APT/)
