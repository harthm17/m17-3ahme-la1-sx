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
    * [Datei plus Ordnerrechte in Linux:](#datei-plus-ordnerrechte-in-linux)






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
## Datei-und Ordnerrechte

### Datei plus Ordnerrechte in Linux:

Linux ist ein Multiusersystem, dass heißt, das jeder auf alles zugreifen kann. Um dies zu vermeiden benötigt Linux diverse Datei-und Ordnerrechte die man in der Shell festlegen kann und sollte.

Jedes Element im Dateisystem hat unter Linux einen Eigentümerund gehört einer Gruppe an. Die Zugriffsrechte werden getrennt für Eigentümer (user), Gruppe (group) und Andere (others), also fremden Benutzern. Über die Wörter „Lesen“, „Schreiben“ und „Ausführen/ Suchen“ werden diese Modi definiert. Letzteres bezieht sich bei Ordnern auf das fundamentale Recht, den Ordner zu öffnen, bei Dateien hingegen auf das Ausführungsrecht. Wenn dieses fehlt, lässt sich eine Datei nicht starten. 

**Bei Dateien:**

1. r...read: Lesen (Dateien dürfen gelesen werden)
2. w...write: Schreiben (Dateien dürfen angelegt,gelöscht, aber auch geändert weden)
3. x...execute: Ausführen/Suchen (Es darf auf Eigenschaften der aktuellen Datei zugegriffen werden)

**Bei Verzeichnissen:**

1. r...read: Lesen (Inhalt gelesen werden)
2. w...write: Schreiben (Inhalt löschen, bzw. anlegen)
3. x...execute: Ausführen/Suchen (Ins Verzeichnis wechseln dürfenn)

Wenn die jeweiligen Rechte zutreffen, sieht man bei der aufgelisteten Datei die entsprechenden Buchstaben dazu, ansonsten werden diese durch ein```-```ersetzt

Das erste Zeichen kennzeichnet Datei Typ:

| Zeichen | Steht für |
|-----------|-------------------|
| "-" | Datei |
| d | Directory |


**Bsp.:** In diesem Beispiel ist es eine Verzeichnisdatei

 ![](http://i.imgur.com/OzXZ6.png)
 
 Wie im oben angeführte Bsp. sieht man, dass die nächsten 9 Zeichen die Zugriffsrechte managen.
 ```
 Zeichen 2-4 für Eigentümer....user
 Zeichen 5-7 für Gruppe....group
 Zeichen 8-10 für Andere....others
 ```


Mit dem Kommando ```ll```, ander geschrieben```ls-alF``` weden alle Dateien im derzeitigen Ordner aufgelistet:

```
ls........list directory content (Liste Verzeichniss Inhalt auf)
a.........all (Alles auflisten)
l.........line (In Linie)
F.........freedom
```





 
 

