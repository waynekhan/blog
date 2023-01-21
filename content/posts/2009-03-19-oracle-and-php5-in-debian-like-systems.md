---
title: Oracle and PHP5 in Debian-like systems
date: 2009-03-19T02:46:20+00:00
---

[This post](http://remorse.nl/weblog/debian_oracle_xe_and_php5/) helped me install Oracle XE on my developer machine successfully! It worked for my Debian Lenny system previously, and I've personally verified it to work with MEPIS 8.0, Ubuntu 9.04 and Linux Mint 7, Linux Mint 8 and Xubuntu 10.04.

### Oracle Express Edition (XE)

This step is optional if you already have an Oracle server to use, but in my experience, it's far better to have one setup locally.

Add the following repository to your apt sources:

```text
deb http://oss.oracle.com/debian unstable main non-free
```

Install Oracle XE:

```text
wget http://oss.oracle.com/el4/RPM-GPG-KEY-oracle -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install oracle-xe-universal
```

It's a pretty big download (~260 MB). The installation, like most in Debian systems, is a breeze. When the installer completes there is one extra step:

```text
sudo /etc/init.d/oracle-xe configure
```

You'll be asked to create a system/sys (administrative user) password, and whether or not to start Oracle on boot.

## Oracle Instant Client

You can skip this step if Step 1 was completed. Instant Client is required only if Oracle XE is unavailable.

Downloaded the RPMs from [here](http://www.oracle.com/technology/software/tech/oci/instantclient/htdocs/linuxsoft.html). You'll need the `basic` and `devel` packages for Linux. Once the download is complete, use `alien` to convert the `.rpm` into a `.deb` package; e.g.,

```text
sudo apt-get install alien

# Converting and installing RPMs
sudo alien oracle*.rpm
sudo dpkg -i oracle*.deb
```

## OCI8 Static Object

This step is required for Oracle/PHP to play nice.

```text
sudo apt-get install php-pear php5-dev
sudo pecl install oci8
```

At some point, you'll be prompted to input ORACLE_HOME. If Oracle XE is installed, enter `/usr/lib/oracle/xe/app/oracle/product/10.2.0/server`.

Otherwise enter `instantclient,/usr/lib/oracle/11.2/client/lib`.

## oci8.so

Save a new file as `/etc/php5/conf.d/oci8.ini`. Add the text `extension=oci8.so`, so that it becomes available everywhere.

#### Restart Apache

```text
sudo /etc/init.d/apache2 restart
```
