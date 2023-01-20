---
title: OS X Icon file
date: 2013-09-22T08:39:03+00:00
---

When I use Terminal.app, I noticed that the OS creates this `Icon` file for folders that I created. It's quite irritating, and Eclipse \o/ chokes on it. I never figured out why until today. So apparently it is a custom icon -- albeit one I didn't set, so feel free to clean 'em out:

```text
find . -name Icon\* | xargs rm -f
```

## References

* [http://superuser.com/questions/298785/icon-file-on-os-x-desktop](http://superuser.com/questions/298785/icon-file-on-os-x-desktop)
