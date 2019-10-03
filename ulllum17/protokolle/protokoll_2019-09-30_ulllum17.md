# 1. Protokoll | AHME17 
# Uller Lucas
-------------------------------------------------------------------------
* **Thema:** Versionsverwaltungssystem, Git-Befehle(Shell), Shell
* **Datum:** 30.09.2019
* **Gefehlt:** ---
* **Erstellt von:** ulllum17
* **Protokoll nächste Einheit:**
--------------------------------------------------------------------------
## Inhaltsverzeichnis

1. [Versionsverwaltungssystem](#versionverwaltungssystem)
    1. [Absatz](#absatz)
    1. [Zeilenumbruch](#zeilenumbruch)
    1. [Überschrift](#überschrift)
    1. [Hervorheben](#hervorheben)
    1. [Aufzählungen](#aufzählungen)
        1. [Sortiert](#sortiert)
        1. [Unsortiert](#unsortiert)
    1. [Code](#code)
    1. [Text Grau hinterlegen](#text-grau-hinterlegen)
    1. [Zitat](#zitat)
    1. [Links](#links)
        1. [Inline](#inline)
        1. [Referenz](#referenz)
1. [Git](#git)
    1. [Branches](#branches)
    1. [Merge](#merge)
    1. [Klonen](#klonen)
    1. [Uploud eines Repository](#uploud-eines-repositorys)
1. [Shell](#shell) 


--------------------------------------------------------------------------

## Versionverwaltungssystem

[Github][Github] ist ein Onlinedienst, der Software-Entwicklungsprojekte auf seinen Servern bereitstellt.

Beispiele für die Formatierung in Markdown:

### Absatz
Absätze werden mit einer leer Zeile erzeugt.

    Absatz 1

    Absatz 2
    
### Zeilenumbruch

    Text....    
    Text....    
    Text....

### Überschrift
Es sind **maximal 6** Überschiftsstufen möglich!

    # Überschrift 1
    ## Überschrift 2
    ### Überschrfit 3
    #### Überschrift 4
    ##### Überschrift 5
    ###### Überschrift 6


### Hervorheben
Um wichtiges hervorzuheben gibt es 5 möglichkeiten!

    **Fett**
    *Kursiv*
    ***Fett-und-Kursiv***
    ~~Durchgestrichen~~

### Aufzählungen
Es gibt zwei möglichkeiten um etwas Aufzuzählen:    
* sortiert
* unsortiert 
#### Sortiert
        1. Auzählung1
        1. Auzählung2
        1. Auzählung3
            1.Aufzählunga
            1.Aufzählungb
            1.Aufzählungc        
        1. Auzählung4
        1. Auzählung5
        1. Auzählung6
**1. ist immer möglich da *markdown* von sich aus weiter Zählt**        
      
      

#### Unsortiert
        *Punkt1
        *Punkt2
        *Punkt3
            *Punkta
            *Punktb
            *Punktc
        -Punkt4
        -Punkt5
        -Punkt6  
**- und * sind mögliche Aufzählungszeichen**

### Code
Um zu Kennzeichnen das es sich um Computercode handelt

 ```C
    ``` <Computersprache>
    int main(){
    printf("Hello World!");
    return 0;
    }
    ```
```

### Text Grau hinterlegen
Um etwas grau zu hinterlegen zweimal die **Tabulatortaste** drücken

### Zitat
Zitate werden mit **>** eingeleitet 

    > Zitat
   
### Links
Es gibt zwei Möglichkeit um Links einzufügen:
* inline 
* Referenz

#### Inline   

     [Anzeige_Name1](https://test.org)
     [Anzeige_Name2](https://test.org "POPUP Fenster, wenn mit der Maus auf dem Link")

*Veranschaulichung des Popup:*    
[Anzeige_Name1](https://test.org)  
[Anzeige_Name2](https://test.org "POP UP Fenster, wenn mit der Maus auf dem Link")

#### Referenz   

    [Anzeige_Name][1]
    [1]:https://test.org "POP UP Fenster, wenn mit der Maus auf dem Link"

[Mehr Formatierungsmöglichkeiten][cheatsheet]

**Vorteile einer Referenz**
  * Links *können* gebündelt z.B. am Ende zusammengefasst werden
------------------------------------------------------------------------------------------------------  
## Git
### Git-Kommandos und Ebenen
![Git-Data Trasport][Git-Data Trasport]
Quelle: https://www.patrickzahnd.ch/uploads/git-transport-v1.png

**Stash:** 
[Aus Git-SCM][Stash]
> Beim Stashen werden die aus Deinem Arbeitsverzeichnis noch nicht committeten Änderungen – also Deine geänderten beobachteten Dateien und die in der Staging-Area enthaltenen Dateien – in einem Stack voller unfertiger Änderungen gespeichert. Diese kannst Du dann jederzeit wieder vom Stack holen und auf Dein Arbeitsverzeichnis anwenden.    

**Workspace:**    
Hier sind die Arbeitsdateien des Repository gespeichert

**Index:**    
Hier werden die Daten *hingebracht*, welche im nächsten Schritt commitet werden

**Local Repository:**    
Sind die Lokalen änderungen gespeichert

**Remote Repository:**    
Verzeichnis auf einem Git-Server(nicht Lokal)

### Klonen
Ein vorhandes Repository klonen
````bash
git clone https://github.com/ulllum17/labor 
````

### Uploud eines Repositorys
````bash
git add
````
Hier wird dem Repository mitgeteil das eine Änderung getätigt wurde.

````bash
git commit
````
Die Änderungen die in den Index hinzugefügt wurden, werden als Snapshot lokal gespeichert

````bash
git push
````
Hier wird der Snapshot des lokalen Repository auf den *Git-Server* hochgeladen( remote Repository)

````bash
git status
````
Der aktulle Status des lokalen Repository    

[Mehr Befehle](#shell)

### Branches
![Branches][Branches]
Quelle: https://www.patrickzahnd.ch/uploads/gitflow.png

Beim Erstellen eines neuen Repository gibt es nur einen **master** branch    
Im master branch befinden sich *funktionsfähige* Versionen   
Um am Projekt zu arbeiten erstellt man zum Beispiel:
* feature branches
* release branches
* hotfix branches     

### Merge 
Beim Merge(verschmelzen) werden die Änderungen der einzelnen Commits des Branches zusammengefasst und bei dem Ziel Branch angewendet.



----------------------------------------------------------------------------------
## Shell
Die Shell ist eine Benutzerschnittstelle die auf Unix läuft.    
[Mehr Details][Shell_url]
````bash
git --version
````
Gibt die aktuelle Versionsnummer von Git aus

````bash
ls <-l>
````
Zeigt die Ordnerstruktur an    
Mit dem Argument *-l* kann man es in Listenform anzeigen lassen

````bash
cd Verzeichnisname
````
Wechseld das Verzeichnis

````bash
gedit Dateiname
````
Zum bearbeiten von Textdateien

----------------------------------------------------------------------------------

[Github]:https://de.wikipedia.org/wiki/GitHub
[Stash]:https://git-scm.com/book/de/v1/Git-Tools-Stashen
[Shell_url]:https://de.wikipedia.org/wiki/Unix-Shell
[cheatsheet]:https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#emphasis

[Git-Data Trasport]:https://www.patrickzahnd.ch/uploads/git-transport-v1.png
[Branches]:https://www.patrickzahnd.ch/uploads/gitflow.png


