---
category: clean-code
sub_category_1: solid-design-principles
language: de
tags:
- clean-code
- solid-design-principles
- solid
---

# Boy-Scouting-Principle - Pfadfinderregel

## Zusammenfassung

Die SOLID-Design-Prinzipien sind eine Gruppe von fünf Prinzipien, die von Robert C. Martin vorgeschlagen wurden, um Software-Designs zu verbessern. Jedes dieser Prinzipien stellt einen grundlegenden Leitfaden dar, der dabei helfen soll, die Qualität, die Wartbarkeit und die Erweiterbarkeit von Software zu verbessern.

Die fünf SOLID-Prinzipien sind:

### Single Responsibility Principle (SRP)

Single Responsibility Principle (SRP): Eine Klasse sollte nur eine Verantwortlichkeit haben. Das bedeutet, dass sie nur eine Aufgabe erfüllen und nur für eine Art von Änderungen anfällig sein sollte.

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
        // Code zum Senden einer E-Mail
    }
}
/*
In diesem Beispiel ist die `Customer`-Klasse sowohl für das Speichern von Kundeninformationen und das Bereitstellen von Zugriffsmethoden als auch für das Senden von E-Mails verantwortlich. Die Klasse hat damit mehrere Verantwortlichkeiten und ist somit schwerer wartbar und erweiterbar.
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
        // Code zum Senden einer E-Mail
    }
}
/*
In diesem Beispiel ist die `Customer`-Klasse nur für das Speichern von Kundeninformationen und das Bereitstellen von Zugriffsmethoden verantwortlich. Die `EmailSender`-Klasse ist nur für das Senden von E-Mails zuständig. Beide Klassen erfüllen jeweils nur eine Verantwortlichkeit.
*/
```

### Open-Closed Principle (OCP)

Software-Entitäten (Klassen, Module, Funktionen usw.) sollten offen für Erweiterungen, aber geschlossen für Änderungen sein. Das bedeutet, dass die Funktionalität einer Software-Einheit durch Hinzufügen neuer Code-Module oder Klassen erweitert werden sollte, ohne den bestehenden Code ändern zu müssen.

```php

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
            // Weitere Bedingungen für andere Formen
        }

        return $area;
    }
}
/*
In diesem Beispiel ist die `AreaCalculator`-Klasse offen für Modifikationen, da sie geändert werden muss, wenn eine neue Form hinzugefügt wird. Die Klassen `Circle` und `Rectangle` sind auch offen für Modifikationen, da sie neue Methoden benötigen, wenn neue Formen hinzugefügt werden.
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
In diesem Beispiel sind die Klassen `Circle` und `Rectangle` geschlossen für Änderungen, da sie ihre Funktionalität nicht ändern, wenn neue Formen hinzugefügt werden. Die `AreaCalculator`-Klasse ist offen für Erweiterungen, da sie einfach erweitert werden kann, um die Berechnung der Fläche neuer Formen zu unterstützen.
*/
 ```

### Liskov Substitution Principle (LSP)

Liskov Substitution Principle (LSP): Objekte einer abgeleiteten Klasse sollten durch Objekte ihrer Basisklasse ersetzbar sein, ohne das Programm zu beeinträchtigen. Das bedeutet, dass eine abgeleitete Klasse alle Verhaltensweisen ihrer Basisklasse übernehmen sollte, ohne dass das Verhalten des Programms sich ändert.

```php
<?php

// bad
class Vehicle {
    protected $fuel;

    public function refuel($fuel) {
        // Code zum Betanken des Fahrzeugs
    }

    public function accelerate() {
        // Code zum Beschleunigen des Fahrzeugs
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
        // Code zum Beschleunigen des Autos
    }
}

/*
In diesem Beispiel verletzt die `Car`-Klasse das Liskov Substitution Principle, da sie die Vertragsbedingungen der `Vehicle`-Klasse verletzt. Die `refuel()`-Methode der `Car`-Klasse führt eine zusätzliche Überprüfung durch, um sicherzustellen, dass nicht zu viel Kraftstoff hinzugefügt wird. Wenn ein Code-Abschnitt den Aufruf der `refuel()`-Methode auf einer `Vehicle`-Instanz aufruft und stattdessen eine `Car`-Instanz erhält, führt die zusätzliche Überprüfung möglicherweise zu unerwarteten Fehlern oder Ausnahmen.
*/


// good
class Vehicle {
    public function startEngine() {
        // Code zum Starten des Motors
    }
}

class Car extends Vehicle {
    public function startEngine() {
        parent::startEngine();
        // Code speziell für Autos zum Starten des Motors
    }
}

class ElectricCar extends Car {
    public function startEngine() {
        // Code zum Starten des Elektromotors
    }
}

