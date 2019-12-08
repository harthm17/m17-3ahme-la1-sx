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
x | execute | in Verzeichnis wechseln dürfen

#### Kommandos

Zum verändern des Eigentümers:              
```
chown
```

Zum verändern der Gruppe:          
```         
chgrp
```

Zum verändern der Rechte:  
```
chmod
```

-------------------------------------------------

### Benutzer anlegen

