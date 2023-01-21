---
title: Check what services are accepting network connections
date: 2010-04-16T08:34:01+00:00
---

This network statistics command is your friend; e.g.,

```text
$ netstat -tnlp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:1521            0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      -
tcp        0      0 0.0.0.0:17500           0.0.0.0:*               LISTEN      2366/dropbox
```

So that's MySQL (TCP/port 3306), Oracle Application Express (TCP/port 8080), Oracle Database (TCP/port 1521), SSH (TCP/port 22), but what's Dropbox doing?