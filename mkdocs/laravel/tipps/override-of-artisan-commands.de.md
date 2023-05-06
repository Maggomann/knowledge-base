---
category: laravel
sub_category_1: tipps
sub_category_2: artisan
language: de
tags:
- laravel
- best-practice
- artisan
- commands
---

# Überschreibung von Artisanbefehlen

In Laravel können Standard Artisan-Befehle wie "migrate" überschrieben werden, indem ein neuer Befehl definiert wird, der den ursprünglichen Befehl ersetzt. Dies kann in der "app/Console/Kernel.php" Datei durchgeführt werden.

Zunächst müssen Sie einen neuen Befehl erstellen. Verwenden Sie dazu den folgenden Befehl in der Befehlszeile:

```bash
php artisan make:command CustomMigrate
```

Dies erstellt eine neue Datei namens "CustomMigrate.php" im Verzeichnis "app/Console/Commands". Öffnen Sie diese Datei und suchen Sie nach der "handle" Methode.

In dieser Methode können Sie Ihre eigene Logik hinzufügen, um zu bestimmen, ob der Migrationsbefehl ausgeführt werden soll oder nicht. Wenn der Befehl nicht ausgeführt werden soll, können Sie eine Fehlermeldung ausgeben. Ansonsten können Sie den ursprünglichen Migrationsbefehl aufrufen, indem Sie "parent::handle($input, $output);" verwenden.

Hier ist ein Beispiel, das die Logik implementiert, die Sie erwähnt haben:

```php
<?php

namespace App\Console\Commands;

use Illuminate\Console\Command;

class CustomMigrate extends Command
{
    protected $signature = 'migrate';
    protected $description = 'Custom migrate command that outputs an error message on "local" environment';

    public function handle()
    {
        if (app()->environment('local')) {
            $this->error('Migrate command cannot be run on local systems');

            exit;
        }

        parent::handle();
    }
}
```

In diesem Beispiel wird der Migrationsbefehl nur ausgeführt, wenn die Anwendung nicht im Localenmodus läuft. Wenn die Anwendung im Produktionsmodus läuft, wird eine Fehlermeldung ausgegeben.

Um den neuen Befehl zu registrieren, öffnen Sie die "app/Console/Kernel.php" Datei und fügen Sie den folgenden Code hinzu:

```php
<?php
protected $commands = [
    \App\Console\Commands\CustomMigrate::class,
];
```

Dies registriert den neuen Befehl im Laravel-Kernel, so dass er über die Befehlszeile ausgeführt werden kann, indem einfach "php artisan migrate" eingegeben wird.

!!! warning
    Stellen Sie sicher, dass Sie die Bedingungen für die Ausführung des Befehls sorgfältig prüfen, um unbeabsichtigte oder unerwünschte Ergebnisse zu vermeiden.
