---
title: "Completer"
description: "Completer"
lead: ""
date: 2021-05-10T20:33:33+02:00
lastmod: 2021-05-10T20:33:33+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 17
toc: true
---

Dart is an asyncronous language, that means it can queue things to do when noting else is being done. Normally when doing this you would declare an async function to return a future, which will complete when the task has been completed. However there are cases where you cannot use a future but might still want to, this is where completers come in place. It is a way of emulating futures.

## Basics

In order to use completers you first need to import the `dart:async` library.

```dart
import 'dart:async';
```

A completer can be created with the following:

```dart
var completer = Completer<type>();
```

Where `type` is any [data type]({{< ref "/dart/dart/data_types" >}} "Dart Data Types"). This is the type our completer will complete.

A completer can be completed with the `complete()` method.

```dart
completer.complete(value);
```

Where `value` is a value of the same type as declared in the previous step.

An error can also be completed:

```dart
completer.completeError(error);
```

Where `error` is the error.

The future this completer emulates can be accessed with the `future` property:

```dart
completer.future;
```

## Example

Let's demonstrate this with a very simple example:

```dart
import 'dart:io';

Future<bool> waitFiveSeconds() async {
  final completer = Completer<bool>();

  Timer(Duration(seconds: 5), () => completer.complete(true));

  return completer.future;
}

void main() async {
  print(await waitFiveSeconds());
}
```

Here we create a function `waitFiveSeconds()` that declares a completer, sets a timer that completes the completer after five seconds and returns the future of the completer. We then await the result and [prints]({{< ref "/dart/dart/print" >}} "Dart Print") it to the terminal. When running this, our program will wait for five seconds and then print `true` to the terminal.