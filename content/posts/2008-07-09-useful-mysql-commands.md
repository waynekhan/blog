---
title: Useful MySQL commands
date: 2008-07-09T02:33:43+00:00
---

```text
# Set the auto_increment value (e.g. `id`) to one more the highest `id` value currently
alter table `foo` auto_increment=1;

# Show how MySQL will parse this query, including key (indices) used and any additional parameters
explain select * from `foo`;

# Show indices for the given table
show keys from `foo`;
```