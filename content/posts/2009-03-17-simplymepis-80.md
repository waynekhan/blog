---
title: SimplyMEPIS 8.0
date: 2009-03-17T08:05:11+00:00
---

My [slow laptop](http://waynekhan.com/blog/2009/03/oracle-sql-developer-is/) is now running on [SimplyMEPIS](http://www.mepis.org/) 8.0. Surprisingly, it doesn't feel that slow anymore. Maybe it was an OS issue, but I digress.

The install process was a breeze. I used mepis-network to setup wireless access, gparted to partition the hard disk into two partitions of 8GB (root) and 2GB (swap) each, and then it installed by itself. Later, it setup grub for me so that if I wanted to boot into Windows, it would comply. But I won't of course. When I boot into MEPIS for the first time, I wanted to setup wireless again, since the install was a Live CD. But I didn't even need to perform that step! The network settings that I added during the Live CD boot had been saved! Voila!

IMO networking, particularly wireless networking has to improve significantly, even Lenny. I wish it would just work, rather than having to [jump through hoops](http://waynekhan.com/blog/2008/09/wireless-setup-on-debian-fujitsu-lifebook-s7110/), and even then, not work particularly well.

Up till now, I **cannot** connect to my home wireless router. Before Lenny was released, there was a tool called "wlassistant" that worked occasionally. But now it's gone, and all of the other tools (kwifi-radar, wireless-tools) do not work. And it's not a router issue, because my other Windows laptops connect easily.

I'll try to set this up as a development machine; if things go well I just might switch my (primary) laptop to MEPIS.
