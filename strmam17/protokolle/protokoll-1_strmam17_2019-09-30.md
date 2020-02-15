# Protokoll Labor 3AHME (2019-09-30)
* **Thema**: Markdown(Github), Git
* **Datum**: 30.09.2019
* **Gefehlt**:   -
* **Erstellt von**: strmam17
* **Protokoll letzte Einheit**:
* **Protokoll nächste Einheit**: [2.Protokoll](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/strmam17/strmam17/protokolle/protokoll-2_strmam17_2019-10-14.md)
----------------------------------------------------------------------------------------------------------------------------------------
## Inhaltsverzeichnis
   1. [Github](#github)
         * [Vorteile](#vorteile) 
         * [Grundsachen](#grundsachen)    
   2. [Terminal](#terminal)
         * [Befehle](#befehle)      
   3. [Git](#git)
         * [Clonen](#clonen)
         * [Datei zurück auf den Server bringen](#datei-zurück-auf-den-server-bringen)
         * [Merge](#merge)
         * [Branch](#branch)
            
----------------------------------------------------------------------------------------------------------------------------------------
## Github
  ### Vorteile
      1. es kann nichts verschwinden
      2. es ist alles nachvollziehbar
      3. es ist sehr gut für Gruppenarbeiten (erforderlich bei professionellen Gruppenarbeiten)
      4. es ist gratis außer es darf nicht öffentlich sein
      5. es geht sehr schnell
      6. es kann keiner was stehlen, da es sowieso schon öffentlich ist
      7. es kann kein anderer ein Patent auf deine hochgeladenen Sachen anmelden 
      8. andere könnten Fehler entdecken und dich darauf hinweisen
            
  ### Grundsachen
   1. Die Lizens ist sehr wichtig damit man rechtlich abgesischert ist.
   2. Überschriften macht man mit Hashtags (bis zu 6 hashtags): 
   
     # h1
     ## h2
     ### h3
     #### h4
     ##### h5
     ###### h6
   
   3. Liste erstellen: 
                  
     *text
     *text
     *text
   
     1.
     2.
     3.
       
   4. Fett schreiben: 
       
    **Fett**
   5. Kursiv schreiben: 
      
    *Kursiv*
   6. Durchgestrichen: 
   
    ~~Durchgestrichen~~
   7. Unterstreichen geht nicht!
   8. Zeichen für ein Zitat: 
   
    >Zitat
   9. Link einer Webseite: 
   
    [Name](Link)
  10. Inhaltsverzeichnis: 
  
    [Überschrift](#überschrift)
  11. Computersprache

```c
    ```C
    int main () 
    {
    printf("Hallo");
    return 0;
    }
    ```
 ```
  12. Text grau hinterlegen: zweimal Tabulatoren Taste drücken
----------------------------------------------------------------------------------------------------------------------------------  
  ## Terminal
      strg + oder -: größer oder kleiner
  ### Befehle
      strg l: Bildschirm wird nach oben geschoben
      reset: löscht den Bildschirm
      history: zeigt die eingegebenen Befehle
      exit: zum Schließen damit die history nicht gelöscht wird
      Pfeil nach oben oder !<Befehl>: Kommandos können wiederholt werden
      cd <Verzeichniss>: in ein anderes Verzeichniss kommen
      ls -l: abgelegte Dateien
 ---------------------------------------------------------------------------------------------------------------------------------     
  ## Git
   Man kann sich die eigenen Daten von Github auf seinen eigenen Rechner clonen.
   Die Daten kann man dann am eigenen Rechner im Terminal bearbeiten.
   Nachdem man sie bearbeitet hat kann man sie wieder hochladen.
   Bei einem Projekt mit mehreren Leuten ist es gut wenn sich ein jeder die Daten clonen würde da es sicherer ist.
                     
        Remote repository: Dein repository am Server
        Local repository: Dein repository am eigenen Rechner
        Stash: Zwischenspeicher für Änderungen
        Workspace: Speicherplatz für deine Dateien des repository
   ![Git](https://softganz.com/upload/pics/git-transport-v1.png)
   Quelle: https://softganz.com/upload/pics/git-transport-v1.png
   
  ### Clonen
      
         Terminal eingabe: zum clonen der Datei: git clone https://github.com/<Autor>/<Datei>
                           ins richtige Verzeichniss: cd <Datei>
                           die Datei öffnen: gedit README.md
                           Microsft Visual Studio: code ~/<Datei>/README.md
                           
  ### Datei zurück auf den Server bringen
  
         Terminal eingabe: git add README.md          //Wenn man alles hinzufügen will dann: git add -A
                           git status
                           git commit -m "Update README.md"
                           Eingabe des Benutzers damit der Rechner weiß wer man ist: git config --global user.email "<Email>"
                                                                                     git config --global user.name "<Name>"
                           git commit -m "Update README.md"
                           git push
                           Dann muss man noch Benutzername und Passwort eingeben
                           
  ### Merge
      (zusammenführen)
      Beim Merge werden die Änderungen von verschiedenen Personen in deren Projekt zusammengeführt.
   ![Merge](https://cdn-images-1.medium.com/max/1600/1*RTgn1s0GY8r0rSPsAzf8NQ.png)
   Quelle: https://cdn-images-1.medium.com/max/1600/1*RTgn1s0GY8r0rSPsAzf8NQ.png
      
  ### Branch
      (Ast)
      Der Master Branch ist der Hauptast, wenn man nicht im Master Branch arbeiten will, 
      dann macht man sich einen Nebenbranch, 
      danach kann man den Nebenbrunch wieder in den Master Brunch zurück bringen
      
      Branch erstellen: git checkout -b <Name des neuen Branch>
      Nach einer Änderung der Datei: git push --set-upstream origin <Name des neuen Branch>
      Zurück in den Master Branch bringen: git checkout master C
                                         git merge work C
                                         git status
                                         git push
      
      Nach diesem Vorgang sind beide Braches wieder zusammengeführt.
                           
