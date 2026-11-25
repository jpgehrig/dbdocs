## 1.246 OPTIMIZER_CAPTURE_SQL_PLAN_BASELINES

`OPTIMIZER_CAPTURE_SQL_PLAN_BASELINES` enables or disables the automatic recognition of repeatable SQL statements, as well as the generation of SQL plan baselines for such statements.

| Property            | Description                     |
|:--------------------|:--------------------------------|
| Parameter type      | Boolean                         |
| Default value       | `false`                         |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM` |
| Modifiable in a PDB | Yes                             |
| Range of values     | `true | false`                  |
| Basic               | No                              |

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/introduction-to-sql-tuning.md) for more information about the optimizer
