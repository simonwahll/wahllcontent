---
title: "Variables"
description: "Variables"
lead: ""
date: 2021-05-18T17:20:58+02:00
lastmod: 2021-05-18T17:20:58+02:00
draft: false
images: []
menu:
  javascript:
    parent: "JavaScript"
weight: 1
toc: true
---

A variable is something that stores some value that can be used later. These values can be retrieved and used later. JavaScript is a dynamically typed language. That means you don't have to keep track of what data type a variable is. A variable can also change its data type during runtime.

## Syntax

A variable can be declared with the following syntax:

```js
var <name>;
```

Where `<name>` is the name of the variable.

Assignment to a variable has the following syntax:

```js
<name> = <value>;
```

Where `<name>` is the name of the variable and `<value>` is the value to be assigned to it.

A variable can be declared and assigned a value at the same time with the following syntax:

```js
var <name> = <value>;
```

Where `<name>` is the name of the variable and `<value>` is the value that is assigned to it.

## Examples

Declaring a variable with the name `age` and assigning it the value `50`:

```js
var age = 50;
```

Assigning a new value `"Old"` to the variable `age`:

```js
age = "Old";
```

## Using the Value of a Variable

The value of a variable can be retrieved by just typing the name of the variable.

For example, we can declare a variable `greeting` and assign it the value `"Hello"` and then retrieve the value and print it to the console.

```js
var greeting = "Hello";
console.log(greeting);
```

## ES6

ES6 added two keywords that can be used to declare variables. These have some different properties than the `var` keyword.

### let

`let` is used to declare a variable that is only valid within the scope it is declared in. Otherwise, it is identical to the `var` way of declaring a variable.

```js
function myFunction() {
  // This is a function with a local scope.
  // If a variable is declared here with
  // the let keyword, it will not be accessible
  // outside of this function.
  let myLetVariable = 10;
}

// Error: This variable does not
// exist in this scope.
console.log(myLetVariable);
```

### const

`const` is used to declare a variable whose value will never change. Once a value has been assigned it can never be changed. This can be useful if you want to ensure that a variable can never be changed. Just like with `let` this is also local to the scope it is declared within. A const variable is often called a `constant`.

```js
function myFunction() {
  // This is a function with a local scope.
  // If a constant is declared here with
  // the const keyword, it will not be accessible
  // outside of this function.
  const myConst = 10;

  // Error: The value of a constant cannot be changed.
  myConst = 20;
}

// Error: This constant does not exist
// in this scope.
console.log(myConst);
```
