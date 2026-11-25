## 1.243 OPTIMIZER_ADAPTIVE_PLANS

`OPTIMIZER_ADAPTIVE_PLANS` controls adaptive plans. Adaptive plans are execution plans built with alternative choices that are decided at run time based on statistics collected as the query executes.

| Property            | Description                                 |
|:--------------------|:--------------------------------------------|
| Parameter type      | Boolean                                     |
| Default value       | `true`                                      |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`             |
| Modifiable in a PDB | Yes                                         |
| Range of values     | `true | false`                              |
| Basic               | No                                          |
| Oracle RAC          | The same value must be set on all instances |

Setting this parameter to `false` disables the following adaptive features:

- Nested loop join/hash join selection

- Star transformation bitmap pruning

- Adaptive parallel distribution method

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/query-optimizer-concepts.md) for information about adaptive plans
