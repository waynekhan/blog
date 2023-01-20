---
title: CakePHP file caching and debug=0
date: 2012-03-28T05:51:23+00:00
---

Recently I encountered a bug in the system I support. Basically it consumes a web service, writing the results into database-backed logs. The problem was that not every entry was being recorded correctly, resulting in inconsistent data between my system and the web service.

This coincided with a deployment of a new software release, and I puzzled over it, testing, re-testing and logging the sequence of calls. I couldn't find the problem. In fact, I couldn't even find appropriate entries in the log file. Great.

The problem that I was only testing on one web server -- there were **two** -- and it was a deployment issue. Basically if you use the file storage engine for caching, CakePHP writes the schema to app/tmp/cache/models; e.g., `app/tmp/cache/models/cake_model_default_foo`.

The contents is a serialized version of the Foo model, and this will **never be updated** if debug is set to 0 in app/config/core.php. I'd written a script to delete such files, but I didn't run the script on one of the two web servers, and that was the problem. I use saveAll(), and CakePHP compares keys against its cache, removing non-matching ones. One of those fields was set to not null, so saving failed all the time.
