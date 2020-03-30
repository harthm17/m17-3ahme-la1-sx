# Protokoll-4 LABOR/SX 3AHME (2019/20)

* **Thema:** Dienste
* **Datum:** 30.03.2020
* **Gefehlt:** Keiner
* **Erstellt von:** koganm17
* **Protokoll letzte Einheit:** [23.03.2020](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/koganm17/Protokolle/Protokoll-3_koganm17_2020-03-30.md)

----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis
1) [Vorraussetzungen](#vorraussetzungen)
1) [Unterlagen](#unterlagen)
1) [Dämon in Linux-Systemen und Java](#dämon-in-linux-systemen-und-java)
1) [Uebung1: Systemdienst mit syslog-Ausgabe](#systemdienst-mit-syslog-ausgabe)  
          [Programm übersetzen](programm-übersetzen)  
          [Programm testen](programm-testen)  
          [Weitere Punkte](weitere-punkte)  
         
----------------------------------------------------------------------------------------------
## Vorraussetzungen

* Linux Grundkenntnisse ([e-Book LMS Bibliothek / Linux-1](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/7BF1B31508DF3.symlink?resource_id=0-385942208&m=view#150960483))
* Ubuntu 18.04 System native oder via Virtualisierung (zB Virtualbox)

----------------------------------------------------------------------------------------------
## Unterlagen

Diese Unterlagen müssen wir durcharbeiten. Durcharbeiten heißt lesen, verstehen und teilweise nach recherchieren.
* [LMS e-book Bibliothek / Linux-2 / Kapitel 1, 1.1, 1.3
](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#155470713)
* https://wiki.ubuntuusers.de/systemd/

----------------------------------------------------------------------------------------------
## Dämon in Linux-Systemen und Java

Eigendefinition: Ein Dämon ist ein Hintergrundprogramm, dass bestimmte Dienste zur Verfügung stellt.

laut [wikipedia](https://de.wikipedia.org/wiki/Daemon)
>Als Daemon [ˈdiːmən] oder Dämon (auch häufig in der Schreibweise Demon) bezeichnet man unter Unix oder unixartigen Systemen ein Programm, das im Hintergrund abläuft und bestimmte Dienste zur Verfügung stellt. Benutzerinteraktionen finden hierbei nur auf indirektem Weg statt, zum Beispiel über Signale, Pipes und vor allem (Netzwerk-)Sockets. Der Begriff Daemon wird auch als Abkürzung von disk and execution monitor interpretiert, was jedoch ein Backronym ist.

----------------------------------------------------------------------------------------------
## Systemdienst mit syslog-Ausgabe
In dieser Uebung sollen wir einen Dienst mit Hilfe der Programmiersprache C erstellen.
Der Dienst soll im Hintergrund laufen und viermal einen Text im Abstand von zwei Sekunden schreiben.

[Hier](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#155470740) ist die Datei nach der wir vorgegangen sind.
### Programm übersetzen
In diesem Punkt übersetzen wir das vorgefertigte C-Programm mit dem Gnu gcc Compiler. 

verwendete Befehle:
```
1. mkdir mydaemon
1. cd mydaemon
1. nano mydaemon.c
1. gcc -o mydaemon mydaemon.c
1. ls -l
```
### Programm testen

In diesem Punkt starten wir das Programm in der Shell mit
``` ./mydaemon ```
 
Danach können wir uns in neuen seperaten Shells mit Hilfe von folgenden Befehlen die Ausgaben im Log oder im journald anzeigen lassen.
```
1. journalctl -f
1. journalctl -f -p 4
1. journalctl -f -v verbose
1. tail -f /var/log/syslog
```

### weitere Punkte

Die nächsten Punkte sind systemd Service erstellen, Service starten, stoppen und beobachten und Autostart.  
Ich bin leider nur bis zum Punkt systemd Service erstellen gekommen, da es dort ein Problem gab.  
Das Problem war, dass ich keinen Link erstellen konnte, weil er laut Fehlermeldung schon erstellt war und beim nächsten Punkt konnte ich keinen Dienst starten, da kein Link vorhanden war. Ich habe über eine halbe Stunde in die Fehlerbehebung investiert und das leider zu unnütz. Ich habe Hilfe von Herrn Augustin bekommen, aber auch er konnte mir nicht helfen. Wir versuchten diese Datei mit dem Link zu löschen und neu zu erstellen, aber das hat leider nicht funktioniert.

----------------------------------------------------------------------------------------------
