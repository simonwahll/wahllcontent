---
title: "Terminal Input"
description: "Terminal Input"
lead: ""
date: 2021-05-08T11:08:16+02:00
lastmod: 2021-05-08T11:08:16+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 15
toc: true
---

When writing a command line application it can sometimes be useful to ask the user to input some data. But how can this data be read from the terminal and saved into a variable? The answer is with the `stdin` class. In order to use this class you must first import the library `dart:io`.

## Reading One Line

One line of data can be read with the `readLineSync()` method. This returns the data read as a `String?` if you have sound null safety enabled, otherwise it returns a [String]({{< ref "/dart/dart/data_types#string" >}} "Dart String").

```dart
import 'dart:io';

void main() {
  print('Enter something: ');
  String? input = stdin.readLineSync();
  print('You entered: ' + input!);
}
```

Output:

```
$ dart run main.dart
> Enter something: hello
> You entered: hello
```