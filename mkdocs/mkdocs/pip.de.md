---
category: mkdocs
sub_category_1: pip
language: de
tags:
- mkdocs
- pip3
- konsolenkommandos
---

# Pip3 Kommandos

## pip3 Version anzeigen

```bash
pip3 --version
```

## Alle installierten Pakete auflisten

```bash
pip3 list
```

## pip3 aktualisieren

```bash
pip3 install --upgrade pip
```

## Alle installierten Pakete aktualisieren

```bash
pip3 freeze --local | grep -v '^\-e' | cut -d = -f 1  | xargs -n1 pip3 install -U
```

## mkdocs aktualisieren

```bash
pip3 install --upgrade mkdocs
```

## mkdocs Material aktualisieren

```bash
pip3 install --upgrade mkdocs-material
```

## mkdocs Material Extensions aktualisieren

```bash
pip3 install --upgrade mkdocs-material-extensions
```
