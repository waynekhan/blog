---
title: Java plugin (Firefox) on MEPIS
date: 2009-03-26T05:49:32+00:00
---

I found [this link](http://www.mepis.org/node/2104) useful. It helped me to get Java running in Firefox. The instructions are a bit outdated, so I'm reposting.

First we need Java:

```text
apt-get install sun-java6-plugin
```

Go to the Firefox "plugins" folder, and rename for the existing (not working!) plugin with a `.bak` file extension (or whatever you prefer), then create a symlink like so:

```text
cd /usr/lib/firefox/plugins
mv libjavaplugin.so libjavaplugin.so.bak
ln -s /usr/lib/jvm/java-6-sun-1.6.0.12/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin.so
```

You'll also need to restart Firefox for the changes to take effect.
