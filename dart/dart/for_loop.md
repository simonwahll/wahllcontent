---
title: "For Loop"
description: "For Loop"
lead: ""
date: 2021-04-24T11:56:53+02:00
lastmod: 2021-04-24T11:56:53+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 5
toc: true
---

A loop is something that executes some piece of code some specified amount of times. One of these loops is the `for` loop. It is probably the most used loop of them all.

## Syntax

```dart
for (<variable>; <condition>; <step>) {
  <code>
}
```

Where `<variable>` is most often an [integer]({{< ref "/dart/dart/data_types#integer" >}} "Dart Integers") with the name `i`, `<condition>` is a logical condition that determines of the code in the body should run or not and `<step>` is used to change the value of the variable.

The first thing that happens when Dart comes across a `for` loop is to declare and initialize the `<variable>`. After that, Dart checks if the `<condition>` is `true` or `false`. If it is `true` the body of the `for` loop is run. Then Dart executes the `<step>`, which most of the time modifies the `<variable>`. Then the `<condition>` is run again and the process is repeated, except for the `<variable>` step, until the `<condition>` is `false` and the execution of the loop completes.

## Examples

Let's make a `for` loop that [prints]({{< ref "/dart/dart/print" >}} "Dart Print") all numbers from 0 - 10.

```dart
for (int i = 0; i <= 10; i++) {
  print(i);
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

1. The first step that is executed is the `int i = 0;` step. Here Dart declares an [integer]({{< ref "/dart/dart/data_types#integer" >}} "Dart Integers") with the name `i` and initializes it with the value 0.

2. Dart evaluates the condition `i <= 10;` and the condition evaluates to `true` since `0` is less than 10.

3. The body of the `for` loop is executed since the condition in the previous step is `true` and the value of `i` is [printed]({{< ref "/dart/dart/print" >}} "Dart Print") to the terminal.

4. Dart jumps back up to the `i++` statement and evaluates it. So `i` is now `1`.

5. The condition is run again, this time `i` is `1` so the condition is still `true` and the body runs again.

6. Dart jumps back, again, to the `i++` statement, and `i` becomes `2`.

7. The same process is repeated until the condition evaluates to false and the loop is terminated.

Another example:

```dart
for (int i = 10; i > 5; i--) {
  print(i);
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
