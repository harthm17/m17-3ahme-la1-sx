# Protokoll-2 LABOR/SX 3AHME (2019/20)

* **Thema:** Dateirechte
* **Datum:** 02.12.2019
* **Gefehlt:** -
* **Erstellt von:** Stefan Haring (harstm17)
* **Protokoll letzte Einheit:** [18.11.2019](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/harstm17/protokolle/protokoll-1_harstm17_2019-11-18_.md)
----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis

1. [Dateirechte allgemein](#dateirechte-allgemein)
1. [Kommandos um Rechte zu ändern](#kommandos-um-rechte-zu-ändern)
2. [Benutzer anlegen](#benutzer-anlegen)
----------------------------------------------------------------------------------------------


### Dateirechte allgemein

#### Begriffsbestimmung
Bei einem Multiusersystem ist es wesentlich, Rechte zu haben/vergeben. Ohne sie, kann jeder auf alles zugreifen.  
Mit dem Befehl *ll*, den man in der Shell eingibt, werden die Rechte aller Dateien und Verzeichnisse im aktuellen Verzeichnis ausgeben. *ll* ist der Alias für den Befehl *ls -alF* (Ein Alias ist eine verkürzte Variante eines Befehls etc.).
Weiters ist noch zu beachten, wenn man eine Datei in ein anderes Verzeichnis kopiert, ändern sich die Rechte für die jeweilige Datei.

**ls -alF** bedeutet folgendes:
* ls ... list directory content
* a ... all
* l ... list(line)
* F ... freedom

#### Dateityp
Das erste Zeichen steht für den Dateityp. Dieser kann folgfende Zeichen annehmen:
* '-' für eine Datei
* d für directories 
* l, c oder b (wurde nicht genau besprochen)

#### Benutzer
Die weiteren neun Zeichen werden auf drei Arten von Benutzer aufgeteilt:
* Zeichen 2-4 für den Eigentümer ... u (user)
* Zeichen 5-7 für die Gruppe ... g (group)
* Zeichen 8-10 für alle anderen ... o (others)

#### Rechte bei Dateien
Es gibt drei Arten von Rechten:
* r ... read (lesen)
* w ... write (erstellen, ändern)
* x ... execute (Skripte, Binäre Dateien etc. ausführen)

#### Rechte bei Verzeichnissen
Es gibt wieder drei Arten von Rechten:
* r ... read (Inhalt lesen)
* w ... write (Inhalt löschen, anlegen)
* x ... execute (ins Verzeichnis wechseln)

Wenn ein Benutzer das Recht besitzt, wird der Buchstabe des Rechtes geschrieben. Ansonsten ist ein Minus anstelle des Buchstabens.

***Beispiele***
```
d rwx rw- ---
```
Es handelt sich um ein Verzeichnis, inder der Eigentümer alle drei Rechte hat.
Die Gruppe hat das read- und das write-Recht.
Alle anderen besitzen keine der 3 Arten von Rechten.

```
- r-x rw- r--
```
Es handelt sich um eine Datei, inder der Eigentümer das read und das execute-Recht.
Die Gruppe hat read- und das write-Recht.
Alle anderen haben nur das read-Recht

----------------------------------------------------------------------------------------------

### Kommandos um Rechte zu ändern
Falls man die Rechte dazu hat, Rechte zu verwalten, kann man in der shell die Rechte anderer mit Hilfe von Befehlen verändern.
```
chown(change owner) ... Datei //Eigentümer verändern
chown ...:... Datei           //Eigentümer + Gruppe verändern
chgrp(change group) ... Datei //Gruppe ändern
chmod(Rechte ändern)
```
*Beispiele:*
```
chmod ...g+x Datei //Gruppe darf nun ausführen
chmod ...o-rw Datei //Besitzer darf nun nicht mehr lesen und verändern
chmod 751 Datei //Rechte in Oktalzahlen: 111101001 = rwxr-x--x
```
----------------------------------------------------------------------------------------------

### Benutzer anlegen
Voraussetzung ist der Superuser-Zustand. Der Superuser weiß, kann und darf alles.
Folgender Befehl bewirkt das.
```
sudo -i 
```
Anschließend wird nach dem Passwort gefragt. Sobald diese Anforderung erfüllt ist, ist man Superuser.

Es gibt zwei Arten einen Benutzer anzulegen. Die folgenden Befehle können das bewirken:
```
useradd Benutzername //einfachere Variante
adduser Benutzername
```
Mit dem Befehl ***less/etc/passwd*** lassen wir uns die bisherigen Einträge über die Benutzer anzeigen.

Mit den folgenden Befehlen tragen wir uns in die gewünschten Dateien/Verzeichnissen ein.
```
nano/etc/passwd
nano/etc/group
nano/etc/shadow
nano /etc/home
```
Diese Vorgänge kann man mit Strg+O speichern und mit Strg+X beenden.


* Die sudoers kann man sich mit dem Befehl ***sudo/nano/etc/sudoers*** anzeigen lassen.
* Danach kann man mit dem Befehl ***id Benutzername*** Daten über den angelegten Benutzer ausgeben.  
* Das Passwort kann mit dem Befehl ***passwd Benutzername*** geändert werden.  
* Anmelden kann man sich mit dem Befehl ***login Benutzername***.  
