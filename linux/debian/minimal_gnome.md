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
weight: 2
toc: true
---

## Why?

When installing the GNOME version of Debian you will get piles of packages installed that you will never use. I would recommend installing the minimal version of Debian without any desktop environment and then install GNOME later with apt.

## How-To

1. Download the netinstall iso from the Debian [website](https://www.debian.org/) and install it without any desktop environment. 

Note: If you don't need to connect to the internet with WiFi you can skip to step 7.

2. If you need to connect to the internet with [WiFi](https://wiki.debian.org/WiFi/HowToUse) you can do so by editing `/etc/network/interfaces` and adding the following to the bottom of the file:
```sh
allow-hotplug <interface>
iface wlan0 inet dhcp
  wpa-ssid <MySsid>
  wpa-psk <MyPassword>
```
Where `<interface>` is the interface of your WiFi card. (You can find this by running the command `ip a`, an example would be `wlp2s0`), `<MySsid>` is the SSID of your WiFi (commonly referred to as the name) and `<MyPassword>` is the password to your WiFi.

4. Now connect to your WiFi by running the command:
```sh
ifup <interface>
```
Where `<interface>`, again, is the interface of your WiFi card. If you get any errors, make sure you entered the right SSID and password in `/etc/network/interfaces`.

5. Install gnome-core with apt.
```sh
apt install gnome-core
```

6. Remove the lines you entered in step 2 in `/etc/network/interfaces`, but keep any lines that existed before you edited it. This is necessary because GNOME doesn't connect to WiFi by using this file. You will have to connect to your WiFi in GNOME again using the WiFi menu in the top right corner after logging in to GNOME the first time.

7. Reboot and you will be able to log in to GNOME.

## Networking Icon Is a Question mark

In the top right corner, you might have a weird network icon that says `Wired Unmanaged`. You can fix this by edition `/etc/NetworkManager/NetworkManager.conf` and change `managed=false` to `managed=true`.
