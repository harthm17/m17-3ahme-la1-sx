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


  ## Github 
  Laut [Wikipedia](https://de.wikipedia.org/wiki/GitHub)

  GitHub ist ein Onlinedienst, der Software-Entwicklungsprojekte auf seinen Servern bereitstellt (Filehosting). Die Dateien und Dokumente von jemandem, der mit der Gratisversion von Github arbeitet sind Open-Source(Das heißt jeder kann deine Software einlesen, verwenden und ändern). Damit man selbst nicht haftet, falls Dritte deine Software verwenden und jemand dabei zu Schaden kommt, kann man seine Software mit einer Lizenz versehen. Namensgebend war das [Versionsverwaltungssystem](https://de.wikipedia.org/wiki/Versionsverwaltung) [Git](https://de.wikipedia.org/wiki/Git). Ein Versionsverwaltungssystem erfasst Änderungen an Dokumenten oder Dateien. Alle vorherigen Versionen werden gesichert. Es kann eingesehen wer eine Datei verändert hat und wann jemand eine Datei verändert hat. Quelltext wird bei Github in Quelltext-Datenbanken den sogenannten Repositories gespeichert.
  ### Branches
  ![Branches](https://guides.github.com/activities/hello-world/branching.png)
Wenn man an einem Projekt mit mehreren Leuten arbeitet gibt es sehr viele Unterschiedliche Ideen und Funktionen. Einige davon sind einsatzbereit, manche nicht. Um eine Umgebung zu schaffen in der frei experimentieren kann man eine Art Verzweigung(Branch) schaffen. In dieser Branch kann man nun frei experimentieren, ohne dass die Master-Branch beeinflusst wird. Die Master-Branch ist immer funktionsfähig. Wenn man seinen Branch erstellt hat kann man auch schon Änderungen vornehmen. Wenn man eine Datei verändert, erstellt oder löscht macht man einen commit(etwas übergeben). Über Pull-Anfragen löst man  eine Diskussion über seine Commits aus. Da sie eng in das zugrunde liegende Git-Repository integriert sind, kann jeder genau sehen, welche Änderungen zusammengeführt werden, wenn er Ihre Anfrage akzeptiert. Mit GitHub können Sie aus einem Zweig einen endgültigen Test in der Produktion durchführen, bevor Sie zum Master zusammenführen(Deploy). Nachdem die Änderungen überprüft wurden kann man sie mit dem Master-Branch zusammenführen(Merge).

 ### Git-Befehle
 ![Befehle](https://i.pinimg.com/originals/cd/7c/15/cd7c15691839a4eaf41c71274f7ae98c.png)
 
 **git clone:** Kopiert remote repository, um auf einer eigenen Kopie arbeiten zu können. <br><br>
 **git add:** Mit git add werden Dateien in die sog. Index Area aufgenommen. Die Index Area umfasst alle Dateien, deren Inhalt vom nächsten commit erfasst werden sollen. Somit müssen vor einem commit alle zu erfassenden Dateien zur Index Area hinzugefügt werden.<br><br><br>
 **git status:** Der Befehl git status liefert Informationen über Dateien der eigenen Arbeitskopie und listet u.a Dateien, die seit dem letzen commit modifiziert oder hinzugefügt wurden. <br><br>
 **git commit**: Nachdem alle Dateien oder Änderungen mit git add hinzugefügt wurden, kann man nun über den Befehl git commit diese in local repository hochladen.<br><br>
 **git commit -a:** Gleich wie git commit nur wird mit diesem Befehl git add übersprungen.<br><br>
 **git push:** Lädt lokalen Arbeitsstand in das remote repository.<br><br>
 **git checkout:** Änderungen einer Datei verwerfen.<br><br>
 **git reset:** Alle Änderungen seit dem letzen commit verwerfen<br><br>
 
  
  
