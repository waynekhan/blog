---
title: "Failed dependencies when installing rpmforge"
date: 2011-03-30T03:36:52+00:00
---

Got this error today whilst trying to install [collectd](http://collectd.org/), which is kindly provided by [RPMForge](http://wiki.centos.org/AdditionalResources/Repositories/RPMForge):

`$ sudo rpm -i rpmforge-release-0.5.2-2.el6.rf.i686.rpm
error: Failed dependencies:
rpmlib(FileDigests) <= 4.6.0-1 is needed by rpmforge-release-0.5.2-2.el6.rf.i686
rpmlib(PayloadIsXz) <= 5.2-1 is needed by rpmforge-release-0.5.2-2.el6.rf.i686`

Googled about it for awhile, nothing forthcoming. Now, if you 'rpm -qa | grep rpmlib' no results will return. The actual package name is 'rpm-lib'.

So after awhile I noticed that the versions stated above were higher than the one I had installed, and I'd just done a 'yum upgrade'. That was swiftly followed by the "el6" part, and that I had completely missed out the title "1. RPMforge for (upcoming) CentOS 6". Well done.

So if you get the error in CentOS 5, it's because you were trying to install an .rpm for CentOS 6. The correct URLs are:

i386: http://packages.sw.be/rpmforge-release/rpmforge-release-0.5.2-2.el5.rf.i386.rpm
x86-64: http://packages.sw.be/rpmforge-release/rpmforge-release-0.5.2-2.el5.rf.x86\_64.rpm


