# Protokoll LAB/Sx 3.AHME (2019/2020)

* **Themen:** Dateirechte, Benutzer anlegen
* **Datum:** 2.12.2019
* **Gefehlt:** -
* **Erstellt von:** Franz Lieleg 
* **Protokoll der letzten Einheit:** [18.11.2019](https://github.com/HTLMechatronics/m17-3ahme-la1-sx/blob/liefrm17/SxLab%20Protokolle/protokoll-1_liefrm17_2019-11-18.md)
* **Protokoll der nächsten Einheit:** -

---------------------------------------------------------------------------------------------------------------------------------------
## Inhaltsverzeichnis:

1. [Letzte Einheit](#letzte-einheit)
1. [Benutzerverwaltung in der Shell](#benutzerverwaltung-in-der-shell)
    * [Benutzer:](#benutzer)
    * [Passwörter:](#passwörter)
1. [Datei-und Ordnerrechte](#datei-und-ordnerrechte)
    * [Dateirechte im Allgemeinen:](#dateirechte-im-allgemeinen)






-------------------------------------------------------------------------------------------------------------------------------------------
## Letzte Einheit:
-------------------------------------------------------------------------------------------------------------------------------------------
## Benutzerverwaltung in der Shell

### Benutzer:
Linux ist als Mehrbenutzer-Betriebssystem konzipiert. Alle benutzer haben nicht unbedingt dieselben Rechte und Privilegien. Ein Standardbenutzerkonto erhält vollen Zugriff auf das eigene Home-Verzeichnis, aber nicht auf alle Ordner, nur auf sehr wenige. Das Systemverwalterkonto „root“ hat dagegen alle Rechte im gesamten Dateisystem. Dazwischen liegen aber viele Abstufungen. Deswegen kommt es immer zu Problemen aufgrund mangelnder Benutzerrechte. Dann ist z.B. kein Zugriff auf eine zweite Festplatte möglich. Jedes Element im Dateisystem hat unter Linux einen Eigentümer und es gehört einer Gruppe. Die Zugriffsrechte werden getrennt für Eigentümer und Gruppe.

**Für Verwaltung von Gruppen, Benutzern und Passwörter gibt es folgende Dateien:**

* */etc/passwd* 
* */etc/group* 
* */etc/shadow* 

(Alle Gruppen + Mitglieder werden in /etc/group festgelegt)

(Passwörter/Kennwörter werden in Datei /ect/shadow in Form von Hash-Prüfsummen gespeichert(Achtung, man kann hier sehr                    vieles falsch machen!!!))

Mann sollte darauf achten, dass Benutzer, sowie Gruppennamen, mit einem Kleinbuchstaben beginnen, dahinter können z.B. auch Ziffern und Underlines folgen. Aber Achtung!!! Verwendete Namen dürfen nur einmalig im System Vorkommen.


**In Linux gibt es viele Möglichkeiten um Benutzer und Gruppen anlegen zu können, oder auch um sie zu löschen. Unsere Methode der Veränderung:**

 **In der Shell durch Veränderung der folgenden Textdateien:**
* */etc/passwd*
* */etc/group*
* */etc/shadow*

Bei dieser Variante muss vielleicht das Home-Verzeichnis des Benutzers manuell erstellt (mkdir /home/ ...) oder gelöscht werden.



### Passwörter:

Wenn man ein Passwort in der Shell ändern möchte, so lässt es sich unter dem Kommando passwd ändern.

![](https://static.giga.de/wp-content/uploads/2015/04/linux-passwort-%C3%A4ndern-terminal.jpg)

Der Super-User root kann auch das Kennwort jedes Benutzers neu vergeben!

**Beispiel:**
```
 user@ubuntu:~$ sudo-i
 root@ubuntu:~# passwd liefrm
 
```


Was aber passiert wenn man das Benutzer Passwort und das root Passwort vergisst?
Wenn man das Passwort doch vergessen sollte, dann kann man es durch ein paar Schritte händisch auf dem Rechner zurücksetzten, ist die einfachste Methode. 

-------------------------------------------------------------------------------------------------------------------------------------------
## Dateirechte-und Ordnerrechte:

### Dateirechte im Allgemeinen:



Jedes Element im Dateisystem hat unter Linux einen Eigentümer und es gehört einer Gruppe. Die Zugriffsrechte werden getrennt für Eigentümer und Gruppe über die Modi „Lesen“, „Schreiben“ und „Ausführen/ Suchen“ bestimmt. Letzterer bezieht sich bei Ordnern auf das fundamentale Recht, den Ordner zu öffnen, bei Dateien hingegen auf das Ausführungsrecht. Wenn dieses fehlt, lässt sich eine Datei nicht als Programm starten. Ist ein Benutzer weder Eigentümer noch Mitglied der definierten Gruppe, gehört er zu „Andere“. Auch für ihn lassen sich die drei genannten Modi einstellen.

