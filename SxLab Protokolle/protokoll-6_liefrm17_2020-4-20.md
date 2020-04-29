# Protokoll LAB/Sx 3.AHME (2020)

* **Thema:** Debian Paket erzeugen
* **Datum:** 27.04.2020
* **Gefehlt:** -
* **Esrtellt von:** Franz Lieleg (liefrm)
* **Protokoll der letzten Einheit:**![5tes Protokol](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/edit/liefrm17/SxLab%20Protokolle/protokoll-5_liefrm17_2020-4-20.md)
* **Protokoll der nächsten Einheit:** -

----------------------------------------------------------------------------------------------------------------------------------
## Inhaltsverzeichnis 

1) [Aufgabenstellung](#aufgabenstellung)
1) [Theorie](#theorie)
1) [Übung 1: Debian Paket erzeugen](#übung-1-debian-paket-erzeugen)
    * [Java Programm erstellen](#java-programm-erstellen)
    * [Debian Paketverzeichnis erstellen](#debian-paketverzeichnis-erstellen)
    * [Datei DEBIAN/control](#datei-debian-control)
1) [Resümee](#resümee)

--------------------------------------------------------------------------------------------------------------------------------------
## Aufgabenstellung

Die Aufgaben die in der 6ten Einheit (27.04.2020) zu erledigen waren:

   * **Auf Lms (Lab Kurs Sx),E-book: Linux-2, Kapitel 3 und 3.1 studieren**
   * **Übung 1 (Kapitel 3.2) erledigen**
   * **Übung 2 (Kapitel 3.3) erledigen**

------------------------------------------------------------------------------------------------------------------------------------
## Theorie

Um uns die Theorie anzueignen, die wir für die Übung 1: Debian Paket erzeugen (im Kapitel 3.2) brauchen, besteht der erste Arbeitsschritt im Durchlesen der Kapitel (alle zu finden auf Lms (Lab Kurs Sx),im E-Book: Linux-2): 

   * **[3 Installationspakete](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#472857424)**
   * **[3.1 Tools und Konfigurationsdateien](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#472937916)**
   
Kapitel 3: Im Kapitel 3 (Installationspakete) werden die Techniken aufgelistet/angeführt, die in Debian- und Ubuntu Systemen (und Subsystemen) verwendeten werden, um Software zu installieren.

-------------------------------------------------------------------------------------------------------------------------------------
## Übung 1: Debian Paket erzeugen

Link zur kompletten Anleitung der Übung: [Übung 1 (Kapitel 3.2)](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#473068402)

**Allgemeine Beschreibung der Aufgabe:** In dieser Übung soll ein Java GUI-Programm als Debian Installationsdatei zur Verfügung gestellt werden.

**Wichtig:** Durch Missgeschicke in der Übung können fehlerhafte Pakete entstehen, dies führt dazu, dass reguläre Pakete nicht mehr installiert oder aktualiesiert werden können. Dies hat grobe Auswirkungen auf das System, es wird untauglich/nutzlos. Um solche Komplikationen zu vermeiden führen wir die Übung in einer sicheren Umgebung durch (virtuelle Maschine-Ubuntu)! 

### Java Programm erstellen

Um ein Java Swing GUI Programm erstellen zu können, arbeiten wir in Netbeans (bereits durch das Herunterladen HTL-Paketen enthalten).

**Tipp:** Durch das Aktualiseren (angeführt im 5ten Protokoll) der HTL-Pakete, steht uns die neueste Version Netbeans zur Verfügung.

Folgende Schritte werden zur Erstellung des Swing GUI Programmes benötigt:

1) Java Projekt erzeugen
1) Java Paket gui erzeugen
1) Java Klasse abgeleitet von JFrame erzeugen (Netbeans JFrame Form ...)
1) Titel und Mindestgröße konfigurieren, Fenster in der Bildschirmmitte öffnen lassen
1) "Flow Layout" setzen
1) Einen Button "Press me..." einfügen
1) In der Button-Handler-Methode ein Dialogfenster öffnen und einen Text ausgegeben
1) Das Projekt ausführen und testen
1) Das Projekt mit "Clean und Build" übersetzen
1) Aus dem Ordner dist die fertige Java Archiv Datei entnehmen

**Tipp:** Ein uns bereit gestelltes Video erleichtet die Erstellung: https://cloud.htl-mechatronik.at/index.php/s/AlyXs7YglQDLZSP

----------------------------------------------------------------------------------------------------------------------------------------
### Debian Paketverzeichnis erstellen

Mit den darunter angeführten Befehlen wir ein Unterordner für das zu erstellende Debianpaket erstellt:

```
user@host:~$ mkdir sx-guiapp_1.0~1_all
user@host:~$ cd sx-guiapp_1.0~1_all
user@host:~/sx-guiapp_1.0~1_all$ 
```

**Wichtig:** Der Kürzel "sx" wird durch den eigenen Kursnamen ersetzt!

Der Verzeichnisname enthält drei Auskünfte die durch ```_``` getrennt sind:
   * **Paketname**
   * **Version des Paketes**
   * **Unterstützte Architektur**

Genaueres zu "Debian Paketverzeichnis erstellen" ist im Kapitel [3.2 (Übung 1 - Debian Paket erzeugen)](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#473068402) 
zu entnehmen.

---------------------------------------------------------------------------------------------------------------------------------
### Datei DEBIAN/control

Mit den darunter angeführten Befehlen wir ein Unterordner für **Debian** erstellt.

**Wichtig:** In diesem Unterordner muss sich die Datei **control** befinden!

```
user@host:~/sx-guiapp_1.0~1_all$ mkdir DEBIAN
user@host:~/sx-guiapp_1.0~1_all$ cd DEBIAN
user@host:~/sx-guiapp_1.0~1_all/DEBIAN$ nano control
```

Die Steuerdatei **control** muss folgendes Enthalten (zugriff mit ```nano``` auf Editor von control):

```
Package: sx-guiapp
Architecture: all
Depends: default-jre (>=2:1.11)
Installed-Size: 1000
Maintainer: Manfred Steiner <sx@htl-kaindorf.ac.at>
Description: My first Java GUI Application
```



