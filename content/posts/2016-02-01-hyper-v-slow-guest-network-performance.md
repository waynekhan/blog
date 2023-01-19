---
title: "Hyper-V: Slow Guest Network Performance"
date: 2016-02-01T01:58:05+00:00
---

A couple weeks ago, I discovered that guest network performance was abysmally slow, copy-pasting files from host to guest (RDP) felt like it took days instead of the (expected) minutes! This delayed the commissioning of a new application, and it bugged me for a bit. Later on, a different guest exhibited the same issue; i.e., I could actually *see* the images it sent over being (very slowly) downloaded in the browser...

After a bit of Google-ing and experimentation, it appears to be related to a NIC issue (our HP server uses Broadcom) and this Virtual Machine Queues (VMQ) option in Windows Server 2012 R2. It's weird that it hasn't already been resolved by Broadcom/Microsoft, but [here's the full Reddit link](https://www.reddit.com/r/sysadmin/comments/2k7jn5/after_2_years_i_have_finally_solved_my_slow/) if you need more details.

Do note however that I tried out the Registry update `BelowTenGigVmqEnabled=1`, but it didn't work in my case. I'm just going to quote from the the Redditor in closing:

> My world is beautiful.

## References

* [https://www.reddit.com/r/sysadmin/comments/2k7jn5/after_2_years_i_have_finally_solved_my_slow/](https://www.reddit.com/r/sysadmin/comments/2k7jn5/after_2_years_i_have_finally_solved_my_slow/)
