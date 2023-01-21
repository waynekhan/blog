---
title: Subversion server repository migration
date: 2010-01-28T09:39:24+00:00
---

```text
svnadmin dump old_svn_repos --deltas > svnrepos.dmp
svnadmin create new_svn_repos
svnadmin load new_svn_repos < svnrepos.dmp
```