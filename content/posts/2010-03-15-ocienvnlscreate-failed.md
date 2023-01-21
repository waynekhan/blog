---
title: OCIEnvNlsCreate() failed
date: 2010-03-15T02:44:23+00:00
---

Wanted to work on an Oracle-backed project from home last weekend; e.g.,

```text
Warning (2): ocilogon() [function.ocilogon]: OCIEnvNlsCreate() failed. There is something wrong with your system - please check that ORACLE_HOME and LD_LIBRARY_PATH are set and point to the right directories [CORE/cake/libs/model/datasources/dbo/dbo_oracle.php, line 171]
```

`ORACLE_HOME` and `LD_LIBRARY_PATH` are environment variables I'd defined in my `~/.bashrc`; e.g.,

```text
. /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle_env.sh
```

And `phpinfo()` seems to suggest that it's OK:

```text
OCI8 Support enabled
Version 1.4.1
Revision $Revision: 293235 $
Active Persistent Connections 0
Active Connections 0
Compile-time ORACLE_HOME /usr/lib/oracle/xe/app/oracle/product/10.2.0/server
Libraries Used -Wl,-rpath,/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/lib -L/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/lib -lclntsh
Temporary Lob support enabled
Collections support enabled
```

Except it isn't. The fix is in `/etc/apache2/envvars`; e.g.,

```text
export ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
export LD_LIBRARY_PATH=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/lib:
```

My journey with Oracle Database has been rocky. I wonder why this is so... inaccessible.