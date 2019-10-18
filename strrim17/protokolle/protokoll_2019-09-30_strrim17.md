# Protokoll LA1 / 3AHME (2019/20)
* **Thema:** Git / Github (Markdown)
* **Datum:** 30.09.2019
* **Gefehlt:** ---
* **Erstellt von:** strrim17
* **Protokoll nächste Einheit:** [Linux / Shell](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/edit/strrim17/strrim17/protokolle/protokoll_2019-10-14_strrim17.md)

------------------------------------------------------------------------------------------------------------------------

## Inhaltsverzeichnis

1. [Github](#github)
2. [Mastering Markdown](#mastering-markdown)
   1. [Überschriften](#überschriften)
   2. [Betonung](#betonung)
   3. [Listen](#listen)
      1. Ungeordnet
      2. Geordnet
   4. [Bilder](#bilder)
   5. [Links](#links)
   6. [Block Zitate](#block-zitate)
   7. [Inline-Code](#inline-code)
3. [Git](#git)
   1. [Befehle](#befehle)
   2. [Branche](#branche)
4. [Was ist Markdown?](#was-ist-markdown)
5. [Markdown](#markdown)

------------------------------------------------------------------------------------------------------------------------

## Github
Informationen von Github:

GitHub ist ein Onlinedienst, der Software-Entwicklungsprojekte auf seinen Servern bereitstellt (Filehosting). Namensgebend war das Versionsverwaltungssystem Git. Die GitHub, Inc. hat ihren Sitz in San Francisco in den USA. Ähnliche Dienste sind GitLab und Bitbucket.

Quelle: [https://de.wikipedia.org/wiki/GitHub]

## Mastering Markdown

### Überschriften
Es gibt verschiedene Überschrifts Unterteilungen die wie folgt angegeben werden können:

```
#        <h1> tag
##       <h2> tag
###      <h3> tag
####     <h4> tag
#####    <h5> tag
######   <h6> tag
```

Das heißt: Man kann nur bis zu 5 Unter Überschriften angeben.

### Betonung
Es gibt verschiedene Betonungen die den Text verbessern.
Manche Betonungen können auch anders angegeben werden.

```
*Dieser Text wird kursiv geschrieben*
_Dieser Text wird kursiv geschrieben_

**Dieser Text wird fett geschrieben**
__Dieser Text wird fett geschrieben__

_Man **kann** beide Betonungen auch kombinieren_
```

### Listen
Man kann eine Liste erstellen die geordnet oder ungeordnet ist.

#### Ungeordnet
```
* Item 1
* Item 2
  * Item a
  * Item b
```

Ungeordnet bezeichnet man in diesem Fall als aufgezählt (z. B.: aufgereit nach Wichtigkeit).

#### Geordnet
```
1. Item 1
2. Item 2
  3. Item a
  4. Item b
```

Geordnet bezeichnet man in diesem Fall als nummeriert.

### Bilder
Es können selbst Bilder eingefügt werden. Hinweis: Bilder werden mit einem ! am Anfang angegeben.

```
![GitHub Logo](/images/logo.png)
Format: ![Alt Text](url)
```

### Links
Man kann Links angeben, die einem zu jener Seite führt, die man angegeben hat.

```
http://github.com - automatic!
[GitHub](http://github.com)
```

### Block Zitate
Wie Kanye West sagte:

```
> Wir leben die Zukunft so
> die gegenwart ist unsere vergangenheit.
```

### Inline-Code

```
Ich denke, Sie sollten eine verwenden
Stattdessen hier das Element `<addr>`.
```

Quelle: [https://guides.github.com/features/mastering-markdown/]

------------------------------------------------------------------------------------------------------------------------

## Git
Informationen laut Wikipedia:

Git ist ein verteiltes Versionskontrollsystem zur Verfolgung von Änderungen im Quellcode während der Softwareentwicklung. Es wurde für die Koordinierung der Arbeit zwischen Programmierern entwickelt, kann jedoch zum Nachverfolgen von Änderungen in einer Reihe von Dateien verwendet werden. Zu seinen Zielen gehören Geschwindigkeit, Datenintegrität und Unterstützung für verteilte, nichtlineare Workflows.
Git wurde 2005 von Linus Torvalds für die Entwicklung des Linux-Kernels entwickelt, wobei andere Kernel-Entwickler zu dessen anfänglicher Entwicklung beitrugen. Sein derzeitiger Betreuer seit 2005 ist Junio Hamano. Wie bei den meisten anderen verteilten Versionskontrollsystemen und im Gegensatz zu den meisten Client-Server-Systemen ist jedes Git-Verzeichnis auf jedem Computer ein vollwertiges Repository mit vollständigem Verlauf und vollständigen Funktionen zur Versionsverfolgung, unabhängig vom Netzwerkzugriff oder einem zentralen Server. Git ist freie und Open-Source-Software, die unter den Bedingungen der GNU General Public License Version 2 vertrieben wird.

Quelle: [https://en.wikipedia.org/wiki/Git]

### Befehle
Es gibt wichtige Git-Befehle die man unbedingt braucht bzw. wissen sollte die wie folgt lauten:

Hinweis: Es werden nur ein paar aufgezählt die es gibt. Anbei wird ein Link zu den Befehlen unterhalb angegeben.

* git
* git clone
* git add
* git commit
* git push
* git pull
* git config
* git status
* git branch
* git checkout

Quelle des Dokuments: [https://pgi-jcns.fz-juelich.de/pub/doc/git_gitflow.pdf]

### Branche
Laut Wikipedia:

Verzweigung in der Versionskontrolle und im Software-Konfigurationsmanagement ist das Duplizieren eines Objekts, das der Versionskontrolle unterliegt (z. B. eine Quellcodedatei oder ein Verzeichnisbaum), sodass Änderungen parallel in mehreren Verzweigungen erfolgen können.
Zweige werden auch als Bäume, Bäche oder Codelines bezeichnet. Der Ursprungszweig wird manchmal als übergeordneter Zweig, als vorgelagerter Zweig (oder einfach als vorgelagerter Zweig, insbesondere wenn die Zweige von verschiedenen Organisationen oder Einzelpersonen verwaltet werden) oder als Hintergrundzweig bezeichnet. Untergeordnete Zweige sind Zweige mit einem übergeordneten Element. Ein Zweig ohne Elternteil wird als Stamm oder Hauptleitung bezeichnet.
In einigen verteilten Revisionskontrollsystemen, wie z. B. Darcs, wird nicht zwischen Repositorys und Zweigen unterschieden. In diesen Systemen entspricht das Abrufen einer Kopie eines Repositorys dem Verzweigen.
Verzweigung impliziert im Allgemeinen auch die Möglichkeit, Änderungen später wieder in die übergeordnete Verzweigung einzufügen oder zu integrieren. Häufig werden die Änderungen wieder in den Trunk übernommen, auch wenn dies nicht der übergeordnete Zweig ist. Ein Zweig, der nicht zum Zusammenführen vorgesehen ist (z. B. weil er von einem Dritten unter einer inkompatiblen Lizenz erneut lizenziert wurde oder einen anderen Zweck zu erfüllen versucht), wird normalerweise als Fork bezeichnet.

Quelle: [https://en.wikipedia.org/wiki/Branching_(version_control)]

------------------------------------------------------------------------------------------------------------------------

## Was ist Markdown?

Mit Markdown kann man den Text im Web formatieren. Somit steuert man die Anzeige des Dokuments. Fett und Kursiv formatierte Wörter, das Hinzufügen von Bildern sowie das Erstellen von Listen sind nur einige der Möglichkeiten, die wir mit Markdown nutzen können. Meist ist Markdown nur ein normaler Text mit ein paar nicht alphabetischen Zeichen, wie # oder *.

Man kann Markdown an den meisten Orten in Github verwenden:
Gists

Kommentare in Issues und Pull Requests
Dateien mit der Erweiterung .md oder .markdown

Quelle: [https://guides.github.com/features/mastering-markdown/]

## Markdown
Hier wird einiges über Markdown als Information laut Wikipedia angegeben:

Markdown ist eine vereinfachte Auszeichnungssprache, die von John Gruber und Aaron Swartz entworfen und im Dezember 2004 mit Version 1.0.1 spezifiziert wurde. Ein Ziel von Markdown ist, dass schon die Ausgangsform ohne weitere Konvertierung leicht lesbar ist. Als Auszeichnungselemente wurden daher vor allem Auszeichnungsarten verwendet, die in Plain text und E-Mails üblich sind. Auch andere Auszeichnungssprachen mit ähnlichen Zielen zur Lesbarkeit – wie reStructuredText oder Textile – hatten Einfluss auf die Syntax. Der MIME-Type lautet text/markdown.
Eine Markdown-Konvertierungssoftware wandelt Text in gültiges und W3C-konformes XHTML um. Die Referenzimplementierung in Perl steht unter einer BSD-artigen Lizenz. Weiter sind inzwischen Implementierungen in den gängigsten Programmiersprachen wie PHP, Python oder JavaScript sowie R verfügbar.

Quelle: [https://de.wikipedia.org/wiki/Markdown]

------------------------------------------------------------------------------------------------------------------------

## Links

Hier sind alle Links aufgelistet die oben angegeben worden sind:

[Github]: https://de.wikipedia.org/wiki/GitHub
[Mastering-Markdown]: https://guides.github.com/features/mastering-markdown/
[Git]: [https://en.wikipedia.org/wiki/Git]
[Befehle]: https://pgi-jcns.fz-juelich.de/pub/doc/git_gitflow.pdf
[Branche]: https://en.wikipedia.org/wiki/Branching_(version_control)
[Was-ist-Markdown]: https://guides.github.com/features/mastering-markdown/
[Markdown]: https://de.wikipedia.org/wiki/Markdown
