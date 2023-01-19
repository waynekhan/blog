---
title: Windows laptop can't find Wi-Fi; others can
date: 2015-06-02T05:23:57+00:00
---

From the Start menu, right click "Computer", then "Manage".

"Computer Management" window comes up, navigate to System Tools -> Device Manager > Network adapters. Right click the correct one (e.g. Atheros AR5B97 Wireless Network Adapter), then Uninstall. Keep the driver software for the device, now you should have one less adapter.

Again from "Computer Management", click Action > Scan for hardware changes.

The wireless adapter should be detected, and then previously missing wireless network should re-appear.

Extracted from [http://www.tomshardware.com/answers/id-1728029/laptop-find-wifi.html](http://www.tomshardware.com/answers/id-1728029/laptop-find-wifi.html).
