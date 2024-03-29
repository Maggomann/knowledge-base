---
category: laravel
sub_category_1: tests
language: en
tags:
- laravel
- tests
- exception
- event
- mock
- spy
- expectException
- expectExceptionMessage
- assertDispatched
- assertNotDispatched
- assertDispatchedTimes
- assertNotDispatchedTimes
- once()
---

# Tests

## expectException and expectExceptionMessage


```php
<?php

use Application\User\Queries\ListUserQuery;
use Illuminate\Http\Request;
use Spatie\QueryBuilder\Exceptions\InvalidFilterQuery;
use Tests\TestCase;

class ListUserQueryTest extends TestCase
{
    /** @test */
    public function it_throws_an_exception_when_the_key_for_filtering_is_not_supported(): void
    {
        $this->expectException(InvalidFilterQuery::class);
        $this->expectExceptionMessage('Requested filter(s) `key_not_supported` are not allowed. Allowed filter(s) are `id, email, nickname`.');

        $request = new Request(['filter' => ['key_not_supported' => 'value is irrelevant']]);

        new ListMyModelQuery($request);
	}
}
```

## it_uses_the_right_query_filters


```php
<?php

    /** @test */
    public function it_uses_the_right_query_filters(): void
    {
        $this->assertQueryFilterEquals(
            ListMyModelQuery::class,
            [
                AllowedFilter::exact('id'),
                AllowedFilter::exact('handle'),
                AllowedFilter::partial('name', 'display_name'),
            ]
        );
    }
```

## assertThrows | it_throws_an_error_if_model_doesnt_exist

```php
<?php

    /** @test */
    public function it_throws_an_error_if_model_doesnt_exist(): void
    {
        $className = User::class;

        $this->assertThrows(
            fn () => User::findOrFail(0),
            ModelNotFoundException::class,
            "No query results for model [{$className}] 1"
        );
    }
```

## it_uses_the_right_query_class


```php
<?php

    /** @test */
    public function it_uses_the_right_query_class(): void
    {
        $query = $this->mock(
            ListMyModelQuery::class,
            fn (MockInterface $mock) => $mock->shouldReceive('simplePaginate')
                ->once()
                ->andReturn(MyModelFactory::new()->create()->simplePaginate()),
        );

        $controller = new ViewMyModelListController();
        $controller($query, new Request());

        $this->assertControllerUsesClass(
            ViewMyModelListController::class,
            ListMyModelQuery::class
        );
    }
```

## it_uses_the_right_collection


```php
<?php

    /** @test */
    public function it_uses_the_right_collection(): void
    {
        $this->assertControllerReturns(
            ViewMyModelListController::class,
            MyModelCollection::class
        );
    }
```

## it_uses_the_right_middleware

```php
<?php

    public function middlewares(): array
    {
        return [
            'group1' => ['group1_sub1', 'group1_sub2'],
            'group2' => ['group2_sub1', 'group2_sub2'],
            MyMiddleware::class => [MyMiddleware::class],
        ];
    }

    /**
     * @test
     *
     * @dataProvider middlewares
     */
    public function it_uses_the_right_middleware($middleware)
    {
        $this->assertControllerUsesMiddleware(
            ViewMyModelListController::class,
            $middleware,
        );
    }
```

## it_returns_the_right_structure | Collection


```php
<?php

    /** @test */
    public function it_returns_the_right_structure(): void
    {
        MyModelFactory::new()->create();

        $response = $this->createResource(MyModelCollection::class, MyModel::simplePaginate());

        $response->assertJsonStructureExact([
            'data',
            'links',
            'meta',
        ]);

        $this->assertEquals(MyModelResource::class, MyModelCollection::make([])->collects);
    }
```

## it_returns_the_right_structure | Resource


```php
<?php

	/** @test */
    public function it_returns_the_right_structure(): void
    {
        $response = $this->createResource(
            MyModelResource::class,
            MyModelFactory::new()->create()
        );

        $response->assertJsonStructureExact([
            'id',
            'my_column_one',
            'my_column_two',
            'created_at',
            'updated_at',
        ]);

        $response->assertJson(
            fn (AssertableJson $json) => $json
                ->whereAllType([
                    'id' => ['integer'],
                    'my_column_one' => ['string'],
                    'my_column_two' => [null, 'string'],
                    'created_at' => ['string'],
                    'updated_at' => ['string'],
                ])
                ->etc()
        );
    }
```

## examples_for_mock_actions


```php
<?php

    /** @test */
    public function examples_for_mock_actions(): void
    {
        $myAction = $this->spy(MyActionn::class);
        $myAction->shouldReceive('execute')
            ->once()
            ->withArgs(fn ($arg) => $arg === 'foo')
            ->andReturn('bar');

        // or
        $spy = $this->spy(MyActionn::class);
        $spy->shouldReceive('execute')
            ->once()
            ->with(MyExampleModel::class, MyExampleData::class)
            ->andReturn('bar');
    }
```

---

## Event::fake

### Event:: assertDispatched


