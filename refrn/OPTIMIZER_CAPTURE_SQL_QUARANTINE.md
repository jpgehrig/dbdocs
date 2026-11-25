## 1.247 OPTIMIZER_CAPTURE_SQL_QUARANTINE

`OPTIMIZER_CAPTURE_SQL_QUARANTINE` enables or disables the automatic creation of SQL Quarantine configurations.

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

  Enables the automatic creation of SQL Quarantine configurations. If the Resource Manager terminates a SQL statement because the statement has exceeded resource limits, then the database automatically creates a SQL Quarantine configuration for the execution plan used by the terminated SQL statement. Note that the plan for a terminated SQL statement is quarantined, not the statement itself.

- `false`

  Disables the automatic creation of SQL Quarantine configurations.

**Note:**

This parameter is available on Oracle Autonomous Database starting with Oracle Database 19c. It is available on other types of Oracle databases starting with Oracle Database 19c, Release Update 19.27.

**See Also:**

- "[DBA_SQL_QUARANTINE](DBA_SQL_QUARANTINE.md)"

- "[OPTIMIZER_USE_SQL_QUARANTINE](OPTIMIZER_USE_SQL_QUARANTINE.md)"

- [Oracle Database SQL Tuning Guide](../tgsql/query-optimizer-concepts.md) for more information about SQL Quarantine
