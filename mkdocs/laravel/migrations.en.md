---
category: laravel
sub_category_1: migrations
language: en
tags:
- laravel
- databse
- DB
- migrations
---
# Laravel Migrations

Laravel Migrations is a version control system for databases that allows defining, modifying, and deleting tables. Migrations make collaboration within a team easier.

## Creating a Migration

```bash
php artisan make:migration create_your_table_name_table
```

## Running Migrations

This command executes all the up methods of migration files that have not yet been executed.

```bash
php artisan migrate
```

## Checking the Status of Migrations

```bash
php artisan migrate:status
```

## Rolling Back Migrations

This command executes all the down methods of migration files that were previously executed by the `php artisan migrate` command.

```bash
php artisan migrate:rollback
```

## Specifying How Many `php artisan migrate` Commands to Roll Back

In this case, all the down methods of migration files that were applied with the last three `php artisan migrate` commands will be executed.

```bash
php artisan migrate:rollback --step=3
```

## Merging (Squashing) Migrations into a SQL File

```bash
php artisan schema:dump

# Dump the current database schema and prune all existing migrations...
php artisan schema:dump --prune
```
