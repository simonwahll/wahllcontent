---
title: "Print"
description: "Print"
lead: ""
date: 2021-04-01T18:45:39+02:00
lastmod: 2021-04-01T18:45:39+02:00
draft: false 
images: []
menu: 
  dart:
    parent: "Reference"
weight: 1
toc: true
---

In order to print something to the console in Dart we use the `print()` function. It works in the same way as it does in most languages. You can find some examples down below.

## Printing a String

```dart
print("Printing a String!");
```

Output:

```sh
> Printing a String!
```

## Printing a number

```dart
print(11);
```

Output:

```sh
> 11
```

## Printing an object

```dart
class MyClass {
  final myString = "This is a String!";
}

void main() {
  var myClass = MyClass();
  print(myClass);
}
```

Output:

```sh
> Instance of 'MyClass'
```

This is probably not something you would like to print. To make this prettier we can make a `toString()` method in `MyClass`. When `print()` prints an object it first checks if there is a `toString()` method in that object and if it is, it calls that method and prints the result to the console.

Example:

```dart
class MyClass {
  final myString = "This is a String!";
  String toString() => myString;
}

void main() {
  var myClass = MyClass();
  print(myClass);
}
```

Output: 

```sh
> This is a String!
```

## Printing multiple objects

The `print()` function takes exaclty one argument. If you want to print more than one object you will have to call the `print()` function more than once or concatenate the objects in some way. 

Concatenation example:

```dart
print(1.toString() + " " + 2.toString());
```

Output:

```sh
> 1 2
```
