---
title: MVP hosts file
date: 2011-10-24T05:41:37+00:00
---

[MVP hosts](https://winhelp2002.mvps.org/) is a good start if you're looking to block ad-serving domains.

However, these entries have to be FQDNs -- fully qualified domain names, so `*.doubleclick.net` or `doubleclick.net` won't work.

wildcard domains; e.g., `*.doubleclick.net` and sub-domains `foo.doubleclick.net` do not work correctly.

Furthermore, the scope of this setup applies only to your local machine.

The large filesize (~16k lines) also means reduced performance since there are multiple lines for the same TLD; e.g., `activity.serving-sys.com`, `bs.serving-sys.com`.
