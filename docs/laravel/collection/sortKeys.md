---
category: laravel
sub_category_1: collection
language: de
tags:
- laravel
- collection
---

```php
<?php
	$exampleEntries = [
		'key_1' => 'value_1',
		'key_3' => 'value_3',
		'key_2' => 'value_2',
		'key_7' => 'value_7',
		'key_4' => 'value_4',
		'key_6' => 'value_6',
		'key_5' => 'value_5',
	];

	$result = collect($exampleEntries)->sortKeys()->dump();
	
	$result = [
		"key_1" => "value_1",
		"key_2" => "value_2",
		"key_3" => "value_3",
		"key_4" => "value_4",
		"key_5" => "value_5",
		"key_6" => "value_6",
		"key_7" => "value_7",
	]
```
