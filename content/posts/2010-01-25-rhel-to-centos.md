---
title: RHEL to CentOS
date: 2010-01-25T07:57:12+00:00
---

I installed RHEL today, but to get updates (via `yum`), a subscription is required. Not CentOS however.

Some Google-ing uncovered [this article](http://www.unixmen.com/linux-tutorials/documentations-a-howto/213-how-to-jul-convert-rhel-5-to-centos-5), which pretty much works, except I had to make a few edits here and there.

```text
# Remove cached packages
yum clean all

# Create /root/centos/
mkdir ~/centos && cd ~/centos

# Import CentOS's GPG key
wget http://mirror.centos.org/centos/5.4/os/i386/RPM-GPG-KEY-CentOS-5
rpm --import RPM-GPG-KEY-CentOS-5

# Download packages
wget http://mirror.centos.org/centos/5.4/os/i386/CentOS/centos-release-5-4.el5.centos.1.i386.rpm
wget http://mirror.centos.org/centos/5.4/os/i386/CentOS/centos-release-notes-5.4-4.i386.rpm
wget http://mirror.centos.org/centos/5.4/os/i386/CentOS/yum-3.2.22-20.el5.centos.noarch.rpm
wget http://mirror.centos.org/centos/5.4/os/i386/CentOS/yum-fastestmirror-1.1.16-13.el5.centos.noarch.rpm
wget http://mirror.centos.org/centos/5.4/os/i386/CentOS/yum-updatesd-0.9-2.el5.noarch.rpm

# Install 'em
rpm -Uvh {centos,yum}*.rpm

# Erase RHN-related packages
rpm -e --nodeps redhat-release
rpm -e --nodeps yum-rhn-plugin

# Profit!
yum upgrade
```

At this moment, my download is progressing nicely, [thanks to NUS's mirror](http://mirror.nus.edu.sg/).