# Protokolle-2 Labor/SX 3AHME(2019/20)

------------------------------------------------------------

* ***Protokollführer:*** Riegelnegg Lukas (rielum17)
* ***Datum:*** 13.01.2020
* ***Thema:*** Terminal
* ***Gefehlt:*** Pfanner Jan
* ***Protokoll nächste Einheit:***-

------------------------------------------------------------

## Inhaltsverzeichnis
1. [Themen der Einheiten](#themen-der-einheit)
1. [Befehle](#Befehle)


------------------------------------------------------------

### Themen der Einheiten
1. Einheit: Befehle im Terminal unter linux

----------------------------------------------------------------------

### Befehle

**Befehl** | **Bedeutung** | **Erklärung**
---------- | ---------- | ----------
**pwd** |      print working directory |  Aktuelles Arbeitsverzeichnis (.) ausgeben
**ls** |      list directory content | Dateien und Verzeichnisse von ./ ausgegeben
**ls -l** || Line-Mode, mehr Infos anzeigen
**ls -a** || all, auch verborgene Dateien anzeigen
**cd**  |    change directory       |   In ein (anderes) Verzeichnis wechseln
**touch** |    touch file        |        Leere Datei anlegen oder Zeitstempel ändern
**mkdir** |   make directory     |       Verzeichnis erstellen
**mv**    |   move              |        Datei/Verzeichnis verschieben oder umbenennen
**cp**   |    copy           |           Date/Verzeichnis kopieren
**scp**  |    secure copy     |          copy über Netzwerk via ssh (secure shell)
**rm**   |    remove             |       Datei oder löschen
**rmdir** |   remove directory     |     Verzeichnis löschen (muss leer sein!)
**cat**   |   concatenate        |       Dateien verbinden und auf stdout ausgeben
**less**   |  less     |       Dateiinhalt im Viewer less anzeigen
**hexdump** | hexadecimal file dump |    Dateiinhalt als Hexdump ausgeben
**grep**   |  +  |    Auf ein Suchmuster passende Zeilen ausgeben
**find** |    find files           |     Dateien oder Verzeichnisse finden
**dd**   |    duplicate data      |      Daten 1:1 kopieren (auch auf Geräte anwendbar) 
**df**   |    disk free space     |      Freien Speicher auf Dateisystemen anzeigen
**du**   |    disk usage           |     Byte-Verbrauch in Verzeichnis(sen) zeigen
**mount**  |  mount a filesystem    |    Partition einbinden
**umount**  | unmount a filesystem   |   Eingebundene Partition trennen  
**whoami**    |   who am i                 |  aktuellen Benutzer ausgeben
**who**       |   who is logged on         |  wer ist gerade angemeldet
**w**         |   who is logged on and ... |  wer ist wie angemeldet
**passwd**    |  set new password          |  Passwort neu setzen
**su**        |   set (change) user id     |  andere Benutzer-ID annehmen
**sudo**      |   super-user do            |  in den Super-User Mode (root) wechseln
**sudo -s**   |                            | -> Neue Shell mit user root
**sudo -i**   |                            | -> Neuer Login mit user root  
**login**     |   login with new session   |  startet eine neue Session im System
**id**       |   display user id ...      |  Benutzerinfos anzeigen
**groups**   |   display groups           |  Gruppenmitgliedschaft anzeigen
**adduser**   |   add new user             |  Neuen Benutzer hinzufügen
**deluser**   |   delete user              |  Benutzer entfernen
**logout**   |  log out from shell     |     Aus aktueller Login-Shell abmelden
**login**    |  log in in new shell   |      Neue Login-Shell (bash) starten
**reset**    | reset terminal  | Terminal in den Grundzustand zurücksetzen
**clear**    | clear screen   |  Terminalschirm leeren (scroll nach unten)
**vssh**      | secure shell  |   OpenSSH SSH client, verschlüsselte remote client shell
**nano**     |  Terminalbasierender Editor
**gedit**    |  GUI-Editor für Ubuntu (Unity/Gnome3)
**leafpad**  |  GUI-Editor für Lubuntu (LXDE)
**vi**       |  Standard-Editor für Linux (Modal-Editor)
