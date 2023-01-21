---
title: Shell commands for Ubuntu Netbook Edition 9.10
date: 2010-02-24T06:27:28+00:00
---

```text
# Install Wine, IEs4Linux
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get update
sudo apt-get install wine
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux

# Uninstall games
sudo apt-get remove gnome-games
sudo apt-get autoremove

# Cleanup
history -c
```