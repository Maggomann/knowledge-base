---
category: php
sub_category_1: destruct
language: de
tags:
- php
- desctruct
- try-catch
---

# php

## Try catch finally

Beim Ausführen unserer Skripte treten Fehler und Ausnahmen auf, das gehört zur Natur der Sache.
Jedoch ist es nötig, Fehler voneinander zu unterscheiden und entsprechend zu behandeln.
Dafür können wir in PHP die Schlüsselwörter **try**, **catch** und **finally** verwenden.

### **1\. Ein einfacher PHP try catch Block**

Fehler und Ausnahmen können wir behandeln, wenn der Code, der diese produziert, in einem **try** Block geschrieben wird.
Mit dem Schlüsselwort **catch** können wir diese dann abfangen.

```php
<?php
try {
    # Tu was
} catch (Exception $e) {
    # Kümmere dich um Ausnahmen
}
```

#### **1.1 Fehler und Ausnahmen**

Ein Fehler tritt zum Beispiel auf, wenn du eine Funktion aufrufst, die nie definiert wurde.

```php
<?php undefinierte_funktion(); ?>
```

Output:

```batch
Fatal error: Uncaught Error: Call to undefined function undefinierte\_funktion() in C:\\xampp\\htdocs\\codecitrus\\try\_catch.php:1 Stack trace: #0 {main} thrown in C:\\xampp\\htdocs\\codecitrus\\try\_catch.php on line 1
```

Um Code zu definieren, der nur ausgeführt wird, wenn ein Fehler (**Error**) auftritt, kannst du **try** und **catch** anwenden.

```php
<?php
try {
    undefinierte_funktion();
    echo 'Es ist kein Fehler aufgetreten';
} catch (Error $e) {
    echo 'Ein Fehler ist aufgetreten' . '<br>';
    echo $e->getMessage();
}
```

Output:

```batch
Ein Fehler ist aufgetreten
Call to undefined function undefinierte_funktion()
```

Wenn stattdessen eine Ausnahme (**Exception**) auftritt, musst du das im **catch** Block so angeben, um diese zu behandeln.

```php
<?php
function ausnahme() {
    throw new Exception('Eine Ausnahme ist aufgetreten');
}
try {
    ausnahme();
} catch (Exception $e) {
    echo $e->getMessage();
}
```

Output:

```batch
Eine Ausnahme ist aufgetreten
```

#### **1.2 Beide abfangen mit Throwable**

Die vorigen Erklärungen haben sowohl Exceptions als auch Errors behandelt. Um beide abzufangen, könntest du zwei **catch** Blöcke hintereinander definieren.

```php
<?php
try {
    undefinierte_funktion();
} catch (Exception $e) {
    echo 'Exception';
} catch (Error $e) {
    echo 'Error';
}
```

Output:

```batch
Error
```

Eine weitere Möglichkeit ist, **Throwable** mit **catch** abzufangen.
Throwable ist das Interface, das jede PHP-Klasse implementieren muss, soll sie mit **throw** aufgerufen werden.
Für das nächste Beispiel wird die Funktion _ausnahme_, die wir vorhin definiert haben, erneut genutzt.

```php
<?php
try {
    undefinierte_funktion();
} catch (Throwable $t) {
    echo 'Gotta catch \'em all!';
}
// Gotta catch 'em all!
try {
    ausnahme();
} catch (Throwable $t) {
    echo 'Schnapp sie dir alle!';
}
// Schnapp sie dir alle!
```

### **2\. finally um den Block zu beenden**

Mit dem Schlüsselwort **finally** kannst du deinem Block weiteren Code hinzufügen.
**finally** ermöglicht es dir, Code zu schreiben, der ausgeführt wird egal ob ein Fehler auftritt oder nicht.

```php
<?php
function finally_beispiel_1() {
    try {
        throw new Exception();
    } catch (Exception $e) {
        echo "Exception!" . '<br>';
    } finally {
        echo "Finally!";
    }
}
finally_beispiel_1();
```

Output:

```batch
Exception!
Finally!
```

#### **2.1 Vorsicht mit return**!

**return** kann bei Verwendung von **finally** zu unerwarteten Ergebnissen führen.

```php
<?php
function finally_beispiel_2() {
    try {
        throw new Exception();
        return 1;
    } catch (Exception $e) {
        echo "Exception!" . '<br>';
        return 2;
    } finally {
        echo "Finally!" . '<br>';
        return 3;
    }
}
echo finally_beispiel_2();
```

Output:

```batch
Exception!
Finally!
3
```

Im vorigen Beispiel wurde der Wert von **return** aus dem **catch** Block einfach mit dem aus **finally** überschrieben.
Dasselbe würde passieren, wenn **return** bereits einen Wert aus **try** empfangen hätte.

### **3\. Fazit** – PHP try & catch

Mit **try**, **catch** und **finally** stellt uns PHP mächtige Werkzeuge zur Verfügung, um Ausnahmefälle und Fehler zu behandeln.
Damit können wir Logs erstellen, alternative Routinen ausführen oder einfach unser Skript stoppen.
Vorsicht ist jedoch geboten, wenn wir unseren Code in solchen Blöcken mit **return** verwenden, da dies zu unerwarteten Ergebnissen führen kann.

- [Original Artikel von Patrick](https://codegree.de/php-try-catch/)

---

## When does PHP call __destruct()?

In PHP,

`__construct()
` is called while creating an object and
`__destruct()
` is called while the object is being removed from memory. Using this knowledge, we can create more fluent APIs as demonstrated by Freek Van der Herten in this short video.

Now let's see when PHP calls

`__destruct()
` exactly.

An object is removed from memory if you explicitly remove it:

```php
<?php
$object = new Object();

unset($object); // __destruct will be called immediately.

$object = null; // __destruct will be called immediately.
```

It's also called when the scope where the object live is about to be terminated, for example at the end of a controller method:

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

Even if we're within a long running process, queued job for example, __destruct will be called before the end of the handle method:

```php
<?php
function handle()
{
   $object = new Object();

   User::create(...);

   // __destruct will be called here.
}
```

It'll also be called when the script is being terminated:

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
