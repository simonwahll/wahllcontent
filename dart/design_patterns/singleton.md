---
title: "Singleton"
description: "Singletons in Dart"
lead: ""
date: 2021-03-22T21:38:23+01:00
lastmod: 2021-03-22T21:38:23+01:00
draft: false
images: []
menu: 
  dart:
    parent: "Design Patterns"
weight: 9
toc: true
---

A singleton is a design pattern for creating an object that can only have one instance.

In Dart this can be done with the following code:

```dart
class Singleton {
  static Singleton _instance;

  Singleton._internal() {
    _instance = this;
  }

  factory Singleton() => _instance ?? Singleton._internal();
}
```
