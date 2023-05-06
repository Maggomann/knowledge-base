---
category: clean-code
sub_category_1: solid-design-principles
language: en
tags:
- clean-code
- solid-design-principles
- solid
---

# Solid-Design-Principles

## Summary

The SOLID design principles are a group of five principles proposed by Robert C. Martin to improve software designs. Each of these principles provides a basic guide to help improve the quality, maintainability, and extensibility of software.

The five SOLID principles are:

### Single Responsibility Principle (SRP)

Single Responsibility Principle (SRP): A class should have only one responsibility. This means that it should perform only one task and be vulnerable to only one type of change.

```php
<?php


// bad
class Customer {
    private $name;
    private $email;

    public function __construct($name, $email) {
        $this->name = $name;
        $this->email = $email;
    }

    public function getName() {
        return $this->name;
    }

    public function getEmail() {
        return $this->email;
    }

    public function sendEmail($subject, $body) {
        // Code to send an e-mail
    }
}
/*
In this example, the `Customer` class is responsible for storing customer information and providing access methods as well as sending emails. The class thus has multiple responsibilities, making it harder to maintain and extend.
*/

// good
class Customer {
    private $name;
    private $email;

    public function __construct($name, $email) {
        $this->name = $name;
        $this->email = $email;
    }

    public function getName() {
        return $this->name;
    }

    public function getEmail() {
        return $this->email;
    }
}

class EmailSender {
    public function sendEmail(Customer $customer) {
        $email = $customer->getEmail();
        // Code to send an e-mail
    }
}
/*
In this example, the `Customer` class is only responsible for storing customer information and providing access methods. The `EmailSender` class is only responsible for sending emails. Both classes fulfill only one responsibility each.
*/
```

### Open-Closed Principle (OCP)

Software entities (classes, modules, functions, etc.) should be open to extension but closed to modification. This means that the functionality of a software entity should be extended by adding new code modules or classes without having to change the existing code.

```php
<?php

// bad
class AreaCalculator {
    public function calculate($shapes) {
        $area = 0;

        foreach ($shapes as $shape) {
            if ($shape instanceof Circle) {
                $area += pi() * pow($shape->getRadius(), 2);
            } elseif ($shape instanceof Rectangle) {
                $area += $shape->getLength() * $shape->getWidth();
            }
            // Other conditions for other forms
        }

        return $area;
    }
}
/*
In this example, the `AreaCalculator` class is open to modification because it needs to be changed when a new shape is added. The `Circle` and `Rectangle` classes are also open to modification, as they require new methods when new shapes are added.
*/

// good
 interface Shape {
    public function area();
}

class Circle implements Shape {
    private $radius;

    public function __construct($radius) {
        $this->radius = $radius;
    }

    public function area() {
        return pi() * pow($this->radius, 2);
    }
}

class Rectangle implements Shape {
    private $length;
    private $width;

    public function __construct($length, $width) {
        $this->length = $length;
        $this->width = $width;
    }

    public function area() {
        return $this->length * $this->width;
    }
}

class AreaCalculator {
    public function calculate(Shape $shape) {
        return $shape->area();
    }
}

/*
In this example, the `Circle` and `Rectangle` classes are closed to changes because they do not change their functionality when new shapes are added. The `AreaCalculator` class is open to extensions, since it can be easily extended to support calculating the area of new shapes.
*/
```

### Liskov Substitution Principle (LSP)

Objects of a derived class should be replaceable by objects of its base class without affecting the program. This means that a derived class should inherit all the behaviors of its base class without changing the behavior of the program.

```php
<?php

// bad
class Vehicle {
    protected $fuel;

    public function refuel($fuel) {
        // Code for refueling the vehicle
    }

    public function accelerate() {
        // Code for accelerating the vehicle
    }
}

class Car extends Vehicle {
    public function refuel($fuel) {
        if ($fuel > 50) {
            throw new Exception('Too much fuel');
        }

        parent::refuel($fuel);
    }

    public function accelerate() {
        // Code to accelerate the car
    }
}

/*
In this example, the `Car` class violates the Liskov Substitution Principle because it violates the contract terms of the `Vehicle` class. The `refuel()` method of the `Car` class performs an additional check to ensure that too much fuel is not added. If a section of code calls the `refuel()` method on a `Vehicle` instance and gets a `Car` instance instead, the additional checking might result in unexpected errors or exceptions.
*/


// good
class Vehicle {
    public function startEngine() {
        // Code to start the engine
    }
}

class Car extends Vehicle {
    public function startEngine() {
        parent::startEngine();
        // Code specifically for cars to start the engine
    }
}

class ElectricCar extends Car {
    public function startEngine() {
        // Code for starting the electric motor
    }
}

/*
In this example, the `ElectricCar` class can be used instead of the `Car` class without any problems, since it inherits all the methods and behaviors of the `Car` class and can also override them if necessary.
*/
```

