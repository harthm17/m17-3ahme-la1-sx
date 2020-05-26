# Protokoll 6 Labor-SX 2020
--------------------------------
## GUI-Applikation / Debian Paket erzeugen
* **Datum:** 25.05.2020
* **Fehlend:** --
* **Erstellt von:** Resch Paul
* **Übungsort:** Wegen Corona im Home-Office
---------------------------------
### Inhaltsangabe
* [Unterhaltung](#unterhaltung)
* [Java GUI-App](#java-gui-applikation)
    * [Zusammenfassung](#zusammenfassung)
* [Dabian Paket](#debian-paket-erzeugen)

--------------------------------------------------
-------------------------------------------------------


### Unterhaltung

Gleich am Anfang der Laboreinheit wurde ich auf Discord in den Sprachkanal "SX" gebeten. Dort wurden dann gemeinsam mit Herrn Steiner Probleme der vorigen AIIT Stunde besprochen und anschließend auch gelöst. 

------------------------------
### Java GUI-Applikation

Um die anschließdende Übung überhaupt durchführen zu können, sollten wir zuerst mit Hilfe eines Videos eine GUI-Applikation erstellen. Allgemeine Informationen zu GUI auf [Wikipedia](https://en.wikipedia.org/wiki/Graphical_user_interface).

#### Zusammenfassung

* Mit NetBeans 11.3 haben wir zunächst ein Javaprojekt erzeugt (Kategorie: Java with Ant | Projekt: Java Application). Man muss keine Hauptklasse erzeugen
* Paket erstellen (Paketname immer klein)
* Java Klasse *JFrame Form* erzeugen (Java Swing GUI Form für GUI-Apps)
* Zwei Arten der Bearbeitung
    * *Source* für den Quelltext
    * *Design* um verscheidene Elemente im dargestellten Fenster abzulegen
* Layout einstellen 
    * Im *[Jframe]-Navigator* (linkes untere Fenster)
    * Rechtsklick auf den Punkt *[JFrame]*
    * *Set Layout* wählen und *Flow Layout* auswählen
    * Layouts bestimmen wie sich Dinge am Bildschirm verhalten
* Button einfügen
    * Am leichtesten ist es den *Button* im rechten oberen Fenster in den markierten Bereich zu ziehen
* Button beschreiben/benennen
    * Im *Navigator* Fenster rechtsklick auf den Button
    * *Edit Text* wählen
    * Im *Navigator* Fenster den Button anklicken und *F2* drücken
* Auf die Kategorie *Source* wechseln
* In der *public MainGui ()* folgendes schreiben
* Um dem Button einen Titel zu geben -> *setTitle("......");
* Um die Positionierung zu bestimmen -> *setLocationrelativeTo(null);* 
* *null* um den Button auf der Mitte des Bildschirmes anzuzeigen
* Um die größe des Buttons zu bestimmen -> *setMinimumSize(300, 200);*

Nun ist das Programm Theoretisch lauffähig. Da es aber noch keine *Handler Methode* gibt passiert aber noch nichts. Diese Methode reagiert dann auf die betätigung des Buttons. Um eine solche Methode zuerstellen folgendes tun:

* Auf die Kategorie *Design* wechseln
* *Doppelklick* auf den *Button*
*  Es wird Automatisch die Methode erstellt
*  Um ein Meldungsfenster zu erzeugen
    * *JOptionPane.showMessageDialog(rootPane, evt, title, .....);* aufrufen
    * statt *rootPane* **this** eintragen
    * statt *evt* zB. **"Button wurde gedrückt"** eingeben
    * statt *title* zb. **"Nachricht...."**  eingeben
    * dann (nach *title*) noch *JOptionPane.INFORMATION_MESSAGE* eintragen

Nun ist das Programm fertig und von der Konsole aus zu starten. Das Kommando hierzu ist: *java -jar VERZEICHNISS*
Das heist in unserem Fall: *java -jar NetBeansProjects/MyJavaGuiApp/dist/MyJavaGuiApp.jar*

----------------------------------------------
### Debian Paket erzeugen

Laut Wikipedia:

> [Debian-Pakete](https://de.wikipedia.org/wiki/Debian-Paket) (Dateiendung: .deb) dienen der Softwareinstallation auf Debian-basierten Betriebssystemen. Sie enthalten die zu installierenden Programme in komprimierter Form.

Für die Übung sollten wir uns genau an [diese](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#473068402) Angabe halten.
Ich habe es in der Unterrichtseinheit bis einschließlich Punkt 6 geschafft.

1. Java Programm erstellen ([hier](#java-gui-applikation) beschrieben)

1. Debian Paketverzeichnis erstellen
    * Mit dem Kommando *mkdir respam17-guiapp_1.0~1_all*
    > Die **Version 1.0~1 des Pakets**. 1.0 steht für die Version des Programmes und ~1 für die Unterversion des Pakets. 
    > Die unterstützte Architektur (all, amd64, i386, armhf, ...). **all** steht dabei für eine Unterstützung aller Architekturen.
    * anschließend mit *cd respam17-guiapp_1.0~1_all* auf dieses Verzeichnis wechseln

1. DEBIAN/control
    * Mit dem Kommando *mkdir DEBIAN* ein neues Verzeichnis anlegen
    * Mit *cd DEBIAN* auf das Verzeichnis wechseln
    * *nano control* eingeben und diese Datei laut [Angabe](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#473068402) befüllen

1. DEBIAN/postinst und DEBIAN/postrm
    * Mit *touch postinst* eine leere Datei anlegen
    * Mit *chmod +x postinst* Rechte erweitern
    * *nano postinst*
    * Datei wieder laut [Angabe](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#473068402) befüllen
    * Schritte wiederholen für *postrm*
    
1. Java Programm einfügen
    * Neues Verzeichniss anlegen
    * Hierfür erstmal *cd ..* eingeben
    * Dann mit *mkdir -p usr/share/sx-guiapp* das Verzeichnis anlegen
    > Die Option -p ermöglicht, dass gleich mehrere Verzeichnisse auf einmal erzeugt werden.
    * Mit *cp ~/NetBeansProjects/MyJavaGuiApp/dist/*.jar usr/share/respam17-guiapp/* das Programm ins neue Verzeichnis kopieren
    * Um es auch als GUI-App ausführen zu können, muss ein weiteres Verzeichniss angelegt werden in dem eine *.desktop* datei liegt
    * *mkdir usr/share/applications*
    * *nano respam17-guiapp.desktop* laut [Angabe](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#473068402) befüllen
    
1. Paketdokumentation
    * Weiteres Verzeichnis mit *mkdir -p usr/share/doc/sx-guiapp* anlegen
    * Zwei leere Dateien anlegen
    * *touch usr/share/doc/sx-guiapp/changelog* und *touch usr/share/doc/sx-guiapp/copyright*
    * Beide Dateien jeweils wieder laut [Angabe](https://lms.at/dotlrn/classes/informatik/610437.3AHME_LA1SX.19_20/xolrn/9F2714A93B69A.symlink?resource_id=0-420357452&m=view#473068402) befüllen (*nano changelog* und *nano copyright*)

------------------------------------------------

Ende der Unterrichtseinheit. Abgabe einer [tar.gz Datei](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/respam17/protokoll/protokoll-5_respam17_2020-05-18.md#targz-datei).

Widerholung:
* *sudo -i* um in den *Superuser* modus zu kommen 
* *tar -czf /tmp/archive2.tar.gz /root/.bash_history /home/paul4/.bash_history /home/paul4/NetBeansProjects /home/paul4/respam17-guiapp_1.0~1_all* um Dateien in *archive2* zu speichern
* *tar -tzf /tmp/archive2.tar.gz* zur Überprüfung ob alle Dateien vorhanden sind
