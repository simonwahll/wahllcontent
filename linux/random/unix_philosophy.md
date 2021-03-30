---
title: "Unix Philosophy"
description: "Unix Philosophy"
lead: ""
date: 2021-03-30T18:01:07+02:00
lastmod: 2021-03-30T18:01:07+02:00
draft: false 
images: []
menu: 
  linux:
    parent: "Random"
weight: 4 
toc: true
---

## Introduction

In 1978 Dough Mcllroy documented the Unix Philosophy in the Bell System Technical Journal. It has since been considered a well thought out system and been used as the design philosophy of most Unix-like operating systems. 

## The Four Truths

The Unix philosophy consists 4 main points. These are:
1. Programs should do one thing and one thing only really well. No "features" should exist and if you need more functionality you should create a new program for that task.
2. The output of one program should be considered the input of another program. This means output should not be cluttered and use a format like simple text. If possible, don't use binary formats and avoid interactive input.
3. Test new software quickly in the development process. Throw avaid bad parts of the software early and rebuild it if it isn't working right.
4. Use tools to help you. If you need to build these tools yourself, do so, even if you have no use for them after you have finished using them.

Ritchie and Thompson summarized these points into the following in 1974:
1. Make it easy to write, test, and run programs.
2. Interactive use instead of batch processing.
3. Economy and elegance of design due to size constraints ("salvation through suffering").
4. Self-supporting system: all Unix software is maintained under Unix.

## Do One Thing and Do It Well

Arguably the most importand part of the Unix philosophy is DOTADIW, Do One Thing And Do It Well. This simplifies development of software and makes them extensible. One piece of software that is limited in size is easier for the user to understand and at the same time a lot easier for the software developer to write and maintain. 

## Simplicity Over Perfection

Making a piece of software simple is much more important than making it perfect in the Unix philosophy. A software that does one thing with a simple interface is what makes it so powerful. Think of the `cat` program, it does one thing really well at the same time as having a simple interface. Take away one of these properties, DOTADIW or simple interface, and it would instantly be harder to use or not be as usable as it is now.
