## 1.139 HEAT_MAP

Use `HEAT_MAP` to enable or disable both the Heat Map and Automatic Data Optimization (ADO) features.

| Property            | Description                                       |
|:--------------------|:--------------------------------------------------|
| Parameter type      | String                                            |
| Syntax              | `HEAT_MAP = { ON | OFF }`                         |
| Default value       | `OFF`                                             |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`                   |
| Modifiable in a PDB | Yes                                               |
| Basic               | No                                                |
| Oracle RAC          | If specified, use the same value on all instances |

Setting the `HEAT_MAP` initialization parameter to `ON` causes the database to track read and write access of all segments, as well as modification of database blocks, due to DMLs and DDLs. These activities are not tracked for objects in the `SYSTEM` and `SYSAUX` tablespaces.

**See Also:**

- [Oracle Database VLDB and Partitioning Guide](../vldbg/ilm-strategy-heatmap-ado.md) for more information about enabling and disabling the Heat Map feature

- [Oracle Database VLDB and Partitioning Guide](../vldbg/ilm-strategy-heatmap-ado.md) for more information about Heat Map tracking
