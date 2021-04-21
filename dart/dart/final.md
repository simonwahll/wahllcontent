---
title: "Final"
description: "Final"
lead: ""
date: 2021-04-16T16:55:59+02:00
lastmod: 2021-04-16T16:55:59+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 4
toc: true
---

Finals are similar to [constants]({{< ref "/dart/dart/constants" >}} "Dart Constants") in the way that it is not possible to change their values after they have been assigned a value and they must be assigned a value at the same time as they are declared. The difference is that final can be the result of an expression that cannot be known at compile time so it can be used to hold an instance of an object.

## Syntax

The syntax for declaring a final is quite simple:

```dart
final name = value;
```

Where `name` can be any identifier, following the same naming rules as [variables]({{< ref "/dart/dart/variables" >}} "Dart Variables") and `value` can be any value of any `data type`.

## Simple Examples

Declaring a final named `text` of the type [string]({{< ref "/dart/dart/data_types#string" >}} "Dart Strings") with the value `"Hello World!"`.

```dart
final text = "Hello World!";
```

The value of a final can never be changed. If you need to do this you should use a [variable]({{< ref "/dart/dart/variables" >}} "Dart Variables") instead.

```dart
final text = "Hello World!";

// This will not work!
// It will throw a compile-time error.
//text = "Hello Universe!";
```

## Final With Objects

When assigning an instance of an object to a final the object will work exactly as expected. The only difference from doing this from assigning it to a [variable]({{< ref "/dart/dart/variables" >}} "Dart Variables") is that the instance of the object of a final can never be changed while this can be done with variables.
