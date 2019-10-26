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
  
  
  ## Github
[Github](https://de.wikipedia.org/wiki/GitHub) ist ein Onlinedienst, der Software-Entwicklungsprojekte auf seinen Servern bereitstellt. Github stellt auch eine Gratisversion zur verfügung (Open-Source), jedoch kann jeder deine Software einlesen, verwenden und ändern. Zum Schutze gegen eine Anklage falls deine Software nicht funktioniert kann man die besagte Software mit einer Lizenz versehen. Namensgebend war das [Versionsverwaltungssystem](https://de.wikipedia.org/wiki/Versionsverwaltung) [Git](https://de.wikipedia.org/wiki/Git). Ein Versionsverwaltungssystem erfasst Änderungen an Dokumenten oder Dateien. Es werden alle vorherigen Versionen gesichert. Der Quelltext wird bei Github in sogenannte Repositories (Quelltext-Datenbanken) gespeichert.

  ### Branches
  ![Branches](https://guides.github.com/activities/hello-world/branching.png)
Wenn an einem Projekt mehrere Personen arbeiten existieren viele unterschiedliche Ideen und Funktionen. Um eine Arbeitsumgebung zu erschaffen in der man frei experimentieren kann, wird eine Verzweigung (Branch) erstellt. Bei einem neuen Experiment wird nicht die Master-Branch verändert, dazu ist sie immer funktionsfähig. Hat man einen eigenen Branch erstellt kann man Änderungen vornehemen. Wird eine Datei verändert, erstellt oder gelöscht wir ein commit (etwas übergeben) ausgeführt. Mit einer Pull-Anfrage wird eine Diskussion über seinen commit erstellt. Daher das sie eng mit dem Git-Repository integriert sind, kan jeder sehen, welche Änderungen vorgenommen wurden, wenn Ihre Anfragen akzeptiert wurden. Eine Datei die sich noch in Produktion befindet kann in Github als Test schon durchgeführt werden, bevor man diese mit dem Master-Branch zusammenführt (Deploy). Nach der Überprüfung aknn man die Änderung mit dem Master-Branch zusammenführen (Merge).

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
