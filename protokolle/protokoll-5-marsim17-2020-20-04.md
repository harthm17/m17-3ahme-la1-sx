# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Linux Scripting
* **Datum:** 20.04.2020
* **Gefehlt:** -
* **Erstellt von:** Marcher Simon
* **Protokoll letzte Einheit: ** [Protokoll 30.03.2020](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/protokoll-4-marsim17-2020-30-03.md)
* **Protokoll nächste Einheit: ** [Protokoll 27.04.2020](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/protokoll-6-marsim17-2020-27-04.md)
---------
## Inhaltsverzeichnis
[Die Shell](#die-shell)  
[Das Shellscrript](#das-shellscript)  
[Hello World](#hello-world)  
[Debugging](#debugging)  
[Login-shell bei Debian/Ubuntu](#login-shell-bei-debian/ubuntu)  
[Interaktiver Modus](#interaktiver-modus)  

## Die Shell

Die Linux Shell ermöglicht es dem Benutzer mit dem Kernel zu kommunizieren. Ihr Name kommmt daher, dass sie den Kernel quasi "umhüllt". Sie ist ein [Interpreter](https://en.wikipedia.org/wiki/Interpreter_(computing)), der die eingegebenen Befehle in [System Calls](https://en.wikipedia.org/wiki/System_call) umwandelt und ausführt. Eine gibt auch eine große Anzahl an GUIs (Terminals), mit dem man auf die Shell zugreifen kann.

In den 1980ern wurde die [Bourne-Shell](https://en.wikipedia.org/wiki/Bourne_shell) (sh) entwickelt. Ihr folgten die [Debian Almquist SHell](https://en.wikipedia.org/wiki/Almquist_shell#dash) (dash) mit sehr schnellem Startup, die [Bourne again SHell](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) (bash) mit einigen neuen features und die [Restricted Bourne Again SHell](https://en.wikipedia.org/wiki/Restricted_shell) (rbash) für erhöhte Sicherheit. 

Die fälschich bezeichnete [Remote Shell](https://en.wikipedia.org/wiki/Remote_Shell) (rsh) und die [Secure Shell](https://en.wikipedia.org/wiki/Secure_Shell) (ssh) sind lediglich Schnittstellen zu einem Computer und werden dort zu einer richtigen Shell weitergeleitet.

Die verwendete Shell kann man mit dem Befehl
`ls -l /bin/sh` 
herausfinden. Diese Datei ist ein symbolischer Link zur Shell. (Meist `/bin/bash` oder `/bin/dash`)

## Das Shellscript
Die Shell kann nicht nur eingegebene Befehle des Users verarbeiten, sondern auch Scripts, also Textdateien, mit einer Ansammlung an Befehlen. Solche Skripten sind schnell erstellt und einfach anzupassen. Außerdem werden sie nicht kompiliert, wodurch das Skript zwar langsamer ist, aber der Quellcode geht hierbei nicht verloren. Eine übersichtliche Zusammenfassung der Shell Command Language wird von [Opengroup](https://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html) bereitgestellt. Die man-pages zur jeweiligen Shell sind auch sehr nützlich.

## Hello world
Eine Script-Datei besteht nur aus Plain-Text und kann daher auch mit jedem Text-Editor erstellt werden. 
Sie hat üblicherweise (aber nicht zwingend) die Dateiendung `.sh`. Kommentare beginnen mit einem `#`. Steht ein `#!` jedoch in der ersten Zeile, ist der folgende String jedoch der Name des Programms, mit dem das Script interpretiert werden soll. Im Falle von bash beginntjedes Script also mit der Zeile `#!/bin/bash`. Um die Datei auszuführen führt man `./skriptname.sh` oder `sh skriptname.sh`aus. Die Datei muss jedoch ausführbar sein (`sudo chmod +x skriptname.sh`). Man kann das Skript mit `exit 0` beenden lassen, es ist jedoch nicht erforderlich. Das Programm sieht so aus:
```bash
#!/bin/bash

echo "Hello"
echo "World"
```
Führt man das Skript aus erhält man:
```bash
[simon@simon sripting]$ ./helloWorld.sh 
Hello
World
```

## Debugging
Mit `sh -x helloworld.sh` wird vor der Ausführung jeder Zeile die Zeile ausgegeben.
```bash
[simon@simon sripting]$ sh -x helloWorld.sh 
+ echo Hello
Hello
+ echo world
world
```
Der String vor der jedeiligen Zeile kann (auch mit `sh`) mit der Umgebungsvariable `PS4` festgelegt werden. Zum Beispiel:
```bash
user@ubuntu:~$ export PS4='--> Zeile ${LINENO}: '
user@ubuntu:~$ sh -x helloworld.sh
--> Zeile 3: echo Hello
Hello
--> Zeile 4: echo World
World
```
* `-v`
  Die Shell schreibt das Skript unverändert auf stderr. Damit kann man feststellen, ob das richtige Skript ausgeführt wird.

* `-n`
  Die Befehle werden überprüft, aber nicht ausgeführt. Damit kann man das Skript auf syntaktische Fehler überprüfen.
 
* `-e`
  Das Skript bricht ab, sobald es auf einen Fehler stößt.
  
* `-u`
  Wird eine unbekannte Variable verwendet, wird das auf stderr ausgegeben.
  
  ## Login-Shell bei Debian/Ubuntu
  
Loggt sich ein Benutzer ein wird die interakrive Login-Shell gestartet. Alle Befehle des Benutzers laufen über sie. Welche das ist findet man mit `head -n 1 /etc/passed` heraus. Die Ausgabe ist meistens:
```bash
root:x:0:0::/root:/bin/bash
```
Führt man also ein Skript mit dash auf, läft dash jedoch noch immer in bash. Will man diese Problem umgehen, muss man die Shell im interaktiven Modus starten, indem man sie ohne Argumente aufruft, oder mit den Befehl mit `-c command` direkt der Shell übergibt.

## Interaktiver Modus
Um eine interaktive Shell zu starten muss man sie ohne Argumente starten. Mit `exit` wird wird die Shell wieder beendet. Das erste Argument, das kein `-` ist wird als Programmname und alle weiteren als Programmparameter angenommen. Innerhalb des Skripts können diese Parameter mit `$1`, `$2`, `$3`, ... verwendet werden. Wichtige Argumente zum starten der Shell sind:
* `-c ...` Interpretiert die folgenden Befehle
* `-e ...` Beendet das Programm beim ersten Fehler
* `-x` Schreibt jeden Befehl vor der Ausführung auf stderr. Nützlich zum debuggen
* `-u` Wird auf eine unbekannte Variable zugegriffen, wird das auf stderr ausgegeben
* `-s` Legt die eingabe auf stdin fest (Standard)

## Elemente eines Skripts
### Operatoren
Steueroperatoren: `& && ( ) ; ;; | || <newline>`

Umleitungsoperatoren: `< > >| << >> <& >& <<- <>`

### Schlüsselwörter
`! elif fi while case else for then { } do done until if esac`

### Commands
Commands werden in shell functions (Programme, direkt von der Shell zur Verfügung gestellt), builtins (cd, echo, exit,...) und normale Programme (ausführbare Datei, zB. mkdir, chmod,...) eingeteilt.
