# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Versionsverwaltungssysteme, git, Github, Markdown
* **Datum:** 18.11.2019
* **Gefehlt:** keiner
* **Erstellt von:** Felix Hamrle
* **Protokoll nächste Einheit:** 02.12.2019

## Inhaltsverzeichniss
1. [Versionsverwaltung](#versionsverwaltung)  
2. [Dokumentation](#dokumentation)
3. [Markdown](#markdown)
   1. [Überschrift](#überschrift)
   2. [Kursiv, Fett, Fett & Kursiv](#kursiv, fett, fett & fursiv)
        1.[Fett](#fett)
        2.[Kursiv](#kursiv)
        3.[Fett & Kursiv](#fett & kursiv)
   3. [Listen](#listen)
   4. [Code](#code)
   5. [Tabele](#tabele)
   5. [Links](#links)
   5. [Bilder](#bilder)
4. [Github](#github)


# Versionsverwaltung

Versionsverwaltungsysteme sind entstanden weil wenn mann nur die gerade gebrauchte Datei(Programm,...) vorhanden hat,  
dann kann mann nicht auf vohrherige Datei zugreifen und schuen was sich verändert hat. Versionsverwaltungsysteme sind auch 
sehr gut für Projekte wo mehrere zusammen arbeiten, weil wenn jemand etwas in der Datei ändert können andere das sehen. Da man 
alle vorherigen Versionen auch hatt braucht man keine angst zu haben einen großen Fehler zu machen da man auf die 
vorherigen Versionen zugreifen kann.

# Dokumentation

Art der Dokumentation | Vorteil | Nachteil
----------------------|---------|---------
Handschriftlich       | flexibel, schnell| unleserlich, elektronisch nicht suchbar, unübersichtlich
**Markdown**          | flexibel, schnell, leserlich, übersichtlich, elektronisches Suchen, veränderbar|
Textverarbeitung      | leserlich, übersichtlich, elektronisches Suchen, veränderbar | Zeitbedarf

# Markdown

## Überschrift

Um eine Überschrift da zu stellen git man vor dem Text ein hashtag zB. `# Markdown`. Desto mehr hashtags desto kleiner wird
die Überschrift zB. `#### Markdown`.

## Kursiv, Fett, Fett & Kursiv

#### Fett
Damit der Text **Fett** ist muss mann nur am Anfang und am Ende zwei * stellen.  
zB. `**Test**`

#### Kursiv
Wenn der Text *kursiv* sein soll dan das ganz gleich wie bei Fett aber einfach nur mit *.
zB. `*Test*`

#### Fett & Kursiv
Man kann das ganze ***kombinieren*** dann mus man nur drei * hin stellen
zB. `***Test***`

## Listen

### Ungeordnete Liste
Um eine Ungeordnete Liste zu erstellen muss mann vor einer Aufzählung einem * geben.

zB.

* Test 1           
* Test 2             
* Test 3              
```
* Test 1
* Test 2
* Test 3 
```

### Geordnete Liste
Bei der Geordnete Liste braucht mann nur eine Zahl eingeben danach dan einen Punkt. Die Zahl ist egal weil es wird von selbst geordnet.
Man muss nur aufpassen was die erste Zahl ist von der wird dan weiter gezehlt zB 10, 11, 12   
und dan mit 1: 1, 2, 3.

zB.

10. Test 1           
1. Test 2             
1. Test 3              
```
1. Test 1
1. Test 2
1. Test 3 
```
## Code
Um einen Code dazustelen braucht mann nur ``` `Text` ```. Um mehrer Zeilen so dazustellen braucht man einfach drei.       
zB.

    ```
    Codezeile 1
    Codezeile 2
    Codezeile 3
    ```
    
Dieser code kann dann auch mit C-Makierungen ausgegeben werden man muss nur ein C nach den ersten drei ` geben.    
zB.

    ```C   
    int main(){    
    printf("Hello World");   
    return 0;    
    }   
    ```

das würde dan so ausschauen
    
```C   
int main(){    
printf("Hello World");   
return 0;    
}   
```
## Tabele
zB.
```
| 1 | 2 | 3 |
| - | - | - |
|11 | 12 | 13 |
| 21 | 22 | 23 |
| 31 | 32 |  33 |
```
Eine Tabele muss man nicht genau formartieren.

## Links
Wenn mann einen Link zu einer bestimten Webseite so ausgeben will das er anklickbar ist muss mann  es so schreiben  
`[text](Der Link zur Webseite)`.

zB. [Wikipedia](https://de.wikipedia.org/wiki/Wikipedia:Hauptseite)

Mann kann auch zu einer bestimten Überschrift in der Datei springen mit (Die überschrift muss kleingeschrieben sein)   
`[text](#überschrift)`

zB. [Github](#Github)

## Bilder
Bilder fügt man ein wie Links nur voher ein ! so würde das aus sehen  
`![text](Bild-adress)`


# Github

Bei Github kann jeder ein Repository erstellen. Ein Repository ist ein Platz wo alle Datein von 
jedem Branch gespeichert werden. Jedes Repository hat einen Master Branch. Dan kann man noch weitere Branchs erstelen 
wo zB. neben projekte gespeichert sind.

Bei Github kann mann auch offlin arbeiten.

Um offline zu arbeiten muss man das Repository auf dem Computer speichern das geht mit dem Befehl `git clone <Link zum Repository>` dan hat man das Repository am Computer.

Mit `git checkout <Branch>` kann mann zwischen den Branchs wechseln

Wenn mann was geändert hat und man wil es speichern dan geht das mit dem Befehl `git add <Dateiname>`. Damit währe es auf der Warteschlange vom lokalem Repository. Um es komplet zu speicher braucht man den Befehl `git commit -m "Kommentar"`.

Um es dan online zu stehlen braucht man nur mehr den Befehl `git push`. Beim ersten mall muss man email und seinen Namen eingeben.
