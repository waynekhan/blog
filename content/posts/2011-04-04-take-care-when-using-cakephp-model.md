---
title: Take care when using CakePHP Model methods
date: 2011-04-04T06:43:40+00:00
---

Fixed a subtle bug in our code recently:

```php
$options = array(); // method params
$this->Foo->id = 'bar';
$this->Foo->baz($options);
```

Setting `->id` is fairly handy, but unexpected results occur when used in conjunction with `->find()` and `->del()`; e.g.,

```text
$options = array('contain' => array());
$this->Foo->id = 'bar';
$this->Foo->find('first', $options)); // BUG
```
Now for `->del()`:

```text
$this->Foo->id = 'bar';
$this->Foo->del(); // BUG
```

This is especially bad behavior when deleting a record, so take care to inspect the query log -- we use Oracle 11g Release 2 here.
