# Protokoll LABOR/SX 3AHME (2019/20)

* **Thema:** Dateirechte
* **Datum:** 02.12.2019
* **Gefehlt:** Keiner
* **Erstellt von:** koganm17
* **Protokoll letzte Einheit:** [18.11.2019](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/koganm17/Protokolle/Protokoll1.md)

----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis

1. [Dateirechte grundlegend](#dateirechte-grundlegend)
1. [Rechtekommandos](#rechtekommandos)
2. [Benutzer anlegen](#benutzer-anlegen)


----------------------------------------------------------------------------------------------

### Dateirechte grundlegend

Rechte benötigt man, wenn man ein Multiusersystem hat.  
In der Shell, welche man mit Strg+Alt+T öffnet, kann man mit dem Befehl *ll* die Rechte aller Dateien und Verzeichnisse im aktuellen Verzeichnis ausgeben. Dieser Befehl ist ein Alias für *ls -alF*.

Die Rechte für eine Datei gibt man in 10 Zeichen an.

#### Typ
Das erste Zeichen steht für den typ der Datei. Dieser kann sein
* '-' für Dateien
* d für direchtories (Verzeichnisse)
* l, c oder b, was wir aber nicht besprochen haben

#### Benutzer
Die anderen neun Zeichen werden auf drei Arten von Benutzer aufgeteilt.
* Zeichen 2-4 für den Eigentümer ... u
* Zeichen 5-7 für die Gruppe ... g
* Zeichen 8-10 für alle anderen ... o

#### Rechte
Es gibt drei Arten von Rechten. 
* r ... read
* w ... write
* x ... execute

Bei Dateien:
* r entspricht lesen
* w entspricht ändern
* x entspricht ausführen (binäre Dateien, Skript)

Bei Verzeichnissen:
* r entspricht Inhalt lesen
* w entspricht Inhalt löschen, ändern
* x entspricht ins Verzeichnis wechseln

Wenn ein Benutzer das Recht besitzt, wird der Buchstabe des Rechtes geschrieben. Ansonsten ist ein Minus anstelle des Buchstabens.

#### Beispiel
```
drwxr-xr-x
```
Es handelt sich um ein Verzeichnis, indem der Eigentümer alle drei Rechte hat. Die Gruppe und alle anderen haben jeweils das read- und das execute-Recht.

----------------------------------------------------------------------------------------------

### Rechtekommandos
Wenn man die Rechte dazu hat kann man in der shell die Rechte anderer mit Hilfe von Befehlen verwalten.
```
chown(change owner) ... Datei //Eigentümer verändern
chown ...:... Datei //Eigentümer + Gruppe verändern
```
```
chgrp(change group) ... Datei //Gruppe ändern
```
```
chmod(Rechte ändern)
chmod ...g+x Datei //Gruppe darf nun ausführen
chmod ...o-rw Datei //Besitzer darf nun nicht mehr lesen und verändern
chmod 751 Datei //Rechte in Oktalzahlen: 111101001 = rwxr-x--x
```
----------------------------------------------------------------------------------------------

### Benutzer anlegen
Zuerst muss man zum Superuser werden. Der Superuser weiß, kann und darf alles.
```
sudo -i 
```
Mit dem Befehl *less /etc/passwd* lassen wir uns die Einträge über die Benutzer anzeigen.

Mit den folgenden Befehlen tragen wir uns in den folgenden Dateien nach dem Muster, das man bei den anderen Einträgen ablesen kann, ein.
```
nano/etc/passwd
nano/etc/group
nano/etc/shadow
nano /etc/home
```
Diese Vorgänge speichern wir immer mit Strg+O ab und beenden sie mit Strg+X.

Danach kann man mit dem Befehl *id Benutzerkürzel* Daten über den angelegten Benutzer ausgeben.  
Das Passwort kann man mit dem Befehl *passwd Benutzername* geändert werden.  
Anmelden kann man sich mit dem Befehl *login Benutzername*.  
Die sudoers kann man sich mit dem Befehl *sudo/nano/etc/sudoers* anzeigen lassen.

----------------------------------------------------------------------------------------------
