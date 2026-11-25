## 1.245 OPTIMIZER_ADAPTIVE_STATISTICS

`OPTIMIZER_ADAPTIVE_STATISTICS` controls adaptive statistics. Some query shapes are too complex to rely on base table statistics alone, so the optimizer augments these statistics with adaptive statistics.

| Property            | Description                                 |
|:--------------------|:--------------------------------------------|
| Parameter type      | Boolean                                     |
| Default value       | `false`                                     |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`             |
| Modifiable in a PDB | Yes                                         |
| Range of values     | `true | false`                              |
| Basic               | No                                          |
| Oracle RAC          | The same value must be set on all instances |

Setting this parameter to `false` disables the following adaptive features:

- SQL plan directives

- Statistics feedback for joins

- Adaptive dynamic sampling for parallel execution

**Note:**

Setting `OPTIMIZER_ADAPTIVE_STATISTICS` to `false` preserves the statistics feedback functionality that was introduced in Oracle Database 11g.

`OPTIMIZER_ADAPTIVE_STATISTICS` does not control the creation of SQL plan directives. SQL plan directives will be created even if this parameter is `false`, but they will not be used to refine SQL execution plans with dynamic sampling.

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/query-optimizer-concepts.md) for information about adaptive plans
