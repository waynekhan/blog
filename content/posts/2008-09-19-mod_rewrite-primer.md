---
title: Mod_rewrite primer
date: 2008-09-19T09:34:31+00:00
---

I've had to write a number of `.htaccess` files over the past week or so. My uses of `mod_rewrite` are simple enough, but I thought to post here since there in case anybody just wants to accomplish something quickly. Ask your system administrator to set the `AllowOverride` property to `FileInfo` or `All`, otherwise these overrides won't work.

```text
RewriteEngine On
RewriteRule ^(.*)$ https://blog.waynekhan.net/ [R=301,L]
```

Permanent (301) redirect `some_page.html`:

```text
RewriteEngine On
RewriteCond %{REQUEST_URI} ^/some_page.html
RewriteRule ^(.*)$ https://blog.waynekhan.net/posts/2008-09-10-mod-rewrite-primer/ [R=301,L]
```

That's all, folks!