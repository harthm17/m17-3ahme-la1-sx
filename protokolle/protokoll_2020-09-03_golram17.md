# Protokoll 4 La1/SX 3AHME (2019/20)

-------------------------

* **Thema:** Erstellen und Starten von C -Programmen auf dem Raspberry PI
  * **Datum:** 09.03.2020
  * **Gefehlt:** Danko Sebastian
  * **Erstellt von:** Golser Raphael
  
  -------------------------------------------------------
  
## Inhaltsverzeichnis

1. [Kopieren von Daten vom Rapberry PI auf den Computer](#kopieren-von-daten-vom-raspberry-pi-auf-den-computer)
2. [Startup Systeme](#startup-systeme)
2. [systemctl](#systemctl)
3. [Automatisches Starten von C-Programmen](#automatisches-starten-von-c-programmen)
4. [Automatisches Starten von Java-Programmen](#automatisches-starten-von-java-programmen)

----------------------------------------------------------

# Kopieren von Daten vom Rapberry PI auf den Computer

Als aller erstes sind wir in das ````/tmp```` Verzeichnis gegangen, weil dort die Dateien täglich gelöscht werden und das in unserem Fall gut ist da nicht Speicher unnötig verbraucht wird.
````bash
  schueler@pcxx:~$ cd /tmp
  ````
Nun können wir mit dem Befehl ````rsync```` Daten vom Raspberry PI auf unseren Computer speichern:
````bash
  schueler@pcxx:~$ rsync -aP pi25:/home/golram17 ./
  ````
  mit dem Kommando ````-aP```` wird der Fortschritt vom Kopieren in Balken angezeigt. Der hintere Teil ````pi25:/home/golram17 ./```` sagt von wo ich die Daten die ich kopieren will her bekomme.
  Mit dem Kommando ````-aPn```` zeigt das Terminal nur die Daten an die mit dem ````rsync```` Befehl her kopiert werden würden. Doch will man diese kopierten Daten vom Computer löschen musss man nach dem ````-aP```` Kommando ein ````--delete```` Kommando anhängen.
  
  # Startup Systeme
  Laut: [LMS-Skriptum](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#155470713)
  > Mittlerweile sind drei unterschiedliche Systeme zu finden:
    Sys-V-Init
    Sys-V-Init ist das init-System des Unix-Betriebssystems System V. Die einzelnen Dienste werden hintereinander gestartet,      wodurch der Startup sehr überschaubar aber auch sehr langsam ist. Ein Nachbau wird in vielen Linux-Distributionen genutzt. So auch beim Debian System, also auch im Raspbian am Raspberry PI.
    Upstart
    Hier handelt es sich um ein Ubuntu-Projekt zur Beschleunigung des Systemstarts. Es verfügt über die Möglichkeit Prozesse mittels Events parallel zu starten. Upstart arbeitet nach dem Prinzip "greedy event-based". Alle Dienste die ein Start-Event erhalten werden so schnell wie möglich gestartet.
    Upstart kommt bis Ubuntu 14.10 zu Einsatz und eine Weiterentwicklung wurde eingestellt.
    systemd
    In Konkurrenz zu Upstart entstand systemd. Nachdem Debian auf systemd gewechselt hat, ist auch Ubuntu ab Version 15.10 auf systemd gewechselt. systemd arbeitet nach dem Prinzip "lazy dependency-based", das heisst, eine "Unit" wird nur dann gestartet wenn eine andere "Unit" davon abhängt.
    Aufgrund dieser historischen Entwicklung sind in einem Ubuntu 15.04 System alle drei Init-Systeme parallel im Einsatz. Langfristig wird ein Wechsel zu systemd erfolgen.
   
   Siehe auch: [wiki.ubuntuusers](https://wiki.ubuntuusers.de/Dienste/)
  
