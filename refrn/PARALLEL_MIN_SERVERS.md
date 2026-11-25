## 1.275 PARALLEL_MIN_SERVERS

`PARALLEL_MIN_SERVERS` is the number of parallel execution processes Oracle creates when the instance is started. These processes will be kept active to service parallel statements.

| Property            | Description                                          |
|:--------------------|:-----------------------------------------------------|
| Parameter type      | Integer                                              |
| Default value       | `CPU_COUNT * PARALLEL_THREADS_PER_CPU * 2`           |
| Modifiable          | `ALTER SYSTEM`                                       |
| Modifiable in a PDB | No                                                   |
| Range of values     | Default value to the value of `PARALLEL_MAX_SERVERS` |
| Basic               | No                                                   |
| Oracle RAC          | Multiple instances can have different values.        |

**Note:**

This parameter applies to parallel execution in exclusive mode as well as in an Oracle Real Application Clusters environment.

**Note:**

When the `PROCESSES` initialization parameter is set to a value that is lower than the documented default value for the `PARALLEL_MIN_SERVERS` parameter in the table above, the database sets the default value of `PARALLEL_MIN_SERVERS` to a value that is lower than the documented default value. The lower default value enables the database to start service processes and allows user processes to connect to the database.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-processes.md) for more information about parallel execution servers
