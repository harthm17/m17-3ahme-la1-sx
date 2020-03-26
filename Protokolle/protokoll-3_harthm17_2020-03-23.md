# 3. Protokoll
---------------------------------------------
## Thema: Installation von Ubuntu
---------------------------------------------
* Datum:      23.03.2020
* Gruppe:     2  
* Abwesend:   keiner
* Verfasser:  Thomas Harrer 
* Klasse:     3AHME
* Schuljahr:  2019/20
---------------------------------------------
## Inhaltsverzeichnis

* [Download und Installation einer Virtual Box](#download-und-installation-einer-virtual-box)
  * [Herunterladen](#herunterladen)
  * [Installation](#installation)
* [Oracle VM VirtualBox Extension Pack installieren](#oracle-vm-virtualbox-extension-pack-installieren)
* [Virtuelle Maschine einrichten](#virtuelle-maschine-einrichten)
* [Ubuntu Auflösung](#ubuntu-auflösung)
* [HTL Paket installieren](#htl-paket-installieren)
* [Lesezeichen in Firefox konfigurieren](#lesezeichen-in-firefox-konfigurieren)

---------------------------------------------
### Download und Installation einer Virtual Box
#### Herunterladen
Der erste Schritt ist, eine Virtual Box herunterzuladen. In meinen Fall musste ich eine Virtual Box für Windows herunterladen.
Um auf die Website zu kommen, klicken Sie [hier](https://www.virtualbox.org/wiki/Downloads)

#### Installation
Nachdem Sie die Installationsdatei heruntergeladen haben, müssen Sie diese dann ausführen und die Installationsschritte befolgen.

### Oracle VM VirtualBox Extension Pack installieren
Dannach muss das Oracle VM VirtualBox Extension Pack heruntergeladen werden. Dies wird dann auch automatisch installiert. Um das Pack herunterzuladen, klicken Sie [hier](https://download.virtualbox.org/virtualbox/6.1.4/Oracle_VM_VirtualBox_Extension_Pack-6.1.4.vbox-extpack)

### Virtuelle Maschine einrichten
Als Betriebssystem haben wir uns für Ubuntu entschieden, deswegen haben wir Ubuntu 18.04 LTS heruntergeladen. Dies ist eine .iso Datei. Um zum Download dieser Datei zu kommen, klicken Sie [hier](https://ubuntu.com/download/desktop/thank-you?version=18.04.4&architecture=amd64).

Der erste Schritt ist es eine **neue** Virtual Box zu erstellen.

![](https://cdn.discordapp.com/attachments/692432976503373854/692693827693051974/bild1.PNG)

Der nächste Schritt ist es, seinen Wunschnamen für die VirtualBox eingeben, den Dateipfad angeben, wo die Datein der neuen Distribution gespeichert werden.

![](https://cdn.discordapp.com/attachments/692432976503373854/692693816234213386/bild2.PNG)

Dannach muss man angeben, wie viel Arbeitsspeicher dein neues Betriebssystem in Anspruch nehmen darf. In unserem Fall waren das **mindestens** 4GiB.

![](https://cdn.discordapp.com/attachments/692432976503373854/692693819547975800/bild3.PNG)

Der logisch folgende Schritt ist es, anzugeben wie viel Speicher es zu verfügung hat. In unserem Fall waren dies **mindestens** 50GiB.
Nach diesem Schritt kann man die VirtualBox erzeugen.

![](https://cdn.discordapp.com/attachments/692432976503373854/692693820961193984/bild4.PNG)

**WICHTIG:**
Nach diesem Schritt kann man logischerweiße die VirtualBox noch nicht starten, da noch kein Betriebssystem ausgewahlt ist. Um ein Betriebssystem auszuwählen, muss man einmal auf "Ändern" klicken und dann auf "Massenspeicher" gehen. Dannach muss man die .iso Datei, die man vorher heruntergeladen hat, auswählen.

![](https://cdn.discordapp.com/attachments/692432976503373854/692693822551097344/bild5.PNG)

Der letzte Schritt vor dem Starten ist es, erneut in "Ändern" zu gehen, dann in "Allgemein" -> "Erweitert" und beide Auswahlmöglichkeiten auf bidirektional zu stellen, wie Sie im unterem Bild sehen können.

![](https://cdn.discordapp.com/attachments/692432976503373854/692707847212892181/bild10.PNG)

Nun kann man die VirtualBox starten.
Wenn die VirtualBox gestartet ist, muss man oben auf "Geräte" gehen, dann auf "Gästerweiterungen einlegen". Dannach kann man die Guest Additions installieren.

![](https://cdn.discordapp.com/attachments/692432976503373854/692693824874741810/bild7.PNG)

![](https://cdn.discordapp.com/attachments/692432976503373854/692693826216788039/bild8.png)

Wenn man erneut auf "Ändern" geht und dann auf "Gemeinsamer Ordner" geht, kann man einen Gemeinsamen Ordner erstellen. Mit diesem kann man zwischen dem Gastsystem und dem virtuellen System ein Verzeichnis teilen.
![](https://cdn.discordapp.com/attachments/692432976503373854/692693823565856809/bild6.PNG)

### Ubuntu Auflösung
Ich hatte das Problem, dass meine Auflösung in der VirtualBox sehr unbrauchbar war. Deswegen musste ich diese auch bearbeiten.
Als Erstes muss man in Ubuntu "Anzeigegeräte" suchen. Dann wählt man unter Auflösung 1920x1200 (16:10) aus und drückt dann **Rechte Steuerung + F** und startet die Maschine neu. Dann haben Sie die passende Auflösung für Ihren Bildschirm. In meinem Fall war es 1920x1080 (16:9).

![](https://cdn.discordapp.com/attachments/692694428128772116/692702639829286972/bild9.png)

### HTL Paket installieren
Anschließend muss das HTL Paket installiert werden.
Um das HTL Paket zu installieren, muss man zu allererst als Superuser einsteigen.
```
thomas@thomas-VirtualBox:~$ sudo -i
-> [sudo] Passwort für Thomas: 
```
Dannach müssen Sie die folgenden Befehle nach der vorgegeben Reihenfolge eingeben.
```
root@thomas-VirtualBox:~# wget -O - http://www.htl-mechatronik.at/ubuntu-htl/install | bash
root@thomas-VirtualBox:~# apt update
root@thomas-VirtualBox:~# apt dist-upgrade
root@thomas-VirtualBox:~# install htl
```

### Lesezeichen in Firefox konfigurieren
Der erste Schritt ist es Firefox zu öffnen. Dann geht man rechts oben im Eck auf das "Bücherregel"-Logo und dann sieht man dann Lesezeichen. Anschließend geht man dann auf den Stern und dann unten auf "Lesezeichen verwalten". Nun öffnet sich ein neues Fenster, wo man oben in der Menüleisten "Importieren und Sichern" steht. Wenn man diesen klickt, bekommt man eine Auswahl von verschiedenen Möglichkeiten.

**Sichern:** Um die aktuelle Lesezeichen zu sichern.

**Wiederherstellen:** Mit dieser Funktion können Sie alte Lesezeichen mit Hilfe des Datum wiederherstellen.

**Lesezeichen von HTML importieren:** Hiermit kann man die aktuelle Lesezeichenleiste als HTML Dokument speichern und diese dann ins Internet geben.

**Lesezeichen nach HTML exportieren:** Damit kann man Lesezeichen als HTML Format herunterladen und diese dann zu Ihrer Leiste hinzufügen.

**Daten aus einem aderen Browser importieren:** Hiermit kann man die Lesezeichen aus z.B Chronium exportieren und diese in Firefox importieren.

Man kann sich die HTL-Lesezeichen unter /usr/share/htl/links/firefox/ herunterladen und diese dann in Firefox importieren.
Ich habe diesen Schritt in der schulischen Zeit nicht geschafft, weil ich es sehr lange mit Chronium versucht habe, aber leider nicht geschafft habe. Jedoch sind in Chronium die Schritte ziemlich ähnlich wie in Firefox.

Ich habe von Mitschülern eine Link bekommen, wo diese Schritte genauer erklärt wurden. Um zu dieser Website zu kommen, klicken sie [hier](https://support.mozilla.org/de/kb/Lesezeichen-sichern-und-wiederherstellen)
