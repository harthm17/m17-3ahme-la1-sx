# Laborprotokoll 25.05.2020 Pfanner


* **Thema:** Debian-Paket analysieren und entpacken
* **Datum:** 25.05.2020
* **Gefehlt:** -
* **Erstellt von:** Pfanner Jan

## Inhaltsverzeichnis
* [Erstellen des Debian-Paketes](#erstellen-des-debian-paketes)
* [Paket analysieren](#paket-analysieren)
* [Paket entpacken](#paket-entpacken)

## Erstellen des Debian-Paketes
Als Voraussetzung für die Laborübung gilt die absolvierte Arbeit der letzten Einheit, will heißen, ein funktionierendes Debian-Paket. Die dazu notwendigen Schritte finden sich im [letzten Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/pfajam17/protokolle/protokoll-4_pfajam17_2020-05-18.md). 

## Paket analysieren
Alle `hervorgehobenen` Stellen in diesem Absatz beziehen sich auf Befehle, die in der Ubuntu-Shell (Terminal) auszuführen sind.

Befehle des Typ `dpkg` dienen zur Verwaltung von Debian-Paketen. Dpkg besitzt ein frontend namens aptitude, kann aber auch rein über das Terminal bedient werden. In dpkg-commands wird stets nur eine Aktion ausgeführt, mit 0 oder mehr Parametern. Ausgeschriebene Befehle, z.B. `dpkg --install <filename>` haben zwei vorangestellte Bindestriche, die Kurzversion des selben Befehls `dpkg -i <filename>` kommt mit einem aus.

Der Befehl `dpkg --list | grep pfajam-appgui` liefert folgende Ausgabe:
```console
jan@jan-VirtualBox:~$ dpkg --list | grep guiapp
ii  pfajam17-guiapp                            1.0                                        all          My first Java GUI Application
```
Dies beweist, dass das Paket installiert ist. --list gibt Pakete mit gesuchten Zeichenfolgen aus, der grep-Befehl sucht in Dateien nach Zeichenfolgen. Oben wurde *guiapp* im filename erkannt.

Befehle, die mit `apt` beginnen, gehören zum apt-command-interface, das ebenfalls der Paketverwaltung dient. Mit `apt show pfajam17-guiapp` (kann mit tab eingefügt werden) wird Information über das Paket pfajam17-guiapp ausgegeben:
```console
jan@jan-VirtualBox:~$ apt show pfajam17-guiapp 
Package: pfajam17-guiapp
Version: 1.0
Status: install ok installed
Maintainer: Jan Pfanner
Installed-Size: 49,2 kB
Depends: default-jre (>= 2:1.11)
Download-Size: unknown
APT-Manual-Installed: yes
APT-Sources: /var/lib/dpkg/status
Description: My first Java GUI Application
```
Die installed size entspricht hierbei nicht genau dem von mir in der control-Datei angegebenen Wert von 48 KiB, da sie hier in kB angegeben wird (48*1,024 = 49,152 ≈ 49 kB).

Der Befehl `apt depends pfajam17-guiapp` gibt die Abhängigkeiten des Paketes wieder. Da es ein Java-Programm ausführt, muss es von einem Java Runtime Environment abhängen. 
```console
jan@jan-VirtualBox:~$ apt depends pfajam17-guiapp 
pfajam17-guiapp
  Depends: default-jre (>= 2:1.11)
```
Siehe da, die Abhängigkeit ist vorhanden. Die Rückwärtsabhängigkeit der JRE lässt sich mit `apt rdepends default-jre` einsehen. Dies gibt eine lange Liste von Java-abhängigen Prozessen aus, ganz zuoberst:
```console
an@jan-VirtualBox:~$ apt rdepends default-jre
default-jre
Reverse Depends:
  Depends: pfajam17-guiapp (>= 2:1.11)
```

`apt policy pfajam17-guiapp` gibt die Versionsinformation und den Herkunftsort des Paketes an:
```console
jan@jan-VirtualBox:~$ apt policy pfajam17-guiapp 
pfajam17-guiapp:
  Installed: 1.0
  Candidate: 1.0
  Version table:
 *** 1.0 100
        100 /var/lib/dpkg/status
```
Wenig spannend, da es nur eine Version von pfajam17-guiapp gibt. Mit `apt policy default-jre` kann man dieselbe Information des JRE einsehen:
```console
jan@jan-VirtualBox:~$ apt policy default-jre
default-jre:
  Installed: 2:1.11-72
  Candidate: 2:1.11-72
  Version table:
 *** 2:1.11-72 500
        500 http://www.htl-mechatronik.at/ubuntu focal/main amd64 Packages
        100 /var/lib/dpkg/status
```

## Paket entpacken
Wie bereits erwähnt, dient `dpkg` der Arbeit mit Debian-Paketen. Auch entpacken kann man sie damit, und zwar so:

Im superuser-Modus (`sudo -i`) erst überprüfen, ob das installierte Verzeichnis bereits vorhanden ist: `ls -l *.deb`. Der ls-Befehl gibt Verzeichnisinhalte wieder, der Parameter `-l` bestimmt bloß das Ausgabeformat und `*.deb` bedeutet, alle Debian-Dateien auszugeben.
```console
root@jan-VirtualBox:~# ls -l *.deb
-rw-r--r-- 1 root root 67137920 Apr 25 05:30 google-chrome-stable_current_amd64.deb
-rw-r--r-- 1 root root     6452 Mai 18 16:01 pfajam17-guiapp_1.0~1_all.deb
```
Wie man sieht, ist pfajam17-guiapp schon vorhanden. Mit `rm -rf pfajam17-guiapp_1.0~1_all` entfernt man das Verzeichnis und alle Unterverzeichnisse. Da jetzt alles weg ist, das Verzeichnis neu anlegen mit `mkdir pfajam17-guiapp_1.0~1_all` und anwählen mit `cd pfajam17-guiapp_1.0~1_all`. 

Zum Entpacken der Dateien dient jetzt `dpkg` mit den beiden Optionen `-x` zum Entpacken der Dateien und `-e` für die Steuerdateien.
Die Befehle `dpkg -e ../pfajam17-guiapp_1.0~1_all.deb` und `dpkg -x ../pfajam17-guiapp_1.0~1_all.deb ./` entpacken alle nötigen Dateien an ihre Positionen. 

Sieht man sich nun das Verzeichnis mit `ls -lR` an, sollte alles da sein:
```console
root@jan-VirtualBox:~/pfajam17-guiapp_1.0~1_all# ls -lR
.:
total 12
drwxr-xr-x 2 root root 4096 Mai 18 15:43 DEBIAN
-rw-rw-r-- 1 root root  341 Mai 18 15:34 pfajam17-guiapp.desktop
drwxrwxr-x 3 root root 4096 Mai 18 15:30 usr

./DEBIAN:
total 12
-rw-r--r-- 1 root root 174 Mai 18 15:43 control
-rwxr-xr-x 1 root root 105 Mai 18 15:26 postinst
-rwxr-xr-x 1 root root 105 Mai 18 15:28 postrm

./usr:
total 4
drwxrwxr-x 5 root root 4096 Mai 18 15:38 share

./usr/share:
total 12
drwxrwxr-x 2 root root 4096 Mai 18 15:33 applications
drwxrwxr-x 3 root root 4096 Mai 18 15:38 doc
drwxrwxr-x 2 root root 4096 Mai 18 15:37 pfajam17-guiapp

./usr/share/applications:
total 0

./usr/share/doc:
total 4
drwxrwxr-x 2 root root 4096 Mai 18 15:41 pfajam17-guiapp

./usr/share/doc/pfajam17-guiapp:
total 8
-rw-rw-r-- 1 root root 105 Mai 18 15:40 changelog
-rw-rw-r-- 1 root root 347 Mai 18 15:41 copyright

./usr/share/pfajam17-guiapp:
total 16
-rw-rw-r-- 1 root root 5099 Mai 18 15:35 icon.png
-rw-rw-r-- 1 root root 5419 Mai 18 15:31 MyJavaGuiApp.jar
```

Damit ist das Paket sauber entpackt.
