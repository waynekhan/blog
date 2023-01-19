---
title: "PSA: Empty mysql root password for Ubuntu 16.04 LTS"
date: 2016-06-16T11:28:08+00:00
---

Today, I was trying out the new release, and then I ran into a wall: logging in to `mysql` didn't work, even though I was sure that I'd configured it correctly; i.e. `root` with an empty password.

I'd done this hundreds of times already, so I was sure it'd work, but then again, it **just didn't**. So I tried to reset the root password by killing mysql and then starting `mysql_safe` with a new password. In the past, this process has worked successfully, but then I kept getting the message that `mysql_safe` has ended; i.e. *not good*.

I left things as-is for awhile, before thinking to read the manual (RTM):

> Password behaviour when the MySQL root password is empty has changed. Packaging now enables socket authentication when the MySQL root password is empty. This means that a non-root user can't log in as the MySQL root user with an empty password. For details, see the [NEWS](https://anonscm.debian.org/cgit/pkg-mysql/mysql-5.7.git/tree/debian/NEWS?id=1025a9fa9c6c112913c59138db49dbc94891d20f) file.

Tldr: Non-root *nix users can no longer login as MySQL root, so just use `sudo root`.

p.s. `sudo` is not the answer to everything. The trick here is knowing why: an upstream change.
