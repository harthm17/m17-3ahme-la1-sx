# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Linux Scripting
* **Datum:** 20.04.2020
* **Gefehlt:** -
* **Erstellt von:** Marcher Simon
* **Protokoll letzte Einheit:** [Protokoll 30.03.2020](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/protokoll-4-marsim17-2020-30-03.md)
---------
## Inhaltsverzeichnis
[Begriffserklärung](#begriffserklärung)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Deamons in Linux](#deamons-in-linux)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Daemons in Java](#deamons-in-java)  
[Erstellen eines eigenen Deamons](#erstellen-eines-eigenen-deamons)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Programm erstellen](#programm-erstellen)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[systemd Service erstellen](#systemd-service-erstellen)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Service ausführen und überwachen](#service-ausführen-und-überwachen)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Autostart](#autostart)

## Die Shell

Die Linux Shell ermöglicht es dem Benutzer mit dem Kernel zu kommunizieren. Ihr Name kommmt daher, dass sie den Kernel quasi "umhüllt". Sie ist ein [Interpreter](https://en.wikipedia.org/wiki/Interpreter_(computing)), der die eingegebenen Befehle in [System Calls](https://en.wikipedia.org/wiki/System_call) umwandelt und ausführt. Eine gibt auch eine große Anzahl an GUIs (Terminals), mit dem man auf die Shell zugreifen kann.

In den 1980ern wurde die [Bourne-Shell](https://en.wikipedia.org/wiki/Bourne_shell) (sh) entwickelt. Ihr folgten die [Debian Almquist SHell](https://en.wikipedia.org/wiki/Almquist_shell#dash) (dash) mit sehr schnellem Startup, die [Bourne again SHell](https://en.wikipedia.org/wiki/Bash_(Unix_shell)) (bash) mit einigen neuen features und die [Restricted Bourne Again SHell](https://en.wikipedia.org/wiki/Restricted_shell) (rbash) für erhöhte Sicherheit. 

Die fälschich bezeichnete [Remote Shell](https://en.wikipedia.org/wiki/Remote_Shell) (rsh) und die [Secure Shell](https://en.wikipedia.org/wiki/Secure_Shell) (ssh) sind lediglich Schnittstellen zu einem Computer und werden dort zu einer richtigen Shell weitergeleitet.

Die verwendete Shell kann man mit dem Befehl
`ls -l /bin/sh` 
herausfinden. Diese Datei ist ein symbolischer Link zur Shell. (Meist `/bin/bash` oder `/bin/dash`

## Das Shellscript
Die Shell kann nicht nur eingegebene Befehle des Users verarbeiten, sondern auch Scripts, also Textdateien, mit einer Ansammlung an Befehlen.
