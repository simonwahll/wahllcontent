---
title: "Isolate"
description: "Isolate"
lead: ""
date: 2021-05-07T19:38:37+02:00
lastmod: 2021-05-07T19:38:37+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 18
toc: true
---

Isolates are similar to threads in the way that they can execute code concurrently. However, they differ in two important ways:

- Isolates have their own memory.
- Isolates can communicate with messages.

Every Dart program has at least one isolate, the main isolate.

The main use case for isolates is to execute some expensive code in the background that will not block the main isolate. When doing this you can for example fetch some data or process some data in an isolate so the UI in the main isolate doesn't get blocked.

## Creating a Simple Isolate

```dart
import 'dart:isolate';

void myIsolateFunction(String message) {
  print(message);
}

void main() {
  Isolate.spawn<String>(myIsolateFunction, "I'm running in an isolate"); 
}
```

Here we create a function `myIsolateFunction` which takes one parameter, a message to print. We can run this function in an isolate with the `Isolate.spawn<String>(myIsolateFunction, "I'm running in an isolate");`. `<String>` simply means that the argument of the function is a [String]({{< ref "/dart/dart/data_types#string" >}} "Dart Strings"). The first argument in the `spawn()` method is the function to run and the second argument is the argument to send to that function. The function to run in the isolate must take exactly one argument.

## Advanced Isolate

More advanced isolates can also be created. We can for example pass messages between them.

```dart
import 'dart:async';
import 'dart:io';
import 'dart:isolate';

class IsolatePackage {
  final SendPort sendPort;
  final ReceivePort receivePort;
  final Isolate isolate;

  IsolatePackage(this.sendPort, this.receivePort, this.isolate);
}

void printMessages(SendPort sendPort) {
  var receivePort = ReceivePort();
  sendPort.send(receivePort.sendPort);

  receivePort.listen((message) {
    print('Isolate received message: $message');
  });
}

Future<IsolatePackage> startIsolate(Function(SendPort) initFunction) async {
  var completer = Completer<SendPort>();
  var receivePort = ReceivePort();

  receivePort.listen((message) {
    if (message is SendPort) {
      completer.complete(message);
    }
  });

  var isolate = await Isolate.spawn<SendPort>(initFunction, receivePort.sendPort);

  return IsolatePackage(await completer.future, receivePort, isolate);
}

void main() async {
  var t = await startIsolate(printMessages);
  String? input;

  print('Type exit to exit');

  while (input != 'exit') {
    input = stdin.readLineSync();
    t.sendPort.send(input);
  }

  t.isolate.kill(priority: Isolate.immediate);

  exit(0);
}
```

Let's step through this code and explain it.

Let's start with the `printMessages()` function.

```dart
void printMessages(SendPort sendPort) {
  var receivePort = ReceviePort();
  sendPort.send(receivePort.sendPort);

  receivePort.listen((message) {
    print('Isolate received message: $message');
  });
}
```

We create a function that will run in the isolate. The `sendPort` parameter is what we will use to send messages to the main isolate. `receivePort` is used to receive messages from other isolates. We then send a message to the main isolate with the `receivePort.sendPort` message. This will give the main isolate the ability to send messages to this isolate with that object. The last thing here is that we listen to the receivePort. When a message is sent to this receivePort we get the message in the `message` variable. In this case, we just print it to the terminal.

The next thing we do is creating the `IsolatePackage` class. This class is used to collect a `SendPort`, used to send messages to the isolate, `ReceivePort` used to listen to messages sent by the isolate, and the `Isolate` itself.

```dart
class IsolatePackage {
  final SendPort sendPort;
  final ReceivePort receivePort;
  final Isolate isolate;

  IsolatePackage(this.sendPort, this.receivePort, this.isolate);
}
```

Next, we create a function that starts an isolate and builds an `IsolatePackage` that can be used to communicate with the isolate.

```dart
Future<IsolatePackage> startIsolate(Function(SendPort) initFunction) async {
  var completer = Completer<SendPort>();
  var receivePort = ReceivePort();

  receivePort.listen((message) {
    if (message is SendPort) {
      completer.complete(message);
    }
  });

  var isolate = await Isolate.spawn<SendPort>(initFunction, receivePort.sendPort);

  return IsolatePackage(await completer.future, receivePort, isolate);
}
```

This function takes a function as an argument. This is the function the isolate will run. Next, we create a completer which you can read about [here]({{< ref "/dart/dart/completer" >}} "Dart Completer"). A `ReceivePort` is created that can be used to send messages to this isolate, i.e. the main isolate. Next, we listen to messages on the `receivePort`, and if the message is a `SendPort` we complete the completer with this `SendPort`. Remember, the isolate will send it's `sendPort` to the isolate that starts it. `var isolate = await Isolate.spawn<SendPort>(initFunction, receivePort.sendPort);` creates an isolate and passes this isolate's `sendPort` as the argument to it. The return statement creates the `IsolatePackage` object and returns it to the caller.

The main function looks like this:

```dart
void main() async {
  var t = await startIsolate(printMessages);
  String? input;

  print('Type exit to exit');

  while (input != 'exit') {
    input = stdin.readLineSync();
    t.sendPort.send(input);
  }

  t.isolate.kill(priority: Isolate.immediate);

  exit(0);
}
```

The first line creates the isolate with the function we just created. It then waits for the user to type something on the keyboard and sends the input to the isolate with the `sendPort.send()` method. Remember, the `sendPort` property on the `t` object is used to send messages to the isolate. The isolate can be stopped by calling the `kill()` method on the isolate. We set the priority to `Isolate.immediate` to kill the isolate immediately. Exit the program with the `exit()` method.
