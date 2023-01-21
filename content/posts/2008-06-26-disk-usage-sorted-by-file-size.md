---
title: Disk usage sorted by file size
date: 2008-06-26T09:11:29+00:00
---

The following shell command runs the `du` command to a max folder depth of 1, pipes its output to `sort`, and the finally writes it `du_log`; e.g.,

```text
du -h --max-depth=1 | sort -n -r > du_log
```