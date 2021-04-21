---
title: "Comments"
description: "Comments"
lead: ""
date: 2021-04-13T17:26:43+02:00
lastmod: 2021-04-13T17:26:43+02:00
draft: false
images: []
menu: 
  dart:
    parent: "Dart"
weight: 1
toc: true
---

Dart has three types of comments. These are the following:

- Single line comments
- Multiple lines comments
- Documentation comments

Let's take a look at each one of them.

## Single Line Comments

Single line comments start with two slashes (`//`) and are only valid to the end of the line. 

Example:
```dart
// This is a comment

// Assign the value 5 to the variable number
int number = 5;
```

## Multiple Lines Comments

These are the same types of comments you can find in C. They start with a slash followed by an asterisk (`/*`) and end with an asterisk followed by a slash (`*/`). This type of comment can span multiple lines because everything between the `/*` and the `*/` is part of the comment.

Example:

```dart
/* This is a comment */

/* This is
   a multiple lines
   comment */

/* Assign the
   value 5
   to the variable number
*/
int number = 5;
```

## Documentation Comments

Documentation comments are used by Dart's documentation tool. These are quite powerful and will be explored more in-depth in a documentation article. 

These comments start with three slashes (`///`) and are valid until the end of the line. 

Example:

```dart
/// This is a documentation comment.
/// They can span multiple lines too.
/// However, each line must start with
/// three slashes.
```
