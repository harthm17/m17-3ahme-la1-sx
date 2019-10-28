# Protokoll m17-3ahme-la1

-----

**Name**: Andreas Augustin  
**Datum**: 21.10.2002  
**Klasse**: 3AHME  
**Gruppe**: 1  
**Gefehlt**: /

-----

## Inhaltsverzeichniss:

1) [Versionsverwaltung](#versionsverwaltung) 
1) [Git](#git)
1) [Markdown](#markdown)
1) [Formatierung](#formatierung)
    * [Schriftformatierung](#Schriftformatierung) 

-----

## Versionsverwaltung:

 Es können mehrere Leute gleichzeitig an einem Projekt Arbeiten.  
 Das heißt das jeder an seinem Teil des Projektes Arbeiten und dann den aktuellen Stand wieder hochladen kann.

-----

## Git:

* Git ist eine freie Software zur verteilten Versionsverwaltung von Dateien, die durch Linus Torvalds initiiert wurde.
```
Torvalds wünschte sich ein verteiltes System, das wie BitKeeper genutzt werden kann und die folgenden  
Anforderungen erfüllt:
1) Unterstützung verteilter, BitKeeper-ähnlicher Arbeitsabläufe
2) Sehr hohe Sicherheit gegen sowohl unbeabsichtigte als auch böswillige Verfälschung
3) Hohe Effizienz

Quelle: [Wikipedia] [Wikipedia Geschichte]
```
* Repository ≙ Datenbank in dem sämtliche Dateien enthalten sind.  
Es gibt also den *remote-Repository* auf den alle Mitglieder zugreifen können und ebenso hat jeder sein eigenes  
*local-Repository*

![Bild](https://www.stephenmarron.com/wp-content/uploads/2017/02/git.png)  
*Quelle:* https://www.stephenmarron.com/wp-content/uploads/2017/02/git.png 

**Bedeutung einzelner Begriffe:**

* git stash   --> Hier werden Dateien im Hintergrund in einem Stack gespeichert. Diese kannst Du dann jederzeit wieder vom Stack holen und auf Dein Arbeitsverzeichnis anwenden.  
* git add     --> Mit git add werden Dateien in die sog. Staging Area aufgenommen. Die Staging Area umfasst alle Dateien, deren aktueller Inhalt beim nächsten Commit erfasst werden soll  .
* git commit  --> Hier kann man nach dem git add änderungen Protokollieren.
* git push    --> Hier wird das Dokument **online** Hochladen.  

**Der Workflow:**  


![Bild](https://arccwiki.uwyo.edu/images/1/19/GitHub_Flow_steps.png)  
*Quelle:* https://arccwiki.uwyo.edu/images/1/19/GitHub_Flow_steps.png 

-----

## Markdown:

>*Markdown* ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde. Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere Konvertierung leicht lesbar ist. Als Auszeichnungselemente wurden daher vor allem Auszeichnungsarten verwendet, die in Plain text und E-Mails üblich sind. Auch andere Auszeichnungssprachen mit ähnlichen Zielen zur Lesbarkeit – wie reStructuredText oder Textile – hatten Einfluss auf die Syntax. Der MIME-Type lautet text/markdown.

Quelle: [Wikipedia] [Markdown]

* Der Vorteil bei Markdown ist, das man es überall leserlich abrufen kann und das es mit den meisten Open Source Programmen kompatibel ist.

-----

## Formatierung:

Ein Absatz wird mit zwei Leerzeichen am Ende einer Zeile gemacht oder gleich mit einer leeren Zeile.
Ein Queltext oder Zitat wird mit ( ´´´ ) gemacht. Man kann zusätzlich hinter den ´´´C oder eine andere Programmiersprache schreiben damit der Queltext entsprechende Farben bei Schlüsselwörter aufweist.  

```C
#include <stdio.h>

int main () {
   printf ("TEST");
   return 0;
}
```

Tabellen werden mit | formatiert. In der Zwischenzeile kommen Trennstriche mit Bindestriche.

Schriftart    | Größe       | Programm
--------------|-------------|------------
Arial         | 12          | Libre Office

Ein Zitat wird mit (>) vor dem Text gemacht.  
> Das ist ein sinnloses Zitat.

Ein Trennstrich wird mit beliebig vielen Bindestrichen gemacht.

-----

Aufzählungen kann man mit ( * ) oder mit ( 1) ) machen. Man kann bei der Aufzählungen immer 1) schreiben da die Nummierung selbst stattfindet. Das hat den Vorteil das wenn man etwas in einer Liste Hinzufügt muss man nicht alle Nummern selbst wechseln.  

***Beispiel Liste:***
* Audi
* BMW

1) Skoda
1) Mercedes

### Schriftformatierung:

* Es gibt sechs größen von Überschriften. 
* Vor jener Überschrift muss die gewählte Größe somit die Hash's vor dem Wort stehen jedoch mit einem Leerzeichen Abstand.
# Überschrift (#)
## Überschrift (##)
### Überschrift (###)
#### Überschrift (####)
##### Überschrift (#####)
###### Überschrift (######)  
  
**"Fett" geschriebenes wird mit zwei**  **  **vor und nach dem Wort gemacht.**  

*Kursive Wörter werden mit einem* * *vor und nach dem Wort gemacht.*  

***Kursiv und Fett geschriebene Wörter werden mit drei***  ***  ***vor und nach dem Wort gemacht.***    

~~Durchgestrichene~~ Wörter werden mit zwei ~~ vor und nach dem Wort gemacht.  

`Grau` hinterlegte Wörter werden mit einem ' vor und nach dem Wort gemacht.


[Wikipedia Geschichte]: https://de.wikipedia.org/wiki/Git 
[Markdown]: https://de.wikipedia.org/wiki/Markdown
