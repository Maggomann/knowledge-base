---
category: laravel
sub_category_1: validation
language: de
tags:
- laravel
- validation
- request
- prepareForValidation
- prepare
---

# prepareForValidation

```php
<?php
use Illuminate\Validation\Rule;
use Smake\Common\Http\Requests\Request;

class EditUserRequest extends Request
{
    protected function prepareForValidation()
    {
        // do something before the data has been validated
        // Example:
        parent::prepareForValidation();

        $this->merge([
            'nickname' => $this->input('nickname', '') . ' with Love',
        ]);
    }

//...
```

## passedValidation

```php
use Illuminate\Validation\Rule;
use Smake\Common\Http\Requests\Request;

class EditUserRequest extends Request
{
    protected function passedValidation()
    {
        // do something after the data has been validated
        // Example:
        $this->merge([
            'nickname' => $this->input('nickname', '') . '❤️', 
        ]);


        // override the data for the request()->validated() method hack
        $this->getValidatorInstance()->setData(
            collect($this->input())
                ->only(collect($this->rules()]->keys())
                ->all()
        );
    }
//...
```