---
title: MEPIS 8 and Fujitsu Lifebook S7110
date: 2009-03-23T14:40:41+00:00
---

Previously, [I wrote]({{< ref "2009-03-17-simplymepis-80" >}}) that MEPIS worked (sound, wired networking, wireless networking) out of the box on my IBM R52.

FYI, the wireless card is the Intel PRO/Wireless 2200BG. I'd also [previously detailed]({{< ref "2008-09-10-wireless-setup-on-debian-fujitsu-lifebook-s7110" >}}) instructions on Debian "Etch". 

What I didn't state was that I would encounter issues where `wlassistant` would complain about being unable to get an IP address whilst connected to a standard WEP SSID. However if it alone, it'd mysteriously work later on. I got fed up, and mostly used a wired connection thereafter.

I'm pleased to note that there are no such issues for my Fujitsu Lifebook S7110, which uses the Intel PRO/Wireless 3945ABG; e.g.,

```text
lspci -nn | grep 3945
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
```

When I booted up via the LiveCD, I feared the worst, as it was unable to connect to that same SSID. For a time I feared that my laptop would reach it's end of useful life before I found a distro as excellent as MEPIS, but that's all in the past now.

:)
