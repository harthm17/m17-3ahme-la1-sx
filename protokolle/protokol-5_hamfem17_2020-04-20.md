# Protokoll LA2/SX 3AHME (2019/20)

* **Thema:** Linux Scripting
* **Datum:** 20.03.2020
* **Erstellt von:** Felix Hamrle
* **Protokoll nächste Einheit:** --

## Inhaltsverzeichnis



## Shell

Die Shell stammt von den Anfangstagen der Unix/Linux Systeme. Dieses soll dem Benutzer  
einen Systemzugang ermöglicht. So bald die Entertast gedrückt wird nach dem man ein Komando  
in die Shell geschrieben hat interpretiert die Shell das Kommando und führt die  
erforderlichen Systemaufrufe durch. Das Ergebniss zu dem die Shell kommt wir ausgegeben.

Heut zu Tage kann man in den Systemen Ubuntu- und Debian/Raspian folgende Shells sehen

1. dash (Debian Almquist SHell)  
1. bash (Bourne Again SHell)
1. rbash (Restricted Bourne Again SHell)

Unter Ubuntu 14.04 kann man sie mit den Komandos ``ls -l /bin/dash``, ``ls -l /bin/bash`` und  
``ls -l /bin/rbash`` finden.

## Shellscript

Ein Shellscript ist eine Text-Datei mit Shell-Kommandos  

Vorteile so eines Shellscript sind:  

1. schnell erstellbar  
1. rasche Anpassbarkeit  
1. kein Verlust des Quellcode möglich 

Nacteile:  

1. wird erst bei der Ausführung von der Shell interpretiert  
1. langsamer als compilierte Programme  
1. moderne Programmierparadigmen (Objektorientierung, Fehlerhandling, ...) fehlen  

## Script-Interpreter  

Ein Shellscript ist einfach eine Text-Datei, die mit dem Editor bearbeit  
werden kann. Sie muss auch Executeable-Rechte verfügen (chmod +x).  

Der ``#`` wird beginnt normalerweise ein Zeilenkommentar und der Text  dahinter wird  
ignoriert. Aber wenn die erste Zeile der Textdatei mit ``#!`` dann wird das dahinter  
stehende als Programm für die Ausführung des Scripts herangezogen.  

## Start, Ende eines Shellscripts

Das Shellscript kann man entweder mit ``./myscript`` oder ``sh myscript`` starten.

zB.
```console  
felix@felix-VirtualBox:~$ nano myscript  
felix@felix-VirtualBox:~$ cat myscript  
#!/bin/sh  
  
echo "Hallo"  
echo "ich bin ein"  
echo "Script"  
  
exit 0  
felix@felix-VirtualBox:~$ chmod +x myscript  
felix@felix-VirtualBox:~$ ls -l myscript  
-rwxr-xr-x 1 felix felix 65 Apr 20 16:08 myscript  
felix@felix-VirtualBox:~$ ./myscript  
Hallo  
ich bin ein
Script
felix@felix-VirtualBox:~$ sh myscript  
Hallo  
ich bin ein
Script
```
