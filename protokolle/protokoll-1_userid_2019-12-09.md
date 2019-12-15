# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Versionsverwaltung, Markdown
* **Datum:** 09.12.2019
* **Gefehlt:** -
* **Erstellt von:** Peyer Kassandra
* Ver**Protokoll letzte Einheit:**
* **Protokoll nächste Einheit**

----------------------------------------------------------------------------------------------

## Inhaltsverzeichnis

1. [Mobile Computing](#mobile-computing)  
2. [Web Apps](#web-apps)
3. [Software und IDE](#software-und-ide)
   1. [Node.js](#node.js)
   2. [Angular](#angular)
   3. [Angular CLI](#angular-cli)
   4. [Visual Studio Code](#visual-studio-code)
4. [Installation](#installation)

----------------------------------------------------------------------------------------------
## Versionsverwaltung
Versionsverwaltung, auch Version control systems (CVS) genannt, ist ein System, dass alle Versionen einer beliebigen Datei in einem sogennanten Repository (engl. Aufbewahrungsort) speichert. Somit kann man auch nach vielen Änderungen sehen wer, was, wann verändert hat.

Dieses System ist auch noch praktisch für Teamworking, da man die Repositories Online erstellt und somit auch mehrere Leute, ohne große Umstände, an einem Projekt arbeiten können. Ein weiterer Punkt der für die Versionsverwaltung spricht ist der Schutz vor Daten verlust, der durch z.B. Zerstörung einer Festplatte oder eines PC's erfolgen kann, da die Daten nicht lokal aufbewahrt werden.

Das einzig "Negative" am Versionsverwaltungssystem ist, dass die Verwendung dieses Systems erlernt werden muss.

## Git

Die heutzutage populärste Software der Versionsverwaltung ist **Git**, welches von [Linus Torvalds](https://de.wikipedia.org/wiki/Linus_Torvalds) entwickelt wurde. Git ist bekannt für seine Nicht-lineare Entwicklung die Hauptsächlich durch das **branching** entsteht. Jedes Repository besitzt einen Hauptentwicklungszweig, bei Git heißt dieser **master-Branch**. Wenn man etwas an diesem ändern möchte erstellt man einen **side-Branch** welcher zuerst eine exakte Kopie von dem master-Branch ist. Wenn man dann Dateien verändert hat kann man einen **pull request** beantragen und wenn dieser angenommen wurde werden der side-Branch und der master-Branch verschmolzen, man spricht von einem **merge**. mmmmÝÝÝ
Eine weitere Funktion von Git ist das Erstellen von **lokalen Repositories**, welche eine Kopie der Online Version ist und man somit auch ohne Internetzugriff weiter arbeiten kann.

Um mit einem lokalen Repository zu arbeiten benutz man folgende Befehle:

Mit **git clone _Link zum Repository_** kopiert man das online Repository auf seinen lokalen Rechner.

Mit **git add _Name der Datei_** wird eine Datei in den Index gegeben und kann dort noch bearbeitet werden.

Mit **git status** erfährt man in welchem Branch man sich befindet.

Mit **git checkout _Name des Branches_** wechselt man in den angegebenen Branch.

Mit **git commit -m "Kommentar"** werden alle Dateien vom Index in den local Repository gegeben. Um diesen Befehl 
git config
git push
