## 1.266 PARALLEL_ADAPTIVE_MULTI_USER

`PARALLEL_ADAPTIVE_MULTI_USER`, when set to `true`, enables an adaptive algorithm designed to improve performance in multiuser environments that use parallel execution.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Boolean        |
| Default value       | `false`        |
| Modifiable          | `ALTER SYSTEM` |
| Modifiable in a PDB | No             |
| Range of values     | `true | false` |
| Basic               | No             |

The algorithm automatically reduces the requested degree of parallelism based on the system load at query startup time. The effective degree of parallelism is based on the default degree of parallelism, or the degree from the table or hints, divided by a reduction factor.

The algorithm assumes that the system has been tuned for optimal performance in a single-user environment.

Tables and hints use the default degree of parallelism.

**Note:**

The `PARALLEL_ADAPTIVE_MULTI_USER` initialization parameter is deprecated in Oracle Database 12c Release 2 (12.2.0.1) and may be removed in a future release. Oracle recommends that you use the parallel statement queuing feature instead.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/Comments.md) for more information about optimizer hints

- [Oracle Database VLDB and Partitioning Guide](../vldbg/about-parallel-queuing.md) for more information about parallel statement queuing
