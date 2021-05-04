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
  var age = int.parse(stdin.readLineSync());

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

What if we would like to run some code only if an `if` condition did not run? We could do this with multiple `if` statements if we wanted to. Look at the following example.

```dart
import 'dart:io';

void main() {
  print('Enter your age: ');
  var age = int.parse(stdin.readLineSync());

  if (age > 20) {
    print('You are older than 20');
  }

  if (age <= 20) {
    print('You are not older than 20');
  }
}
```

If we would run this program and enter the age of 18 we would get the result that we expect.

Output:

```
$ dart run main.dart
> Enter your age: 18
> You are not older than 20
```

However, having two `if` statements is not necessary since the second condition (`age <= 20`) is always `true` if the first condition (`age > 20`) is `false`. It is quite common in programming to do similar things to this, so common that there is a special statement for this, the `else` statement.

### Syntax

```dart
if (<condition>) {
  <if_code>
}
else {
  <else_code>
}
```

Where the `if` part is exactly the same as we learned above and `<else_code>` is any amount of code that will run only if the `<condition>` evaluates to `false`.

### Example

Let's rewrite the code we just wrote to use the `else` statement instead of two `if` statements.

```dart
import 'dart:io';

int main() {
  print('Enter your age: ');
  var age = int.parse(stdin.readLineSync());

  if (age > 20) {
    print('You are older than 20');
  }
  else {
    print('You are not older than 20');
  }
}
```

If we run this program we get exactly the same result as the previous version.

Output:

```
$ dart run main.dart
> Enter your age: 18
> You are not older than 20
```

## Else If

Any number of `if` statements can be chained together. This can be useful in some situations but in some other situations, you want to have multiple `if` statements but only run the first one that the condition evaluated to `true` on. This can be done with the `else if` statement.

### Syntax

```dart
if (<if_condition>) {
  <if_code>
}
else if (<else_if_condition>) {
  <else_if_code>
}
```

Where `if` part is exactly the same as we have learned before and the `<else_if_condition>` is a logical condition that can evaluate to ether `true` or `false`. The `<else_if_code>` is any amount of code that will run only if the first `if` condition's condition evaluates for `false` and the `<else_if_condition>` evaluates to `true`.

### Example

Let's continue building on the code we made in the [else]({{< ref "/dart/dart/if#else" >}} "Dart else") part of this article. We might want to print `You are older than 50` if the user entered an age older than 50 and `You are older than 30` if the user entered an age older than 30 but younger than 50.

```dart
import 'dart:io';

void main() {
  print('Enter your age: ');
  var age = int.parse(stdin.readLineSync());

  if (age > 50) {
    print('You are older than 50');
  }
  else if (age > 30) {
    print('You are older than 30');
  }
  else if (age > 20) {
    print('You are older than 20');
  }
  else {
    print('You are not older than 20');
  }
}
```

Here, Dart will start by evaluating the condition in the `if` statement. If the condition is `true` it will run the body of that `if` statement and skip the `if else` and `else` statements. If the `if` statement's condition evaluates to `false` Dart will evaluate the condition of the first `else if` statement and if the condition evaluates to `true` it will run the code in that body and then skip the next `else if` and `else` statements. This will continue until there are no more `else if` statements and if the last one also evaluates to `false` the `else` statement's body will run.

Output:

```
$ dart run main.dart
> Enter your age: 55
> You are older than 50
```

```
$ dart run main.dart
> Enter your age: 33
> You are older than 30
```

```
$ dart run main.dart
> Enter your age: 22
> You are older than 20
```

```
$ dart run main.dart
> Enter your age: 18
> You are not older than 20
```

Note that you can chain together any number of `else if` statements and you are not required to use the `else` statement.
