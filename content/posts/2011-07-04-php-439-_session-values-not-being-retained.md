---
title: PHP 4.3.9 $_SESSION values not being retained
date: 2011-07-04T04:08:40+00:00
---

Problem: After calling `session_start()` and assigning key-value pairs to the `$_SESSION` array, calling `print_r($_SESSION)` subsequently don't work.

Solution: Assuming your php.ini session `save_handler`, `save_path` variables are set correctly, also check for free disk space.

I spent 90 minutes trying to resolve the problem thinking it was a PHP-related issue, but in the end, nullifying the 5+ gigabytes of Apache error logs promptly resolved the problem. Doh!
