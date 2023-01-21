---
title: "Creating a branch in Subversion"
date: 2010-03-18T02:16:07+00:00
---

Beginning at the root of your repository:


```

svn mkdir branches/wayne
cd branches/wayne
svn merge http://your.subversion.server/projectName/trunk
svn ci -m 'Issuing "svn merge http://your.subversion.server/projectName/trunk".'

```

