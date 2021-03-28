---
title: "Minimal GNOME"
description: "Minimal GNOME"
lead: ""
date: 2021-03-28T18:03:36+02:00
lastmod: 2021-03-28T18:03:36+02:00
draft: false
images: []
menu: 
  linux:
    parent: "Debian"
weight: 1
toc: true
---

## Loads of packages

When installing the GNOME version of Debian you will get piles of packages installed that you wille never use. I would recommend installing the minimal version of Debian without any desktop environment and then install GNOME later with apt.

## How to

1. Download the netinstall iso from the Debian [website](https://www.debian.org/) and install it without any desktop enviroment.
2. Install gnome-core with apt.
```sh
apt install gnome-core
```
3. Reboot and you will be able to log in to GNOME.

## Networking icon

In the top right corner you wight have a weird network icon that says `Wired Unmanaged`. You can fix this by edition `/etc/NetworkManager/NetworkManager.conf` and change `managed=false` to `managed=true`.
