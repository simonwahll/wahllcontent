---
title: "While Loop"
description: "While Loop"
lead: ""
date: 2021-04-25T17:21:57+02:00
lastmod: 2021-04-25T17:21:57+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 12
toc: true
---

A loop is something that executes some piece of code some specified amount of times. One of these loops is the `while` loop.

## Syntax

```dart
while (<condition>) {
  <code>
}
```

Where `<condition>` is a logical condition that determines if the code in the body should run or not.

When Dart comes across a `while` loop it starts by checking the condition inside the parenthesis. If the condition is `true` it runs the code in the body and jumps back up to the condition inside the parenthesis. If the condition is still true it will run the body again, and continue doing this until the condition is `false`.

## Examples

Let's make a `while` loop that [prints]({{< ref "/dart/dart/print" >}} "Dart Print") all numbers from 0 - 10.

```dart
// Start by declaring a variable and initialize it to 0.
int i = 0;

// Run the loop and increment i by one every time.
// Stop running the loop when i is greater than 10.
while (i <= 10) {
  print(i);
  i++;
}
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

1. The first thing that Dart does is creating and [integer]({{< ref "/dart/dart/data_types#integer" >}} "Dart Integers") with the name `i` and assigning it the value `0`.

2. Dart then evaluates the condition `i <= 10` and the condition evaluates to `true` since `0` is less than 10.

3. The body of the `while` loop is executed and `i` is printed to the terminal and `i` is incremented by one.

4. Dart jumps back up to the condition `i <= 10` and this time `i` is `1` so the condition is still `true` and the body is executed again.

5. This process is repeated until the condition `i <= 10` evaluated to `false`, when `i` is `11`, and the loop is terminated.

Another example:

```dart
int i = 10;

while (i > 5) {
  print(i);
  i--;
}
```

Output:

```
$ dart run main.dart
> 10
> 9
> 8
> 7
> 6
```

This follows the same process as the previous example but instead of incrementing `i` we decrement it until `i` no longer is greater than `5`.