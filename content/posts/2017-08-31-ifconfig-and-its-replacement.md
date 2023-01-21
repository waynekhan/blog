---
title: Ifconfig and its replacement
date: 2017-08-31T05:16:54+00:00
---

Recently I installed CentOS 7 Minimal, and lo and behold, command not found. As it turns out, `ifconfig` you can still get via `yum install net-tools`, we should be a bit more forward looking, and use it's designated replacement.

To quote Doug Vitale's [excellent article](https://dougvitale.wordpress.com/2011/12/21/deprecated-linux-networking-commands-and-their-replacements/):

> some Linux tools that, while still included and functional in many Linux distributions, are actually considered [deprecated](http://en.wikipedia.org/wiki/Deprecation "Deprecation on Wikipedia") and therefore should be phased out in favor of more modern replacements.
> 
> Specifically, the deprecated Linux networking commands in question are: **arp**, **ifconfig**, **iptunnel**, **iwconfig**, **nameif**, **netstat**, and **route**. These programs (except **iwconfig**) are included in the [net-tools](http://www.linuxfoundation.org/collaborate/workgroups/networking/net-tools "net-tools on the Linux Foundation") package that has been unmaintained for years.

Now, his article was written in 2011, so this probably means a decade or so after the software was essentially abandoned, there are still unknowing users like me who had no idea, happily using it for whatever we use it for.

So software and blog posts, the gift that keeps on giving then!
