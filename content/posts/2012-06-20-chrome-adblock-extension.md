---
title: Chrome AdBlock extension
date: 2012-06-20T02:57:23+00:00
---

I've been thinking about writing a userscript to prevent loading of particular network resources. The problem is that particular FQDNs seem to either be blocked outright, or timeout by this Niometrics thing.

This makes for a poor web browsing experience, so I made my own little list:

```text
http://*.addthis.com/*
http://www.facebook.com/*
http://connect.facebook.net/*
http://static.ak.fbcdn.net/*
http://*.fmpub.net/*
https://secure.google-analytics.com/*
http://www.google-analytics.com/*
http://*.googlesyndication.com/*
http://*.pinterest.com/*
http://*.sharethis.com/*
http://www.stumbleupon.com/*
http://platform.tumblr.com/*
http://platform.twitter.com/*`
```

The good thing is that wildcard is a supported feature, makes things much less verbose than say [a custom hosts file]({{< ref "2011-10-24-mvp-hosts-file" >}}).
