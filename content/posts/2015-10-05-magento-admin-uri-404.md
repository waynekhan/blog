---
title: Magento Admin URI 404
date: 2015-10-05T08:57:35+00:00
---

Today I was informed that navigating to a (previously working) Magento installation's admin page was no longer working. Obviously, paid orders cannot be processed. So it's pretty serious, to say the least.

Stack Overflow gave me the solution, but it's buried pretty deep down, so I'm copy-pasting for posterity, from [http://stackoverflow.com/questions/18724995/magento-404-on-admin-page](http://stackoverflow.com/questions/18724995/magento-404-on-admin-page):

> One common cause for this behavior is an invalid value (or no value at all) being set for a custom admin path. Since you can't access the admin, try running the following SQL query. If you see results similar to the above, or admin/url/custom_path is blank/not-present but admin/url/use_custom_path is still 1 — then that's your problem.

Hope this helps someone else out there then.
