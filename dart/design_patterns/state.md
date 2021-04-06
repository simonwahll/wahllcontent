---
title: "State"
description: "State"
lead: ""
date: 2021-04-06T21:24:09+02:00
lastmod: 2021-04-06T21:24:09+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Design Patterns"
weight: 5
toc: true
---

The state design pattern can change its internal state without changing its outer state. This can be useful when you have an object that changes its behavior depending on its state or when an object is getting too many conditional behaviors it can be split into separate objects with the state design pattern.

It consists of three parts:

1. An interface the different states can implement.
2. A number of different states that can be used by the state context class.
3. A state context class that keeps track of the current state and provides a common interface.

Let's start from the beginning.

## State Interface

This is quite straight forward.

```dart
abstract class State {
  void describe();
}
```

## A Number of Different States

Each state should implement the State() interface. We will create two states for now.

```dart
class LiquidState implements State {
  @override
  void describe() {
    print('This is liquid.');
  }
}
```

```dart
class SolidState implements State {
  @override
  void describe() {
    print('This is solid.');
  }
}
```

## State Context Class

This is the class the clients will interact with. It contains its internal state and provides a common interface for the clients.

```dart
class StateContext {
  State _currentState = SolidState();

  void setState(State newState) {
    _currentState = newState;
  }

  void describe() {
    _currentState.describe();
  }
}
```

## Testing Our State

This can be tested with a simple `main()` function:

```dart
void main() {
  var state = StateContext();
  state.describe();
  state.setState(LiquidState());
  state.describe();
  state.setState(SolidState());
  state.describe();
}
```

When you run this program you will get the following output:

```sh
$ dart run main.dart
> This is solid.
> This is liquid.
> This is solid.
```

Congratulations, you just used the state design pattern. Optionally you could use some kind of function in the `StateContext()` class that cycles through all the possible states.
