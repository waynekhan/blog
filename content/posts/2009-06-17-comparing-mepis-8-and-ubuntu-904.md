---
title: Comparing MEPIS 8 and Ubuntu 9.04
date: 2009-06-17T04:34:01+00:00
---

I tried out Ubuntu 9.04 a week ago. I know I'm not exactly comparing apples with apples, since MEPIS 8 is based on Debian 5.0 and uses KDE 3.5, whilst Ubuntu 9.04 uses GNOME 2. I might be better off evaluating Kubuntu, the 9.04 release uses KDE 4, which [I'd used previously]({{< ref "2009-02-26-back-to-kde-351" >}}), and disliked due to its gradual reduction in snappiness.

But back to Ubuntu versus MEPIS. I've been running MEPIS on a (slow) Compaq nc8230, while Ubuntu runs on a (fast) IBM R52.We'll see if that pans out in Ubuntu's favour later on.

## Package Management

I develop in PHP, so I use Apache, MySQL and Oracle (remote server) on a daily basis. From my point of view as a developer, all of the packages I use have the same name as in MEPIS. Synaptic in both MEPIS and Ubuntu, handles packages well, so a tie here.

MEPIS 1, Ubuntu 1.

## Apps

Apps-wise, I felt that, overall KDE's were more suitable, even though I was able to find GNOME-based replacements for the ones I used in MEPIS:

* Kate/Gedit. Kate can syntax highlight my `.ctp` files, while Gedit has no such configuration option. Kate has sessions so I can quickly switch between projects, Gedit does not.
* Konsole/Terminal. Konsole remembers my tabs, Terminal does not.
* Katapult/Do. I prefer the default Alt+Space shortcut for Katapult, Do does it like Win+Space, because Alt+Space is used by GNOME. I also prefer if a calculator is built into Do, so I press Win+Space+32\*5 and I get the result (160) onscreen.
* Kdesvn, Kdiff, and Kompare/Meld. Meld is MUCH better than either of those 3 apps, I can do a 3-way file/directory comparison easily. It can even open a Subversion-ed directory and handle it correctly.
* No Dropbox client in MEPIS. The Ubuntu client works well. I'm still waiting (or hoping) for a KDE-based one, but maybe they are reluctant to write one in KDE 3.5, then later rewrite for KDE4?

MEPIS 1, Ubuntu 0.5 (due to Meld, Dropbox).

## Speed/Stability

I feel that Ubuntu 9.04 has some way to go, as I'd to POWER OFF the laptop as Ubuntu does the dreaded "window goes dark" thing, and I see/hear alot of hard drive activity, and then I have to (painfully) switch to Terminal, and then use `killall`. Usually, the culprit is Firefox.

I've also written about how unstable 9.04 was. After some reading on the forums, I figured it might be a graphics issue. Setting System -> Preferences -> Appearance -> Visual Effects to "None" seem to have resolved my stability problems. Ubuntu is now as stable as MEPIS.

MEPIS 8, on the IBM R52, meanwhile is fast and stable, albeit with less special effects. I must admit, I was wowed by the special effects, but not at the expense of speed, and particularly stability.

MEPIS 1, Ubuntu 0.

## Overall

The overall score is MEPIS 3, Ubuntu 1.5.

Nevertheless, I do so enjoy using Dropbox and Meld, so much so that I'm probably willing to accept the differences between Kate/Gedit, Konsole/Terminal, Katapult/Do.