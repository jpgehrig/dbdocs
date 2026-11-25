## 1.255 OPTIMIZER_MODE

`OPTIMIZER_MODE` establishes the default behavior for choosing an optimization approach for the instance.

| Property            | Description                                                                           |
|:--------------------|:--------------------------------------------------------------------------------------|
| Parameter type      | String                                                                                |
| Syntax              | `OPTIMIZER_MODE =`<br>` { FIRST_ROWS_[1 | 10 | 100 | 1000] | FIRST_ROWS | ALL_ROWS }` |
| Default value       | `ALL_ROWS`                                                                            |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`                                                       |
| Modifiable in a PDB | Yes                                                                                   |
| Basic               | No                                                                                    |

### Values

- `FIRST_ROWS_``n`

  The optimizer uses a cost-based approach and optimizes with a goal of best response time to return the first `n` rows (where `n` = 1, 10, 100, 1000).

- `FIRST_ROWS`

  The optimizer uses a mix of costs and heuristics to find a best plan for fast delivery of the first few rows.

  `FIRST_ROWS` is available for backward compatibility and plan stability; use `FIRST_ROWS_`n instead.

- `ALL_ROWS`

  The optimizer uses a cost-based approach for all SQL statements in the session and optimizes with a goal of best throughput (minimum resource use to complete the entire statement).

**See Also:**

- [Oracle Database SQL Tuning Guide](../tgsql/influencing-the-optimizer.md) for more information on setting this parameter

- [Oracle Database Concepts](../cncpt/sql.md) and [Oracle Database SQL Tuning Guide](../tgsql/query-optimizer-concepts.md) for more information about the optimizer
