---
title: "rsync"
description: "rsync"
lead: ""
date: 2021-05-08T14:18:06+02:00
lastmod: 2021-05-08T14:18:06+02:00
draft: false
images: []
menu: 
  linux:
    parent: "Random"
weight: 4
toc: true
---

rsync is a program that copies files. It can copy files locally on a system or to/from a remote system. However, it cannot copy files from a remote system to another remote system.

There are several reasons you might want to use rsync instead of, for example, `cp` or `scp`. Some of them are:

- Only differences between files are copied, saving bandwidth and time.
- Can be used to copy files to/from a remote system with either the rsync daemon or ssh.
- Content can be compressed during the copy, saving bandwidth and time.

## Syntax

```
rsync [OPTIONS] <source> <destination>
```

Where:

- `[OPTIONS]` can be a massive amount of options, see `man rsync`.
- `<source>` is the source file or folder to copy.
- `<destination>` is the destination to copy the `<source>` to.

## Examples

Copy `/home/user/data.txt` to `/data/data.txt`

```
rsync /home/user/data.txt /data
```

Copy `/home/user/data.txt` to the remote location `pi@MyPi:/home/pi`.

```
rsync /home/user/data.txt pi@MyPi:/home/pi
```

Copy remote folder `pi@MyPi:/home/pi/folder` into `/home/user/folder`.

```
rsync pi@MyPi:/home/pi/folder /home/user
```