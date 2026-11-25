## 1.248 OPTIMIZER_DYNAMIC_SAMPLING

`OPTIMIZER_DYNAMIC_SAMPLING` controls both when the database gathers dynamic statistics, and the size of the sample that the optimizer uses to gather the statistics.

| Property            | Description                                                                                                                                                                                                |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | Integer                                                                                                                                                                                                    |
| Default value       | If `OPTIMIZER_FEATURES_ENABLE` is set to `10.0.0` or higher, then `2`<br>If `OPTIMIZER_FEATURES_ENABLE` is set to `9.2.0`, then `1`<br>If `OPTIMIZER_FEATURES_ENABLE` is set to `9.0.1` or lower, then `0` |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`                                                                                                                                                                            |
| Modifiable in a PDB | Yes                                                                                                                                                                                                        |
| Range of values     | `0` to `11`                                                                                                                                                                                                |
| Basic               | No                                                                                                                                                                                                         |

**Note:**

Dynamic statistics were called dynamic sampling in releases earlier than Oracle Database 12c Release 1 (12.1).

If the value of `OPTIMIZER_DYNAMIC_SAMPLING` is set to `11`, the `OPTIMIZER_FEATURES_ENABLE` setting has no effect on the `OPTIMIZER_DYNAMIC_SAMPLING` setting.

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/options-for-optimizer-statistics-gathering.md) for detailed information about the values (0 – 11) that can be set for the `OPTIMIZER_DYNAMIC_SAMPLING` parameter.
