---
title: CakePHP database connection "Sqlite" is missing, or could not be created
date: 2012-04-25T01:53:12+00:00
---

Just downloaded [2.1.1 stable](https://github.com/cakephp/cakephp/zipball/2.1.1) to read a SQLite database.

There's a nice diagnostics page to welcome any developer, except it complained about my [database config](stackoverflow.com/questions/8035314/using-sqlite3-with-cakephp-2-0); e.g.,

> Database connection "Sqlite" is missing, or could not be created.

I thought it might've been a missing driver, or something, so I looked in `lib/Cake/Model/Datasource/Database/`; e.g.,

```text
-rw-rw-r-- 1 waynekhan waynekhan 20K 2012-03-25 18:30 Mysql.php
-rw-rw-r-- 1 waynekhan waynekhan 25K 2012-03-25 18:30 Postgres.php
-rw-rw-r-- 1 waynekhan waynekhan 16K 2012-03-25 18:30 Sqlite.php
-rw-rw-r-- 1 waynekhan waynekhan 23K 2012-03-25 18:30 Sqlserver.php
```

So it turns out additional stuff is required for PHP to talk to SQLite. If you're on Oneiric Ocelot (11.10), you're in luck. The package name is `php5-sqlite`; e.g.,

```text
sudo apt-get install php5-sqlite -y
sudo /etc/init.d/apache2 restart
```

Once that is done, use `:memory:` for the database param to make sure that the server setup is OK.

Lastly, adjust the filename of the database file; e.g. mine is `app/webroot/trac.db`, so I simply say `trac.db`. Once this is done, you may encounter another error:

> Database connection "SQLSTATE[HY000] [14] unable to open database file" is missing, or could not be created.

This is due to file permissions, so check if the `www-data` group owns `trac.db`; e.g.,

```text
drwxr-xr-x 6 waynekhan www-data 4.0K 2012-04-25 10:46 .
-rw-rw---- 1 waynekhan www-data 12M 2012-04-24 18:45 trac.db
```
