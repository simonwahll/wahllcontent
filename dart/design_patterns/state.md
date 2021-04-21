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
weight: 105
toc: true
---

The state design pattern can change its internal state without changing its outer state. This can be useful when you have an object that changes its behavior depending on its state or when an object is getting too many conditional behaviors it can be split into separate objects with the state design pattern.

It consists of three parts:

1. An interface the different states can implement.
2. Several different states that can be used by the state context class.
3. A state context class that keeps track of the current state and provides a common interface.

Let's start from the beginning.

## State Interface

This is quite straightforward.

```dart
abstract class State {
  void describe(StateContext stateContext);
}
```

## Some Different States

Each state should implement the `State()` interface. We will create two states for now.

```dart
class LiquidState implements State {
  @override
  void describe(StateContext stateContext) {
    print('This is liquid.');
    stateContext.setState(SolidState()); 
  }
}
```

```dart
class SolidState implements State {
  @override
  void describe(StateContext stateContext) {
    print('This is solid.');
    stateContext.setState(LiquidState());
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
  state.describe();
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

Congratulations, you just used the state design pattern.

Note that you can have multiple current states in the state context but keep in mind that this will increase the complexity significantly and should generally be avoided.

## State vs Strategy

Below we will outline the main differences:

### State
- The states can be aware of each other.
- The states can change the current state in the state context.
- An actor outside of the state context or the states should not be able to directly change the current state.
- A change in the state should be a side effect of some action in the state context. This can be in either the state context or in one of the states.

### Strategy
- The strategies should not be aware of each other.
- A strategy should not be able to change any current strategy in the strategy context.
- An actor outside of the strategy context should be able to change the current strategies.
- A change in the strategy contexts strategies should not be a side effect of some action in the strategy context. 
