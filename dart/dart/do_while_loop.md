---
title: "Do While Loop"
description: "Do While Loop"
lead: ""
date: 2021-04-27T20:13:45+02:00
lastmod: 2021-04-27T20:13:45+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 15
toc: true
---

The `do while` loop is similar to a [while]({{< ref "/dart/dart/while_loop" >}} "Dart While Loop") loop except that the loop will run at least once.

## Syntax

```dart
do {
  <code>
} while (<condition>)
```

Where `<condition>` is a logical condition that determines if the code in the body should run or not.

When Dart comes across a `do while` loop it starts by running the code in the body and then evaluates the condition inside the parenthesis after the `while` word. If the condition evaluates to `true` the body will run again but if the condition evaluates to `false` the `do while` loop is terminated and Dart will continue executing the code after the loop.

## Examples

Let's make a `do while` loop that [prints]({{< ref "/dart/dart/print" >}} "Dart Print") all numbers from 0 - 10.

```dart
// Start by declaring a variable and initialize it to 0.
int i = 0;

// Run the loop and increment i by one every time.
// Stop running the loop when i is greater than 10.
do {
  print(i);
  i++;
} while (i <= 10)
```

Output: 

```
$ dart run main.dart
> 1
> 2
> 3
> 4
> 5
> 6
> 7
> 8
> 9
> 10
```

Let's step through the code to understand it.

1. The first thing that Dart does is declaring an [integer]({{< ref "/dart/dart/data_types#integer" >}} "Dart Integers") with the name `i` and assigning it the value `0`.

2. Dart then comes across the `do while` loop and the code inside the body is executed so the value of `i` is printed to the terminal and `i` is incremented.

3. The condition inside the parenthesis after the `while` word is evaluated (`i <= 10`). Remember, `i` is 1 and 1 is less than 10 so the condition evaluates to `true`.

4. The body runs again and after that, the condition is evaluated again. This keeps going until the condition evaluates to `false`.

## While vs Do While

You should use the `do while` loop when you have some code that should always run at least once. If you don't have this requirement, you should use the [while]({{< ref "/dart/dart/while_loop" >}} "Dart While Loop") loop instead.
