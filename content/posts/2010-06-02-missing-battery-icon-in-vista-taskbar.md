---
title: Missing battery icon in Vista taskbar
date: 2010-06-02T02:33:13+00:00
---

With reference to [this post](http://social.msdn.microsoft.com/forums/en-US/tabletandtouch/thread/be2d442f-bd71-4326-9fd2-0c88992ff0f7/), I encountered this same problem last night, on a Vista install.

Right-clicking the taskbar, then selecting Properties -> Taskbar and Start Menu Properties -> Notification Area -> System Icons -> Battery does not work, as the check boxes are greyed out.

The easiest solution is to hit Ctrl+Alt+Del, bring up the Task Manager, and then restart explorer.exe. Here's the solution that I've directly taken from Akshit's reply to that thread:

1. Go to Task Manager.
1. Go to Process tab.
1. End the "explorer.exe" process
1. Go to Applications tab
1. Select "New Task..."
1. Type "explorer.exe"

Hope this helps somebody, as Akshit's reply was about halfway down the thread.