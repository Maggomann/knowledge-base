---
category: php
sub_category_1: destruct
language: en
tags:
- php
- try-catch
---

# php

## Try catch finally

Errors and exceptions occur when running our scripts, that is part of the nature of things.
However, it is necessary to distinguish errors from each other and handle them accordingly.
For this we can use the keywords **try**, **catch** and **finally** in PHP.

### try catch Block

We can handle errors and exceptions if the code that produces them is written in a **try** block.
We can then catch them with the **catch** keyword.

```php
<?php
try {
    # Tu was
} catch (Exception $e) {
    # Kümmere dich um Ausnahmen
}
```

#### Errors and exceptions

An error occurs, for example, when you call a function that was never defined.

```php
<?php undefinierte_funktion(); ?>
```

Output:

```batch
Fatal error: Uncaught Error: Call to undefined function undefinierte\_funktion() in C:\\xampp\\htdocs\\codecitrus\\try\_catch.php:1 Stack trace: #0 {main} thrown in C:\\xampp\\htdocs\\codecitrus\\try\_catch.php on line 1
```

To define code that is executed only when an error (**Error**) occurs, you can apply **try** and **catch**.

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

If instead an exception (**exception**) occurs, you must specify so in the **catch** block to handle it.

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

#### Multiple catch blocks

The previous explanations have dealt with both exceptions and errors. To catch both, you could define two **catch** blocks in a row.

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

Another possibility is to intercept **throwable** with **catch**.
Throwable is the interface that every PHP class must implement if it is to be called with **throw**.
For the next example, the _exception_ function we defined earlier will be used again.

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

### finally Block

You can add more code to your block with the **finally** keyword.
**Finally** allows you to write code that will be executed whether an error occurs or not.

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

#### return in finally

**return** can lead to unexpected results when using **finally**.

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

In the previous example, the value of **return** from the **catch** block was simply overwritten with that from **finally**.
The same would happen if **return** had already received a value from **try**.

### Conclusion

With **try**, **catch** and **finally**, PHP provides us with powerful tools to handle exceptions and errors.
We can use them to create logs, run alternate routines, or simply stop our script.
However, care should be taken when we use our code in such blocks with **return**, as this may lead to unexpected results.

- [Original Artikel von Patrick](https://codegree.de/php-try-catch/)
