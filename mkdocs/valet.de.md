---
category: valet
sub_category_1: commandos
language: de
tags:
- valet
- commandos
---

# Valet

## Kommandos

### Erstellt V-Hosts Links

```bash
valet link --secure meine-lokale-webseite
```

!!! info

htttp://www.meine-lokale-webseite.test 
htttps://www.meine-lokale-webseite.test

### Löscht die V-Hosts Links

```bash
valet unlink --secure meine-lokale-webseite
```

!!! info

htttp://www.meine-lokale-webseite.test 
htttps://www.meine-lokale-webseite.test

### Alle registrierten Valet-Links anzeigen

```bash
valet links
```

### Listet alle verfügbaren Valet Kommandos auf

```bash
valet -h
valet --help
```
