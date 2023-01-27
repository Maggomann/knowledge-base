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