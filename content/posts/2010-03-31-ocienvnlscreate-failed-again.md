---
title: OCIEnvNlsCreate() failed again
date: 2010-03-31T08:19:36+00:00
---

I encountered [OCIEnvNlsCreate() failed]({{< ref "2010-03-15-ocienvnlscreate-failed">}}) again, this time on Fedora 12.

I was looking for that same file to export environment variables -- Apache's `SetEnv` directive does not work -- and there is no equivalent of `/etc/apache2/envvars` as far as I can tell.

Many others seem to have encountered this same problem before, but never found the solution. Eventually I did, [in an Oracle-hosted article](http://www.oracle.com/technology/tech/php/htdocs/inst_php_apache_linux.html) about Oracle, PHP and Linux.

It's not called out explicitly, so here's my go at it: insert the call to `oracle_env.sh` somewhere in `/etc/init.d/httpd`; e.g., mine are above the `start()` function definition; e.g.,

```text
. /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle_env.sh
```

And the `oracle_env.sh` file itself should be like so (or similar):

```sh
ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
export ORACLE_HOME
ORACLE_SID=XE
export ORACLE_SID
NLS_LANG=`$ORACLE_HOME/bin/nls_lang.sh`
export NLS_LANG
PATH=$ORACLE_HOME/bin:$PATH
export PATH
if [ $?LD_LIBRARY_PATH ]
then
    LD_LIBRARY_PATH=$ORACLE_HOME/lib:$LD_LIBRARY_PATH
else
    LD_LIBRARY_PATH=$ORACLE_HOME/lib
fi
export LD_LIBRARY_PATH
```

Save your update (to `httpd`), restart the server, and it should be good then.