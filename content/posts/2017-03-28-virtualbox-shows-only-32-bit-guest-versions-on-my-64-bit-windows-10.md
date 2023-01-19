---
title: VirtualBox shows only 32-bit guest versions on my (64-bit) Windows 10?
date: 2017-03-28T08:23:30+00:00
---

> I quickly pressed Windows Key + q to open the Search box and typed in: turn windows features on or off Turn windows features on or off I scanned a few options but one in particular was salient: Hyper-V was enabled.

So I installed the 64-bit version of [Docker](https://www.docker.com/what-docker) for Windows after configuring a shiny new [VirtualBox](https://www.virtualbox.org/wiki/VirtualBox) CentOS 7 guest. The latter'd ran just fine previously, but was now causing a [BSOD](https://duckduckgo.com/?q=bsod&t=hf&ia=web), and I wasn't even able to create new 64-bit guests.

As it turns out, installing Docker enables Hyper-V, but uninstalling Docker doesn’t disable Hyper-V; i.e. these virtualization technologies are incompatible. The fix to this is quoted above: disable Hyper-V.

## References

* [http://www.fixedbyvonnie.com/2014/11/virtualbox-showing-32-bit-guest-versions-64-bit-host-os/](http://www.fixedbyvonnie.com/2014/11/virtualbox-showing-32-bit-guest-versions-64-bit-host-os/)
