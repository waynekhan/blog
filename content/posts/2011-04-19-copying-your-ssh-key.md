---
title: Copying your SSH key
date: 2011-04-19T01:36:55+00:00
---

I frequently try new OSes courtesy of VirtualBox, and I keep forgetting about `xclip` so I'm reposting snippets of [this article](http://help.github.com/linux-set-up-git/) here:

```text
sudo apt-get install xclip
xclip -sel clip < ~/.ssh/id_rsa.pub
```
