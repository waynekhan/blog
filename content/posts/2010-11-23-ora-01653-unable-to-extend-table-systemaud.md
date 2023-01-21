---
title: ORA-01653 unable to extend table SYSTEM.AUD$
date: 2010-11-23T09:02:04+00:00
---

This set of commands helped me resolve this error quickly. First we need to find out the path to the appropriate datafile(s):

```text
$ sqlplus sys as sysdba
SQL> select name from v$datafile where name like '%system%';

NAME
--------------------------------------------------------------------------------
/oradata/foo/system01.dbf

1 rows selected.
```

There's only one datafile, so we'll need to check if `/oradata` has free disk space; e.g.,

```text
$ df -h
Filesystem Size Used Avail Use% Mounted on
/dev/sda1  50G  47G  2.0M  100% /
/dev/sdg   50G  32G  16G   67%  /mnt/sdg
```

Per the Use% column, `/dev/sda1` is full while `/dev/sdg` isn't, so create a new datafile while logged in as `sys`; e.g.,

```text
SQL> alter tablespace system add datafile '/mnt/sdg/oradata/foo/system02.dbf' size 1g;
```