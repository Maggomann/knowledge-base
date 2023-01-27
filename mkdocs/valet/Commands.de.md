---
category: valet
sub_category_1: commandos
language: de
tags:
- valet
- commandos
---

# Kommandos

## Valet: Erstellt V-Hosts Links: htttp://www.meine-lokale-webseite.test und htttps://www.meine-lokale-webseite.test

```bash
valet link --secure meine-lokale-webseite
```

## Valet: Löscht die V-Hosts Links: htttp://www.meine-lokale-webseite.test und htttps://www.meine-lokale-webseite.test

```bash
valet unlink --secure meine-lokale-webseite
```

## Valet: Alle registrierten Valet-Links anzeigen

```bash
valet links
```

## Valet: Listet alle verfügbaren Valet Kommandos auf

```bash
valet -h
valet --help
```