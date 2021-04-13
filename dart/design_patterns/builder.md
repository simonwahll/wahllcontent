---
title: "Builder"
description: "Builder"
lead: ""
date: 2021-04-10T14:14:20+02:00
lastmod: 2021-04-10T14:14:20+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Design Patterns"
weight: 5
toc: true
---

The `builder` design pattern is a creational design pattern. It is used to create complex object without requiring the client to know the construction code.

One common use case for the builder design pattern is to replace a large constructor with lots of logic the clients need to know about. When doing this you can avoid the following types of constructors:

```dart
House(1, 100, false, true, 40, false);
```

The builder design pattern consists of the following components:

1. Products, the products the builders can create.
2. A builder interface.
3. Concrete builders that implements the builder interface.
4. A director that can use a builder to create objects.

## Products

We will create two products, a house and a shed. The builders we will create in a later step can produce these products.

```dart
class House {
  String floor;
  String walls;
  String doors;
  String windows;
  String roof;

  @override
  String toString() => '$floor\n$walls\n$doors\n$windows\n$roof';
}
```

```dart
class Shed {
  String floor;
  String walls;
  String doors;
  String windows;
  String roof;

  @override
  String toString() => '$floor\n$walls\n$doors\n$windows\n$roof';
}
```

## Builder Interface

```dart
abstract class Builder {
  void reset();
  void buildFloor(int size);
  void buildWalls(int height);
  void buildDoors(int numberOfDoors);
  void buildWindows(int numberOfWindows);
  void buildRoof(int height);
}
```

## Concrete Builders

We have two builders, one that can build houses and one that can build sheds.

```dart
class HouseBuilder implments Builder {
  House _house = House();

  @override
  void reset() => _house = House();

  @override
  void buildFloor(int size) => _house.floor = 'House floor, size: $size';

  @override
  void buildWalls(int height9 => _house.walls = 'House walls, height: $height';

  @override
  void buildDoors(int numberOfDoors) => _house.doors = 'House walls, numberOfDoors: $numberOfDoors';

  @override
  void buildWindows(int numberOfWindows) => _house.windows = 'House windows, numberOfWindows: $numberOfWindows';

  @override
  void buildRoof(int height) => _house.roof = 'House roof, height: $height';

  House getResult() => _house;
}
```

```dart
class ShedBuilder implements Builder {
  Shed _shed = Shed();

  @override
  void reset() => _shed = Shed();

  @override
  void buildFloor(int size) => _shed.floor = 'Shed floor, size: $size';

  @override
  void buildWalls(int height) => _shed.walls = 'Shed walls, height: $height';

  @override
  void buildDoors(int numberOfDoors) => _shed.doors = 'Shed doors, numberOfDoors: $numberOfDoors';

  @override
  void buildWindows(int numberOfWindows) => _shed.windows = 'Shed windows, numberOfWindows: $numberOfWindows';

  @override
  void buildRoof(int height) => _shed.roof = 'Shed roof, height: $height';

  Shed getResult() => _shed;
}
```

## Director

The director knows how to build common products. The clients can use this to make the building process easier but if the client needs something more specific the director doesn't know how to do, it can construct the products itself.

```dart
class Director {
  Builder _builder;

  Director(this._builder);

  void changeBuilder(Builder builder) => _builder = builder;

  void buildLargeBuilding() {
    _builder.reset();
    _builder.buildFloor(100);
    _builder.buildWalls(4);
    _builder.buildDoors(4);
    _builder.buildWindows(20);
    _builder.buildRoof(5);
  }

  void buildSmallBuilding() {
    _builder.reset();
    _builder.buildFloor(20);
    _builder.buildWalls(2);
    _builder.buildDoors(1);
    _builder.buildWindows(0);
    _builder.buildRoof(1);
  }
}
```

## Testing Our Builder

We can test our bilder with a simple main function.

```dart
void main() {
  var houseBuilder = HouseBuilder();
  var shedBuilder = ShedBuilder();
  var director = Director(houseBuilder);

  director.buildLargeBuilding();
  var largeHouse = houseBuildet.getResult();
  print(largeHouse);

  director.changeBuilder(shedBuilder);
  director.buildSmallBuilding();
  var smallShed = shedBuilder.getResult();
  print(smallShed);
}
```

When you run this program you will get the following output:

```sh
$ dart run main.dart
> House floor, size: 100
> House walls, height: 4
> House doors, numberOfDoors: 4
> House windows, numberOfWindows: 20
> House roof, height: 5

> Shed floor, size: 20
> Shed walls, height: 2
> Shed doors, numberOfDoors: 1
> Shed windows, numberOfWindows: 0
> Shed roof, height: 1
```

Note that if you need more control over the builder than the director provides you can build you own object directly with a builder.

Congratulation, you just used the builder design pattern.
