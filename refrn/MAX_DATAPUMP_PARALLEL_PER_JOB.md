## 1.197 MAX_DATAPUMP_PARALLEL_PER_JOB

`MAX_DATAPUMP_PARALLEL_PER_JOB` specifies the maximum number of parallel processes allowed per Oracle Data Pump job.

| Property            | Description                                              |
|:--------------------|:---------------------------------------------------------|
| Parameter type      | String                                                   |
| Syntax              | `MAX_DATAPUMP_PARALLEL_PER_JOB = { ``integer`` | AUTO }` |
| Default value       | `50`                                                     |
| Range of values     | `1` to `1024`, or `AUTO`                                 |
| Modifiable          | `ALTER SYSTEM`                                           |
| Modifiable in a PDB | Yes                                                      |
| Basic               | No                                                       |
| Oracle RAC          | Different instances can use different values.            |

When this parameter has a value of `AUTO`, Oracle Data Pump derives its value to be 50 percent of the value of the `SESSIONS` initialization parameter.

**Note:**

This parameter is available starting with Oracle Database 19c, Release Update 19.1.
