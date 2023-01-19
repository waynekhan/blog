---
title: "CentOS: Forced shutdown"
date: 2017-11-24T01:42:52+00:00
---

Yesterday, we encountered a disk issue on one of our CentOS servers. Some of the disks had either failed, or were predicting failure, so our vendor swooped in, changed some of the disks, as well as the RAID controller. Unfortunately, this worked for only a short time, before we started seeing "input/output error" verbiage in the console. The concern was data loss, so we tried to shutdown, reboot: same "input/output error".

And then I learnt that it's possible to force a shutdown via the Magic SysRq key. I mean, magic!!

```text
echo 1 > /proc/sys/kernel/sysrq
echo o > /proc/sysrq-trigger
```

New disks are incoming as I type this, we'll have to keep a close look on this developing situation.

## References

* https://www.linuxquestions.org/questions/linux-newbie-8/input-output-error-222152/
* https://en.wikipedia.org/wiki/Magic\_SysRq\_key
