## 1.261 OPTIMIZER_USE_SQL_PLAN_BASELINES

`OPTIMIZER_USE_SQL_PLAN_BASELINES` enables or disables the use of SQL plan baselines stored in SQL Management Base.

| Property            | Description                     |
|:--------------------|:--------------------------------|
| Parameter type      | Boolean                         |
| Default value       | `true`                          |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM` |
| Modifiable in a PDB | Yes                             |
| Range of values     | `true | false`                  |
| Basic               | No                              |

When enabled, the optimizer looks for a SQL plan baseline for the SQL statement being compiled. If one is found in SQL Management Base, then the optimizer will cost each of the baseline plans and pick one with the lowest cost.

**See Also:**

- [Oracle Database SQL Tuning Guide](../tgsql/overview-of-sql-plan-management.md) for information on enabling automatic initial plan capture

- [Oracle Database SQL Tuning Guide](../tgsql/managing-sql-plan-baselines.md) for information about configuring the capture and use of SQL plan baselines
