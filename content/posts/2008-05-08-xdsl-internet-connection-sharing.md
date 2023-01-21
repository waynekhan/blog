---
title: xDSL Internet connection sharing
date: 2008-05-08T02:10:38+00:00
---

Want to share your xDSL Internet connection? You'll need three devices:

1. A xDSL modem;
1. A router (optionally, wireless);
1. One (or more) machines.

Some of the newer modems have router/switch functionality, but we'll focus on making the modem act as a bridge, a so-called dumb device, between the Wide Area Network (WAN) and your Local Area Network (LAN); which comprises of your router and machine(s).

If you already have an existing xDSL service, you will already own a modem and host machine, so all you will need in addition is a router; I recommend the Linksys WRT54G (or WRT54C is OK too), which has served me faithfully.

Your xDSL modem has at least four ports (Power, USB, Telephone, Ethernet). If your modem has more than one Ethernet port, it means that your modem is an all-in-one device with WAN/LAN functionality, so you won't need to read further.

So suppose we only have one host machine; the final setup should look like the following, where '-----' represents a Ethernet cable, which looks like a (fat) telephone cable.

```text
Modem [Ethernet port] ----- [Internet port] Router [Ethernet port 1] ----- [Ethernet port] Host machine
```

But first we need to set the modem to bridge mode. Connect it as follows:

```text
Modem [Ethernet port] ----- [Ethernet port] Host machine
```

Now you need to access the modem's web interface (assuming it is a fairly modern device!). Make sure your Ethernet connection is set to `DHCP`, so that the host machine gets a local IP address. I will be using the default `192.168.1.x` convention. Now our machine gets an IP like `192.168.1.100` (or whatever, just as long as it is different from the modem). The gateway (modem) should be `192.168.1.1`, and so we'll access its web UI at [http://192.168.1.1/](http://192.168.1.1/).

Each web interface differs, but you should be looking for bridge mode. Set it to bridge mode, and disable DHCP. The modem will restart, and the machine will no longer have an IP address (because DHCP is disabled). Now we connect as follows:

```text
Router [Ethernet port 1] ----- [Ethernet port] Host machine
```

The router should be configured to PPPoE (xDSL) mode -- you will be prompted for the username and password to the DSL service with your Internet Service Provider (ISP). Also set the router IP address like 192.168.1.2 and enable DHCP. Remember that the IP address must differ from the address of the modem; e.g.,

* Modem [192.168.1.1]
* Router [192.168.1.2]

You can ask the router to begin allocation host machine addresses from a certain number onwards; e.g. 10. So the first host machine would be:

```text
Host machine [192.168.1.10]
```

Now let's set everything to its final connection state:

```text
Modem [Ethernet port] ----- [Internet port] Router [Ethernet port 1] ----- [Ethernet port] Host machine
```

Here's where I furiously reload the router's web UI. Setup correctly, the router should have a WAN IP address from the modem, and you'll be able to access the internet from your machine then.