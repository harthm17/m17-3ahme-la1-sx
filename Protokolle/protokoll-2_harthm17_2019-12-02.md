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

Nach den Aufrufen von ll sieht man, wer hier Rechte hat. Daraus kann man erkennen, ob es eine Datei oder ein Verzeichniss ist und wer
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
Es gibt drei verschiedene Benutzer. Hier werden neun Zeichen hintereinander aufgezählt. Oben sind sie in drei Bereiche zerteilt.

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

Wenn ein Benutzer kein Recht hat steht an dieser Stelle eine '**-**'.

Beispiel:
```
    d rwx rw- r--
```
In diesem Beispiel handelt sich es um ein Verzeichniss, indem der Eigentümer alle Rechte besitzt. Die Gruppe nur das read und write Recht und die anderen können nur den Inhalt lesen.


## Commands um Rechte zu ändern
Man kann die Rechte mit Hilfe von Befehlen ändern, angenommen man hat selbst die Rechte dazu, Rechte zu verwalten.

```
  chown ... Datei -> Eigentümmer verändern (chown = change owner)
  chown ...:... Datei -> Eigentümer und Gruppe verändern
  chgsp ... Datei -> Gruppe verändern (chgsp = change group)
  chmod ... -> Rechte ändern 
```

Beispiele:
```
  chmod g+x Datei -> Gruppe darf nun auch ausführen
  chmod o-rw Datei -> die anderen darf nun nicht mehr lesen und verändern
  chmod u+rwx Datei -> der User bekommt nun alle Rechte für diese Datei
  chmod 751 Datei 
```
chmod 751 ist eine oktale Schreibweiße. Hier ist eine der wenigen Anwendungen wo die oktale Schreibweiße nützlich ist.
Wenn man 751 von oktal ins binäre übersetzt bekommt man die Zahlen:
751 = 111 101 001

Das heißt:
    111 101 001
->  rwx r-x --x

Der User bekommt alle Rechte, die Gruppe nur read und execute und die anderen können die Datei nur ausführen.


## Benutzer über Terminal anlegen
Man kann verschiedene Benutzer auch über eine Shell anlegen.

Es gibt 2 Kommandos wie man es direkt macht, jedoch haben wir keines dieser benutzt.

* adduser -> high level
* useradd -> low level

Der Grund, warum es zwei Kommandos gibt ist, dass useradd als erstes da war und dann wurde adduser hinzugefügt. Da bestimmt Beschwerden eingetreten wären, wieso man alle neu lernen müsse, wurde die "leichte" Version nicht entfernt.

Zuerst muss man als Superuser einsteigen. 
```
  sudo -i
```

root = Superuser
 => Ein Superuser kann, darf alles. Er hat **keine** Einschränkungen. Als Superuser kann man sein Betriebssystem zerstören, indem man       wichtuge Dokumente löscht. **Es ist sehr gefährlich und man sollte damit nicht Sachen ausprobieren!**
 
 Mit dem Befehl **less/etc/passwd** sind wir dann in den Benutzer eingestiegen und sieht dann alle bisherigen Einträge des Benutzers.
 
**Wichtig**: passwd ist auch ein Programm!
              
Gibt man in der Shell "man man" ein, bekommt man eine Auflistung von 1 bis 8. Wo 1 Programme sind und 2 dann .....
              
Gibt man sich den Punkt 5 genauer aus mit "man 5 man" zeigt es uns genauere Information an.
passwd ist auch dafür um Benutzer zu erstellen.


Mit sudo -i und dann mit dem Passwort ist man als Superuser eingeloggt.

Nach dem Befehl less/etc/passwd gibt man **nano/etc/passwd** ein.
Hier tragen wir unseren Benutzer ein. 
Im Unterricht haben wir die Daten des schuelers koopiert und unseren HTL-Kürzel eingesetzt und wir haben auch die ID geändert.
Mit STRG + O speichert man (Buchstabe O und nicht Zahl 0) und man beendet es mit STRG + X.

Mit **nano/etc/group** haben wir die Gruppe bearbeitet.
```
  harthm17;x;1001;
```

Um ein Passwort zu setzten müssen wir den Befehl **nano/etc/shadow** ausfüren.
Ein ! heißt, das man sich nicht einloggen kann.

Die Rechte ändern wir wenn wir **nano/etc/home** eingeben.

Um den Benutzer perfekt zu machen brauchen wir nur noch die Ordner.
```
  ls -la /etc/shell
  cp /etc/shell/.*/home/harthm17/    -> * nimmt keine verborgende Verzeichnisse
```

Mit dem Befehl **sudo nano /etc/sudoers** kann man alles ändern. **-> sehr gefährlich**


### Hash
Passwörter sind mit einem Hash verschlüsselt. Ein Hash ist ein zufälliger Algorithmus.
Ein Hash ist ein elektronischer Fingerabdruck.

**Salt and Pepper Prinzip**
Beim gleichen Passwort ist nicht der gleiche Hash.
Kleine Änderungen wirken große Änderungen beim Hash aus.


### History
Alle Befehle werden in der History gespeichert.
Man kann sie ansehen mit dem Befehl -> .bash_history.

Falls man was löschen möchte gibt man nano .bash_history ein.
