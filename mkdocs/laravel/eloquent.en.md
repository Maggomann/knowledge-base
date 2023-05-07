---
category: laravel
sub_category_1: eloquent
language: en
tags:
- laravel
- eloquent
- touch
---

# Eloquent

## Touch eloquent method

```php
<?php

$user = User::find(1);

// instead of
$user->update(['subscribed_at' => now()]);

// use
$user->touch('subscribed_at');
```

- [Original tweet by Oussama Sid](https://twitter.com/sky_0xs/status/1557673614345895936)
