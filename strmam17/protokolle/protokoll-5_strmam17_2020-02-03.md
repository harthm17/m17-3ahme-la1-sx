# Protokoll Labor 3AHME (2020-02-03)
* Thema: Autostart, Passwörter
* Datum: 03.02.2020
* Gefehlt: -
* Erstellt von: strmam17
* Protokoll letzte Einheit: [4.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/strmam17/strmam17/protokolle/protokoll-4_strmam17_2020-01-27.md)
* Protokoll nächste Einheit: [6.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/strmam17/strmam17/protokolle/protokoll-6_strmam17_2020-02-10.md)
--------------------------------------------------------------------------------
## Inhaltsverzeichnis
1. [Programm Status](#programm-status)
2. [Autostart](#autostart)
    * [Logrotate](#logrotate)
        * [Log-Datei erstellen](#log-datei-erstellen)
    * [System Account](#system-account) 
3. [Passwort](#passwort)
4. [Programm installieren](#programm-installieren)
--------------------------------------------------------------------------------
## Programm Status
Abfragen ob das Programm läuft oder nicht 

    systemctl status programm

Starten und Stoppen des Programmes

    systemctl start programm
    systemctl stop programm
    
Das folgende Kommando zeigt laufend an was das Programm tut:

    journalctl -f -u programm 
    
Mit dem folgenden Kommando werden dir die letzten paar Zeilen, was das Programm gemacht hat, angezeigt: 
    
    tail -f /var/log/programm.log

--------------------------------------------------------------------------------
## Autostart
Wenn man ein Gerät einschaltet möchte man dass sich das Programm von selber startet und nicht dass man es immer extra starten muss, deshalb gibt es den Autostart. Das heißt das Programm startet automatisch sobald man das Gerät einschaltet.

    systemctl enable programm

## Logrotate
Damit nicht sofort alles gelöscht wird was das Programm gemacht hat gibt es das Logrotate.

Es gibt eine eigentliche log datei: kern.log .

Nach einer gewissen Zeit speichert er die erste Datei in kern.log.1 und löscht kern.log, da da wieder die neuen sachen gespeichert werden.

Nach wieder einer gewissen Zeit speichert er die Datei kern.log.1 in kern.log.2 und diese wird dann komprimiert.

Das geht bis zur Datei kern.log.4 danach werden die Dateien gelöscht.

### Log-Datei erstellen 

Ins Verzeichnis wechseln:

    cd /etc/logrotate.d
    
Datei erstellen:

    nano programm
    
Deine Eigenschaften: 

    z.B.: /var/log/programm.log
          {
              rotate 4
              weekly
              missingok
              notifempty
          }
          

## System Account

System Account ohne Homeverzeichnis erstellen:

    adduser --disabled password --system programm --no-create home

Benutzer unter dem der Service läuft:

    nano /etc/systemd/system/programm.service
    
Dann muss man unter [Service] User=Programm dazu schreiben.

Dann sollte man es neustarten:

    systemctl daemon-reload
    systemctl restart programm
    
Kontrollieren unter welchen Benutzer das Programm läuft

    ps -ef / grep <Nummer von systemctl status>
    
Bentzer wechsel:
  
    chown programm /var/log/programm.log

-------------------------------------------------------------------------------
## Passwort
Damit man auch sicher arbeiten kann gibt es ein asymetrisches Schlüsselpaar: öffentlicher und privater Schlüssel.

Schlüsseldateien: 

    ll.ssh
    
Schlüsselpaar erstellen:

    ssh-keygen
    
Öffentlicher Schlüssel:

    cat .ssh/id-rsa.pub

Privater Schlüssel: 

    cat .ssh/id-rsa
    
Das Passwort auf den Raspberry bringen:

    ssh-copy-id strmam17@10.200.114.217
    
    root@pi17:~# mkdir.ssh
                 chmod 700.ssh
                 cp /home/strmam17/.ssh/authrized_keys.ssh/
    rsync root@10.200.114.217 /home/tmp

-------------------------------------------------------------------------------
## Programm installieren

Ein Programm auf dem Rasperry zu installieren geht so: 

    apt uptdate
    apt insatll <Dein zu installierentes Programm>
