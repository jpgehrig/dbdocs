## 1.254 OPTIMIZER_INMEMORY_AWARE

`OPTIMIZER_INMEMORY_AWARE` enables or disables all of the optimizer cost model enhancements for in-memory.

| Property            | Description                             |
|:--------------------|:----------------------------------------|
| Parameter type      | Boolean                                 |
| Default value       | `true`                                  |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`         |
| Modifiable in a PDB | Yes                                     |
| Range of values     | `true | false`                          |
| Basic               | No                                      |
| Oracle RAC          | All instances should use the same value |

Setting the parameter to `false` causes the optimizer to ignore the in-memory property of tables during the optimization of SQL statements. This behavior can also be achieved by setting the `OPTIMIZER_FEATURES_ENABLE` initialization parameter to values lower than 12.1.0.2.

**See Also:**

- "[OPTIMIZER_FEATURES_ENABLE](OPTIMIZER_FEATURES_ENABLE.md)"

- [Oracle Database Concepts](../cncpt/sql.md) and [Oracle Database SQL Tuning Guide](../tgsql/query-optimizer-concepts.md) for more information about the optimizer
