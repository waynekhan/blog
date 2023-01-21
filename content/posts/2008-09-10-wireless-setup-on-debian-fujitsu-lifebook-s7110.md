---
title: Wireless setup on Debian (Fujitsu Lifebook S7110)
date: 2008-09-10T03:41:15+00:00
---

The S7110 uses the Intel® PRO/Wireless 3945ABG Network Connection adapter `iwl3945`. Use `lspci` to find out what type of network card you have:

```text
# lspci -nn | grep Intel
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)
```

You'll need at least the `2.6.24` kernel, available on Lenny onwards. If you're using Etch (or even Sarge), tough luck. Significant upgrades to follow. Find out what kernel is loaded:

```text
# uname -a
Linux woteba 2.6.26-1-686 #1 SMP Thu Aug 28 12:00:54 UTC 2008 i686 GNU/Linux
```

I'm using 2.6.26, which is recent. Otherwise add the following line to `/etc/apt/source.list`:

```text
deb http://ftp.tw.debian.org/debian/ lenny main contrib non-free
```

Now use Synaptic Package Manager to download at least the following packages:

```text
linux-image-2.6.26-1-686
firmware-iwlwifi
```

After everything is downloaded and set up successfully, you'll need to reboot into the new kernel, then:

```text
# modprobe iwl3945
# iwconfig
.
.
.
wlan0     IEEE 802.11  ESSID:"MakeTeaNotWar"
Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:9E:CF:58:B0
Bit Rate=54 Mb/s   Tx-Power=14 dBm
Retry min limit:7   RTS thr:off   Fragment thr=2352 B
Encryption key:6565-1671-75
Link Quality=76/100  Signal level=-58 dBm  Noise level=-87 dBm
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

(Should the `iwconfig` command be not found, install `wireless-tools`.)

The output above shows a connection to the router with SSID `MakeTeaNotWar`.

## References

* [Debian Wiki](http://wiki.debian.org/iwlwifi)