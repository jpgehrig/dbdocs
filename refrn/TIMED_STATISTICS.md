## 1.364 TIMED_STATISTICS

`TIMED_STATISTICS` specifies whether statistics related to time are collected.

| Property            | Description                                                                                                              |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | Boolean                                                                                                                  |
| Default value       | If `STATISTICS_LEVEL` is set to `TYPICAL` or `ALL`, then `true`<br>If `STATISTICS_LEVEL` is set to `BASIC`, then `false` |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`                                                                                          |
| Modifiable in a PDB | Yes                                                                                                                      |
| Range of values     | `true | false`                                                                                                           |
| Basic               | No                                                                                                                       |

### Values

- `true`

  The statistics are collected and stored in trace files or displayed in the `V$SESSTATS` and `V$SYSSTATS` dynamic performance views.

- `false`

  The value of all time-related statistics is set to zero. This setting lets Oracle avoid the overhead of requesting the time from the operating system.

Starting with release 11.1.0.7.0, the value of the `TIMED_STATISTICS` parameter cannot be set to `false` if the value of `STATISTICS_LEVEL` is set to `TYPICAL` or `ALL`.

On some systems with very fast timer access, Oracle might enable timing even if this parameter is set to `false`. On these systems, setting the parameter to `true` can sometimes produce more accurate statistics for long-running operations.

**See Also:**

- [Oracle Database SQL Tuning Guide](../tgsql/performing-application-tracing.md) for more information on setting this parameter

- [Statistics Descriptions](statistics-descriptions.md) indicates which statistics depend on the setting of this parameter.
