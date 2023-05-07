---
category: php
sub_category_1: destruct
language: de
tags:
- php
- desctruct
---

# PHP __desctruct

In PHP,

`__construct()`

wird bei der Erstellung eines Objekts aufgerufen und

`__destruct()`

wird aufgerufen, während das Objekt aus dem Speicher entfernt wird. Mit diesem Wissen können wir flüssigere APIs erstellen, wie Freek Van der Herten in diesem kurzen Video zeigt.

Schauen wir uns nun an, wann PHP Folgendes aufruft

`__destruct()`
` exactly.`

Ein Objekt wird aus dem Speicher entfernt, wenn Sie es explizit entfernen:

```php
<?php
$object = new Object();

unset($object); // __destruct will be called immediately.

$object = null; // __destruct will be called immediately.
```

Sie wird auch aufgerufen, wenn der Bereich, in dem das Objekt lebt, beendet werden soll, zum Beispiel am Ende einer Controller-Methode:

```php
<?php
function store(Request $request)
{
   $object = new Object();

   User::create(...);

   // __destruct will be called here.

   return view('welcome');
}
```

Selbst wenn wir uns in einem lang laufenden Prozess befinden, zum Beispiel in einer Warteschlange, wird __destruct vor dem Ende der Handle-Methode aufgerufen:

```php
<?php
function handle()
{
   $object = new Object();

   User::create(...);

   // __destruct will be called here.
}
```

Es wird auch aufgerufen, wenn das Skript beendet wird:

```php
<?php
function handle()
{
   $object = new Object();

   User::create(...);

   // __destruct will be called here.

   exit(1);
}
```

- [Original article by Mohamed Said](https://divinglaravel.com/when-does-php-call-__destruct)
