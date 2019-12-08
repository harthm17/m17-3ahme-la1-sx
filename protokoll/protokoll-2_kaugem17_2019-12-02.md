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
In einem MultiUserSystem ist es wichtig zu kennzeichnen wer was darf. Deswegen gibt es sogennante Rechte.

Das erste Zeichen einer Datei steht immer für den Typ.
Diese lauten:
* **- für Dateien**
* **d für Verzeichnisse**

Die Dateirechte in Unix-Dateisystemen werden unterteilt in Benutzerklassen. 
Diese lauten:
* **Eigentümer bzw. User** 
* **Gruppe bzw. group**
* **alle anderen bzw. others**

![Bild](https://www.webhostone.de/images/FAQ/Webpakete/dateirechte3.png)
[Quelle](https://www.webhostone.de/images/FAQ/Webpakete/dateirechte3.png) 

Die Rechte der jeweiligen Benutzerklassen werden in Buchstaben wiedergegeben. 
Diese lauten:

Buchstabe | Ausgeschrieben | Funktion
--------- | -------------- | --------
r | read | Inhalt lesen
w | write | Inhalt löschen bzw. anlegen
x | execute | Inhalt ausführen

#### Kommandos

Zum verändern des Eigentümers:              
```
chown ... Datei
```

Zum verändern der Gruppe:          
```         
chgrp ... Datei
```

Zum verändern der Rechte:  
```
chmod g+x         group darf nun ausführen
chmod o-rw        others dürfen nicht mehr lesen und verändern
chmod u+rwx       user darf lesen, veränder und ausführen
chmod 751         ändern durch Oktalzahl 751 = 111 101 001 = rwx r-x --e
```

-------------------------------------------------

### Benutzer anlegen

Um einen Benutzer anlegen zu können muss man zu alles erst **Superuser** werden. 
Ein Superuser hat die Eigenschaft das er alle Rechte aufweist.
```
sudo -i
```
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
