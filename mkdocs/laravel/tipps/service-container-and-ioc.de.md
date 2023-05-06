---
category: laravel
sub_category_1: tipps
sub_category_2: ioc
language: de
tags:
- laravel
- best-practice
- tipps
- ioc
- service-container
---

# Service Container und IoC-Container

## Was ist ein Service Container?

```php
<?php
// good
app(MyAction::class->execute($myModel);

// bad
(new MyAction())->execute($myModel);
```

Der Service Container ist ein leistungsfähiges Tool, mit dem Sie Ihre Abhängigkeiten zwischen Ihren Klassen definieren und organisieren können. Durch die Verwendung des Service Containers können Sie Ihre Abhängigkeiten zentral verwalten und vermeiden, dass Sie harte Abhängigkeiten in Ihren Klassen haben. Sie können auch leicht Mock-Objekte für Tests erstellen, indem Sie Abhängigkeiten durch Testdoubles ersetzen.

Das Konzept des Service Containers wird häufig in Laravel-Anwendungen verwendet, um Klasseninstanzen zu erstellen und zu verwalten. Anstatt Klassen manuell zu instanziieren, können Sie eine Klasse als "Service" im Container registrieren und dann auf diese Klasse durch den Container zugreifen.

Wenn Sie `new MyAction()` verwenden, instanziieren Sie die Klasse manuell. Dies kann problematisch sein, wenn die Klasse selbst Abhängigkeiten hat, die ebenfalls manuell instanziiert werden müssen. Wenn Sie stattdessen die Klasse im Service Container registrieren und den Container verwenden, um auf die Klasse zuzugreifen, kann der Container die Abhängigkeiten für Sie automatisch auflösen.

Der folgende Code zeigt, wie Sie eine Klasse im Service Container registrieren und dann auf diese Klasse zugreifen können:

```php
<?php
// Registrieren Sie die Klasse im Container
app()->bind(MyAction::class);

// Zugriff auf die Klasse durch den Container
app()->make(MyAction::class)->execute($myModel);

// or
app(MyAction::class)->execute($myModel);
```

Indem Sie den Service Container verwenden, können Sie die Abhängigkeiten Ihrer Klassen zentral verwalten und die Code-Wartbarkeit verbessern.

## Vorteile der Verwendung des Service Containers

Einer der Vorteile der Verwendung des Service Containers ist, dass Sie Ihre Abhängigkeiten zentral verwalten und austauschen können. Wenn Sie eine Klasse manuell instanziieren, können Sie diese Klasse nur schwer austauschen, wenn Sie sie in Ihren Tests durch eine Mock-Klasse ersetzen möchten.

Wenn Sie jedoch eine Klasse im Service Container registrieren und den Container verwenden, um auf diese Klasse zuzugreifen, können Sie die registrierte Klasse durch eine andere Klasse ersetzen, die die gleiche Schnittstelle implementiert. Dies ist insbesondere nützlich, wenn Sie Tests durchführen möchten, bei denen Sie bestimmte Funktionen einer Klasse isoliert testen möchten, ohne von anderen Klassen abhängig zu sein.

Ein weiterer Vorteil ist, dass die Verwendung des Service Containers den Code lesbarer macht, da es einfacher ist, die Abhängigkeiten von Klassen zu sehen, wenn sie im Container registriert sind. Darüber hinaus kann der Service Container dazu beitragen, den Code modularer zu gestalten, da er es einfacher macht, Ihre Anwendung in kleinere, wiederverwendbare Komponenten zu unterteilen.

Insgesamt bietet die Verwendung des Service Containers viele Vorteile für die Entwicklung von Laravel-Anwendungen, einschließlich der zentralen Verwaltung von Abhängigkeiten, der Verbesserung der Testbarkeit und der Lesbarkeit des Codes.

## Was ist der Unterschied zwischen dem Service Container und dem IoC-Container?

Der Service Container in Laravel ist eine Implementierung des Inversion of Control (IoC) Containers. Die Idee hinter dem IoC-Container ist es, die Kontrolle über die Erstellung und Verwaltung von Objekten von der Anwendungsklasse selbst an eine externe Komponente, den IoC-Container, zu delegieren.

Der IoC-Container ist ein Design-Pattern, das eng mit dem Dependency Injection (DI) Design-Pattern verbunden ist. Beide Muster haben das Ziel, die Abhängigkeiten von Klassen zu zentralisieren und die Erstellung von Objekten und die Verwaltung von Abhängigkeiten zu vereinfachen.

In Laravel ist der Service Container der primäre Mechanismus zur Verwaltung von Abhängigkeiten. Er erlaubt es, Klassen im Container zu registrieren und die Instanziierung und Verwaltung von Objekten automatisch zu handhaben. Der Service Container bietet auch Unterstützung für Dependency Injection, da Abhängigkeiten automatisch aufgelöst werden können, wenn eine Klasse instanziiert wird.

Insgesamt sind der Service Container und der IoC-Container eng miteinander verbunden und werden oft synonym verwendet. Beide sind wichtige Konzepte in der objektorientierten Programmierung und sind unverzichtbar für die Erstellung skalierbarer und wartbarer Anwendungen.
