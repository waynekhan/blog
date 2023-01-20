---
title: Failed dependencies when installing RPMForge
date: 2011-03-30T03:36:52+00:00
---

Got this error today whilst trying to install an [RPMForge package](http://wiki.centos.org/AdditionalResources/Repositories/RPMForge), `collectd`:

```text
error: Failed dependencies:
rpmlib(FileDigests) <= 4.6.0-1 is needed by rpmforge-release-0.5.2-2.el6.rf.i686
rpmlib(PayloadIsXz) <= 5.2-1 is needed by rpmforge-release-0.5.2-2.el6.rf.i686
```

Googled about it for awhile, nothing forthcoming. Now, if you `rpm -qa | grep rpmlib` no results will return. The actual package name is `rpm-lib`.

So after awhile I noticed that the versions stated above were higher than the one I had installed, and I'd just done a `yum upgrade`.

So those error messages/web page titles actually mean something:

> RPMforge for (upcoming) CentOS 6

I was, of course on CentOS 5, and trying (in vain) to install on CentOS 6. The correct URLs are:

## References

* i386: [http://packages.sw.be/rpmforge-release/rpmforge-release-0.5.2-2.el5.rf.i386.rpm](http://packages.sw.be/rpmforge-release/rpmforge-release-0.5.2-2.el5.rf.i386.rpm)
* x86-64: [http://packages.sw.be/rpmforge-release/rpmforge-release-0.5.2-2.el5.rf.x86_64.rpm](http://packages.sw.be/rpmforge-release/rpmforge-release-0.5.2-2.el5.rf.x86_64.rpm)
