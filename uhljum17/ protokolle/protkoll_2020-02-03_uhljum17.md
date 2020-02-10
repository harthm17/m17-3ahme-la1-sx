# 5. Protokoll

------------------------------

* **Thema:** Raspberry Pi
* **Datum:** 03.02.2020
* **Gefehlt:** -
* **Gruppe:** 4
* **Protkollverfasser:** Uhl Julian
* **Letztes Protokoll:** [4. Protokol](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/uhljum17/uhljum17/%20protokolle/protkoll_2020-01-27_uhljum17.md)
* **Nächstes Protkoll:**

-----------------------

# Inhaltsverzeichnis

1. [Prorgamm Status abfragen](Prorgamm-Status-abfragen)
2. [Autostart](Autostart)
3. [Logrotate](Logrotate) 
     1. [Logrotate erstellen](Logrotate-erstellen)        
     2. [System Account](System-Account)
     3. [Passwort](Passwort)

-----------------------

## Prorgamm Status abfragen

Um zu schauen ob das Programm läuft, erkennt man dann am grünen bzw. den weißen Punkt (grüm=läuft, weiß=läuft nicht).

        systemctl status programm
      
Programm starten

        systemctl start programm
      
Programm Stoppen

        systemctl stop programm
Mit ***journalctl -f -u programm*** kann man z.B. in einer zweiten Shell sehen was das programm macht. 

Mit ***tail -f /var/log/programm.log*** kann man sich die letzten Zeilen des Programmes anzeigen lassen.

-------------------------------

## Autostart

Mit ***stystemctl enable programm*** kann man über die Shell das programm Automatisch beim Hochfahren Starten lassen. Den Raspberry muss man danach ein mal aus und wieder einschalten. 

---------------------------------------------

## Logrotate

>logrotate ist dazu entworfen, die Verwaltung von Systemen zu vereinfachen, die eine große Anzahl von Log-Dateien generieren. Es erlaubt eine automatische Rotation, Kompression, Entfernung und Verschickung der Logdateien. Jede Logdatei kann täglich, wöchentlich, monatlich oder dann erfolgen, wenn sie zu groß geworden ist. 
Normalerweise wird logrotate als täglicher cron-job ausgeführt. Es bearbeitet eine Logdatei nicht mehr als einmal täglich, wenn das Kriterium für die Behandlung dieser Logdatei nicht seine Größe ist, logrotate mehr als einmal täglich aufgerufen wird oder die -f oder --force Option angegeben wurde. 
Auf der Kommandozeile können beliebig viele Konfigurationsdateien angegeben werden. Spätere Konfigurationsdateien können Optionen von früheren überschreiben, so daß es wichtig ist, auf die richtige Reihenfolge zu achten. Normalerweise sollte eine Konfigurationsdatei benutzt werden, die ihrerseits weitere solcher Dateien per include-Befehl einfügt. Weiter unten wird die Anwendung der include-Direktive genauer beschrieben. Wird auf der Kommandozeile ein Verzeichnis angegeben, so werden alle darin enthaltenen Dateien als Konfigurationsdateien abgearbeitet. 
Werden keine Kommandozeilenparameter angegeben, gibt logrotate einen kurzen Hilfstext und Versionsinformationen aus. Treten während der Rotation von Logdateien Fehler auf, so gibt logrotate einen Rückgabewert ungleich 0 zurück. 

[Quelle](http://www.linux-praxis.de/lpic1/manpages/logrotate.html)


Logrotate funktioniert folgender Maßen:

Es gibt in unseren Fall vier Datien:

    kern.log1.ggz
    kern.log2.ggz
    kern.log3.ggz
    kern.log4.ggz
Nach einer gewissen Zeit werden die Daten vom Ersten in Zweiten, vom Zweiten in Dritten usw. gespeichert bis die Datein erst nach dem Vierten gelöscht werden. 

Vorteil der Speicher wird nie voll.

### Logrotate erstellen

Der Logrotate ist im Verzeichnis ***/etc/logrotate.d/*** zu finden.

unser Logrotete:

     /var/log/programm.log {
      rotate 4
      weekly
      compress
      missingok
      notifempty
     }

### System Account

System Account ohne Homeverzeichnis erstellen:

        adduser --disabled password --system programm --no-create home

Benutzer unter dem der Service läuft:

        nano /etc/systemd/system/programm.service

Dann muss man unter [Service] User=Programm dazu schreiben.


          [Unit]
          Description=Labor Programm

          [Service]
          Type=simple
          ExecStart=/home/uhljum17/programm/a.out
          User=programm

          [Install]
          WantedBy=multi-user.target


        systemctl daemon-reload
        systemctl restart programm

Kontrollieren unter welchen Benutzer das Programm läuft

        ps -ef / grep <Nummer von systemctl status>

Bentzer wechsel:
        
        chown programm /var/log/programm.log

### Passwort

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

        ssh-copy-id uhljum17@10.200.114.227

        root@pi27:~# mkdir.ssh

                     chmod 700.ssh
        
                     cp /home/uhljum17/.ssh/authrized_keys.ssh/
        
        rsync root@10.200.114.227 /home/tmp

