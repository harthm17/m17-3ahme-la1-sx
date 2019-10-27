# Protokoll LA1/sx AHME17 (2019/20)
-------------------------------------------------------------
  * **Thema:** Github und Markdown
  * **Datum:** 20.09.2019
  * **Gefehlt:** ---
  * **Erstellt von:** Raphael Golser
  --------------------------------------------------------------
  ## Inhaltsverzeichnis
  1. [Github](#github)
     1. [Branches](#branches)
     1. [Git-Befehle](#git-befehle)
  1. [Markdown](#markdown)
     1. [Vorteile](#vorteile)
  1. [Textformatierung im Markdown](#textformatierung-im-markdown)
     1. [Absätze](#absätze)
     1. [Text mit grauen Hintergrund hervorheben](#text-mit-grauen-hintergrund-hervorheben)
     1. [Zitate](#zitate)
     1. [Listen](#listen)
     1. [Fette Wörter](#fette-wörter)
     1. [Kursive Wörter](#kursive-wörter)
     1. [Überschriften](#überschriften)
     1. [Verlinken](#verlinken)
     1. [Horizontale Linien einfügen](#horizontale-linien-einfügen)
     1. [Bilder einfügen](#bilder-einfügen)
  
  ## Github
[Github](https://de.wikipedia.org/wiki/GitHub) ist ein Onlinedienst, der Software-Entwicklungsprojekte auf seinen Servern bereitstellt. Github stellt auch eine Gratisversion zur verfügung (Open-Source), jedoch kann jeder deine Software einlesen, verwenden und ändern. Zum Schutze gegen eine Anklage falls deine Software nicht funktioniert kann man die besagte Software mit einer Lizenz versehen. Namensgebend war das [Versionsverwaltungssystem](https://de.wikipedia.org/wiki/Versionsverwaltung) [Git](https://de.wikipedia.org/wiki/Git). Ein Versionsverwaltungssystem erfasst Änderungen an Dokumenten oder Dateien. Es werden alle vorherigen Versionen gesichert. Der Quelltext wird bei Github in sogenannte Repositories (Quelltext-Datenbanken) gespeichert.
  ### Branches
  ![Branches](https://guides.github.com/activities/hello-world/branching.png)
Wenn an einem Projekt mehrere Personen arbeiten existieren viele unterschiedliche Ideen und Funktionen. Um eine Arbeitsumgebung zu erschaffen in der man frei experimentieren kann, wird eine Verzweigung (Branch) erstellt. Bei einem neuen Experiment wird nicht die Master-Branch verändert, dazu ist sie immer funktionsfähig. Hat man einen eigenen Branch erstellt kann man Änderungen vornehemen. Wird eine Datei verändert, erstellt oder gelöscht wir ein commit (etwas übergeben) ausgeführt. Mit einer Pull-Anfrage wird eine Diskussion über seinen commit erstellt. Daher das sie eng mit dem Git-Repository integriert sind, kan jeder sehen, welche Änderungen vorgenommen wurden, wenn Ihre Anfragen akzeptiert wurden. Eine Datei die sich noch in Produktion befindet kann in Github als Test schon durchgeführt werden, bevor man diese mit dem Master-Branch zusammenführt (Deploy). Nach der Überprüfung kann man die Änderung mit dem Master-Branch zusammenführen (Merge).
  ### Git-Befehle
  ![Befehle](https://i.pinimg.com/originals/cd/7c/15/cd7c15691839a4eaf41c71274f7ae98c.png)

`git clone`: Kopiert remote, repository, um auf einer eigenen Kopie zu arbeiten.
z.B.:
```bash 
git clone https://github.com/HTLMechatronics/m17-3ahme-la1-sx.git
``` 
`git add`: Mit `git add` werden Datein in den *Index-Bereich* aufgenommen. Diese umfasst alle Dateien, deren Inhalte vom nächsten commit erfasst werden sollen. Deshalb können vor einem commit alle zu erfassenden Dateien zum *Index-Bereich* hinzugefügt werden.

`git status`: Dieser Befehl liefert Informationen über die gewünschte Datei die eine Arbeitskopie ist, u.a. listet dieser auch noch Dateien auf die seit dem letzten *commit* verändert oder hinzugefügt worden sind.

`git commit`: Nachdem `git add` ausgeführt worden ist, ladet dieser die hinzugefügten Dateien in das *local repository* hoch.

`git commit-a`: Hat die gleiche Funktion wie `git commit` nur wird der Vorgang `git add` übersprungen.

`git push`: Jetzt wird die Datei vom *local repository* in das *remote repository* hochgeladen.

`git checkout`: Die Änderungen einer bestimmten Datei werden verworfen.

`git reset`: Alle Änderungen der Datei werden zum Zeitunkt des letzten *commits* verworfen.

------------------------------------------------------------------------------------------------------
  ## Markdown
  Laut [Wikipedia](https://de.wikipedia.org/wiki/Markdown)
  >Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde. Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere Konvertierung leicht lesbar ist. Als Auszeichnungselemente wurden daher vor allem Auszeichnungsarten verwendet, die in Plain text und E-Mails üblich sind. Auch andere Auszeichnungssprachen mit ähnlichen Zielen zur Lesbarkeit – wie reStructuredText oder Textile – hatten Einfluss auf die Syntax. Der MIME-Type lautet text/markdown.
Eine Markdown-Konvertierungssoftware wandelt Text in gültiges und W3C-konformes XHTML um. Die Referenzimplementierung in Perl steht unter einer BSD-artigen Lizenz. Weiter sind inzwischen Implementierungen in den gängigsten Programmiersprachen wie PHP (z. B.[3]), Python (z. B.[4]) oder JavaScript (z. B.[5]) sowie R verfügbar.
  ### Vorteile
  * Markdown-Texte werden mit jedem Textwerkzeug editiert.
  * Diese Texte sind auf jeder Plattform aufrufbar, lesbar und editierbar.
  * Viele Open-Source Programme, Programmiersprachen und Plattformen unterstützen Markdown.
  * Markdown-Texte sind Platzsparend.
  * Mit Textverarbeitugsprogrammen ist amn mit dem Speichern auf der sicheren Seite, aber daher das es so viele Formatierungsmöglichkeiten gibt dauert es länger als wenn man es mit Hand schreiben würde. Mit Markdown hat man beide Vorteile drinnen, es ist schnell zu schreiben und man hat ein paar der Formatierungen der Textverarbeitungsprogrammen und die Dateien gehen auch nicht einfach verloren.
  ### Textformatierung im Markdown
  #### Absätze
  Ein Absatz wird durch eine leere Zeile eingefügt
   
    Adam
    
    Bdam
 
  #### Text mit grauen Hintergrund hervorheben
  Um dem Hintergrund in einer Zeile einen grauen Ton zu verpassen muss man nur zweimal hinteianander die Tabulatortaste drücken,
  
    Adam
    
  aber wenn man nur ein einzelnes Wort mit `grauen` Hintergrund haben will muss man nur man Anfang und am Ende ein ´ (in die andere Richtung) machen, diese Weise Funktioniert auch mit Sätzen oder mehrereren Wörtern. (ohne einem Absatz)
  #### Zitate
  Ein Zitat wird mit dem > Zeichen erstellt
  > Adam geht in den Wald
  #### Listen
  Eine Liste ohne einer Aufzählung wird mit einem * am Zeilenanfang und einem Leerzeichen erstellt.
  * Adam
  * Bdam
  * Cdam
  
  Bei einer Aufzählung das gleiche nochmal nur mit Zahlen (Zahl ist egal es muss nur mit einem 1ser anfangen, weil wird von selbst sotiert).
  1. Adam
  3. Bdam
  1. Cdam
  #### Fette Wörter
  Um etwas **fett** zu schreiben muss am Anfang und am Ende des Wortes zwei * Zeichen stehen.
  #### Kursive Wörter
  Um ein Wort *kursiv* zu schreiben wird ein * am Anfang und am Ende des Wortes hinzugefügt.
  #### Überschriften
  Eine Überschrift erstellt man mit einer # am Anfang der Zeile + einem Leerzeichen. Für Unterüberschriften wird jeweils eine # hinzugefügt.
  # Adam
  ## Bdam
  ### Cdam
  #### Bob
  #### Programiersprachen
  Um eine bestimmte Programmiersprache zu kennzeichnen muss man das gleiche wie bei Bsp. 2 im Punkt [Text mit grauen Hintergrund hervorheben](#text-mit-grauen-hintergrund-hervorheben) nur mit drei Zeichen machen und danach die Programiersprache angeben einen Absatz Abstand und dann am Ende nochmal dreimal das Zeichen.
  ```C
  int main()
{
    printf("Hello world!\n");
    return 0;
}
```
  #### Verlinken
  Nachdem man in ekigen klammern den Namen der Website geschrieben hat, wird eine normale Klammer mit der URL angeschlossen.
  
  `[Wikipedia](https://de.wikipedia.org/wiki/GitHub)`[Wikipedia](https://de.wikipedia.org/wiki/GitHub)
  #### Horizontale Linien einfügen
  Horizontale Linien können mit drei oder mehreren Bindestrichen oder Sternchen erstellt werden (Leerzeichen dazwischen sind erlaubt).
  ```
  ------------
  **************
   _ _ _ 
   ```
   #### Bilder einfügen
   Hier fast das gleiche wie beim verlinken jedoch wird vorne ein ! hinzugefügt.
   `[Alt-Text](/Pfad/zum/Bild.jpg)`
