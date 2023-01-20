---
title: Google Reader to Springpad
date: 2013-01-12T05:32:35+00:00
---

Awhile back I decided to start using [Springpad](http://www.springpad.com/) for bookmarking and notes. It's worked out pretty well so far.

Springpad has various ways of saving stuff; e.g. browser extensions, a bookmark-let, email but I was looking a way to feed stuff from [Reader](http://reader.google.com/) (which I love); i.e. without opening a new window, waiting for the page to load and then finally using either the extension or bookmark-let to save it to Springpad. It's just so... slow.

So I extracted the URL from their bookmarklet, and I found that it works well with a custom Reader's "Send to" option. There are a bunch of defaults (e.g., Delicious, Instapaper) but none for Springpad. Fortunately, it is possible to manually setup a custom link. 3 fields are required: Name, URL and Icon URL, plus there's some documentation about field mapping. If all this sounds a bit alien, that's ok, here's what you want for each field:

```text
Name: Springpad
URL: https://springpad.com/clip.action?url=${url}&title=${title}
Icon URL: https://springpad.com/favicon.ico
```

Voilà!

![Google Reader to Springpad](/2013-01-12-google-reader-to-springpad.jpg)
