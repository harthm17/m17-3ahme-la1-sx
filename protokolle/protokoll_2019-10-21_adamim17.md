# m17-3ahme-la1-sx 1. Protokoll 
-----------------------------
### Erstellt:
  * 26.10.2019
  * Mike Adam (adamim17)
-----------------------------
  
 ## Inhaltsverzeichniss:
 1) [Versionsverwaltung](#versionenverwaltung)
 2) [git](#git)
 3) [GitHub](#github)
 4) [Git Ebenen und Commands](#git-ebenen-und-commands)
    * [Ebenen](#ebenen)
    * [Commands](#commands)
 5) [Github Workflow](#github-workflow)
    * [Ablauf](#ablauf)
 6) [GitWeb](#gitweb)
 7) [Markdown](#markdown)
 8) [Formatierung bei Markdown](#formatierung-bei-markdown)
-----------------------------
 ## Versionenverwaltung:
 * ermöglicht **mehreren** leuten an **einem** Projekt zu arbeiten
 * man kann auf alte Backups zugreifen, wenn ein neues feherhaft ist
 
 ## git:
 * Software zur Versionsverwaltung
 * auch offline verfügbar
 * Repositories werden lokal gespeichert
 
 ## GitHub:
 * ist ein online-Dienst 
 * Kostenlose Registrierung 
 * Kostenlose öffentliche Repositories

 ## Git Ebenen und Commands:
 ### Ebenen:
 * Stash (verstecken)
 * Workspace (Arbeitskopie)
 * Index
 * Local repository
 * Remote repository
 ### Commands:
 Abbildung der Commands ![](https://readsahil.files.wordpress.com/2016/09/git_cheat_sheet.png?w=636g)
 ## Github workflow:
 Abbildung des Arbeitsprinzipes ![](https://hackernoon.com/hn-images/1*iHPPa72N11sBI_JSDEGxEA.png)
 ### Ablauf:
 1) Create repository (erstellen)
 2) Create Branch
 3) Add/edit (bearbeiten) und commit branch
 4) Submit pull request
 5) Deploy
 6) Merge pull request
 7) Delete merged branch
 
 ## GitWeb:
 Visualisiert ein Git - repository im Internet
 
 ## Markdown: 
>Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde. Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere Konvertierung leicht lesbar ist. Als Auszeichnungselemente wurden daher vor allem Auszeichnungsarten verwendet, die in Plain text und E-Mails üblich sind. Auch andere Auszeichnungssprachen mit ähnlichen Zielen zur Lesbarkeit – wie reStructuredText oder Textile – hatten Einfluss auf die Syntax. Der MIME-Type lautet text/markdown

Quelle: [Wikipedia][Wikipedia - Markdown]

--------------------------------------
## Formatierung bei Markdown:
## Titel Formatierung:
 Ein Titel wird mit einem "Hash" (#) vor dem Text eingefügt.
# Titel (#)
## Untertitel (##)
### Kleiner Untertitel (###)

## Bild Formatierung:
Ein Bild wird mit ![](adresse des bildes) eingefügt.

![](https://webserver.x-technik.com/upload/images/113087.jpg)

## Aufzählen/Listen:

Eine Auflistung wird mit entweder 1), oder * eingefügt.

### Automarken und Modelle:
1) BMW ( 1) )
* X1 ( * )
* X2
2) Audi
* A3
* A4
3) Mercedes Benz
* A
* CLA
4) VW
* Golf
* Polo

## Tabellen:

Version    | Name       | Datum
-----------|------------|------------
V 1.0      | Protokoll.docx | 27.10.2019


## Programm:

Ein Programm wird mit ( ´´´(Programiersprache) Programm... ´´´) eingefügt.

```C
#include <stdio.h>

int main () {
 printf("Hello");
 return 0;
 }
```
## Schriftformatierung:
* *Kursiv* ( * )
* **Fett** ( ** )
* ***Fett und Kursiv*** ( *** )
* ~~Durchgestrichen~~ ( ~~ )
## Zitieren:

Texte kann man mit ">" vor dem Text zitieren
>Es macht keinen Sinn zu erwähnen, dass dieser Text eigentlich gar keinen Sinn hat. Schließlich habe ich ihn ja „Text ohne Sinn“ genannt.

Quelle: [schattenengel.wordpress][schattenengel - wordpress]






[Wikipedia - Markdown]: https://de.wikipedia.org/wiki/Markdown
[schattenengel - wordpress]: https://schattenengel.wordpress.com/2015/02/15/text-ohne-sinn/