### Interface Segregation Principle (ISP)

Interface Segregation Principle (ISP): Interfaces should be tailored to the specific needs of clients. This means that a class should not be forced to implement methods or properties that it does not need.

```php
<?php

// bad
interface Animal {
    public function move();
    public function fly();
    public function swim();
}

class Bird implements Animal {
    public function move() {
        // Code for the movement of a bird
    }

    public function fly() {
        // Code for flying a bird
    }

    public function swim() {
        throw new Exception('Birds cannot swim');
    }
}

class Fish implements Animal {
    public function move() {
        // Code for the movement of a fish
    }

    public function fly() {
        throw new Exception('Fish cannot fly');
    }

    public function swim() {
        // Code for swimming a fish
    }
}
/*
In this example, the `Animal` interface violates the interface segregation principle because it combines methods for flying, swimming, and moving, even though not all animals have these abilities. The `Bird` class must implement the `swim()` method even though birds cannot swim, and the `Fish` class must implement the `fly()` method even though fish cannot fly. This leads to unexpected errors or exceptions when the code accesses an instance of `Bird` or `Fish` and calls an unexpected method.
*/

// good
interface Animal {
    public function move();
}

interface FlyableAnimal extends Animal {
    public function fly();
}

interface SwimmableAnimal extends Animal {
    public function swim();
}

class Bird implements FlyableAnimal {
    public function move() {
        // Code for the movement of a fish
    }

    public function fly() {
        // Code for flying a bird
    }
}

class Fish implements SwimmableAnimal {
    public function move() {
        // Code zur Bewegung eines Fisches
    }

    public function swim() {
        // Code for swimming a fish
    }
}

/*
In this example, we have applied the interface segregation principle by defining separate interfaces for flying and swimming, each inheriting from the general `Animal` interface. This allows us to ensure that classes that cannot fly are not forced to implement a `fly()` method, and classes that cannot swim are not forced to implement a `swim()` method. In this case, the `bird` and `fish` classes implement only the methods relevant to their respective modes of locomotion.
*/
```

### Dependency Inversion Principle (DIP)

Dependency Inversion Principle (DIP): Dependencies should be based on abstract interfaces, not on concrete implementations. This means that higher modules should not depend on lower modules and that abstract modules should not depend on concrete modules.

```php
<?php

// bad
class MySqlDatabase {
    public function connect() {
        // Code to connect to a MySQL database
    }
}

class UserRepository {
    private $database;

    public function __construct() {
        $this->database = new MySqlDatabase();
    }

    public function getUsers() {
        $this->database->connect();
        // Code to retrieve users from the database
    }
}
/*
In this example, the Dependency Inversion Principle is violated because the `UserRepository` class is directly bound to the concrete implementation `MySqlDatabase`. If we want to use another database like PostgreSQL, we have to change the code in the `UserRepository` class. This causes the code to become rigid and difficult to extend. To preserve the DIP, the `UserRepository` class should use the `DatabaseInterface` abstraction instead of being directly bound to the concrete implementation..
*/

// good
interface DatabaseInterface {
    public function connect();
}

class MySqlDatabase implements DatabaseInterface {
    public function connect() {
        // Code to connect to a MySQL database
    }
}

class PostgreSqlDatabase implements DatabaseInterface {
    public function connect() {
        // Code to connect to a PostgreSQL database
    }
}

class UserRepository {
    private $database;

    public function __construct(DatabaseInterface $database) {
        $this->database = $database;
    }

    public function getUsers() {
        $this->database->connect();
        // Code to retrieve users from the database
    }
}
/*
In this example, we have applied the Dependency Inversion Principle by creating a `DatabaseInterface` abstraction that is implemented by concrete implementations `MySqlDatabase` and `PostgreSqlDatabase`. Instead of instantiating the concrete implementations directly in the `UserRepository` class, we inject the abstraction through the constructor. This way, the `UserRepository` class is no longer bound directly to concrete implementations, but only to the `DatabaseInterface` abstraction. This makes it easier to replace the database used and promotes flexibility and reusability of the code.
*/
```
