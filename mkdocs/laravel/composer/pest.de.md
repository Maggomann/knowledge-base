---
category: composer
sub_category_1: pest
language: de
tags:
- composer
- pest
---

# Pest

## composer.json

```json
{
	"require-dev": {
		"pestphp/pest": "^1.22",
		"pestphp/pest-plugin-laravel": "^1.3",
		"pestphp/pest-plugin-livewire": "^1.0",
		"phpstan/extension-installer": "^1.1",
		"phpstan/phpstan-deprecation-rules": "^1.0",
		"phpstan/phpstan-phpunit": "^1.0",
		"phpunit/php-code-coverage": "^9.2",
		"phpunit/phpunit": "^9.5"
	},
	"scripts": {
		"test:pest": "vendor/bin/pest --order-by default -d memory_limit=6144M",
		"test:pest-coverage": "php -dpcov.enabled=1 -dpcov.directory=. -dpcov.exclude='~vendor~' vendor/bin/pest -d memory_limit=6144M --testdox --verbose --coverage --min=85",
	"test:unit": "vendor/bin/testbench package:test --no-coverage",
	"test:types": "vendor/bin/phpstan analyse",
	"test": [
		"@lint:fix",
		"@test:types",
		"@test:unit"
	]
}
```
