---
title: CakePHP, MongoDB primer
date: 2010-12-14T02:59:42+00:00
---

First you'll need MongoDB Server running on your system. It's easy on Debian/Ubuntu.

Add 10gen's package source to your `/etc/apt/sources.lst`. This one in particular is for Ubuntu Jaunty (9.4).

```text
deb http://downloads.mongodb.org/distros/ubuntu 9.4 10gen
```

Then download and install `mongodb-stable`; e.g.,

```text
sudo apt-get update
sudo apt-get install mongodb-stable
```

`ps` should something like so:

```text
$ ps -aef | grep mongodb
.
.
.
mongodb 8322 1 2 17:49 ? 00:02:59 /usr/bin/mongod --dbpath /var/lib/mongodb --logpath /var/log/mongodb/mongodb.log run --config /etc/mongodb.conf
```

To access a MongoDB database/collection in PHP, you'll need PECL's package; e.g., `pecl install mongo`.

Remember to add `extension=mongo.so` somewhere in your `php.ini` file; e.g., create a separate `/etc/php5/conf.d/mongo.ini` as you like.

You'll also need a CakePHP-specific MongoDB plugin; e.g.,

```text
cd /your/path/to/cakephp/app/plugins
git clone https://github.com/ichikaway/cakephp-mongodb mongodb
```

Configure your `app/config/database.php` like so:

```php
var $mongo = array(
    'database' => 'someApp',
    'driver' => 'mongodb.mongodbSource',
    'host' => 'localhost',
    'port' => 27017
);
```

Your CakePHP model should have, at the very least:

```php
var $mongoSchema = array(
    'type' => 'string'),
    'created' => array('type' => 'date'),
    'modified' => array('type' => 'date')
);
var $useDbConfig = 'mongo';
```

Here's where CakePHP's scaffolding feature comes in handy to create, read, and update a row (or two).

Connect to the server using using the `mongo` cli, poke around a bit; e.g.,

```text
$ mongo
mongo> show dbs;
mongo> use someApp;
mongo> show collections;
mongo> db.somes.count();
```