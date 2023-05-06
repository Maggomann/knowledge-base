---
category: awesome
sub_category_1: awesome
language: de
tags:
- awesome
---

# Mac OS Kommandobefehle

## Dateiverwaltung:

### cd

Ändern des aktuellen Verzeichnisses. Zum Beispiel: `cd ~/Documents` ändert das aktuelle Verzeichnis zu "Documents" im Home-Verzeichnis.

### ls

Listet den Inhalt des aktuellen Verzeichnisses auf. Zum Beispiel: `ls -l` zeigt eine Liste der Dateien und Verzeichnisse im aktuellen Verzeichnis an.

### pwd

Zeigt das aktuelle Verzeichnis an. Zum Beispiel: `pwd` zeigt das aktuelle Verzeichnis an.

### mkdir

Erstellt ein neues Verzeichnis. Zum Beispiel: `mkdir ~/Documents/MyProject` erstellt ein neues Verzeichnis namens "MyProject" im Verzeichnis "Documents" im Home-Verzeichnis.

### rm

Entfernt eine Datei oder ein Verzeichnis. Zum Beispiel: `rm ~/Documents/MyProject` entfernt das Verzeichnis "MyProject" im Verzeichnis "Documents" im Home-Verzeichnis.

### cp

Kopiert eine Datei oder ein Verzeichnis. Zum Beispiel: `cp ~/Documents/MyProject ~/Desktop/MyProject` kopiert das Verzeichnis "MyProject" im Verzeichnis "Documents" im Home-Verzeichnis in das Verzeichnis "MyProject" auf dem Desktop.

### mv

Verschiebt eine Datei oder ein Verzeichnis. Zum Beispiel: `mv ~/Documents/MyProject ~/Desktop/MyProject` verschiebt das Verzeichnis "MyProject" im Verzeichnis "Documents" im Home-Verzeichnis in das Verzeichnis "MyProject" auf dem Desktop.

### open

Öffnet eine Datei oder ein Verzeichnis. Zum Beispiel: `open ~/Documents/MyProject` öffnet das Verzeichnis "MyProject" im Verzeichnis "Documents" im Home-Verzeichnis.

### find

Sucht nach Dateien und Verzeichnissen. Zum Beispiel: `find ~/Documents -name MyProject` sucht nach Dateien und Verzeichnissen mit dem Namen "MyProject" im Verzeichnis "Documents" im Home-Verzeichnis.

### grep

Durchsucht eine Datei oder einen Text nach einem bestimmten Muster oder Ausdruck. Zum Beispiel: `grep "error" log.txt` zeigt alle Zeilen in der Datei "log.txt" an, die das Wort "error" enthalten.

### less

Zeigt den Inhalt einer Datei an. Zum Beispiel: `less log.txt` zeigt den Inhalt der Datei "log.txt" an.

### head

Zeigt die ersten Zeilen einer Datei an. Zum Beispiel: `head log.txt` zeigt die ersten 10 Zeilen der Datei "log.txt" an.

### tail

Zeigt die letzten Zeilen einer Datei an. Zum Beispiel: `tail log.txt` zeigt die letzten 10 Zeilen der Datei "log.txt" an.

### touch

Erstellt eine leere Datei. Zum Beispiel: `touch log.txt` erstellt eine leere Datei namens "log.txt".

## Systemüberwachung

### top

Zeigt eine Liste der laufenden Prozesse an. Zum Beispiel: `top` zeigt eine Liste der laufenden Prozesse an.

### ps

Zeigt eine Liste der laufenden Prozesse an. Zum Beispiel: `ps aux` zeigt alle Prozesse auf dem System an.

### ifconfig

Zeigt die Netzwerkkonfiguration an. Zum Beispiel: `ifconfig en0` zeigt die Konfiguration des Netzwerkadapters "en0" an.

## Netzwerk-Tools

### ping

Sendet einen Ping an einen Host. Zum Beispiel: `ping google.com` sendet einen Ping an "google.com".

### ssh

Verbindet sich mit einem entfernten Server per Secure Shell (SSH). Zum Beispiel: `ssh user@server.com` verbindet sich mit dem Server "server.com" als Benutzer "user".

## Dateisystem-Tools

### df

Zeigt den freien Speicherplatz auf den Dateisystemen an. Zum Beispiel: `df -h` zeigt den freien Speicherplatz in einer menschenlesbaren Form an.

### du

Zeigt die Größe von Dateien und Verzeichnissen an. Zum Beispiel: `du -sh` zeigt die Größe des aktuellen Verzeichnisses in einer menschenlesbaren Form an.

### tar

Erstellt oder extrahiert ein tar-Archiv. Zum Beispiel: `tar -xvf archive.tar` extrahiert das Archiv "archive.tar".

### unzip

Entpackt eine ZIP-Datei. Zum Beispiel: `unzip archive.zip` entpackt die ZIP-Datei "archive.zip".

### diskutil

Zeigt Informationen über die Festplatten an. Zum Beispiel: `diskutil list` zeigt eine Liste der Festplatten an.

### ln

Erstellt einen symbolischen Link. Zum Beispiel: `ln -s ~/Documents/MyProject ~/Desktop/MyProject` erstellt einen symbolischen Link zum Verzeichnis "MyProject" im Verzeichnis "Documents" im Home-Verzeichnis auf dem Desktop.

### mount

Bindet ein Dateisystem ein. Zum Beispiel: `mount -t iso9660 image.iso /mnt/iso` bindet die ISO-Datei "image.iso" in das Verzeichnis "/mnt/iso" ein.

## Zugriffsrechte-Tools

### chmod

Ändert die Zugriffsrechte für eine Datei oder ein Verzeichnis. Zum Beispiel: `chmod 755 script.sh` gibt dem Skript "script.sh" die Berechtigung, ausgeführt zu werden.

### chown

Ändert den Eigentümer einer Datei oder eines Verzeichnisses. Zum Beispiel: `chown user file.txt` ändert den Eigentümer der Datei "file.txt" auf den Benutzer "user".

## Root-Tools

### sudo

Führt einen Befehl als Superuser aus. Zum Beispiel: `sudo reboot` startet den Computer neu.
