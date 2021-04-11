---
title: "Factory"
description: "Factory"
lead: ""
date: 2021-04-05T14:55:04+02:00
lastmod: 2021-04-05T14:55:04+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Design Patterns"
weight: 5
toc: true
---

The factory design pattern can create an object without exposing the creation logic to the client. It also allows the client to use one interface for all objects that the factory can create. 

This design pattern can be useful when you need to be able to create different types of object but still need to have one interface that all objects understand.

## The interface

Start by creating an interface that each object implements. In Dart we also have a special kind of constructor, the factory constructor. A standard constructor would return a new instance of the same type as the object the constructor resides in but with a factory constructor we can return any instance, a new or an existing one, as long as its the same type as the class or a class that implements its methods.

Below you can find an abstract class that can be used as the interface:

```dart
abstract class Shape {
  factory Shape(String type) {
    switch (type) {
      case 'CIRCLE':
        return Circle();
      case 'RECTANGLE':
        return Rectangle();
      case 'TRIANGLE':
        return Triangle();
      default:
        return nul;
    }
  }

  void draw();
}
```

## Classes Implementing the Interface

The next step is to create classes that implements the `Shape` interface. In the constructor of the `Shape` class we return either a `Circle()`, a `Rectangle()` or a `Triangle()`. Let's create these classes and implement the `Shape` interface on them.

Circle:

```dart
class Circle implements Shape {
  @override
  void draw() {
    print('Circle');
  }
}
```

Rectangle:

```dart
class Rectangle implements Shape {
  @override
  void draw() {
    print('Rectangle');
  }
}
```

Triangle:

```dart
class Triangle implements Shape {
  @override
  void draw() {
    print('Triangle');
  }
}
```

## Testing the Factory

To test the factory we can create a simple `main()` function and run it.

```dart
void main() {
  var circle = Shape('CIRCLE');
  var rectangle = Shape('RECTANGLE');
  var triangle = Shape('TRIANGLE');

  circle.draw();
  rectangle.draw();
  triangle.draw();
}
```

When we run this function the output will be:

```sh
$ dart run main.dart
> Circle
> Rectangle
> Triangle
```

Congratulations, you just created a factory. In most other languages, that don't have the factory constructor, you would need to create a separate class that handles the creation of the objects and kept the `Shape` class purely as an interface. But Dart is wonderful so we don't need to do this.
