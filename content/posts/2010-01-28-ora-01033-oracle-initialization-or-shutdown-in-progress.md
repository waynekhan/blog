---
title: ORA-01033 ORACLE initialization or shutdown in progress
date: 2010-01-28T05:00:48+00:00
---

Encountered this issue todya/

The verbiage indicates that Oracle is starting up (or down), but waiting doesn't work.


```text
sqlplus sys/xxxxxxx as sysdba
```

Replace the 'xxxxxxx' part with your actual password. If `sqlplus` command is not found, it's probably a problem with your environment variables, but that's another can of worms altogether. Let's see whether the db can be mounted:

```text
SQL> alter database mount;
ERROR at line 1:
ORA-01100: database already mounted
```

OK, so the database needs to be opened too, whatever that means:

```text
SQL> alter database open;
ERROR at line 1:
ORA-01113: file 1 needs media recovery
```

OK let's try to recover from this:

```text
ORA-01110: data file 1: '/usr/lib/oracle/xe/oradata/XE/system.dbf'
SQL> recover datafile '/usr/lib/oracle/xe/oradata/XE/system.dbf'
Media recovery complete.
SQL> alter database open;
Database altered.
SQL> quit
Disconnected from Oracle Database 10g Express Edition Release 10.2.0.1.0 - Production
```

Hope this helps then.