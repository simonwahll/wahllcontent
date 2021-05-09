---
title: "Chapter 4 - Variables"
description: "Chapter 4 - Variables"
lead: ""
date: 2021-03-17T22:26:41+01:00
lastmod: 2021-03-17T22:26:41+01:00
draft: false
images: []
menu: 
  python:
    parent: "Python Tutorial"
weight: 4
toc: true
---

When programming you will come across scenarios where you would want to save one value for later use. Think of this as taking a real-life object, such as a coffee cup, and putting it away in a cabinet. Next time you want to use this cup you simply open the cabinet where you will find your cup. In the same way in programming, we can take a value, like the number 4, and put it in a box we give a name. Later when we have forgotten what that value is we can open the box we created and retrieve the value again.

Let's look at an example:
```py
x = 4
```
Here we take the value 4 and assigns it to the variable x. This is like taking an object and putting it in a box and giving the box a name. In this case, the object to put away is 4 and the name of the box we put it in is `x`. 

But how can we retrieve the value from this box? Since we know how to print something in the terminal we can print the value of this variable in the terminal:
```py
x = 4
print(x)
```

Note that we don't use quotes inside the parenthesis after print. If we would put quotes around `x` we would simply print the letter x to the terminal.

When we run this program it will print `4` in the terminal.

Let's go through the code and understand how it works. First, we create a variable named `x` and stores the value `4` in it. Then we instruct Python to print something to the terminal and the thing we want to print is the value of x. Python will then look up what value is stored in the variable `x`, replace `x` with this value and print it to the terminal. 

In the same way, we can print a string to the terminal:

```py
x = "Hello World!"
print(x)
```

This will print Hello World! in the terminal. Note that when we want to print a string we still need to use quotes around it. This is not necessary when we only want to store a number in the variable. We will talk more about strings and numbers in a future chapter. 

To summarize, we learned that we can take any number or string and store it in a variable that we give a name. We can then retrieve this value and use it. 
