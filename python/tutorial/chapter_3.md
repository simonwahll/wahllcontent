---
title: "Chapter 3 - Comments"
description: "Chapter 3 - Comments"
lead: ""
date: 2021-03-17T22:25:13+01:00
lastmod: 2021-03-17T22:25:13+01:00
draft: false
images: []
menu: 
  python:
    parent: "Python Tutorial"
weight: 3
toc: true
---

Sometimes when writing a program it can be quite hard to understand what something does or even why something is done. This can be solved by commenting our code. It basically means we insert any text that Python will know to ignore. 

We can add a comment to the program we created in the previous tutorial like this:
```py
# Outputs Hello World! to the terminal
print("Hello World!")
```

Comments are lines that start with a `#`. Anything we put after this `#` to the end of the line will be ignored by Python and only available for us, programmers, to help us understand the code.

In our example we gave an entire line to a comment. This type of comment is probably the most used comment in programming but there is one more way to do this. We don't have to put comments on separate lines, we can also put them at the end of a line:
```py
print("Hello World!") # Prints Hello World! to the terminal
```

Whether you want to put you comments on separate lines or at the end of another line is up to you. Most of the time you will most likely want to put comment on their own lines since it makes the code a lot more readable and easy to understand. 

To summarize, we learned how we can create comments that will be ignored by Python. They only exist for us to explain something tricky or explain why something is being done. Comments can be put on their own lines or at the end of another line, like so:
```py
# I use my own line
print("Hello World!") # I share this line with the print() function
```
