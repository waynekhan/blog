---
title: InnoDB transactions
date: 2016-03-01T03:07:35+00:00
---

Yesterday I updated the date column of **an entire table** meant for its subset only. The solution to this mistake was to recover from daily `mysqldump`, and filling in the gaps that were, thankfully, able to be filled in.

Writing in 2010, the author of the answer said:

> When something goes wrong, the only restoration option available is to reconstruct the data from a backup (providing one exists).

Here are two answers that I found useful; i.e., Stack Overflow, the gift(s) that keeps on giving:

## References

* [http://stackoverflow.com/questions/2950676/difference-between-set-autocommit-1-and-start-transaction-in-mysql-have-i-misse](http://stackoverflow.com/questions/2950676/difference-between-set-autocommit-1-and-start-transaction-in-mysql-have-i-misse)
* [http://stackoverflow.com/questions/5727827/update-one-mysql-table-with-values-from-another](http://stackoverflow.com/questions/5727827/update-one-mysql-table-with-values-from-another)
