---
title: Using grep with Subversion
date: 2010-03-19T06:58:57+00:00
---

I use `grep` alot, but it false positives when searching in a Subversion working copy. So I'm using the `-r` flag to recursively search for the phrase `quick brown fox`:

```text
$ grep -r 'quick brown fox' *
app/controllers/users_controller.php: quick brown fox
app/controllers/.svn/text-base/users_controller.php.svn-base: quick brown fox
```

I don't really want a hit on anything in `.svn`, so exclude it like `--exclude-dir=.svn`.