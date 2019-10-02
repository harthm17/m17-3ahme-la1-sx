# Protokoll La1/SX 3AHME (2019/20)
--------------------------------------------------
  * **Thema:** Github und Markdown
  * **Datum:** 30.09.2019
  * **Gefehlt:** ---
  * **Erstellt von:** Michael Ully
  * **Protokoll letzte Einheit:**
  * **Protokoll nächste Einheit:** 
  --------------------------------------------------
  ## Inhaltsverzeichnis
  1. [Github](#github)
     1. [Branches](#branches)
     1. [Git-Befehle](#git-befehle)
  2. [Markdown](#markdown)<br>
     2. [Vorteile von Markdown](#vorteilevonmarkdown)
  3. [Formatieren von Text mit Markdown](#formatierenvontextmitmarkdown)
     3. [Absatz](#absatz)


  ## Github 
  Laut [Wikipedia](https://de.wikipedia.org/wiki/GitHub)

  GitHub ist ein Onlinedienst, der Software-Entwicklungsprojekte auf seinen Servern bereitstellt (Filehosting). Die Dateien und Dokumente von jemandem, der mit der Gratisversion von Github arbeitet sind Open-Source(Das heißt jeder kann deine Software einlesen, verwenden und ändern). Damit man selbst nicht haftet, falls Dritte deine Software verwenden und jemand dabei zu Schaden kommt, kann man seine Software mit einer Lizenz versehen. Namensgebend war das [Versionsverwaltungssystem](https://de.wikipedia.org/wiki/Versionsverwaltung) [Git](https://de.wikipedia.org/wiki/Git). Ein Versionsverwaltungssystem erfasst Änderungen an Dokumenten oder Dateien. Alle vorherigen Versionen werden gesichert. Es kann eingesehen wer eine Datei verändert hat und wann jemand eine Datei verändert hat. Quelltext wird bei Github in Quelltext-Datenbanken den sogenannten Repositories gespeichert.
  ### Branches
  ![Branches](https://guides.github.com/activities/hello-world/branching.png)
Wenn man an einem Projekt mit mehreren Leuten arbeitet gibt es sehr viele Unterschiedliche Ideen und Funktionen. Einige davon sind einsatzbereit, manche nicht. Um eine Umgebung zu schaffen in der frei experimentieren kann man eine Art Verzweigung(Branch) schaffen. In dieser Branch kann man nun frei experimentieren, ohne dass die Master-Branch beeinflusst wird. Die Master-Branch ist immer funktionsfähig. Wenn man seinen Branch erstellt hat kann man auch schon Änderungen vornehmen. Wenn man eine Datei verändert, erstellt oder löscht macht man einen commit(etwas übergeben). Über Pull-Anfragen löst man  eine Diskussion über seine Commits aus. Da sie eng in das zugrunde liegende Git-Repository integriert sind, kann jeder genau sehen, welche Änderungen zusammengeführt werden, wenn er Ihre Anfrage akzeptiert. Mit GitHub können Sie aus einem Zweig einen endgültigen Test in der Produktion durchführen, bevor Sie zum Master zusammenführen(Deploy). Nachdem die Änderungen überprüft wurden kann man sie mit dem Master-Branch zusammenführen(Merge).

 ### Git-Befehle
 ![Befehle](https://i.pinimg.com/originals/cd/7c/15/cd7c15691839a4eaf41c71274f7ae98c.png)
 
 **git clone:** Kopiert remote repository, um auf einer eigenen Kopie arbeiten zu können.<br> z.B git clone https://github.com/ullmim17/Labor <br><br>
 **git add:** Mit git add werden Dateien in die sog. Index Area aufgenommen. Die Index Area umfasst alle Dateien, deren Inhalt vom nächsten commit erfasst werden sollen. Somit müssen vor einem commit alle zu erfassenden Dateien zur Index Area hinzugefügt werden.<br><br><br>
 **git status:** Der Befehl git status liefert Informationen über Dateien der eigenen Arbeitskopie und listet u.a Dateien, die seit dem letzen commit modifiziert oder hinzugefügt wurden. <br><br>
 **git commit**: Nachdem alle Dateien oder Änderungen mit git add hinzugefügt wurden, kann man nun über den Befehl git commit diese in local repository hochladen.<br><br>
 **git commit -a:** Gleich wie git commit nur wird mit diesem Befehl git add übersprungen.<br><br>
 **git push:** Lädt lokalen Arbeitsstand in das remote repository.<br><br>
 **git checkout:** Änderungen einer Datei verwerfen.<br><br>
 **git reset:** Alle Änderungen seit dem letzen commit verwerfen<br><br>
 
  ------------------------------------------------------------------------------------------
  ## Markdown
  Laut [Wikiepdia](https://de.wikipedia.org/wiki/Markdown)<br>
  Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde. Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere Konvertierung leicht lesbar ist. Als Auszeichnungselemente wurden daher vor allem Auszeichnungsarten verwendet, die in Plain text und E-Mails üblich sind. Auch andere Auszeichnungssprachen mit ähnlichen Zielen zur Lesbarkeit – wie reStructuredText oder Textile – hatten Einfluss auf die Syntax. Der MIME-Type lautet text/markdown.
Eine Markdown-Konvertierungssoftware wandelt Text in gültiges und W3C-konformes XHTML um. Die Referenzimplementierung in Perl steht unter einer BSD-artigen Lizenz. Weiter sind inzwischen Implementierungen in den gängigsten Programmiersprachen wie PHP (z. B.[3]), Python (z. B.[4]) oder JavaScript (z. B.[5]) sowie R verfügbar.

  ### Vorteile von Markdown
  * Markdown-Texte editiert man mit jedem Textwerkzeug. <br>
  * Markdown-Textdateien sind leichtgewichtig. <br>
  * Markdown-Texte sind auf jeder Plattform lesbar.<br>
  * Markdown wird von zahlreichen (kostenlosen) Programmen, Programmiersprachen und Plattformen unterstützt.<br>
  * Wenn man etwas auf Papier schreibt ist man zwar schnell, aber Papier geht leicht verloren und über Textverarbeitungsprogramme geschriebene Dokumente gehen zwar nicht verloren, aber man braucht aufgrund der vielen Formatierungsmöglichkeiten länger. Markdown verbindet die Vorteile von Schreiben über Textverarbeitung und Schreiben mit Hand, weil das Geschriebene nicht verloren gehen kann, man mit Markdown schneller ist und es trotzdem ein paar Formatierungen gibt.<br> <br>
  
  ### Formatieren von Text mit Markdown
  
  #### Absatz
  Einen Absatz kann man über eine leere Zeile einfügen
  
    Text1

    Text2
  
  #### Text grau hervorheben
  Um einen Text grau hervorzuheben muss man zweimal hintereinander die Tabulatortaste betätigen.
  
    Beispiel
    
  #### Zitat
  Über das > Zeichen kann ein Zitat erstellen
  
  > Beispiel
  
  #### Listen
  Um eine unsortierte Liste zu erstellen einen Stern vor das zu Listende schreiben. 
  * A
  * B
  * C
  * D<br>
  Bei einer sortierten Liste das Gleiche mit Zahlen.
  1. A
  2. B
  3. C
  4. D
  
  #### Fett
  Um etwas Fett zu schreiben Text mit zwei * einklammern.
  
  **Beispiel**
  
  #### Kursiv
  Um etwas Kursiv zu schreiben Text mit einem * einklammern. z.B * Bsp *
  
  *Beispiel*
  
  #### Überschrift
  Um Überschriften zu erstellen einen oder mehr # vor die Überschrift schreiben.
  
  # Überschrift1
  ## Überschrift2
  ### Überschrift3
  #### Überschrift4
  
  #### Code
  Um einen Code zu kennzeichnen. Beispiel mit einem C-Code: 
  ```C
  int main()
{
    printf("Hello world!\n");
    return 0;
}
```

  #### Links
 Um einen Inline-Link zu erstellen schreibt man direkt hinter der schließenden eckigen Klammer normale Klammern. In diese Klammern wird die URL geschrieben auf die verlinkt werden soll zusammen mit einem optionalen Titel für den Link in Anführungsstrichen. Beispiele:
 
    [Wikipedia](https://de.wikipedia.org/wiki/GitHub)
 [Wikipedia](https://de.wikipedia.org/wiki/GitHub)<br>
 
 Ein Referenz-Link wird folgendermaßen erstellt. Links können gebündelt an einer Stelle des Dokuments eingefügt werden.
 
 [Name][id]<br>
 [1]https:///github.com
 
 #### Horizontale Linien
 Der Tag für horizontale Linien kann generiert werden indem 3 oder mehr Bindestriche oder Sternchen allein auf einer Zeile geschrieben werden. Leerzeichen zwischen den Zeichen sind auch erlaubt. Alle folgenden Beispiele würden eine horizontale Linie generieren:<br>
  
    --------
    *********
    - - -
  #### Bilder
    ![Alt-Text](/Pfad/zum/Bild.jpg)
  
