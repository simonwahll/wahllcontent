---
title: "Printing"
description: "Printing"
lead: ""
date: 2021-05-19T17:01:29+02:00
lastmod: 2021-05-19T17:01:29+02:00
draft: false
images: []
menu:
  javascript:
    parent: "JavaScript"
weight: 2
toc: true
---

Printing something is the process of outputting some text to the console. This can be done with the `console.log()` function.

## Syntax

```js
console.log(<arguments>);
```

Where `<arguments>` can be any number of arguments that should be printed to the console.

## Examples

Let's print `"Hello World!"` to the console:

```js
console.log("Hello World!");
```

Output:

```
> Hello World!
```

Let's give a user a greeting.

```js
var name = "Adam";
console.log("Hello", name);
```

Output:

```
> Hello Adam
```

Notice that the `console.log()` function adds a space between the arguments when printing them.
