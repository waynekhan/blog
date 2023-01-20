---
title: The mystery of the disappearing laptop screen brightness slider
date: 2011-06-21T01:54:27+00:00
---

Updated for Windows 10.

I noticed that with the power turned off at boot time, I'd be unable to adjust my screen brightness. Instead of the usual 3 options (Turn off the display, Put the computer to sleep, and Adjust plan brightness), just 2 were available; i.e. Adjust plan brightness" had disappeared!

This is probably due to a bad driver (e.g., TeamViewer). The workaround is to restart Windows with the power plugged in, but this takes too long.

A better solution is: Windows + x: Device Manager: Monitors: (Select your monitor): Properties: Driver: Uninstall.

Post-uninstall, click Action: Scan for hardware changes. Your monitor should reappear, this time with the good driver installed.

## References

* [http://social.technet.microsoft.com/Forums/en-US/w7itprohardware/thread/08a3eb1d-b698-4639-af4b-5278b721fcdc/](http://social.technet.microsoft.com/Forums/en-US/w7itprohardware/thread/08a3eb1d-b698-4639-af4b-5278b721fcdc/)
