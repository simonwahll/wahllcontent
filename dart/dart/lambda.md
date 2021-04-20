---
title: "Lambda"
description: "Lambda"
lead: ""
date: 2021-04-20T18:16:20+02:00
lastmod: 2021-04-20T18:16:20+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 5
toc: true
---

Lambdas are a concise way of building functions. These are called `arrow functions` in JavaScript and `anonymous functions` in some other languages. 

## Syntax

There are two types of lambdas, the arrow version and the block version. 

The arrow version:

```dart
(args) => expression
```

Where `args` can be any number of arguments and `expression` is some type of expression that may or may not return a useful value.

The block version:

```dart
(args) {
  expressions;
}
```

Where `args` can be any number of arguments and `expression` is any number of expressions that may or may not end with a return statement.

The block version of lambdas are very similar to normal functions but are used for different purposes.

## Creating Our Own Lambdas

### Arrow Lambda

Lambdas are treated as first class objects in Dart. This means that we can assign them to variables and pass them as arguments to functions.

Let's define a lambda that takes two [int]({{< ref "/dart/dart/data_types#integer" >}} "Dart Integer") arguments and adds them together and returns it to the caller.

```dart
var add = (int a, int b) => a + b;
print(add(1, 1));
```

When running this program you will get the following output:

```
$ dart run main.dart
> 2
```

We created a lambda and assigned it to a variable. Then we called this lambda and printed its result to the terminal.

### Block Lambda

We can do the same as we did in the previous example with a block lambda too.

```dart
var add = (int a, int b) {
  var sum = a + b;
  print(sum);
  return sum;
};

a(1, 1);
```

When running this program you will get the follwing output:

```
$ dart run main.dart
> 2
```

With the block lambda we can have multple expressions in the body, just like with functions. In this case we print the sum of the two numbers in the lambda instead of after. We then return sum in case we would like to use it later.

## Lambdas as Function Arguments

Lambdas can be used as arguments to functions. This can be useful for example if you would like to have some type of callback that runs at the end of a function, for example in an asynchronous function. 

```dart
function f(Function callback) {
  print("Doing something");
  print("Not done yet");
  print("Done soon");
  print("Done");

  callback();
}

void main() {
  f(() => print("This is my callback");
}
```

Here we call out function `f` with the argument of a lambda. At the end of function `f` we then evaluate its expression.

When running this program you will get the following output:

```
$ dart run main.dart
> Doing something
> Not done yet
> Done soon
> Done
> This is my callback
```

## Lambdas Used in Dart

Dart uses lambdas a lot. For example the `forEach` function that can be run on a `List` takes a lambda.

`forEach` example:

```dart
var l = [1, 2, 3];
l.forEach((element) => print(element));
```

Output:

```
$ dart run main.dart
> 1
> 2
> 3
```

## Lambdas vs Functions

Lambdas and functions are almost the same. They even share the same `Function` type. They can be used for the some purposes. Keep in mind that functions are often easier to read and understand and you can use an arrow with a function as well if you only have one expression.
