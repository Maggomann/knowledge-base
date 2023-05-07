---
category: wiki
sub_category_1: linux
sub_category_2: screen
language: de
tags:
- wiki
- linux
- screen
---

1.  Identify the name of the session:

```bash
 $ screen -ls
```

2.  Close a session:

```bash
$ screen -XS <session-id> quit
```

- **screen**

Befehl zum Installieren der Pakete:

```bash
sudo apt-get install screen
```

Oder mit [apturl](https://wiki.ubuntuusers.de/apturl/) installieren, Link: [apt://screen](apt://screen "apt://screen")

## Bedienung

Mit dem Befehl screen in einem Terminal lässt sich der Fenstermanager starten.

### Allgemein

Nach dem Aufruf von screen scheint es so, als ob nichts geschehen wäre. Das stimmt aber nicht, denn im Hintergrund läuft nun screen zum Verwalten der Sitzungen. Man kann nun ganz normal weiterarbeiten und verschiedene Programme starten, wie man es gewohnt ist.

### Wichtige Befehle

Die drei wichtigsten Befehle bzw. Tastenkombinationen, die man kennen sollte, sind:

-   Strg + A , gefolgt von C zum Erstellen eines neuen Fensters
-   Strg + A , gefolgt von N zum Wechseln zum nächsten Fenster
-   Strg + A , gefolgt von D zum Trennen (detach) der Verbindung zur aktuellen Sitzung, die Sitzung läuft dann im Hintergrund weiter

Eine Übersicht über alle Tastenkürzel erhält man mit Strg + A , gefolgt von ? .

Eine Sitzung beendet man, indem man die dort laufende Shell beendet, also entweder mit dem Befehl `exit` oder durch Drücken von Strg + D.

### Weitere Befehle

Starten einer neuen Sitzung mit dem Namen "sitzung1"

```bash
screen -S sitzung1
```

Trennt (engl.: "detach") die Verbindung zur aktuellen Sitzung: Strg + A + D

Nimmt die Sitzung wieder auf, falls nur eine einzige Sitzung im Hintergrund läuft:

Nimmt die Sitzung mit dem Namen "sitzung1" wieder auf:

```bash
screen -r sitzung1
```

Auflisten der Namen aller laufenden Screen-Sitzungen:

Trennt die Verbindung zu einer laufenden Sitzung mit dem Namen "sitzung1" (sehr hilfreich, wenn man z.B. die Verbindung per ssh verloren hat und deswegen die Sitzung nicht trennen konnte):

```bash
screen -d sitzung1
```

Die Sitzung mit dem Namen "sitzung1" kann an mehreren Computern gleichzeitig angezeigt werden:

```bash
screen -rx sitzung1
```

An die Sitzung mit dem Namen "sitzung1" einen Befehl senden und ausführen (\\n für \[ENTER\]):

```bash
screen -S sitzung1 -X stuff $'ls -l\n'
```

Visuelle Benachrichtigung umschalten (Flackern oder Ton; wenn der Bildschirm manchmal flackert, sollte man diesen Befehl ausführen, bis links unten "switched to audible bell" steht.): Strg + A + G

### Unterschied zwischen Sitzung und Fenster

Den Unterschied zwischen einer Screen-Sitzung und einem Screen-Fenster kann man sich etwa so wie bei einem Browser mit Tabs vorstellen, wobei Screen-Sitzungen einem Browserfenster und Screen-Fenster einem Browser-Tab entsprechen. Es können mehrere Screen-Sitzungen gleichzeitig laufen und in jeder Screen-Sitzung können mehrere Screen-Fenster geöffnet sein, so wie man mehrere Browserfenster öffnen kann und in jedem Browserfenster mehrere Tabs geöffnet sein können.

### Ausgabe scrollen

Um in der Ausgabe eines Screen-Fenster mit den bekannten Tastenkombinationen ⇧ + Bild ↑ und ⇧ + Bild ↓ zu scrollen, trägt man die Zeile

```bash
termcapinfo xterm|xterms|xs|rxvt ti@:te@
```

in die Datei **.screenrc** (welche eventuell noch angelegt werden muss) im Heimatverzeichnis ein.

Falls das nicht funktioniert, bleibt noch die Möglichkeit, mit Strg + A + Esc in den copy-Modus zu wechseln und dort mit den Pfeiltasten oder Strg + U (halbes Fenster hoch), Strg + D (halbes Fenster runter), Strg + B (ganzes Fenster zurück), Strg + F (ganzes Fenster vorwärts) zu scrollen. Danach verlässt man den copy-Modus mit Esc oder Q .

## Links

-   [Projektseite](https://www.gnu.org/software/screen/screen.html) 🇬🇧

-   [tmux](https://wiki.ubuntuusers.de/tmux/) - Alternative zu screen

-   [byobu](https://wiki.ubuntuusers.de/byobu/) - Erweiterung für screen
