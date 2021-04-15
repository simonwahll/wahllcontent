---
title: "Abstract Factory"
description: "Abstract Factory"
lead: ""
date: 2021-04-09T22:27:11+02:00
lastmod: 2021-04-09T22:27:11+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Design Patterns"
weight: 100
toc: true
---

The abstract factory design patterns allows you to create collections of related objects without knowing their types.

This design patterns consists of the following parts:
1. One interface for each type of object the factories can produce.
2. Concrete classes that implements the corresponing interface.
3. An abstract factory interface that all factories should implement.
4. Concrete factories that implements the corresponding interface.

## The Interfaces

Start by creating an interface for each type of object the concrete classes can implement. We will create two interfaces for two different types of objects.

```dart
abstract class Laptop {
  void printType();
}
```

```dart
abstract class Desktop {
  void printType();
}
```

## Concrete Classes

These are the objects the factories can produce. They should implement the corresponding interface from the first step. We will create 4 different types of objects that the factories can produce.

```dart
class AwesomeLaptop implements Laptop {
  @override
  void printType() {
    print('Awesome laptop');
  }
}
```

```dart
class AwesomeDesktop implements Desktop {
  @override
  void printType() {
    print('Awesome desktop');
  }
}
```

```dart
class BadLaptop implements Laptop {
  @override
  void printType() {
    print('Bad laptop');
  }
}
```

```dart
class BadDesktop implements Desktop {
  @override
  void printType() {
    print('Bad desktop');
  }
}
```

## Abstract Factory Interface

This is the interface the factories should implement.

```dart
abstract class ComputerFactory {
  Laptop createLaptop();
  Desktop createDesktop();
}
```

## Concrete Factories

These are the factories the client will interact with. They should implement the abstract factory interface. We will create two factories for now.

```dart
class AwesomeFactory implements ComputerFactory {
  @override
  Laptop createLaptop() => AwesomeLaptop();

  @override
  Desktop createDesktop() => AwesomeDesktop();
}
```

```dart
class BadFactory implements ComputerFactory {
  @override
  Laptop createLaptop() => BadLaptop();

  @override
  Desktop createDesktop() => BadDesktop();
}
```

## Testing Our Abstract Factory

This can be tested with a simple main function:

```dart
void main() {
  ComputerFactory computerFactory = AwesomeFactory();
  var laptop = computerFactory.createLaptop();
  car desktop = computerFactory.createDesktop();

  laptop.printType();
  desktop.printType();

  computerFactory = BadFactory();
  laptop = computerFactory.createLaptop();
  desktop = computerFactory.createDesktop();

  laptop.printType();
  desktop.printType();
}
```

When you run this program you will get the following output:

```sh
$ dart run main.dart
> Awesome laptop
> Awesome desktop
> Bad laptop
> Bad desktop
```

Congratulations, you just used the abstract design pattern.
