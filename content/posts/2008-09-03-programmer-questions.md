---
title: Programmer questions
date: 2008-09-03T07:49:37+00:00
---

What is the output for the following 3 code snippets?

```php
// Snippet 1
$x = 3;
if (4 < $x) {
    print "The quick brown fox jumps over the lazy dog.";
} else {
    print "She sells seashells on the seashore.";
}

// Snippet 2
$x = 1;
$x = ++$x * 2;
print $x;

// Snippet 3
$x = 1;
$x = $x++ * 2;
print $x;
```