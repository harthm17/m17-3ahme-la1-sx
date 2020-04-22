# Protokoll LAB/Sx 3.AHME (2020)

* **Thema:** Erstellung eines Dienstes (Dämon), Abschluss 
* **Datum:** 20.04.2020
* **Gefehlt:** -
* **Esrtellt von:** Franz Lieleg (liefrm)
* **Protokoll der letzten Einheit:**![4tes Protokol](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/liefrm17/SxLab%20Protokolle/protokoll-4_liefrm17_2020-3-30.md)
* **Protokoll der nächsten Einheit:**

------------------------------------------------------------------------------------------------------------------------
## Inhaltsverzeichnis 

1) [Aufgabenstellung](#aufgabenstellung)
1) [Erledigte Unterpunkte der letzten Einheit](#erledigte-unterpunkte-der-letzten-einheit)
1) [Übung 1: Erstellen eines Dienstes, Abschluss:](#erstellen-eines-dienstes-abschluss)
    * [systemd Service erstellen](#systemd-service-erstellen)
    * [Service starten, stoppen und beobachten](#service-starten-stoppen-und-beobachten)

---------------------------------------------------------------------------------------------------------------------------
## Aufgabenstellung

Die Aufgaben die in der 5ten Einheit (20.04.2020) zu erledigen waren:

   * **Ubuntu Software update**
   * **Fertigstellung des letzten Arbeitsauftrages (30.03.2020: [Erstellung eines Dienstes (Dämon)](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/liefrm17/SxLab%20Protokolle/protokoll-4_liefrm17_2020-3-30.md))**
   * **Linux Scripting (Auf LMS im E-Book [Linux-Teil 2](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#155470740))**

Wichtig war es, die Aufgabe der 4ten Einheit zu vollenden **(Erstellung eines Dienstes (Dämon))!**

Danach das Beginnen der nächsten Aufgabe, "Linux Scripting"! Mir blieb nicht genügend Zeit um mit dieser Tätigkeit zu starten.

------------------------------------------------------------------------------------------------------------------------------------
## Erledigte Unterpunkte der letzten Einheit

   * **C-Programm**
   * **Programm übersetzen**
   * **Programm testen**

Genuaeres ist im 4ten Protokoll nachzulesen, [Erstellung eines Dienstes (Dämon)](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/liefrm17/SxLab%20Protokolle/protokoll-4_liefrm17_2020-3-30.md)

-------------------------------------------------------------------------------------------------------------------------------------
## Übung 1: Erstellen eines Dienstes, Abschluss:

### systemd Service erstellen

**Erster Schritt: Das Erstellen der Datei mydaemon.service!** 

Dann mit dem Befehl ```nano``` in den Texteditor wechseln. Folgender Text muss manuell geschrieben, oder hineinkopiert werden. Wichtig dabei ist, dass der Text keinen Schreibfehler jeglicher Art enhalten darf, sonst funktioniert es nicht.

```
[Unit]
Description=my background program for testing system services

[Service]
ExecStart=/home/user/mydaemon/mydaemon
IgnoreSIGPIPE=false
KillMode=process
```

**Nächster Schritt: In /etc/systemd/system einen Link auf die Servic Datei erstellen!**

```
franz@franz-VirtualBox: ~/mydaemon$ sudo -i
root@franz-VirtualBox: ~# cd /etc/systemd/system
root@franz-VirtualBox: /etc/systemd/system# ln -s /home/franz/mydaemon/mydaemon
root@franz-VirtualBox: /etc/systemd/system# ls -l
...
lrwxrwxrwx 1 root root   20 Apr 30 14:40  mydaemon.service -> /home/franz/mydaemon/mydaemon.service
...
root@franz-VirtualBox: /etc/systemd/system# exit

```
**Wichtig:** Beim Ausführen dieser Befehle, muss der "user", in meinem Fall franz, unbedingt auf eigenen User geändert werden!!!

Bedeutung der Befehle:

 `sudo -i` (In Super-User root wechseln) 
 
 `cd ` (in Verzeichnis wechseln )
 
 `ln -s` (Link erstellen) 
 
 `ls -l` (Line-Mode, Informationen Anzeigen)
 
 `exit` (Super-User root verlassen)
 
 Wenn alles funktioniert hat  dies folgendermaßen auszusehen:
 ![](https://cdn.discordapp.com/attachments/691664570208616518/702169798712229968/unknown.png)
 
Den Dienst dann abschließend mit diesm Befehl Starten:
```
user@pi: ~/mydaemon$ sudo systemctl start mydaemon
```
Den Dienst kann man in einer anderen Shell mit diesem Befehl bobachten:
```
franz@franz-VirtualBox:: ~/mydaemon$ sudo journalctl -f -u mydaemon
```
Nachfolgend den Dienst erneut starten!!!

**Wichtig:** Wenn Änderungen am Dienst in der Service-Dateivorgenommen werden, dann ist es Notwendig mit dem Befehl ```sudo systemctl daemon-reload``` eine Aktualisierung durchzuführen!!!

----------------------------------------------------------------------------------------------------------------------------------------
## Service starten, stoppen und beobachten

