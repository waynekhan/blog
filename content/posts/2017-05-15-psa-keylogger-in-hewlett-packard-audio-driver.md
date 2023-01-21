---
title: "PSA: Keylogger in Hewlett-Packard Audio Driver"
date: 2017-05-15T02:32:30+00:00
---

> A keylogger records when a key is pressed, when it is released, and whether any shift or special keys have been pressed. It is also recorded if, for example, a password is entered even if it is not displayed on the screen.
> 
> There is no evidence that this keylogger has been intentionally implemented. Obviously, it is a negligence of the developers - which makes the software no less harmful. If the developer would just disable all logging, using debug-logs only in the development environment, there wouldn't be problems with the confidentiality of the data of any user.

I found `MicTray64.exe` in my HP EliteBook 840 G3. It's barely 2 months old, running an up-to-date version of Windows 10 Pro. The prudent measure was to remove this file, as neither Conexant nor Hewlett-Packard hasn't deigned to respond. I was unable to find the log file `C:\Users\Public\MicTray.log`, though.

## References

* [https://www.modzero.ch/modlog/archives/2017/05/11/en_keylogger_in_hewlett-packard_audio_driver/index.html](https://www.modzero.ch/modlog/archives/2017/05/11/en_keylogger_in_hewlett-packard_audio_driver/index.html)
