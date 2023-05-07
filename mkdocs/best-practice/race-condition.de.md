---
category: best-practice
sub_category_1: race-condition
language: de
tags:
- best-practice
- race-condition
---

## Race Condition

Eine Race Condition (ein Wettrennen um den Zugriff auf Ressourcen) ist eine unerwünschte Situation, die entsteht, wenn ein Gerät oder System versucht, zwei oder mehr Operationen gleichzeitig auszuführen. Aber wegen des jeweiligen besonderen Charakters der Geräte oder Systeme müssen die Operationen in der richtigen Reihenfolge ausgeführt werden, um wirklich korrekt zu sein.

Ein einfaches Beispiel für eine Race Condition ist ein Lichtschalter. In einigen Häusern oder Wohnungen gibt es mehrere Lichtschalter, die mit einem gemeinsamen Deckenlicht verbunden sind. Wenn diese Schaltungstypen benutzt werden, wird die jeweilige Schalterposition irrelevant. Ist das Licht eingeschaltet, und man bewegt jeden anderen Schalter aus seiner gegenwärtigen (Einschalt-)Position, wird das Licht wieder ausgeschaltet. Entsprechend gestaltet sich die Situation, wenn das Licht ausgeschaltet ist: Durch die Benutzung jeden Schalters in seiner aktuellen Position wird das Licht eingeschaltet. Auf dieser Grundlage muss man sich nun vorstellen, was passieren könnte, wenn zwei Personen an zwei verschiedenen Schaltern genau zum gleichen Zeitpunkt versuchen, das Licht einzuschalten. Ein Schaltvorgang könnte den anderen ausschalten oder beide gleichzeitigen Aktionen könnten zu einem Kurzschluss führen.

Race Conditions werden in aller Regel mit Computer Science und IT assoziiert. Bei Computer-Memory oder [[Storage]] kann eine Race Condition auftreten, wenn Lese- und Schreibbefehle für große Datenmengen fast zum gleichen Zeitpunkt empfangen werden und das Gerät versucht, einige oder alle der alten Daten zu überschreiben, während diese alten Daten noch gelesen werden. In der Folge können eines oder mehrere der folgenden Phänomene auftreten: ein Computer-Crash, eine nicht näher identifizierbare „illegale Operation“, Aufrufen und Shutdown eines Programms, Fehler beim Lesen der alten Daten oder Fehler beim Schreiben der neuen Daten. Eine Race Condition kann auch auftreten, wenn Anordnungen nicht in der korrekten Reihenfolge umgesetzt werden.

Nehmen wir zum Beispiel an, dass zwei Prozesse einen Bit Flip (Bit-Wechsel) an einem spezifischen Memory-Ort vornehmen müssen. Unter normalen Umständen sollte die Operation wie folgt ablaufen:

<table><tbody><tr><td><p>Process 1</p></td><td><p>Process 2</p></td><td><p>Memory Value</p></td></tr><tr><td><p>Read value</p></td><td></td><td><p>0</p></td></tr><tr><td><p>Flip value</p></td><td></td><td><p>1</p></td></tr><tr><td></td><td><p>Read value</p></td><td><p>1</p></td></tr><tr><td></td><td><p>Flip value</p></td><td><p>0</p></td></tr></tbody></table>

Prozess 1 führt also einen Bit Flip durch, indem er den Memory-Wert von 0 auf 1 setzt. Prozess 2 führt dann einen Bit Flip durch und ändert den Memory-Wert von 1 auf 0.

Bei einer Race Condition führen diese zwei Prozesse zu einer Überlappung, und die Sequenz könnte womöglich wie folgt aussehen:

<table><tbody><tr><td><p>Process 1</p></td><td><p>Process 2</p></td><td><p>Memory Value</p></td></tr><tr><td><p>Read value</p></td><td></td><td><p>0</p></td></tr><tr><td></td><td><p>Read value</p></td><td><p>0</p></td></tr><tr><td><p>Flip value</p></td><td></td><td><p>1</p></td></tr><tr><td></td><td><p>Flip value</p></td><td><p>1</p></td></tr></tbody></table>

In diesem Beispiel hat das Bit einen Schlusswert von 1, sollte aber einen Wert von 0 haben. Dies passiert, weil der zweite Prozess nicht weiß, dass Prozess 1 einen zeitgleichen Bit Flip durchführt.

### Wie man Race Conditions verhindert

In Rechner-Umgebungen kann man Race Conditions verhindern, indem man den Memory- oder Speicherzugang priorisiert. Dies bedeutet, dass der Lesebefehl immer zuerst ausgeführt und beendet wird, wenn Lese- und Schreibkommandos in etwa zeitgleich empfangen werden.

In einem Netzwerk kann eine Race Condition auftreten, wenn zwei Anwender zum gleichen Zeitpunkt auf einen verfügbaren Kanal zugreifen wollen und keiner der beteiligten Computer vor seiner Zugangsgenehmigung eine Mitteilung erhält, dass der Kanal bereits besetzt ist. Statistisch gesehen wird diese Art von Überschneidung mit hoher Wahrscheinlichkeit in Netzwerken mit langen Zeitverzögerungen auftreten – zum Beispiel in solchen, die auf geostationären Satelliten beruhen. Um zu verhindern, dass sich so eine Wettbewerbssituation entwickelt, muss man eine Prioritätsregelung entwerfen. Diese kann zum Beispiel darin bestehen, dass der Anwender, dessen Nutzernamen mit einem früheren Buchstaben im Alphabet (oder einer niedrigeren Nummer) beginnt, immer dann als erster den Zugang bekommt, wenn zwei Anwender in einem definierten Zeitraum versuchen, auf das System zuzugreifen. Hacker sind in der Lage, solche sensiblen Race Conditions für sich auszunutzen und sich mit ihrer Hilfe unautorisierten Zugang zu Netzwerken zu verschaffen.

Race Conditions treten gelegentlich auch bei logischen Zugangsorten (Gates) auf, wenn bestimmte Inputs miteinander in Konflikt geraten. Weil der Output des Gates eine bestimmte Zeit beansprucht, um auf jede Änderung der Inputs zu reagieren, können empfindliche Netze oder Geräte hinter dem Gate darüber getäuscht werden, in welchem Zustand sich der Output gerade befindet, und deshalb nicht korrekt fungieren.
