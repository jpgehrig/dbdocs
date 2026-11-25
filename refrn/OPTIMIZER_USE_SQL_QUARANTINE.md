## 1.262 OPTIMIZER_USE_SQL_QUARANTINE

`OPTIMIZER_USE_SQL_QUARANTINE` determines whether the optimizer considers SQL Quarantine configurations when choosing an execution plan for a SQL statement.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | Boolean                                       |
| Default value       | `true`                                        |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`               |
| Modifiable in a PDB | Yes                                           |
| Range of values     | `true | false`                                |
| Basic               | No                                            |
| Oracle RAC          | Different instances can use different values. |

Values:

- `true`

  The optimizer considers SQL Quarantine configurations when choosing an execution plan for a SQL statement. The statement will be terminated if it would otherwise use a quarantined execution plan.

- `false`

  The optimizer ignores SQL Quarantine configurations when choosing an execution plan for a SQL statement. It may use any execution plan, regardless of its quarantine status.

**Note:**

This parameter is available on Oracle Autonomous Database starting with Oracle Database 19c. It is available on other types of Oracle databases starting with Oracle Database 19c, Release Update 19.27.

**See Also:**

- "[DBA_SQL_QUARANTINE](DBA_SQL_QUARANTINE.md)"

- "[OPTIMIZER_CAPTURE_SQL_QUARANTINE](OPTIMIZER_CAPTURE_SQL_QUARANTINE.md)"

- [Oracle Database SQL Tuning Guide](../tgsql/query-optimizer-concepts.md) for more information about SQL Quarantine
