# Protokoll LA1/SX 3AHME (2019/20)

* **Thema:** Versionsverwaltungssysteme, git, Github, Markdown
* **Datum:** 18.11.2019
* **Gefehlt:** -
* **Erstellt von:** Marcher Simon
* **Protokoll letzte Einheit:** [Protokoll 18.11.2019](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/marsim17/protokolle/protokoll_2019-18-11_marsim17.md)

# Inhaltsverzeichnis

# Benutzer
Linux basierte Betriebssysteme sind meist Multiuser-Systeme, heißt mehrere Benutzer mit eigenen Dateien, Einstellungen und Rechten können parallel auf dem gleichen System arbeiten.
Benutzer müssen aber nicht unbedingt nur Personen sein. Auch verschiedene Dienstprogramme wie zB. pulseaudio oder pgAdmin haben eigene Benutzer, mit denen die Programme auf das System zugreifen. Man kann sich auch mit dem Benutzer root anmelden, um durchgehend uneingeschränkten Zugang auf das System zu haben.
Alle Benutzer werden in der Datei `/etc/passwd`. In Abschnitt 5 der man page wird die Syntax dieser Datei beschrieben (`man 5 passwd`).

# Gruppen
Hat man mehrere gleichrangige und zusammengehörende Benutzer hat man die Möglichkeit, diese in Gruppen einzuteilen. Standardmäßig gibt es für jeden Benutzer eine gleichnamige Gruppe, in der dieser Benutzer bereits Mitglied ist. Eine andere wichtige Gruppe ist "sudoers". Nur wer Mitglied ist, darf Befehle im Superuser-Modus ausführen.
Mit dem Befehl `groups` werden alle Gruppen aufgelistet, in der der ausführende Benutzer Mitglied ist. Alle Gruppen werden in der Datei `/etc/groups` gespeichert.
