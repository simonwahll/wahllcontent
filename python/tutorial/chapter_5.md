---
title: "Chapter 5 - Getting Input"
description: "Chapter 5 - Getting Input"
lead: ""
date: 2021-05-09T20:37:59+02:00
lastmod: 2021-05-09T20:37:59+02:00
draft: false
images: []
menu: 
  python:
    parent: "Python Tutorial"
weight: 5
toc: true
---

A program can be much more useful if the user can give it some data. For example, you might want to ask the user for his/her name. This process is called *getting input* or *reading input*. We can do this with the `input()` function. Don't worry about what a function is at this stage. Just know that the `input()` function will give us some input from the user.

Let's create a program that asks the user for his/her name, saves the answer in a variable, and prints the variable to the terminal.

```py
name = input('Enter your name: ')
print('Your name is', name)
```

The first line tells Python to ask the user for some input. We can type a question in the parenthesis, just make sure the question is surrounded by either double quotes (`"`) or single quotes (`'`). When the user enters his/her name and presses enter, Python will take that input and save it to the variable `name`.

On the second line, we print `Your name is <name>` to the terminal. `<name>` will be whatever the user answered on the `Enter your name: ` question. Multiple things can be printed to the terminal at the same time by putting everything you want to print inside the parenthesis after the `print` word. Remember to separate each of them with a comma (`,`).

This is the output we get when running this program:

```
$ python ask_for_name.py
> Enter your name: My Name
> Your name is My Name
```

In this chapter, we learned how the programmer can ask the user for some input. This can be anything the programmer might need, such as the user's name, age, or phone number.