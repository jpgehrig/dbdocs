## 1.103 DDL_LOCK_TIMEOUT

`DDL_LOCK_TIMEOUT` specifies a time limit for how long DDL statements will wait in a DML lock queue.

| Property            | Description                     |
|:--------------------|:--------------------------------|
| Parameter type      | Integer                         |
| Default value       | `0`                             |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM` |
| Modifiable in a PDB | Yes                             |
| Range of values     | 0 to 1,000,000 (in seconds)     |
| Basic               | No                              |

A value of zero indicates a status of `NOWAIT`. The maximum value of 1,000,000 seconds will result in the DDL statement waiting forever to acquire a DML lock.

If a lock is not acquired before the timeout period expires, then an error is returned.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md) for more information about the `DDL_LOCK_TIMEOUT` parameter

- [Oracle Database Development Guide](../adfns/sql-processing-for-application-developers.md) for information about nonblocking and blocking DDL
