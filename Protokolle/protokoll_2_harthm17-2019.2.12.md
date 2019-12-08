# 2. Protokoll
---------------------------------------------
## Thema: Dateirechte in Linux
---------------------------------------------
* Datum:      2.12.2019 
* Gruppe:     2  
* Abwesend:   keiner
* Verfasser:  Thomas Harrer 
* Klasse:     3AHME
* Schuljahr:  2019/20
---------------------------------------------
## Inhaltsverzeichnis

1) [Dateirechte Grundlagen](#dateirechte-grundlagen)
2) [Commands um Rechte zu ändern](#commands-um-rechte-zu-ändern)
3) [Benutzer über Terminal anlegen](#benutzer-über-terminal-anlegen)

---------------------------------------------
## Dateirechte Grundlagen
Dateirechte sind heutzutage sehr wichtig. Arbeitet man in einem Multiusersystem, dass ich ein Betriebssystem, das mehrere Benutzer 
bereitstellt und von einander abgrenzt. Würde es keine Dateirechte geben, könnte jeder Benutzer auf deine Datein und Verzeichnisse einsehen.
Wenn man den Command **ll** in der Shell eingibt, kann man alle Rechte der Datein und Verzeichnisse im aktuellen Verzeichniss ausgeben.

Der Befehl **ll** ist ein Alias für **ls -alF**.
Ein Alias ist abgekürzte Version eines Befehls.

Nach den Aufrufen von ll sieht man, wer hier Rechte hat. Daraus kann man erkennen, ob es eine Datei oder ein Verzeichniss ist und 
hier Rechte hat.

Dies kann so aussehen:
```
  d rwx rw- r--
 (1 2-4 5-7 8-10 (für Erklärung wichtig, wird so nicht ausgeben. Hier heißt das - bis.))

```

### Dateityp
Es gibt drei verschiedene Dateitypen. Den Datentyp erkennt man am **ersten** Zeichen.

* '-' für Datein
* d für Verzeichnisse
* l,c oder b (wurde im Unterricht nur erwähnt)

### Benutzer
Es gibt drei verschiedene Benutzer. Hier werden 9 Zeichen hintereinander aufgezählt. Oben habe ich sie in 3 Bereiche zerteilt.

* 2 bis 4 ist der Eigentümer selbst (user oder u)
* 5 bis 7 ist eine Gruppe (group oder g)
* 8 bis 10 sind alle anderen (others oder o)

### Rechte in Datein
Es gibt drei verschiedene Arten von Rechten in Datein.

* r -> read (man kann die Datei lesen)
* w -> write (man kann die Datei erstellen und ändern)
* x -> execute (man kann binäre Datein und Skripte ausführen)

### Rechte in Verzeichnissen
Es gibt drei verschiedene Arten von Rechten in Verzeichnissen.

* r -> lesen (man kann den Inhalt lesen)
* w -> write (man kann den Inhalt löschen oder anlegen)
* e -> execute (ins Verzeichnis wechseln)

## Commands um Rechte zu ändern

### Rechte mit Zahlen ändern


## Benutzer über Terminal anlegen
Man kann verschiedene Benutzer auch über eine Shell anlegen.


