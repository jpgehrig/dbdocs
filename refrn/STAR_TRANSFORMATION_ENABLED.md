## 1.354 STAR_TRANSFORMATION_ENABLED

`STAR_TRANSFORMATION_ENABLED` determines whether a cost-based query transformation will be applied to star queries.

| Property            | Description                                                     |
|:--------------------|:----------------------------------------------------------------|
| Parameter type      | String                                                          |
| Syntax              | `STAR_TRANSFORMATION_ENABLED = { FALSE | TRUE | TEMP_DISABLE }` |
| Default value       | `FALSE`                                                         |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`                                 |
| Modifiable in a PDB | Yes                                                             |
| Basic               | Yes                                                             |

### Values

- `FALSE`

  The transformation will not be applied.

- `TRUE`

  The optimizer will consider performing a cost-based query transformation on the star query.

- `TEMP_DISABLE`

  The optimizer will consider performing a cost-based query transformation on the star query but will not use temporary tables in the star transformation.

**See Also:**

- [Oracle Database SQL Tuning Guide](../tgsql/influencing-the-optimizer.md) for information on enabling star queries
