---
title: Changing hostname
date: 2010-03-15T08:19:41+00:00
---

When `/etc/hostname` is updated, be sure to follow suit in the default `tnsnames.ora` and `listener.ora`. Mine were in:

```text
/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/admin
```

Otherwise you'll get an `ORA-12541` error.