# Protokoll LABOR/SX 3AHME (2019/20)

* **Thema:** Dateirechte
* **Datum:** 02.12.2019
* **Gefehlt:** Keiner
* **Erstellt von:** koganm17
* **Protokoll letzte Einheit:** [18.11.2019](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/koganm17/Protokolle/Protokoll1.md)

----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis

1.[Dateiechte grundlegend](#dateirechte-grundlegend)
1.[Benutzer anlegen](#Benutzer-anlegen)


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

### Benutzer anlegen
Zuerst muss man zum Superuser werden
```
sudo -i = man wird zum Superuser (Superuser root)
```
```
nano/etc/passwd
nano/etc/group
nano/etc/shadow
passwd <Benutzer>
nano /etc/shadow
chown <Benutzer>:<Benutzer> /home/<Benutzer>
```
