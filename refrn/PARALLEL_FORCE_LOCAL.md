## 1.270 PARALLEL_FORCE_LOCAL

`PARALLEL_FORCE_LOCAL` controls parallel execution in an Oracle RAC environment.

| Property            | Description                     |
|:--------------------|:--------------------------------|
| Parameter type      | Boolean                         |
| Default value       | `false`                         |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM` |
| Modifiable in a PDB | Yes                             |
| Range of values     | `true | false`                  |
| Basic               | No                              |

By default, the parallel server processes selected to execute a SQL statement can operate on any or all Oracle RAC nodes in the cluster. By setting `PARALLEL_FORCE_LOCAL` to `true`, the parallel server processes are restricted so that they can only operate on the same Oracle RAC node where the query coordinator resides (the node on which the SQL statement was executed).

**See Also:**

[Oracle Database VLDB and Partitioning Guide](../vldbg/parameters-parallel-exec.md) for more information about this parameter
