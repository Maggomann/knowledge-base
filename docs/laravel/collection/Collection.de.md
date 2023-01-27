---
category: laravel
sub_category_1: collection
language: de
tags:
- laravel
- collection
- sort
- sortKeys
---

# Collection

## sort

```php
<?php
	$exampleEntries = [
		'my example exa' => 'value_4',
		'my example' => 'value_1',
		'my example ex' => 'value_3',
		'my example e' => 'value_2',
	];

	$result = collect($exampleEntries)->sort()->toArray();
	
	$result = [
		"my example" => "value_1",
		"my example e" => "value_2",
		"my example ex" => "value_3",
		"my example exa" => "value_4",
	]
```

## sortKeys

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

	$result = collect($exampleEntries)->sortKeys()->toArray();
	
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