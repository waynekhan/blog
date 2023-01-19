---
title: rrd.h not found
date: 2017-05-24T07:13:34+00:00
---

I was trying to compile `collectd` on a old CentOS 6 host, and `./configure` complained that `rrdtool` couldn't be found; e.g.,

```text
rrdtool . . . . . . . no (rrd.h not found)
```

I'd intended to use `rrdtool` to collect instance-level metrics and then graph 'em out with [CGP](https://github.com/pommi/CGP), so it was pretty annoying. TIL that you can use `-ql` to list the files installed by a particular binary; e.g.

```text
$ rpm -ql rrdtool-devel
package rrdtool-devel is not installed
```

I installed `rrdtool-devel`, and then lo and behold:

```text
rrdtool . . . . . . . yes
```

## References

* [https://stackoverflow.com/questions/40753932/python3-pip-cannot-install-rrdtool-on-centos6](2017-07-20-display-bug-in-vsphere-client.png)
