---
title: Cleaning up Oracle SYS_EXPORT_SCHEMA_xx jobs
date: 2017-10-09T08:47:33+00:00
---

Sometimes `expdp` jobs fail for any number of reasons. Re-running the tool, I noticed that the number had increased since the prior run; e.g., `SYS_EXPORT_SCHEMA_02` instead of `SYS_EXPORT_SCHEMA_01`. As it turns out, these are potentially orphaned jobs, so clean 'em up!

Generally, copied from Anar Godjaev's [excellent blog post](https://anargodjaev.wordpress.com/2013/12/17/how-to-cleanup-orphaned-datapump-jobs-from-dba_datapump_jobs/):

```text
SQL> select owner_name, job_name, operation, job_mode, state, attached_sessions from dba_datapump_jobs;

SQL> drop table {owner_name}.SYS_EXPORT_SCHEMA_01;
SQL> purge table {owner_name}.SYS_EXPORT_SCHEMA_01;
```
