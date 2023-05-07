---
category: laravel
sub_category_1: tipps
sub_category_2: calculation
language: en
tags:
- laravel
- best-practice
- calculation
---

**BCMath:** <https://www.php.net/manual/de/book.bc.php>
**github moneyphp/money:** <https://github.com/moneyphp/money>
web2.0rechner: <https://web2.0rechner.de/>

The BcMathCalculator calculates the decimal places exactly when calculating with string values. However, if the values are cast into a float, float rounds up to the 12th decimal place according to the rounding rule and then fills each further decimal place with the number 0.

```php
<?php
use Money\Calculator\BcMathCalculator;

$result = (new BcMathCalculator())->divide('15.000000000000000', '1.19');
// $result => 12.60504201680672

$result = (float) (new BcMathCalculator())->divide('15.000000000000000', '1.19');

// $result => 12.605042016807
// Float rounds up to the 12th decimal place and fills all further decimal places with a 0.
```

**Hier ein Beispiel der genaueren Rechnung:**
![[web2orechner_rundung.png]]
