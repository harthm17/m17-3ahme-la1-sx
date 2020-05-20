# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Erstellung eines Debian Paketes
* **Datum:** 18.05.2020
* **Gefehlt:** -
* **Erstellt von:** Peyer Kassandra

----------------------------------------------------------------------------------------------
## Inhaltsverzeichnis

1. [Java GUI Applikation erstellen](#javaguiapplikationerstellen)
2. [Paket-, Debian-Verzeichnis und control Datei erstellen](#paket-,debian-verzeichnisundcontroldateierstellen)
3. [Erstellung der postinst und postrm Script-Dateien](#erstellungderpostinstundpostrmscript-dateien)
4. [Erstellung der Desktop-Datei](#erstellungderdesktop-datei)

----------------------------------------------------------------------------------------------
## Java GUI Applikation erstellen

Um einen Debian Paket zu erstellen, sollte man zu erst eine Applikation machen. Wir benutzen in unserem Fall Java und erstellen ein JFrame Form. 
Im Navigator ändern wir das Layout von JFrame zu einem Flow Layout. Unter Design fügen wir zu erst einen Button ein und ändern den Text darauf zu
"Press me...". Den Variablen Namen ändern wir auch noch zu jbutPressMe. Im Source Code geben wir unter MainGui mit ```setTitle("")``` einen Titel, mit 
```setLocationRelativeTo()``` wo der Button sein soll (wenn null in der Klammer steht ist er immer in der Mitte) und mit setMinimumSize() geben wir die 
mindest-Größe für das Fenster ein. Damit der Button beim gedrückt werden auch eine Aktion ausführt muss man zu erst im Design den Knopf doppelklicken 
und dann wird man zu einer neuen Methode im Source Code gebracht. Mit dem Befehl ```JOptionPane.showMessageDialog(this, "*ausgebende Nachricht*", "*Name der Titel Leiste*", JOptionPane.INFORMATION_MESSAGE)``` 
wird beim betätigen des Buttons eine Nachricht in einem eigenen Fenster ausgegeben. Wichtig ist jetzt noch das Projekt zu Clean und Build'en, damit 
das Java Archiv komplett und verwendbar ist. 

## Paket-, Debian-Verzeichnis und control Datei erstellen

Nun erstellt man via der shell einen Ordner in seinem persönlichen Ordner. In unserem Fall heißt der Ordner ```*htl-kürzel*-guiapp_1.0~1_all```. 
Dieser Name verrät uns schon welche Version das Paket hat (1.0~1) und welche Architektur es unterstützt (nämlich all). Man wechselt auch gleich zu 
diesen Ordner und erstellt in diesem einen weiteren Ordner namens **DEBIAN**, zu dem man auch sofort wechselt. In diesem Ordner erstellt und bearbeitet 
man sofort die Datei **control** via ```nano```. In dieser Datei schreibt man nun folgendes:

```
Package: *htl-kürzel*-guiapp
Version: [1.0:]~1
Architecture: all
Depends: default-jre (>=2:1.11)
Installed-Size: 1000
Maintainer: *Name* <*E-Mail*>
Description: *Beschreibung*
```

Mit **depends** wird festgelegt was braucht um zu funktionieren. Hier ist die Standard Java Runtime Enviorment, welche Java 11 oder höher 
sein muss hinterlegt. 

## Erstellung der postinst und postrm Script-Dateien

Zur Demonstration erstellen wir noch zwei Script-Dateien. postinst wird nach der Installation und postrm nach der Deinstallation ausgeführt. 
Man realisiert die zwei Dateien mit dem Befehl ```touch``` im Ordner DEBIAN und gibt beiden mit ```chmod +x``` Ausführ-Rechte. Nun schreibt man 
via ```nano``` folgende Dinge:

Für postinst:
```
#!/bin/sh
#set -e
#set -x

printf '%b' "\033[32;1m [INFO] sx-guiapp (postinst) -> $0 $1 \033[0m\n"
```

Für postrm:
```
#!/bin/sh
#set -e
#set -x

printf '%b' "\033[32;1m [INFO] sx-guiapp (postrm) -> $0 $1 \033[0m\n"
```

Bei postinst wird nach der Installation und bei postrm nach der Deinstallation eine Nachricht ausgegeben. 

## Erstellung der Desktop-Datei

Bevor man die Desktop-Datei erstellt sollte man im *htl-kürzel*-guiapp_1.0~1_all Ordner diesen Pfad erstellen usr/share/sx-guiapp und dort die Java Archiv Datei hineinkopieren. 
Man sollte noch einen Ordner im usr/share/ erstellen namens applications. Nun erstellen wir die Desktop Datei im aller ersten Ordner mit ```nano``` und nennt sie *htl-kürzel*-guiapp.desktop.
Man schreibt nun folgendes in diese Datei:

```
[Desktop Entry]
Name=*htl-kürzel*-java-application
GenericName=*Normaler Name*
GenericName[de]=*Normaler Name auf Deutsch*
Comment=*Kommentar/Beschreibung*
Exec=java -jar /usr/share/sx-guiapp/MyJavaApplication.jar
Icon=/usr/share/sx-guiapp/icon.png
Terminal=false
Type=Application
StartupNotify=false
```

Hier wird auch eine Datei namens icon.png beschreiben eine gleichnamige Bilddatei sollte sich im angegebenen Ordner befinden.

***Leider bin ich nicht weiter als das in der Labor Einheit gekommen***
