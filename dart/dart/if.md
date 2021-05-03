---
title: "If"
description: "If"
lead: ""
date: 2021-05-03T16:16:50+02:00
lastmod: 2021-05-03T16:16:50+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 8
toc: true
---

The `if` statement can be used to run some code only if a certain condition is `true`.

## Syntax

```dart
if (<condition>) {
  <code>
}
```

Where `<condition>` is a [boolean]({{< ref "/dart/dart/data_types#boolean" >}} "Dart Boolean") condition that evaluates to `true` or `false` and `<code>` is any amount of code that will run if the `<condition>` evaluates to `true`.

## Example

Let's create a program that asks the user for his or her age. If the user is older than 20 the program should print `You are older than 20` to the terminal.

The first step is to create a `main()` function that asks the user for his or her age and stores the input in a [variable]({{< ref "/dart/dart/variables" >}} "Dart Variables"). This is outside the scope of this article so we will not explain exactly how this works. All you need to know is that the variable `age` is the age the user entered in the terminal.

```dart
import 'dart:io';

void main() {
  print('Enter your age: ');
  var age = int.parse(stdin.readLineSync()));
}
```

Now we only want to print `You are older than 20` to the terminal if `age` is more than 20. To check for this we can use the following `if` statement.

```dart
if (age > 20) {
  print('You are older than 20');
}
```

When Dart comes across an `if` statement it starts with evaluating the condition inside the parenthesis (`age > 20`). This will evaluate to either `true` if age is more than 20, or `false` if age is less than 20. If the condition evaluates to `true` the code inside the body will run, i.e. `print('You are older than 20');`, and if the condition evaluates to `false` the code inside the body will not run.

Putting it together:

```dart
import 'dart:io';

void main() {
  print('Enter your age: ');
  var age = int.parse(stdin.readLineSync()));

  if (age > 20) {
    print('You are older than 20');
  }
}
```

This is what we get as output when entering some different ages:

```
$ dart run main.dart
> Enter your age: 18
```

```
$ dart run main.dart
> Enter your age: 30
> You are older than 20
```

```
$ dart run main.dart
> Enter your age: 20
```

Note that you must press `Enter` after entering your age and you must enter an age that is an [integer]({{< ref "/dart/dart/data_types#integer" >}} "Dart Integers").

## Else

*Comming soon...*

## Else If

*Comming soon...*