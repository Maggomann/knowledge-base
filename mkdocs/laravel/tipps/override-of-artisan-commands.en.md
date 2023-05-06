---
category: laravel
sub_category_1: tipps
sub_category_2: artisan
language: en
tags:
- laravel
- best-practice
- artisan
- commands
---

# Overriding Artisan commands

In Laravel, standard Artisan commands such as "migrate" can be overridden by defining a new command to replace the original command. This can be done in the "app/Console/Kernel.php" file.

First, you need to create a new command. To do this, use the following command in the command line:

```bash
php artisan make:command CustomMigrate
```

This will create a new file called "CustomMigrate.php" in the "app/Console/Commands" directory. Open this file and look for the "handle" method.

In this method, you can add your own logic to determine whether the migration command should be executed or not. If the command should not be executed, you can issue an error message. Otherwise, you can call the original migration command by using "parent::handle($input, $output);".

Here is an example that implements the logic you mentioned:

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

In this example, the migration command is executed only when the application is not running in locale mode. If the application is running in production mode, an error message is issued.

To register the new command, open the "app/Console/Kernel.php" file and add the following code:

```php
<?php
protected $commands = [
    \App\Console\Commands\CustomMigrate::class,
];
```

This registers the new command in the Laravel kernel so that it can be run from the command line by simply typing "php artisan migrate".

!!! warning
    Be sure to carefully review the conditions for executing the command to avoid unintended or undesirable results.
