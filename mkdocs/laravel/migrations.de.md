---
category: laravel
sub_category_1: migrations
language: de
tags:
- laravel
- databse
- DB
- migrations
---

# Laravel Migrations

Laravel Migrations ist eine Versionskontrolle für die Datenbank mit der Tabellen definiert, angepasst und gelöscht werden könnenn. Migrations erleichtern vor allem die Zusammenarbeit innerhalb eines Teams.

## Erstellen einer Migration

```bash
php artisan make:migration create_your_table_name_table
```

## Migrationen ausführen

Mit folgendem Befehl werden alle up Methoden aller migrations-Dateien ausgeführt, die bis Dato noch nicht ausgeführt wurden.

```bash
php artisan migrate
```

## Welche Migrationen wurden bereits ausgeführt

```bash
php artisan migrate:status
```

## Migration zurückdrehen

Mit diesem Befehl werden alle down-Methoden der Migrationsdateien ausgeführt die vorab durch den Befehl php artisan migrate ausgeführt wurden.

```bash
php artisan migrate:rollback
```

## Angeben wieviele php artisan migrate-Befehle wieder zurückgedreht werden sollen

In diesem Fall werden alle down-Methoden der Migrationsdateien ausgeführt, die mit den letzten drei php artisan migrate Befehlen eingespielt wurden.

```bash
php artisan migrate:rollback --step=3
```

## Migrationen in einer SQL-Datei zusammenführen (squaschen)

```bash
php artisan schema:dump

# Dump the current database schema and prune all existing migrations...
php artisan schema:dump --prune
```
