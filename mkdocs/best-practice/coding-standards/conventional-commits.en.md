---
category: coding-standards
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

## Summary

Conventional commits is a method of standardizing commit messages in Git repositories that makes it easier to track and trace changes in the code base. It is a set of rules and conventions that define how commit messages should be structured to ensure consistency and clear meaning.

The structure of Conventional Commits consists of a prefix and a message body. The prefix consists of a type that indicates the nature of the change, and optionally a range specification that identifies the affected code range. The message text should contain a brief summary of the change and optionally a longer description or explanation of the change.

By using Conventional Commits, developers can quickly find out what type of changes were made in a commit and what code areas are affected. This makes it easier to review and track the changes, which is especially beneficial for larger projects or when collaborating with other developers.

Conventional Commits is an open source project and can be used by developers around the world. There are also a number of tools and plugins that support Conventional Commits and facilitate integration into the development toolchain.

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

## Parentheses in prefix for scope specification.

Generally, parentheses are used to indicate the scope of the commit, such as the module or tool that is affected by the change. When using parentheses, you should put the scope in parentheses, followed by a colon and a space, before writing the actual commit description text.

| range specification | description |
| -------------- | ---------------------------------------------------------------------------- |
| (area) | The area affected by the change (e.g. (login), (registration) |
| | |

### Examp

```
feat(login): add remember me checkbox
```

The use of parentheses in the prefix in Conventional Commits is optional and depends on the specific implementation or convention used in your project or organization.

However, if you decide to use parentheses in the prefix, you should make sure that this is clearly stated in your project's documentation so that all developers working on the project can follow the same convention. If you decide not to use parentheses in the prefix, however, it is important that you write a clear and consistent commit description that states the purpose and scope of the change, so that other developers can easily understand and track the change as described above.

## Sources and tools

### Official documentation

[Conventional Commits](https://www.conventionalcommits.org)

### Commitizen

"Commitizen", provides a simplified way to write Git commit messages that conform to the conventions of "Conventional Commits".

The Commitizen web application provides a graphical user interface that helps developers create a standardized commit message through an interactive process. This can help ensure that commit messages are consistent and readable, which can help facilitate team collaboration.

[Commitizen](https://commitizen-tools.github.io/commitizen/)
