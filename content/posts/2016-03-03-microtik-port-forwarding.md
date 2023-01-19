---
title: Microtik port forwarding
date: 2016-03-03T09:27:54+00:00
---

Spent too much time configuring port forwarding (RDP) on my (Microtik) RouterBoard 751G-2HnD. The solution, as usual, was buried in a May 2014 forum post. There needs to be TWO (2) NAT rules enabled; i.e. to forward traffic to/fro the router/server.

In this case, `192.0.78.13` and `10.0.0.254` refers to the router's WAN and LAN IPs respectively, and `10.0.0.243` is the intended recipient of my RDP traffic.

```text
[admin@751g2hnd] > /ip firewall nat print
1 chain=dstnat action=dst-nat to-addresses=10.0.0.243 to-ports=3389 protocol=tcp dst-address=192.0.78.13 dst-port=3389 log=no log-prefix=""
2 chain=srcnat action=src-nat to-addresses=10.0.0.254 to-ports=3389 protocol=tcp dst-address=10.0.0.243 dst-port=3389 log=no log-prefix=""
```

Many thanks to The Digital Doctor [http://forums.ncix.com/forums/topic.php?id=2662521](http://forums.ncix.com/forums/topic.php?id=2662521)!!
