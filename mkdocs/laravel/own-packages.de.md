---
category: laravel
sub_category_1: packages
language: de
tags:
- laravel
- package
- package-entwicklung
---

maggomann/filament-model-translator

## Beispiel anhand maggomann/filament-model-translator

 composer,json-File:

"require": {
	"maggomann/filament-model-translator": "dev-master",

Im CLI folgenden Befehl ausführen:

```console
composer config repositories.maggomann/filament-model-translator '{"type": "path", "url": "../../LaravelPackages/filament-model-translator"}' --file composer.json

composer update
````

Dies sollte folgende Ausgabe wiedergeben:

```console
Lock file operations: 1 install, 0 updates, 0 removals
  - Locking maggomann/filament-model-translator (dev-master)
Writing lock file
Installing dependencies from lock file (including require-dev)
Package operations: 1 install, 0 updates, 0 removals
  - Installing maggomann/filament-model-translator (dev-master): Symlinking from ../../LaravelPackages/filament-model-translator
```

## Webseiten-Verlinkungen

[Paket lokal testen](https://laravel-news.com/developing-laravel-packages-with-local-composer-dependencies)

[Paket-Dokumentation](https://laravelpackage.com/01-the-basics.html#autoloading)
