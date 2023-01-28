---
category: laravel
sub_category_1: routing
language: de
tags:
- laravel
- route
---

# Routing

## Test-Route

```php
<?php
use Illuminate\Support\Facades\Route;

Route::get('/test-route', function () {
    // return your example
})
```

## withoutMiddleware

```php
use App\Http\Middleware\FirstMiddleware;
use App\Http\Middleware\SecondMiddleware;
use Illuminate\Support\Facades\Route;

Route::prefix('my-prefix')
    ->middleware([
        FirstMiddleware::class,
        SecondMiddleware::class,
    ])
    ->group(function () {
        Route::get('my-route', function () {
            // Uses first & second middleware
        });
        Route::withoutMiddleware(FirstMiddleware::class)
            ->get('route-without-first-middleware', function () {
                // Uses second middleware
            });
        Route::withoutMiddleware(SecondMiddleware::class)
            ->get('route-without-second-middleware', function () {
                // Uses first middleware
            });
        Route::withoutMiddleware([
            FirstMiddleware::class,
            SecondMiddleware::class,
        ])->get('route-without-middleware', function () {
            // Uses no middleware
        }
    );
});
```

## with Parameters

```php
<?php
namespace App\Http\Middleware;

use Closure;

class EnsureUserHasRole
{
	public function handle($request, Closure $next, $role)
	{
		if (! $request->user()->hasRole($role)) {
			// Redirect...
		}

		return $next($request);

	}
}
```


```php
<?php
use Illuminate\Support\Facades\Route;

Route::put('/post/{id}', function ($id) {
	//
})->middleware('role:editor');
```
