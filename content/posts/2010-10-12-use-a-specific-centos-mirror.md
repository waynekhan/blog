---
title: Use a specific CentOS mirror
date: 2010-10-12T03:45:44+00:00
---

I want my server to get updates from the CentOS package mirror `mirror.nus.edu.sg`, here we disable the `fastestmirror` plugin; e.g.,

```text
$ cat /etc/yum/pluginconf.d/fastestmirror.conf
[main]
enabled=0
verbose=0
socket_timeout=3
hostfilepath=/var/cache/yum/timedhosts.txt
maxhostfileage=10
maxthreads=15
#exclude=.gov, facebook
```

Now set the `mirrorlist`, `baseurl` and `failovermethod` values for CentOS-Base.repo for the various sections (`base`, `updates`, `addons`, `extras`, `centosplus`, `contrib`). The baseurl value is configured on a per-section basis, so edit carefully.

Here's mine, reproduced in full:

```text
$ cat /etc/yum.repos.d/CentOS-Base.repo 
# CentOS-Base.repo
#
# The mirror system uses the connecting IP address of the client and the
# update status of each mirror to pick mirrors that are updated to and
# geographically close to the client. You should use this for CentOS updates
# unless you are manually picking other mirrors.
#
# If the mirrorlist= does not work for you, as a fall back you can try the 
# remarked out baseurl= line instead.
#

[base]
name=CentOS-$releasever - Base
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=os
baseurl=http://mirror.nus.edu.sg/centos/$releasever/os/$basearch/
failovermethod=priority
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5

#released updates 
[updates]
name=CentOS-$releasever - Updates
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=updates
baseurl=http://mirror.nus.edu.sg/centos/$releasever/updates/$basearch/
failovermethod=priority
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5

#packages used/produced in the build but not released
[addons]
name=CentOS-$releasever - Addons
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=addons
baseurl=http://mirror.nus.edu.sg/centos/$releasever/addons/$basearch/
failovermethod=priority
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5

#additional packages that may be useful
[extras]
name=CentOS-$releasever - Extras
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=extras
baseurl=http://mirror.nus.edu.sg/centos/$releasever/extras/$basearch/
failovermethod=priority
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5

#additional packages that extend functionality of existing packages
[centosplus]
name=CentOS-$releasever - Plus
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=centosplus
baseurl=http://mirror.nus.edu.sg/centos/$releasever/centosplus/$basearch/
failovermethod=priority
gpgcheck=1
enabled=0
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5

#contrib - packages by Centos Users
[contrib]
name=CentOS-$releasever - Contrib
#mirrorlist=http://mirrorlist.centos.org/?release=$releasever&arch=$basearch&repo=contrib
baseurl=http://mirror.nus.edu.sg/centos/$releasever/contrib/$basearch/
failovermethod=priority
gpgcheck=1
enabled=0
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-5
```