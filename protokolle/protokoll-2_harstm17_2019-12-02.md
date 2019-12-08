# Protokoll-2 LABOR/SX 3AHME (2019/20)

---------------------------------------------------------------------------------------------

* **Thema:** Dateirechte
* **Datum:** 02.12.2019
* **Gefehlt:** -
* **Erstellt von:** Stefan Haring (harstm17)
* **Protokoll der letzten Einheit:** [18.11.2019](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/harstm17/protokolle/protokoll-1_harstm17_2019-11-18_.md)

----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis

1. [Dateirechte allgemein](#dateirechte-allgemein)
1. [Kommandos um Rechte zu ändern](#kommandos-um-rechte-zu-ändern)
2. [Benutzer anlegen](#benutzer-anlegen)
----------------------------------------------------------------------------------------------


### Dateirechte allgemein

#### Begriffsbestimmung
*Eigendefinition:*
>Bei einem Multiusersystem ist es wesentlich, Rechte zu haben/vergeben. Ohne sie, kann jeder auf alles zugreifen.  
Mit dem Befehl *ll*, den man in der Shell eingibt, werden die Rechte aller Dateien und Verzeichnisse im aktuellen Verzeichnis ausgeben. *ll* ist der Alias für den Befehl *ls -alF* (Ein Alias ist eine verkürzte Variante eines Befehls etc.).
Weiters ist noch zu beachten, wenn man eine Datei in ein anderes Verzeichnis kopiert, ändern sich die Rechte für die jeweilige Datei.

**ls -alF** bedeutet folgendes:
* ls ... list directory content
* a ... all
* l ... list(line)
* F ... freedom

*[Wikipedia](https://de.wikipedia.org/wiki/Unix-Dateirechte) definiert folgendes:*
>Die Unix-Dateirechte sind Dateiberechtigungen bei Unix und Unix-Derivaten wie Linux und Mac OS X. Die Berechtigungsaufteilung in Eigentümer, Gruppe und Andere gibt es seit UNIX-V4 (1974). In früheren UNIX-Versionen gab es nur 6 Bit für die Dateirechte (Lesen/Schreiben für Eigentümer und Nicht-Eigentümer, Execute und Set-UID). Die aktuellen UNIX-Dateirechte zeichnen sich durch eine einfache Struktur aus, die einerseits intuitiv von Menschen verwendet werden kann und andererseits keine hohen Ansprüche an Computer stellt. Trotzdem lassen sich mit diesen Dateirechten selbst komplexe Alltagsprobleme in einem Mehrbenutzerumfeld lösen.

**Beispiel:**
Um zu verstehen wie es mit den Dateirechten aussieht, könnte diese Grafik sehr hilfreich sein:
![Bild](https://www.ceonaires.com/ceodocs/uploads/2017/05/Dateirechte-symbolisch-1030x278.png)
Quelle: https://www.ceonaires.com/ceodocs/uploads/2017/05/Dateirechte-symbolisch-1030x278.png

----------------------------------------------------------------------------------------------------


***Folgende 3 Überschriften beschreiben die obige Grafik etwas genauer***

#### Dateityp
*Das erste Zeichen steht für den Dateityp. Dieser kann folgfende Zeichen annehmen:*

Zeichen | Beschreibung
--------|-------------
`-` | für eine Datei
d | für directories 
l, c oder b | wurde nicht genau besprochen


#### Benutzer
Die weiteren neun Zeichen werden auf drei Arten von Benutzer aufgeteilt:
* Zeichen 2-4 für den Eigentümer ... u (user)
* Zeichen 5-7 für die Gruppe ... g (group)
* Zeichen 8-10 für alle anderen ... o (others)


#### Rechte bei Dateien
*Es gibt drei Arten von Rechten:*

Kurzform | Ausgeschrieben | Übersetzung/Beschreibung
---------|----------------|-------------------------
r | read | lesen
w | write | erstellen, ändern
x | execute | Skripte, Binäre Dateien etc. ausführen


#### Rechte bei Verzeichnissen
*Es gibt wieder drei Arten von Rechten:*

Kurzform | Ausgeschrieben | Übersetzung/Beschreibung
---------|----------------|-------------------------
r | read | Inhalt lesen
w | write | Inhalt löschen, anlegen
x | execute | ins Verzeichnis wechseln

Wenn ein Benutzer das Recht besitzt, wird der Buchstabe des Rechtes geschrieben. Ansonsten ist ein Minus anstelle des Buchstabens.


#### Folgende Beispiele bringen das Arbeiten mit Dateirechten näher

##### Beispiel 1:
```
d rwx rw- ---
```
Es handelt sich um ein Verzeichnis, inder der Eigentümer alle drei Rechte hat.
Die Gruppe hat das read- und das write-Recht.
Alle anderen besitzen keine der 3 Arten von Rechten.


##### Beispiel 2
```
- r-x rw- r--
```
Es handelt sich um eine Datei, inder der Eigentümer das read und das execute-Recht.
Die Gruppe hat read- und das write-Recht.
Alle anderen haben nur das read-Recht
*(dieses Beispiel ist sehr unrealistisch, da man der Gruppe meist weniger Rechte gibt, als dem Eigentümer)*

----------------------------------------------------------------------------------------------

### Kommandos um Rechte zu ändern
Falls man die Rechte dazu hat, Rechte zu verwalten, kann man in der shell die Rechte anderer mit Hilfe von Befehlen verändern.

Befehl | Anwendung
-------|----------
chown(change owner) ... Dateiname | Eigentümer verändern
chown ...:... Dateiname | Eigentümer + Gruppe verändern
chgrp(change group) ... Dateiname | Gruppe ändern
chmod(zu verändernte Rechte) |Rechte ändern

Folgendes Bild beschreibt einen dieser Vorgänge:
![bild](https://slideplayer.org/slide/5194705/16/images/64/%C3%84nderung+der+Rechte+Der+Eigent%C3%BCmer+einer+Datei%2Feines+Verzeichnisses+kann+die+Zugriffsrechte+mit+Hilfe+des+chmod-Befehls+%C3%A4ndern..jpg)
Quelle: https://slideplayer.org/slide/5194705/16/images/64/%C3%84nderung+der+Rechte+Der+Eigent%C3%BCmer+einer+Datei%2Feines+Verzeichnisses+kann+die+Zugriffsrechte+mit+Hilfe+des+chmod-Befehls+%C3%A4ndern..jpg


***Beispiele:***

Befehl | Auswirkung
-------|-------------
chmod g+x | Gruppe darf nun auch ausführen
chmod o-rw | Andere dürfen nun nicht mehr lesen und verändern
chmod u-x | Besitzer darf nun nicht mehr ausführen
chmod 651 Datei |  Rechte in Oktalzahlen: 110 101 001 = rw- r-x --x

----------------------------------------------------------------------------------------------

### Benutzer anlegen
Aufgabe ist es, einen Benutzer über die Shell anzulegen.
Voraussetzung ist der Superuser-Zustand. Der Superuser weiß, kann und darf alles.
Folgender Befehl bewirkt das Gelangen in diesen Zustand.
```
sudo -i 
```
Anschließend wird nach dem Passwort gefragt. Sobald das korrekte Passwort eingegeben wurde, ist man Superuser.

Es gibt zwei Arten einen Benutzer anzulegen. Die folgenden Befehle können das bewirken:
```
useradd Benutzername //einfachere Variante
adduser Benutzername
```
Mit diesem Befehl erlangt man Einsicht, in die bestehenden Einträge des Benutzers.
```
less/etc/passwd
```

Mit den folgenden Befehlen tragen wir uns in die gewünschten Dateien/Verzeichnissen ein.
```
nano/etc/passwd
nano/etc/group
nano/etc/shadow
nano /etc/home
```
In jedem dieser Verzeichnisse kann/soll man den Benutzer eintragen
Diese Vorgänge kann man mit Strg+O speichern und mit Strg+X beenden.



Befehl | Eigenschaft
------ | -----------
id *Benutzername* | Daten über Benutzer ausgeben
passwd *Benutzername* | Passwort des Benutzers ändern
login *Benutzername* | Anmelden des Benutzers


**Wichtig**
Acht zu geben ist, bei der Eingabe des Passworts.
Es kann immer wieder passieren, dass man irrtümlich das Passwort an einer nicht geforderten Stelle eingibt.
In der History ist das Passwort dann ersichtlich und somit ist es ein leichtes Spiel für Hacker oder Andere,
an dein Passwort zu gelangen. Es ist möglich, teile aus der History zu löschen.
