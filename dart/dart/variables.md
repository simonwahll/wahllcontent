---
title: "Variables"
description: "Variables"
lead: ""
date: 2021-04-14T16:36:05+02:00
lastmod: 2021-04-14T16:36:05+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 9
toc: true
---

A variable is kind of like a box that stores some value that can be accessed later. Every variable has a name that is used to identify it. Dart is a statically typed language, this means that the type of a variable cannot be changed. If you decide that a variable should be of type `int` you can never assign it a value of the type String. 

There are a few rules you must follow when deciding on a name for a variable. These are:

- The name cannot begin with a number.
- The name cannot be a reserved keyword, such as `class` or `String`.
- The name must contain only letters and numbers.
- The name can contain underscores (`_`) or dollar signs (`$`) but cannot contain any other special characters.

## Syntax

A variable declaration has the following syntax:

```dart
type name;
```

A variable assignment has the following syntax:

```dart
name = value;
```

Variable declaration and assignment have the following syntax:

```dart
type name = value;
```

Where `type` can be any data type, `name` can be any name following the rules laid out above and `value` can be any value that is of the correct data type.

## Simple Examples

Declaring a `String` with the name `text`:

```dart
String text;
```

Declaring an `int` with the name `age` and assigning it the value `50`:

```dart
int age = 50;
```

Declaring a `double` with the name `pi` and assigning it the value `3.14` in a separate statement:

```dart
// Declaring the variable.
double pi;

// Assigning the variable a value.
pi = 3.14;
```

## Using the Value of a Variable

The value of a variable can be retrieved by just typing the name of the variable.

For example, if we would like to declare a `String` called `text` with the value `"Hello"` and then print it to the terminal we can do so with the following code:

```dart
String text = "Hello";

print(text);
```

Output:

```sh
$ dart run main.dart
> Hello
```

## The `var` Keyword

The `var` keyword is recommended to use when a variable is declared in a function's `local scope` and the type of the variable is apparent. The variable is still statically typed and the type of the first value assigned to it will be the type of the variable for the rest of the program.

Let's demonstrate this:

```dart
void main() {
  // This is a function with a local scope,
  // therefore we should use the var keyword
  // instead of explicitly typing the data type.
  // The type of text will still be String.
  var text = "Hello";

  // text can still be changed to another value
  // as long as the new value is still a String.
  text = "Banana";

  // This will not work!
  // Trying to assign it a value of some other 
  // data type will not work. It will throw a
  // compile time error.
  //text = 5;
}
```
