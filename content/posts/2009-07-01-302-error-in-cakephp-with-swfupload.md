---
title: 302 error in CakePHP with SWFUpload
date: 2009-07-01T15:15:43+00:00
---

I encountered this issue in a recent project.

Basically I use SWFUpload to post files to a CakePHP controller. It worked beautifully, until I removed this one line in `beforeFilter()`:

```php
$this->Auth->allow("swfupload");
```

I was using the Auth component, and without the line above to allow unauthenticated access to the controller action, then we have a problem.

Hope this helps somebody then.