```php
<?php

	/** @test */
    public function event_assert_dispatched(): void
    {
        Event::fake();

        // or

        Event::fake([
            ExampleCreated::class,
        ]);

        $myExample = MyExampleFactory::new()->create();

        // Assert a event was dispatched...
        Event::assertDispatched(ExampleCreated::class);

        // Assert a event was dispatched...
        Event::assertDispatched(ExampleCreated::class, function ($event) use ($myExample) {
            return $event->myExample->is($myExample);
        });
    }
```

### Event:: assertNotDispatched


```php
<?php

	/** @test */
    public function event_assert_not_dispatched(): void
    {
        Event::fake();

        // or

        Event::fake([
            ExampleCreated::class,
        ]);

        $myExample = MyExampleFactory::new()->create();

        // Assert a event was not dispatched...
        Event::assertNotDispatched(ExampleCreated::class);

        Event::assertNotDispatched(ExampleCreated::class, function ($event, $payload) {
            return $payload[0]->name === 'John Doe';
        });
    }
```

### Event:: assertDispatchedTimes


```php
<?php

	/** @test */
    public function event_assert_dispatched_times(): void
    {
        Event::fake();

        // or

        Event::fake([
            ExampleCreated::class,
        ]);

        $myExample = MyExampleFactory::new()->create();

        // Assert a event was dispatched exactly n times...
        Event::assertDispatchedTimes(ExampleCreated::class, 1);
    }
```

### Event:: assertListening


```php
<?php

	/** @test */
    public function event_assert_listening(): void
    {
        Event::fake();

        // or

        Event::fake([
            ExampleCreated::class,
        ]);

        $myExample = MyExampleFactory::new()->create();

        // assert that a listener is listening to a given event
        Event::assertListening(ExampleCreated::class, ExampleListener::class);
    }
```

## Queue::fake

### Queue:: assertPushed


```php
<?php

	/** @test */
    public function examples_for_queue_fakes(): void
    {
        Queue::fake();

        // or

        Queue::fake([
            ExampleJob::class,
        ]);

        // queue a job
        ExampleJob::dispatch();

        // assert that a job was pushed...
        Queue::assertPushed(ExampleJob::class);

        // assert that a job was pushed a given number of times...
        Queue::assertPushed(ExampleJob::class, 1);

        // assert that a job was pushed with a given payload...
        Queue::assertPushed(ExampleJob::class, function ($job) {
            return $job->example == 'example';
        });
    }
```

### Queue:: assertNotPushed

```php
<?php

	/** @test */
    public function queue_assert_not_pushed(): void
    {
        Queue::fake();

        // or

        Queue::fake([
            ExampleJob::class,
        ]);

        // queue a job
        ExampleJob::dispatch();

        // assert that a job was not pushed
        Queue::assertNotPushed(ExampleJob::class);

        // asser that a job was not pushed with a given payload...
        Queue::assertNotPushed(ExampleJob::class, function (ExampleJob $job) {
            return $job->exampleProperty === 'exampleValue';
        });
    }
```

### Queue:: assertNothingPushed


```php
<?php

	/** @test */
    public function queue_assert_nothing_pushed(): void
    {
        Queue::fake();

        // or

        Queue::fake([
            ExampleJob::class,
        ]);

        // queue a job
        ExampleJob::dispatch();

        // assert that no jobs were pushed...
        Queue::assertNothingPushed();
    }
```

### Queue:: assertPushedOn


```php
<?php

	/** @test */
    public function queue_assert_pushed_on(): void
    {
        Queue::fake();

        // or

        Queue::fake([
            ExampleJob::class,
        ]);

        // queue a job
        ExampleJob::dispatch();

        // assert that a job was pushed on a given queue...
        Queue::assertPushedOn('queue-name', ExampleJob::class);

        // assert that a job was pushed a given number of times on a given queue...
        Queue::assertPushedOn('queue-name', ExampleJob::class, 1);

        // assert that a job was pushed with a given payload on a given queue...
        Queue::assertPushedOn('queue-name', ExampleJob::class, function ($job) {
            return $job->example == 'example';
        });
    }
```

### Queue:: assertPushedWithChain


```php
<?php

	/** @test */
    public function queue_assert_pushed_with_chain(): void
    {
        Queue::fake();

        // or

        Queue::fake([
            ExampleJob::class,
        ]);

        // queue a job
        ExampleJob::dispatch();

        // assert that a job was pushed with a given chain...
        Queue::assertPushedWithChain(ExampleJob::class, [
            new AnotherJob,
            new YetAnotherJob,
        ]);

        // assert that a job was pushed with a given chain...
        Queue::assertPushedWithChain(ExampleJob::class, [
            new AnotherJob,
            new YetAnotherJob,
        ], function ($job) {
            return $job->user->id === 1;
        });
    }
```

### Queue:: assertPushedWithoutChain


```php
<?php

	/** @test */
    public function queue_assert_pushed_without_chain(): void
    {
        Queue::fake();

        // or

        Queue::fake([
            ExampleJob::class,
        ]);

        // queue a job
        ExampleJob::dispatch();

        // assert that a job was pushed without a given chain...
        Queue::assertPushedWithoutChain(ExampleJob::class);

        // assert that a job was pushed without a given chain and with a given payload...
        Queue::assertPushedWithoutChain(ExampleJob::class, function ($job) {
            return $job->exampleProperty === 'exampleValue';
        });
    }
```
