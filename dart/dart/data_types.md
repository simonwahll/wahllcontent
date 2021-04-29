---
title: "Data Types"
description: "Data Types"
lead: ""
date: 2021-04-11T20:34:08+02:00
lastmod: 2021-04-11T20:34:08+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 3
toc: true
---

Dart is a statically typed language. This means the type of a [variable]({{< ref "/dart/dart/variables" >}} "Dart Variables") cannot be changed and variables of different types cannot be used together unless they are explicitly designed to do that. For example, it is not possible to declare a variable as type [String]({{< ref "/dart/dart/data_types#string" >}} "Dart Strings") and assign it a value of type [int]({{< ref "/dart/dart/data_types#integer" >}} "Dart Integers").

There are only six data types in Dart. This is a lot less than most other languages. These are the following:

- Integer
- Double
- String
- Boolean
- List
- Map

## Integer

An integer is a number without any decimal places. Examples of integers are 1, 843, and 25. Dart uses the keyword `int` for integers.

```dart
// Declare an integer with the name "number"
// and assign it the value 1.
int number = 1;

// Assign a new value to the variable "number".
number = 4;

// It is not possible to assign a value
// with a decimal part to the variable "number".
// number = 2.2; // This will not work!
```

## Double

A double is a number with decimal places. Examples of doubles are 4.2, 98.48221, and 31.0004.

```dart
// Declare a double with the name "number"
// and assign it the value 4.5.
double number = 4.5;

// Assign a new value to the variable "number".
number = 3.4;

// Assigning a number without any decimal part
// will work. It is still considered a double.
number = 2;
```

## String

A string is any piece of text. Strings are delimited by double quotes ("). Examples of strings are: "Hello", "monkey" and "I have a cat". Dart spells strings with a capital S (`String`).

```dart
// Declare a string with the name "text"
// and assign it the value "Hello".
String text = "Hello";

// Assign a new value to the variable "text".
text = "monkey";

// Strings can also include white spaces.
text = "Hello World!";
```

## Boolean

A Boolean is either true or false. Dart uses the keyword `bool` for Boolean.

```dart
// Declare a Boolean with the name "isOpen"
// and assign it the value true.
bool isOpen = true;

// Assign a new value to the variable "isOpen".
isOpen = false;
```

## List

A list is the same as an array in Dart. Lists can become quite complex and are covered in [this]({{< ref "/dart/dart/lists" >}} "Dart Lists") article. You can find a simple example down below.

```dart
// Declare a list of integers and
// assign it some values.
List<int> myList = [1, 2, 3];
```

## Map

A map is a collection of key-value pairs. These can be quite complex and we will cover them in a separate article sometime in the future. For now, you can find a simple example down below.

```dart
// Declare a map and assign
// it some values.
Map<String, int> = {
  "thisIsAKey": 4,
  "thisIsAlsoAKey": 8,
};
```
