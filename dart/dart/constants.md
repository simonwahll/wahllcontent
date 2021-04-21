---
title: "Constants"
description: "Constants"
lead: ""
date: 2021-04-15T19:36:42+02:00
lastmod: 2021-04-15T19:36:42+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 2
toc: true
---

Constants are quite similar to a variable. The only difference is that a variables value can be changed during run time, constants cannot, therefore they are constants. Dart uses the `const` keyword to declare a constant. All constants must be initialized with a value at the same time as they are declared, otherwise the Dart compiler will throw an error. You can think of constants as an alias for a value that you, the programmer, define while writing the program and when the Dart compiler does its things it replaces all constants you use with the value you assigned to it.

## Syntax

The syntax for declaring a constant is quite simple:

```dart
const name = value;
```

Where `name` can be any identifier, following the same naming rules as [variables]({{< ref "/dart/dart/variables" >}} "Dart Variables") and `value` can be any value of any [data type]({{< ref "/dart/dart/data_types" >}} "Dart Data Types").

## Simple Examples

Declaring a constant named `text` with the [string]({{< ref "dart/dart/data_types#string" >}} "Dart Strings") value `"Hello World!"`.

```dart
const text = "Hello World!";
```

Declaring a constant named `pi` with the [double]({{< ref "dart/dart/data_types#double" >}} "Dart Double") value 3.1415 and printing the value to the terminal.

```dart
const pi = 3.1415;
print(pi);
```

The value of a constant can never be changed. If you need to do this you should use a [variable]({{< ref "dart/dart/variables" >}} "Dart Variables") instead.

```dart
const text = "Hello World!";

// This will not work!
// It will throw a compile time error.
//text = "Hello Universe!";
```

## Demonstration of How Constants Work

Declaring a constant and printing it multiple times:

```dart
const text = "Hello World!";

print(text);
print(text);
print(text);
```

is exactly the same as doing this:

```dart
print("Hello World!");
print("Hello World!");
print("Hello World!");
```

But it is easier to declare a constant one time so if you need to change the value you only have to do that in one place.
