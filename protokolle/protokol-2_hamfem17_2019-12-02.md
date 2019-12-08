# Protokoll LA2/SX 3AHME (2019/20)

* **Thema:** Dateirechte, Benutzer anlegen
* **Datum:** 02.122019
* **Gefehlt:** keiner
* **Erstellt von:** Felix Hamrle
* **Protokoll nächste Einheit:** --

## Inhaltsverzeichniss
  
  
    
      
      
      
## Dateirechte


Wenn man den Befehl `ls-l` in der Shell ein gibt wird der Verzeichnisinhalt auflisten mit einem langem Listungsformat. Dort wird dann 
aufgelistet wann die Datei erstelt wurde,wie viel Byte sie hat, wie sie benannt wurde und welche Rechte der Super User, die Gruppe und 
andere haben.

Wenn man jetzt den Befehl eingibt schaut das ca. so aus.

``-rwx r-x	r--  2 root     root        13876 Nov 17 15:13   myfile``

Das `-` steht dafür das es eine normale Datei ist.   
Wenn `d` dort stehen würde wäre es ein Verzeichnis. Das `d` steht für **d**irectory.

rwx ...	Was darf der Super User machen.

r-x ...	Was darft die Gruppe machen?

r-- ...	Was darf der "Rest" machen? 


Rechte|Bedeutung|Funktionsumfang
------|---------|-----
r     |Read|Dateiinhalt lesen
w     |Write|Dateiinhalt bearbeiten
x     |Execute|Datei ausführen

bei Verzeichnissen schaut es zimlich gleich aus mit den Rechten.

Rechte|Bedeutung|Funktionsumfang
------|---------|-----
r     |Read|Verzeichnisinhalt lesen 
w     |Write|Verzeichnisinhalt ändern (Dateien hinzufügen, löschen und umbenennen)
x     |Execute|in dieses Verzeichnis hineinwechseln

### Befehle für Dateirechte  

Um Dateirechte zuveränder muss man der Super User sein.    
Das geht mit dem Befehl `sudo -i`.  

#### Rechte ändern

Befehl `chmod Dateiname`  
Beispiel `chmod u+rwx Test.txt`  

Das `u` steht für den User, für Gruppe steht das `g` und für andere steht das `o`.  

`+` zum Rechte vergeben.  
Beispiel `chmod g+rwx Test.txt`  


`-` zum Rechte nehmen.  
Beispiel `chmod o-wx Test.txt`  

Man kann auch die Rechte in Oktal angeben  
Beispiel `chmod 715 Test.txt`  

Das schaut dan in Binär so aus  

 7...1...5    
111 001 101    
rwx --x r-x    

`Test.txt` ist die Datei.  

#### Besitzer, Gruppe der Datei ändern

Befehl `chown besitzer:gruppe dateiname`
Beispiel `chown hamfem:3Ahme test.txt`

#### Nur Gruppe ändern

Befehl `chgrp gruppe dateiname`
Beispiel `chown 3Ahme test.txt`
















