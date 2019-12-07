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
1. [Benutzer:](#benutzer)
1. [Dateirechte:](#dateirechte)






-------------------------------------------------------------------------------------------------------------------------------------------
## Letzte Einheit:
-------------------------------------------------------------------------------------------------------------------------------------------
## Benutzer:
Linux ist als Mehrbenutzer-Betriebssystem konzipiert. Alle benutzer haben nicht unbedingt dieselben Rechte und Privilegien. Ein Standardbenutzerkonto erhält vollen Zugriff auf das eigene Home-Verzeichnis, aber nicht auf alle Ordner, nur auf sehr wenige. Das Systemverwalterkonto „root“ hat dagegen alle Rechte im gesamten Dateisystem. Dazwischen liegen aber viele Abstufungen. Deswegen kommt es immer zu Problemen aufgrund mangelnder Benutzerrechte. Dann ist z.B. kein Zugriff auf eine zweite Festplatte möglich. Jedes Element im Dateisystem hat unter Linux einen Eigentümer und es gehört einer Gruppe. Die Zugriffsrechte werden getrennt für Eigentümer und Gruppe.

**Für Verwaltung von Gruppen, Benutzern und Passwörter gibt es folgende Dateien:**

* */etc/passwd* 
* */etc/group* (Alle Gruppen + Mitglieder werden in /etc/group festgelegt)
* */etc/shadow*



**In Linux gibt es viele Möglichkeiten um Benutzer und Gruppen anlegen zu können, oder auch um sie zu löschen. Unsere Methode der Veränderung:**

* **In der Shell durch Veränderung der folgenden Textdateien:**
/etc/passwd, /etc/group und /etc/shadow

Bei dieser Variante muss vielleicht das Home-Verzeichnis des Benutzers manuell erstellt (mkdir /home/ ...) oder gelöscht werden.

**Passwörter:**
Wenn man ein Passwort in der Shell ändern möchte, so lässt es sich unter dem Kommando passwd ändern.

**Grafik dazu:**![](https://static.giga.de/wp-content/uploads/2015/04/linux-passwort-%C3%A4ndern-terminal.jpg)

Der Super-User root kann dabei dass Kennwort eines jeden Benutzers neu vergeben. In diesem Fall wird der Benutzername als Argument angegeben.

-------------------------------------------------------------------------------------------------------------------------------------------
## Dateirechte:


