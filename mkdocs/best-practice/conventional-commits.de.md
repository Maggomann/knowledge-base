---
category: github-workflow
sub_category_1: conventional-commits
language: de
tags:
- git
- github
- best-practice
- pull-request
- conventional-commits
---

# Conventional Commits

## Zusammenfassung

Conventional Commits ist eine Methode zur Vereinheitlichung von Commit-Messages in Git-Repositories, die es erleichtert, Änderungen in der Codebasis zu verfolgen und nachzuvollziehen. Dabei handelt es sich um eine Reihe von Regeln und Konventionen, die festlegen, wie Commit-Messages aufgebaut sein sollten, um eine einheitliche Struktur und eine klare Bedeutung zu gewährleisten.

Die Struktur von Conventional Commits besteht aus einem Präfix und einem Nachrichtentext. Das Präfix besteht aus einem Typ, der die Art der Änderung angibt, und optional einer Bereichsangabe, die den betroffenen Codebereich kennzeichnet. Der Nachrichtentext sollte eine kurze Zusammenfassung der Änderung enthalten und optional eine längere Beschreibung oder Erklärung der Änderung.

Durch die Verwendung von Conventional Commits können Entwickler schnell herausfinden, welche Art von Änderungen in einem Commit vorgenommen wurden und welche Codebereiche betroffen sind. Dies erleichtert es, die Änderungen zu überprüfen und nachzuvollziehen, was insbesondere bei größeren Projekten oder bei der Zusammenarbeit mit anderen Entwicklern von Vorteil ist.

Conventional Commits ist ein Open-Source-Projekt und kann von Entwicklern auf der ganzen Welt verwendet werden. Es gibt auch eine Reihe von Tools und Plugins, die Conventional Commits unterstützen und die Integration in die Entwicklungs-Toolchain erleichtern.

## Konventionelles Format für Commits

| Präfix   | Art der Änderung                                                                                                         |
| -------- | ------------------------------------------------------------------------------------------------------------------------ |
| feat     | Eine neue Funktion                                                                                                       |
| fix      | Eine Fehlerbehebung                                                                                                      |
| docs     | Nur Änderungen an der Dokumentation                                                                                      |
| style    | Änderungen, die die Bedeutung des Codes nicht beeinflussen (Leerzeichen, Formatierung, fehlende Semikolons usw.)         |
| refactor | Eine Codeänderung, die weder einen Fehler behebt noch eine Funktion hinzufügt                                            |
| perf     | Eine Code-Änderung, die die Leistung verbessert                                                                          |
| test     | Hinzufügen fehlender Tests oder Korrigieren vorhandener Tests                                                            |
| build    | Änderungen, die das Build-System oder externe Abhängigkeiten betreffen (Beispielbereiche: gulp, broccoli, npm)           |
| ci       | Änderungen an unseren CI-Konfigurationsdateien und -Skripten (Beispielbereiche: Travis, Circle, BrowserStack, SauceLabs) |
| chore    | Andere Änderungen, die keine src- oder Testdateien verändern                                                             |

##  Klammern im Präfix für Bereichsangaben

Im Allgemeinen werden Klammern verwendet, um den Bereich des Commits anzugeben, z. B. das Modul oder das Tool, das von der Änderung betroffen ist. Wenn du Klammern verwendest, solltest du den Bereich in Klammern setzen, gefolgt von einem Doppelpunkt und einer Leerstelle, bevor du den eigentlichen Commit-Beschreibungstext schreibst.

| Bereichsangabe | Beschreibung                                                                 |
| -------------- | ---------------------------------------------------------------------------- |
| (area)         | Der Bereich, der von der Änderung betroffen ist (z.B. (login), (registration) |
|                |                                                                             |

### Beispiel

```
feat(login): add remember me checkbox
```

Die Verwendung von Klammern im Präfix bei Conventional Commits ist optional und hängt von der spezifischen Implementierung oder Konvention ab, die in deinem Projekt oder deiner Organisation verwendet wird.

Wenn du dich jedoch für die Verwendung von Klammern im Präfix entscheidest, solltest du sicherstellen, dass dies in der Dokumentation eures Projekts klar angegeben ist, damit alle Entwickler, die am Projekt arbeiten, sich an die gleiche Konvention halten können. Wenn du dich entscheidest, keine Klammern im Präfix zu verwenden, ist es jedoch wichtig, dass du eine klare und konsistente Commit-Beschreibung schreibst, die den Zweck und den Umfang der Änderung angibt, damit andere Entwickler die Änderung leicht verstehen und nachvollziehen können so wie oben beschrieben.

## Quellen und Tools

### Offizielle Dokumentation

https://www.conventionalcommits.org

### Commitizen

"Commitizen", bietet eine vereinfachte Möglichkeit, Git-Commit-Nachrichten zu schreiben, die den Konventionen von "Conventional Commits" entsprechen.

Die Commitizen-Webanwendung stellt eine grafische Benutzeroberfläche zur Verfügung, die Entwicklern dabei hilft, durch einen interaktiven Prozess eine standardisierte Commit-Nachricht zu erstellen. Dadurch kann sichergestellt werden, dass Commit-Nachrichten konsistent und lesbar sind, was dazu beitragen kann, die Zusammenarbeit in einem Team zu erleichtern.

https://commitizen-tools.github.io/commitizen/
