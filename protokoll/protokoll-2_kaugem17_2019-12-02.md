# 2. Protokoll

-------------------------------------------------

## Thema: Dateirechte

-------------------------------------------------

Übungsdatum:   Montag, 02.12.2019     
Übungszeit:    14:10 bis 16:20      
Übungsort:     Arnfels, CAD-Saal    
Verfasser:     Georg Kaufmann    
Abwesend:      keiner      
Anwesend:      Felix Hamrle, Stefan Haring, Thomas Harrer, Georg Kaufmann, Andreas Kogler, Franz Lieleg, Simon Marcher

-------------------------------------------------

### Inhaltsverzeichnis
1) [Dateirechte](#dateirechte) 
      * [Grundlagen](#grundlagen) 
      * [Kommandos](#kommandos)
1) [Benutzer anlegen](#benutzer-anlegen)

-------------------------------------------------

### Dateirechte
#### Grundlagen
Warum gibt es Dateirechte?         
In einem MultiUserSystem ist es wichtig zu kennzeichnen wer was darf. Deswegen gibt es sogennante Rechte oder Dateirechte.        

Wikipedia sagt folgendes dazu:
> Die Unix-Dateirechte sind Dateiberechtigungen bei Unix und Unix-Derivaten wie Linux und Mac OS X. Die aktuellen UNIX-Dateirechte zeichnen sich durch eine einfache Struktur aus, die einerseits intuitiv von Menschen verwendet werden kann und andererseits keine hohen Ansprüche an Computer stellt.                    

[Quelle](https://de.wikipedia.org/wiki/Unix-Dateirechte), 08.12.2019

Das erste Zeichen einer Datei steht immer für den Typ.      
Diese können lauten:
* **- für Dateien**
* **d für Verzeichnisse**

Die Dateirechte in Unix-Dateisystemen werden unterteilt in Benutzerklassen.          
Diese lauten:
* **Eigentümer bzw. User** 
* **Gruppe bzw. group**
* **alle anderen bzw. others**

Ein Beispiel:       
![Bild](https://www.webhostone.de/images/FAQ/Webpakete/dateirechte3.png)                
[Quelle](https://www.webhostone.de/images/FAQ/Webpakete/dateirechte3.png), 08.12.2019 

Die Rechte der jeweiligen Benutzerklassen werden in Buchstaben wiedergegeben.        
Diese lauten:

| Buchstabe | Ausgeschrieben | Funktion |
| --------- | -------------- | -------- |
| r | read | Inhalt lesen |
| w | write | Inhalt löschen bzw. anlegen |
| x | execute | Inhalt ausführen |
| - | no right | kein Recht |

#### Kommandos

Zum verändern des Eigentümers:              
```
chown ...:... Datei
```

Zum verändern der Gruppe:          
```         
chgrp ... Datei
```

Zum verändern der Rechte:  
```
chmod ... Datei
chmod g+x         group darf nun ausführen
chmod o-rw        others dürfen nicht mehr lesen und verändern
chmod u+rwx       user darf lesen, veränder und ausführen
chmod 751         ändern durch Oktalzahl 751 = 111 101 001 = rwx r-x --e
```
Zum hinzufügen eines Benutzers:
```
adduser -> high level
useradd -> low level
```

-------------------------------------------------

### Benutzer anlegen

Wir wollen einen neuen Benutzer über die Shell anlegen. Unten wird gezeigt wie man dies am leichtersten macht.

Um einen Benutzer anlegen zu können muss man zu aller erst **Superuser** werden. 
Ein Superuser hat die Eigenschaft das er alle Rechte aufweist.
```
sudo -i
```
Um Superuser zu werden muss man dessen Passwort wissen.

Um die bisherigen Einträge anschauen zu können muss man folgenden Befehl eingeben:
```
less/etc/passwd
```

Um nun einen Benutzer anlegen zu können müssen folgende Befehle abgearbeitet werden:
```
nano/etc/passwd
nano/etc/group
nano/etc/shadow
nano/etc/home
```

Befehl | Eigenschaft
------ | -----------
id <Benutzername> | Daten über Benutzer ausgeben
passwd <Benutzername> | Passwort des Benutzers ändern
login <Benutzername> | Anmelden des Benutzers
