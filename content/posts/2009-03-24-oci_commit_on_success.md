---
title: OCI_COMMIT_ON_SUCCESS
date: 2009-03-24T01:38:13+00:00
---

I received the following error in my CodeIgniter web application today:

> Notice: Use of undefined constant OCI_COMMIT_ON_SUCCESS - assumed 'OCI_COMMIT_ON_SUCCESS' in ...

It turns out that, on MEPIS at least, the packages `bc`, `libaio`, even having compiled support for OCI8. Adding those packages, restarting the web server and the error should go away.
