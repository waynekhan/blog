---
title: Katapult-like functionality on KDE 4.1
date: 2009-02-16T03:03:20+00:00
---

OK, this post is more about recovering the Katapult functionality that I love.

In KDE 4, which [I recently installed]({{< ref "2009-02-12-kde-4" >}}) there is a program called KRunner. It works like Katapult, but the shortcut key is Alt+F2. It's too much of a stretch to hit both keys at the same time. Katapult's Alt+Space is way friendlier.

To change this shortcut: K -> System Settings -> Keyboard & Mouse -> Keyboard Shortcuts -> KDE Component (Run Command Interface) -> Run Command.

Click Custom, press Alt+Space or whatever, click Apply.

Also unlike Katapult, you'll need to prefix an `=` for math operations; e.g.,

```text
=60*24*365
```