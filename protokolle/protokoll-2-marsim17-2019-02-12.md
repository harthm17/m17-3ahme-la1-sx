# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Versionsverwaltungssysteme, git, Github, Markdown
* **Datum:** 18.11.2019
* **Gefehlt:** -
* **Erstellt von:** Marcher Simon
* **Protokoll letzte Einheit:** [Protokoll 18.11.2019](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/protokoll-1-marsim17-2019-18-11.md)

# Inhaltsverzeichnis

# Benutzer
Linux basierte Betriebssysteme sind meist Multiuser-Systeme, heißt mehrere Benutzer mit eigenen Dateien, Einstellungen und Rechten können parallel auf dem gleichen System arbeiten.
Benutzer müssen aber nicht unbedingt nur Personen sein. Auch verschiedene Dienstprogramme wie zB. pulseaudio oder pgAdmin haben eigene Benutzer, mit denen die Programme auf das System zugreifen. Man kann sich auch mit dem Benutzer root anmelden, um durchgehend uneingeschränkten Zugang auf das System zu haben.
Alle Benutzer werden in der Datei `/etc/passwd`. In Abschnitt 5 der man page wird die Syntax dieser Datei beschrieben (`man 5 passwd`).

# Gruppen
Hat man mehrere gleichrangige und zusammengehörende Benutzer hat man die Möglichkeit, diese in Gruppen einzuteilen. Standardmäßig gibt es für jeden Benutzer eine gleichnamige Gruppe, in der dieser Benutzer bereits Mitglied ist. Eine andere wichtige Gruppe ist "sudoers". Nur wer Mitglied ist, darf Befehle im Superuser-Modus ausführen.
Mit dem Befehl `groups` werden alle Gruppen aufgelistet, in der der ausführende Benutzer Mitglied ist. Alle Gruppen werden in der Datei `/etc/groups` gespeichert.

# Rechte
Jeder Benutzer und jede Gruppe hat verschiedene Rechte auf verschiedene Dateien. Es gibt **Leserechte**, **Schreibrechte** und **Ausführrechte**. Diese 3 Rechte werden jeweils für den **Eigentümer** der Datei, die **Eigentümergruppe** und **alle anderen** vergeben.
Hier ist eine Übersicht, was die Rechte für Dateien bzw. Verzeichnisse beteudet.
* Dateien
	* **read**: Den Inhalt einer Datei ansehen
	* **write**: Den Inhalt einer Datei verändern, bzw. die Datei löschen
	* **execute**: Ins Verzeichnis wechseln 
		* Falls nicht gegeben, darf man den Inhalt (Falls read gegeben ist) ansehen, aber den der Unterornder nicht mehr
* Verzeichnisse
	* **read**: Den Inhalt der Dateien in einem Verzeichnis ansehen
	* **write**: Den Inhalt der Dateien in einem Verzeichnis ändern, bzw die Dateien löschen
	* **execute**: Ein Skript, Programm, etc. ausführen
Mit dem Befehl `ll`, der ein alias für `ls -alF` ist, können diese Rechte sichtbar gemacht werden. Relevant hierfür ist nur der erste Block. Dieser besteht aus:
* Art der Datei
	* `-` für normale Dateien
	* `d` für Verzeichnisse
	* `l` für Softlinks
* Rechte des Eigentümers
* Rechte der Eigentümergruppe
* Rechte aller anderen

Falls ein Recht gegebn ist, ist der dazugehörige Buchstabe zu sehen. `r` für read, `w` für write und `x` für execute. Ist ein Recht nicht gegeben, ist nur ein `-` zu sehen. Der erste Block von `ll` dieser Datei, sieht folgendermaßen aus:
`-rw-rw-r--` -> Es ist eine Datei, der Eigentümer, sowie die Eigentümergruppe darf sie lesen und bearbeiten, jedoch nich ausführen. Alle anderen dürfen nur lesen. Der Eigentümer und die Eigentümergruppe ist der 3. bzw 4. Eintrag bei `ll`.
Für eine erweiterte Verwaltung von Rechten gibt es [ACL](https://wiki.archlinux.org/index.php/Access_Control_Lists) (Access controll list).

# Ändern der Dateirechte
Man kann die Rechte einer Datei mit dem Command `chmod` ändern. Dies geht in zwei Varianten:
* Oktal
Man nimm
	
