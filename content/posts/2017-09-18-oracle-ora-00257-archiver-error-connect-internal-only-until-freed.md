---
title: "Oracle: ORA-00257 archiver error. Connect internal only, until freed"
date: 2017-09-18T07:54:13+00:00
---

Work around for this issue is to increase the amount of space allocated to `db_recovery_file_dest`; e.g.,

```text
$ sqlplus sys as sysdba
SQL> show parameter db_recovery_file;
db_recovery_file_dest string /opt/oracle/flash_recovery_area
db_recovery_file_dest_size big integer 20G
```

Compare this with the output of 'du -sh'; e.g.,

```text
$ du -sh /opt/oracle/flash_recovery_area
21G /opt/oracle/flash_recovery_area
```

21 vs 20, so set it to something a bit bigger; e.g.,

```text
SQL> alter system set db_recovery_file_dest_size = 30G;
```

Extracted from this link on [Remedian.com](https://remidian.com/2012/04/fix-ora-00257-archiver-error-connect-internal-only-until-freed-in-oracle-11g/).
