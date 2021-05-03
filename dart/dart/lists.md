---
title: "Lists"
description: "Lists"
lead: ""
date: 2021-04-21T17:00:22+02:00
lastmod: 2021-04-21T17:00:22+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 10
toc: true
---

Lists are a common type of collection. These are a way of ordering items and storing them together. A list consists of elements, these are the actual objects in the list, and these get their own index. The index starts counting at 0. 

Note that unlike some other programming languages Dart does not separate `arrays` and `lists`, they are simply the same thing here.

There are two types of lists, `fixed-length lists` and `growable lists`. When a fixed-length list is defined they also must be given a maximum amount of elements it can store, this is called the `length` of the list. Growable lists can be any size and do not require a max length, thus the length of them varies depending on how many elements are collected in it.

## Growable Lists

Growable lists are the most used type of list. 

### Syntax

Declaring a list:

```dart
type name = [elements];
```

Where `type` can be any [data type]({{< ref "/dart/dart/data_types" >}} "Dart Data Types"), `name` can be any name following the same naming rules as [variables]({{< ref "/dart/dart/variables" >}} "Dart Variables") and `elements` can be any objects that should be collected in the list, these are separated by commas.

Getting an element from a list:

```dart
name[index];
```

Where `name` is the name of the list and `index` is the index of the element that you want to get. Keep in mind that if you try to get an index that is larger than the lists is Dart will either throw a compile-time error or crash during run time.

Changing the value of an element in a list:

```dart
name[index] = new_value;
```

Where `name` is the name of the list, `index` is the index you want to change the value of and `new_value` is the new value that should be put in the list.

### Examples

Let's create a list that keeps track of some numbers.

```dart
var myList = [1, 2, 3, 4];
```

This list is called `myList` and contains four elements, `1, 2, 3, and 4`.

Print the second element to the terminal. Keep in mind that the index starts at 0 so the second element would have the index `1`.

```dart
print(myList[1]);
```

Output:

```
$ dart run main.dart
> 2
```

Change the value of the third element and print the new value to the terminal.

```dart
myList[2] = 6;
print(myList[2]);
```

Output:

```
$ dart run main.dart
> 6
```

Adding a number to the end of the list can be done with the `add()` method.

```dart
myList.add(10);
print(myList);
```

Output:

```
$ dart run main.dart
> [1, 2, 6, 4, 10]
```

The length of the list can be used with the `length` property.

```dart
print(myList.length);
```

Output:

```
$ dart run main.dart
> 5
```

## Fixed Length Lists

Fixed length lists are similar to growable lists except that their length cannot be changed. There are several ways to define fixed length lists. Here is one way.

### List.filled()

`List.filled(int length, int fill, {bool growable = false})` takes two arguments and and one named argument and returns a list. The first argument is the length of the list, the second argument is what each element's value should be and the named argument is a [Boolean]({{< ref "/dart/dart/data_types#Boolean" >}} "Dart Boolean") with the name `growable` which indicates if the list should be growable or not. 

```dart
var myList = List.filled(3, 0, growable: false);
print(myList);
```

Output:

```
$ dart run main.dart
> [0, 0, 0]
```

If you would try to use the `add()` function on a fixed-length list the Dart compiler will throw an error.
