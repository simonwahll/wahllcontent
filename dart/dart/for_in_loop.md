---
title: "For In Loop"
description: "For In Loop"
lead: ""
date: 2021-04-26T18:08:37+02:00
lastmod: 2021-04-26T18:08:37+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 6
toc: true
---

The `for in` loop can be used to iterate through an objects properties. For example, iteration over every element in a [list]({{< ref "/dart/dart/lists" >}} "Dart Lists").

## Syntax

```dart
for (var <name> in <object>) {
  <code>
}
```

Where `<name>` is a variable with a name following the same rules as normal [variables]({{< ref "/dart/dart/variables" >}} "Dart Variables"), `<object>` is some object to loop through and `<code>` is any code that is inside the body of the loop.

## Example

Let's loop through a [list]({{< ref "/dart/dart/lists" >}} "Dart Lists") and print each element to the terminal.

```dart
var myList = [1, 2, 3, 4, 5];

for (var element in myList) {
  print(element);
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
```

Let's step through the code to understand it.

1. We declare a variable with the name `myList` and initialize it with the list `[1, 2, 3, 4, 5]`.

2. Dart comes across the `for in` loop and iterates through each element in the list and giving the value of the current element to the variable `element`.

3. The value of the current element `element` is printed to the terminal.

4. The process is repeated until each element in the list has been iterated over.