---
title: Display bug in VMware vSphere Client
date: 2017-07-20T10:40:07+00:00
---

Basically, the display is cut off! So if I were trying to install a new OS, it wouldn't be very efficient since I'd have to guess what was on display; e.g.

![Display bug in vSphere client](/2017-07-20-display-bug-in-vsphere-client.png)

As it turns out, using the correct search phrase returns the answer. HINT: it's a compatibility issue between the client and display scaling in Windows 10; e.g. mine was set to 150%.

TLDR: The solution is to set display scaling to 100%, and then log out and in for the changes to take effect.
