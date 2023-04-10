---
category: github-workflow
sub_category_1: pull-request-splitting
language: de
tags:
- git
- github
- best-practice
- pull-request
- pull-request-splitting
---

## Beispiel-Workflow

Hier ein Beispiel-Workflow für das Erstellen und Verwalten von Blog-Einträgen mit Pull-Request-Splitting:

``` mermaid
graph TD
	A((master-branch)) -- erstelle --> B((blog-db-migration))
	A -- erstelle --> C((blog-list-page))
	A -- erstelle --> D((blog-create-entry))
	A -- erstelle --> E((blog-edit-entry))
	B -- merge --> A
	C -- merge --> A
	D -- merge --> A
	E -- merge --> A
	B -- merge --> C
	C -- merge --> D
	D -- merge --> E
```

1.  Erstelle einen neuen Branch vom Master-Branch mit einem aussagekräftigen Namen wie z.B. "blog-db-migration" für die Migrationen.
	1.  Führe alle notwendigen Schritte durch, um die Migrationen zu implementieren und zu testen.
2.  Erstelle einen weiteren Branch vom aktuellen Master-Branch mit einem Namen wie "blog-list-page" für die Auflistung der Blog-Einträge.
	1.  Führe den vorherigen Branch "blog-db-migration" in diesen neuen Branch "blog-list-page" ein und führe alle notwendigen Schritte durch, um die Auflistung der Blog-Einträge zu implementieren und zu testen.
3.  Erstelle einen weiteren Branch vom aktuellen Master-Branch mit einem Namen wie "blog-create-entry" für das Hinzufügen neuer Blog-Einträge.
	1.  Führe den vorherigen Branch "blog-list-page" in diesen neuen Branch "blog-create-entry" ein und führe alle notwendigen Schritte durch, um das Hinzufügen neuer Blog-Einträge zu implementieren und zu testen.
4.  Erstelle einen weiteren Branch vom aktuellen Master-Branch mit einem Namen wie "blog-edit-entry" für das Bearbeiten von bestehenden Blog-Einträgen.
	1.  Führe den vorherigen Branch "blog-create-entry" in diesen neuen Branch "blog-edit-entry" ein und führe alle notwendigen Schritte durch, um das Bearbeiten von bestehenden Blog-Einträgen zu implementieren und zu testen.

!!! warning
	Es ist wichtig, dass jeder Pull-Request unabhängig voneinander funktioniert und nur die notwendigen Änderungen enthält. Daher sollte jeder Pull-Request nur dann bewertet werden, wenn der vorherige Pull-Request bereits gemerged wurde und der zu betrachtende Pull-Request daraufhin aktualisiert wurde. Wenn dies nicht beachtet wird, können zu viele Dateien im Pull-Request zum Review angezeigt werden, was das Review erschweren kann. Es ist auch wichtig, in jedem Pull-Request darauf hinzuweisen, auf welchen anderen Pull-Requests er aufbaut, um sicherzustellen, dass sie in der richtigen Reihenfolge geprüft und gemerged werden.

!!! tip
	Stashes können als Workaround genutzt werden, um Änderungen in verschiedenen Branches zu organisieren

	Falls man während der Arbeit bemerkt, dass man im aktuellen Branch Änderungen vorgenommen hat, die aber eigentlich einem anderen Branch zugeordnet werden müssten, kann man das Stashen als Workaround nutzen. Man kann die betreffenden Dateien in einem Stash zwischenspeichern, um sie später im richtigen Branch zuzuordnen. Auf diese Weise kann man vermeiden, dass Änderungen versehentlich im falschen Branch landen und so den Arbeitsablauf durcheinander bringen. Nachdem man den Stash angelegt hat, kann man ihn später auf den entsprechenden Branch verteilen und den Stash löschen.

!!! tip
	Es ist sinnvoll, den Code regelmäßig mit dem Haupt-Branch zu synchronisieren, um sicherzustellen, dass es zu keinen Konflikten kommt, wenn die Pull-Requests gemerged werden sollen.
