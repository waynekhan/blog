---
title: Skipping incompatible lclntsh
date: 2010-12-06T06:08:32+00:00
---

Received this error whilst `make`-ing OCI8 for PHP. It was a fresh install of 64-bit CentOS 5.4 w/ Oracle XE 10g installed; e.g.,

```text
/usr/bin/ld: skipping incompatible /usr/lib/oracle/10.2.0.4/client/lib/libclntsh.so when searching for -lclntsh
/usr/bin/ld: cannot find -lclntsh
```

So I checked for `/usr/lib/oracle/10.2.0.4/client/lib/libclntsh.so` -- it exists, but for some reason it was "incompatible". Google is [helpful once again](http://www.issociate.de/board/post/171469/Re:_problems_building_DBD::Oracle_1.16_-_help_-_please.html). The problem was that the 10g RPM was 32-bit, but I was trying to compiling a 64-bit version of OCI8.

To resolve the issue, install the 64-bit version of the `-basic`, `-devel` versions of Oracle Instant Client, then specify this path in `configure`; e.g.,

```text
phpize
./configure -with-oci8=instantclient,/usr/lib/oracle/11.2/client64/lib
sudo make
sudo make install
```