---
title: "Chapter 2 - Hello World!"
description: "Chapter 2 - Hello World!"
lead: ""
date: 2021-03-17T22:21:45+01:00
lastmod: 2021-03-17T22:21:45+01:00
draft: false
images: []
menu: 
  python:
    parent: "Python Tutorial"
weight: 2
toc: true
---

Theres a tradition in programming that the first program you will learn to write prints Hello World! in the terminal. In this chapter we will learn how to do this and explain how it works.

Start by opening a file in any text editor and save it with the name hello_world.py anywhere on your computer where you can locate it later. In this file, enter the following and save it.
```py
print("Hello World")
```

Open a terminal and go to the folder you saved the Python file in. In this folder you can run the program we just wrote with the `python` program.

```sh
python hello_world.py
Hello World!
```

Congratulations, you just wrote your first python program. Now lets explore how this works.

Every program in Python is a number of instructions that are executed sequentially. Lets look at our program and understand how it works.

```py
print("Hello World!")
```

Our program only has one line with one instruction: output Hello World! to the terminal.

`print()` is a function that outputs anything we put in its parenthesis to the terminal. This is a function built into Python. Understanding exaclty how a function works is not requred in this chapter, we will get to that in a later chapter, for now its only necessary to know that anything put inside its parenthesis will be printed in the terminal.

Inside the parenthesis we have something that looks like a quote, `"Hello World!"`. Anything enclosed in quotation marks are called strings. This is simply any piece of text and Python will know not to do anything special with this. In the output we can see that the quotation marks itself is not printed to the terminal. This is because the quotation marks are not part of the string itself. They are only the delimiters indicating where the string begins and where it ends.

To summarize, we just learned that each Python program consists of a number of instructions that are executed sequentially. Our program consists only of one instruction, `print("Hello World!")`. This instructs Python to print whatever is inside the parenthesis to the terminal. In this case we want to print the string "Hello World!", so we put this in the parenthesis. 

Running a Python program can be done using the `python` program by typing `python` followed by the name of the file containing the Python code in the terminal.
