## 1.260 OPTIMIZER_USE_PENDING_STATISTICS

`OPTIMIZER_USE_PENDING_STATISTICS` specifies whether the optimizer uses pending statistics when compiling SQL statements.

| Property            | Description                     |
|:--------------------|:--------------------------------|
| Parameter type      | Boolean                         |
| Default value       | `false`                         |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM` |
| Modifiable in a PDB | Yes                             |
| Range of values     | `true | false`                  |
| Basic               | No                              |

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/controlling-the-use-of-optimizer-statistics.md) for more information on setting this parameter