/*
In diesem Beispiel kann die `ElectricCar`-Klasse ohne Probleme anstelle der `Car`-Klasse verwendet werden, da sie alle Methoden und Verhaltensweisen der `Car`-Klasse erbt und sie auch überschreiben kann, wenn dies erforderlich ist.
*/
```

### Interface Segregation Principle (ISP)

Interface Segregation Principle (ISP): Die Schnittstellen sollten auf die spezifischen Bedürfnisse der Clients zugeschnitten sein. Das bedeutet, dass eine Klasse nicht gezwungen werden sollte, Methoden oder Eigenschaften zu implementieren, die sie nicht benötigt.

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
        // Code zur Bewegung eines Vogels
    }

    public function fly() {
        // Code zum Fliegen eines Vogels
    }

    public function swim() {
        throw new Exception('Birds cannot swim');
    }
}

class Fish implements Animal {
    public function move() {
        // Code zur Bewegung eines Fisches
    }

    public function fly() {
        throw new Exception('Fish cannot fly');
    }

    public function swim() {
        // Code zum Schwimmen eines Fisches
    }
}
/*
In diesem Beispiel verletzt die `Animal`-Schnittstelle das Interface Segregation Principle, da sie Methoden für Fliegen, Schwimmen und Bewegung kombiniert, obwohl nicht alle Tiere diese Fähigkeiten besitzen. Die `Bird`-Klasse muss die `swim()`-Methode implementieren, obwohl Vögel nicht schwimmen können, und die `Fish`-Klasse muss die `fly()`-Methode implementieren, obwohl Fische nicht fliegen können. Dies führt zu unerwarteten Fehlern oder Ausnahmen, wenn der Code auf eine Instanz von `Bird` oder `Fish` zugreift und eine unerwartete Methode aufruft.
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
        // Code zur Bewegung eines Vogels
    }

    public function fly() {
        // Code zum Fliegen eines Vogels
    }
}

class Fish implements SwimmableAnimal {
    public function move() {
        // Code zur Bewegung eines Fisches
    }

    public function swim() {
        // Code zum Schwimmen eines Fisches
    }
}

/*
In diesem Beispiel haben wir das Interface Segregation Principle angewendet, indem wir separate Schnittstellen für Fliegen und Schwimmen definiert haben, die jeweils von der allgemeinen `Animal`-Schnittstelle erben. Dadurch können wir sicherstellen, dass Klassen, die nicht fliegen können, nicht gezwungen werden, eine `fly()`-Methode zu implementieren, und Klassen, die nicht schwimmen können, nicht gezwungen werden, eine `swim()`-Methode zu implementieren. In diesem Fall implementieren die `Bird`- und `Fish`-Klassen nur die Methoden, die für ihre jeweilige Art der Fortbewegung relevant sind.
*/
```

### Dependency Inversion Principle (DIP)

Dependency Inversion Principle (DIP): Abhängigkeiten sollten auf abstrakten Schnittstellen basieren, nicht auf konkreten Implementierungen. Das bedeutet, dass höhere Module nicht von niedrigeren Modulen abhängig sein sollten und dass abstrakte Module nicht von konkreten Modulen abhängig sein sollten.

```php
<?php

// bad
class MySqlDatabase {
    public function connect() {
        // Code zur Verbindung mit einer MySQL-Datenbank
    }
}

class UserRepository {
    private $database;

    public function __construct() {
        $this->database = new MySqlDatabase();
    }

    public function getUsers() {
        $this->database->connect();
        // Code zum Abrufen von Benutzern aus der Datenbank
    }
}
/*
In diesem Beispiel wird das Dependency Inversion Principle verletzt, da die `UserRepository`-Klasse direkt an die konkrete Implementierung `MySqlDatabase` gebunden ist. Wenn wir eine andere Datenbank wie PostgreSQL verwenden möchten, müssen wir den Code in der `UserRepository`-Klasse ändern. Das führt dazu, dass der Code starr und schwer erweiterbar wird. Um das DIP zu wahren, sollte die `UserRepository`-Klasse die Abstraktion `DatabaseInterface` verwenden, statt direkt an die konkrete Implementierung gebunden zu sein.
*/

// good
interface DatabaseInterface {
    public function connect();
}

class MySqlDatabase implements DatabaseInterface {
    public function connect() {
        // Code zur Verbindung mit einer MySQL-Datenbank
    }
}

class PostgreSqlDatabase implements DatabaseInterface {
    public function connect() {
        // Code zur Verbindung mit einer PostgreSQL-Datenbank
    }
}

class UserRepository {
    private $database;

    public function __construct(DatabaseInterface $database) {
        $this->database = $database;
    }

    public function getUsers() {
        $this->database->connect();
        // Code zum Abrufen von Benutzern aus der Datenbank
    }
}
/*
In diesem Beispiel haben wir das Dependency Inversion Principle angewendet, indem wir eine Abstraktion `DatabaseInterface` geschaffen haben, die von konkreten Implementierungen `MySqlDatabase` und `PostgreSqlDatabase` implementiert wird. Anstatt die konkreten Implementierungen direkt in der `UserRepository`-Klasse zu instanziieren, injizieren wir die Abstraktion durch den Konstruktor. Dadurch wird die `UserRepository`-Klasse nicht mehr direkt an konkrete Implementierungen gebunden, sondern nur an die Abstraktion `DatabaseInterface`. Dies erleichtert das Austauschen der verwendeten Datenbank und fördert die Flexibilität und Wiederverwendbarkeit des Codes.
*/
```
