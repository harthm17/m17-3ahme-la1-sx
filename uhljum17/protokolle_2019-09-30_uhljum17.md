# 1Protokoll
-----------------------------------------------------
* **Thema:** Verwaltungssystem (Github)
* **Datum:** 30.09.2019
* **Gefehlt:** -
* **Erstellt von:** Uhl Julian
* **Protokoll nächste Einheit:**

--------------------------------------------

## Inhaltsverzeichnis
1. [Versionsverwaltung](#versionsverwaltung)
    1. [Möglichkeiten zur formatierung](#Möglichkeitenzurformatierung)
    1. [Überschriften](#überschriften)
    1. [Listen](#listen)
    1. [Schriftarten](#schriftarten)
    1. [Ziate](#zitate)
    1. [Trennstriche](#trennstriche)
    1. [Absätze](#absätze)
    1. [Links](#links)
    1. [C-Code](#c-code)
1. [Git-Befehle](#git-befehle)
1. [Git-Ebenen](#git-ebenen)
3. [Branch](#branch)


---------------------------------------------

## Versionsverwaltung
Git ist eine freie Software zur Versionsverwaltung von Dateien. Man sollte mit Git arbeiten keine Daten/Informationen verloren gehen.

### möglichkeiten zur formatierung

Für normale schrift schreibt man einfach was ohne jedliche zeichen.

------------------------------------------
#### Überschriften
Überschriften werden mit  # gemacht kann bis zu sechs überschriten haben.

# ... (#)
## ... (##)
### ... (###)
#### ... (####)
##### ... (#####)
###### ... (######)
---------------------------------------------
#### Listen
Listen kann man logischreweise mit 1.  2.  3. ... es ist wäre jedoch vom vorteil wenn man immer 1.  1.  1. schreibt falls man etwas vergisst fenn dann muss man nicht alles umändern.

Bsp.

1. A
1. B
1. C
.
.
.
------------------------------------------------

#### Schriftarten

Man kann Schrift Fett, Kursiv oder beides machen um z.B. einzelne Sachen hervorzuheben. Man macht Sachen fett wenn man vor und nach dem Wort oder einen Satz ** mach (**ABC**). Mit Kursiv funktioniert es gleich jedoch nur mit einem * (*ABC*). Beides kann man auch dann mit mit *** vor und nach dem Wort machen. (***ABC***)

----------------------------------------------

#### Zitate

Zitate werden mit einen > zeichen gemacht, wenn das Zitat über mehrere Zeilen geht dann schreibt man den Text in eine Klammer

Bsp. 

> ABCDEFG...

> (A
   B
   C
   D)

-----------------------------

#### Trennstriche

Trennstriche macht man mit ----------------- vielen Minusen. einen dicken Trennstrich macht man mit einen Abssatz über und unter den geschriebenen. Einen dünnen macht man einfach mit vielen Minusen direkt über und unter dem geschriebnen.

Bsp. 

---------------------

ABC
---------------------

#### Absätze
Absätze macht man ganz einfach mit 2 mal Enter.
Bsp. 

ABC

ABC

ABC

--------------------

#### Links 
Links macht man mit [ABC] (https://...) machen.

Bsp. 

[ABC](https://lms.at)

um z.B. am Ende dieses Protkolls alle Links gebündelt zu schreiben kann man es so machen. 

[ABC]  [1]

[1] : https://lms.at

------------------------

#### C-Code

wenn man über und unter den Text (``` C)  macht wird der Text wie in z.B. Code Blocks dagestellt.

```C
int main () 
{
    printf("Hallo");
    return 0;
}
```

-------------------------

### Git-Befehle 

-------------------------

1. **Zentrales Repository klonen, um auf einer eigenen Kopie arbeiten zu können:**

    • **Lokales Repository klonen:** git clone <Pfad-zum-Repository> [Verzeichnis-Name] 
    
    • **Repository von einem Server klonen:** git clone <Server-Name>:<Pfad-zum-Repository> [Verzeichnis-Name]
    
--------------------------------    
    
1.  **Hat man ein ganz neues leeres Git-Repository geklont, so muss dies zunächst noch initialisiert werden:**

    cd <Repository-Name> 
    
    touch .gitignore 
    
    git add .gitignore git commit -a -m "Initial commit" 
    
    git push -u origin master
--------------------------------

1.  **Dateien oder ganze Verzeichnisse unter Git-Verwaltung stellen:**

    git add <Datei-/Verzeichnisname>
    
------------------------------

1. **NachdemalleDateienfürdennächstenCommit mitgit addhinzugefügtwurden, so kann dieser abgesetzt werden:** 

    git commit -m"..." 
--------------------------------

1. **Alternativ kann die Einstellung auf Git beschränkt werden:**

    git config --global core.editor "<Editor-Name>" 
    
    Die Option --global bewirkt, dass die Einstellung für alle Git-Repositories übernommenwird.OhneAngabevon --global   
    werdenOptionennurindem Repository angewendet, in dem man sich gerade beﬁndet.  
    
------------------

1. **Repository-Status abfragen: **

    git status
    
------------------

1. **Lokalen Arbeitsstand in das entfernte Repository einpﬂegen: **

    git push
 
-----------------

1. **Neuesten Stand eines entfernten Zweiges in den lokalen tracking branch einﬂießen lassen: **

    git merge origin/<Zweig-Name>
    
-----------------

1. **Alle Änderungen seit dem letzten Commit verwerfen: **
    
    git reset --hard HEAD 
    
 
Quelle: https://pgi-jcns.fz-juelich.de/pub/doc/git_gitflow.pdf

------------------------------

### Git-Ebenen

--------------------------------

Dateien bzw Aktionen werden einer der folgenden fünf Ebenen zugeordnet:

**Stash (verstecken)**

Hier "parkt" man Änderungen während etwas anderes gemacht wird.

-------------------------------------------------------------

**Workspace (Arbeitskopie)**

Hier ist der lokale checkout aus dem Repository

-------------------------------------

**Index (staging area, staged files)**

Hier sind jene Dateien die im nächsten commit enthalten sind

----------------------------------

**Local repository**

Lokales Repository im Verzeichnis .git

----------------------------------------

**Remote Repository (Upstream Repository)**

Repository auf einem entfernten Git-Server.


Quelle: https://www.htl-mechatronik.at/e-books/sx/html/git/git.html#(4)

--------------------------------------------------

### Branch

------------------------------------------------

![Branches](https://guides.github.com/activities/hello-world/branching.png)

Eine Verzweigung besteht im Kern aus einer eindeutigen Reihe von Codeänderungen mit einem eindeutigen Namen. Jedes Repository kann einen oder mehrere Branches haben.

Standardmäßig heißt der erste Branch "master".

Quelle: https://www.digitalocean.com/community/tutorials/how-to-use-git-branches
