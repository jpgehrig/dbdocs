## 1.15 APPROX_FOR_PERCENTILE

`APPROX_FOR_PERCENTILE` converts exact percentile functions to their approximate percentile function counterparts.

| Property            | Description                                                                                                                                                      |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | String                                                                                                                                                           |
| Syntax              | `APPROX_FOR_PERCENTILE = { NONE | PERCENTILE_CONT | PERCENTILE_CONT DETERMINISTIC | PERCENTILE_DISC | PERCENTILE_DISC DETERMINISTIC | ALL | ALL DETERMINISTIC }` |
| Default value       | `none`                                                                                                                                                           |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`                                                                                                                                  |
| Modifiable in a PDB | Yes                                                                                                                                                              |
| Basic               | No                                                                                                                                                               |
| Oracle RAC          | Different instances can use different values.                                                                                                                    |

Approximate percentile function queries are faster than their exact percentile function query counterparts, so they can be useful in situations where a tolerable amount of error is acceptable in order to obtain faster query results.

The values that can be set are:

- `NONE`:

  No queries are converted. This is the default value.

- `PERCENTILE_CONT`:

  Converts `PERCENTILE_CONT` queries to `APPROX_PERCENTILE` queries.

- `PERCENTILE_CONT DETERMINISTIC`:

  Converts `PERCENTILE_CONT` queries to `APPROX_PERCENTILE DETERMINSTIC` queries.

- `PERCENTILE_DISC`:

  Converts `PERCENTILE_DISC` queries to `APPROX_PERCENTILE` queries.

- `PERCENTILE DISC DETERMINISTIC`:

  Converts `PERCENTILE_DISC` queries to `APPROX_PERCENTILE DETERMINISTIC` queries.

- `ALL`:

  Converts both `PERCENTILE_CONT` queries and `PERCENTILE_DISC` queries to `APPROX_PERCENTILE` queries.

- `ALL DETERMINISTIC`:

  Converts both `PERCENTILE_CONT` and `PERCENTILE_DISC` queries to `APPROX_PERCENTILE DETERMINISTIC` queries.

**See Also:**

- "[APPROX_FOR_AGGREGATION](APPROX_FOR_AGGREGATION.md)"

- "[APPROX_FOR_COUNT_DISTINCT](APPROX_FOR_COUNT_DISTINCT.md)"

- [Oracle Database SQL Language Reference](../sqlrf/APPROX_MEDIAN.md) for information about `APPROX_MEDIAN` aggregate functions

- [Oracle Database SQL Language Reference](../sqlrf/APPROX_PERCENTILE.md) for information about `APPROX_PERCENTILE` aggregate functions
