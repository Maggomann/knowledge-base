---
category: wiki
sub_category_1: mysql
sub_category_2: commands
language: en
tags:
- wiki
- mysql
- commands
---

## Maximum number of concurrent connections

In MySQL, you can determine the maximum number of concurrent connections with the following query:

```sql
SHOW VARIABLES LIKE 'max_connections';
```

This query returns the maximum limit for the number of connections that can access the MySQL server at the same time. However, note that this limit depends on the configuration of the MySQL server and does not necessarily correspond to the actual number of concurrent transactions that can be executed.

## Current number of connections

To display the current number of connections accessing the MySQL server at a given time, you can use the following query:

```sql
SHOW STATUS WHERE `variable_name` = 'Threads_connected';
```

This query returns the number of active connections accessing the MySQL server. However, note that the number of connections can fluctuate as connections are opened and closed while the database is in use.
