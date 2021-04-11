---
title: "Strategy"
description: "Strategy"
lead: ""
date: 2021-04-08T18:15:45+02:00
lastmod: 2021-04-08T18:15:45+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Design Patterns"
weight: 7
toc: true
---

The strategy design pattern consists of a class, called the strategy context, that has one or more internal states. These internal states are simple properties. An actor outside of the class can change the internal state but the strategies themselves cannot do that. This design pattern can be useful when you want to construct an object out of other object such as a character in a video game.

It consists of three parts:

1. An interface the different strategies can implement.
2. A number of different strategies that is the internal state of the strategy.
3. A strategy context class that keeps track of the current state and provides a common interface.

Let's start from the beginning.

## Strategy Interfaces

This is quite straight forward. We will be creating two strategy component interfaces.

```dart
abstract class CPU {
  void printTypeOfCPU();
}
```

```dart
abstract class GPU {
  void printTypeOfGPU();
}
```

## A Number of Different Strategies

Each strategy should implement its corresponding interface. We will create two strategies for the CPU and two for the GPU.

```dart
class FastCPU implements CPU {
  @override
  void printTypeOfCPU() {
    print('Fast CPU');
  }
}
```

```dart
class SlowCPU implements CPU {
  @override
  void printTypeOfCPU() {
    print('Slow CPU');
  }
}
```

```dart
class FastGPU implements GPU {
  @override
  void printTypeOfGPU() {
    print('Fast GPU');
  }
}
```

```dart
class SlowGPU implements GPU {
  @override
  void printTypeOfGPU() {
    print('Slow GPU');
  }
}
```

## The Strategy Context Class

This is the class the clients will interact with. It contains its internal state and provides a common interface for the clients. The clients can change its internal state directly.

```dart
class Computer {
  CPU _cpu;
  GPU _gpu;

  Computer(this._cpu, this._gpu);

  void setCPU(CPU newCPU) {
    _cpu = newCPU;
  }

  void setGPU(GPU newGPU) {
    _gpu = newGPU;
  }

  CPU getCPU() => _cpu;
  GPU getGPU() => _gpu;

  void printAllComponents() {
    _cpu.printTypeOfCPU();
    _gpu.printTypeOfGPU();
  }
}
``` 

## Testing Our Strategy

This can be tested with a simple `main()` function:

```dart
void main() {
  var computer = Computer(SlowCPU(), FastGPU());
  computer.printAllComponents();

  computer.setCPU(FastCPU());
  computer.printAllComponents();

  computer.setCPU(SlowCPU());
  computer.setGPU(SlowGPU());
  computer.printAllComponents();
}
```

When you run this program you will get the following output:

```sh
$ dart run main.dart
> Slow CPU
> Fast GPU
> Fast CPU
> Fast GPU
> Slow CPU
> Slow GPU
```

Congratulations, you just used the strategy design pattern.

## State vs Strategy

Below we will outline the main differences:

### State
- The states can be aware of eachoter.
- The states can change the current state in the state context.
- An actor outside if the state context or the states should not be able to directly change the current state.
- A change in state should be a side effect of some action in the state context. This can be in either the state context or in on of the states.

### Strategy
- The strategies should not be aware of eachother.
- A strategy should not be able to change any current strategy in the strategy context.
- An actor outside of the strategy context should be able to change the current strategies.
- A change in the strategy contexts strategies should not be a side effect of some action in the strategy context.
