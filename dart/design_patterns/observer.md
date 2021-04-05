---
title: "Observer"
description: "Observer"
lead: ""
date: 2021-04-02T13:19:18+02:00
lastmod: 2021-04-02T13:19:18+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Design Patterns"
weight: 3
toc: true
---

The observer pattern is used in cases where you have an object that some other object would like to listen to changes on. It can be implemented in Dart with two abstract classes. These can be customized to suit your needs but they are generally a good starting point. 
There are two parts to the observer pattern, the subject and the observer. The subject is the object that the observer want to observe.

Note that the observer is sometimes refered to as a subscriber. Calling the observer a subscriber is more clear and might be a better choice. For the sake of this guide we will keep calling it the observer.

## Subject

The subject is the object the observers want to observe. This can for example be a shared state that multiple objects needs to observe.

Below you can find a simple implementation of an abstract subject class that can be extended by the class which should be a subject. You might want to customize this for your use case.

```dart
abstract class Subject {
  int someState = 0;
  
  final _observers = <Observer>[];

  void observe(Observer observer) => _observers.add(observer);
  void unobserve(Observer observer) => 
    _observers.removeWhere((o) => o.id == observer.id);

  void notifyObservers() {
    for (final observer in _observers) {
      observer.update(someState);
    }
  }

  void setSomeState(int newState) {
    someState = newState;
    notifyObservers();
  }
}
```

## Observer/Subscriber

The observer is the object that observes a subject. For example, an observer can observe a subject that is a shared state.

Just like the subject, this is only a simple implementation and will probably need to be modified for your use case. 

```dart
abstract class Observer {
  final id = Uuid().v4();

  void update(int state);
}
```

## Putting it all together

The abstract Subject class must be extended by another class. For example:

```dart
class MySubject extends Subject {
  MySubject() {
    Timer.periodic(
      const Duration(seconds: 1), (_) => setSomeState(someState + 1));
  }
}
```

The abstract class Observer must be extended by another class as well. For example:

```dart
class MyObserver extends Observer {
  String name;

  MyObserver(String name) : name = name;

  @override
  void update(int state) {
    print(name + ' recieved state ' + state.toString());
  }
}
```

This is the main function that starts the observing.

```dart
void main() {
  var subject = MySubject();
  var observerOne = MyObserver('Observer One');
  var observerTwo = MyObserver('Observer Two');

  subject.observe(observerOne);
  subject.observe(observerTwo);
}
```

If you run this you will get the following output:

```sh
$ dart run main.dart
> Observer One recieved state 1
> Observer Two recieved state 1
> Observer One recieved state 2
> Observer Two recieved state 2
> Observer One recieved state 3
> Observer Two recieved state 3
> ...
```

You can kill the process by pressing Control+C.
