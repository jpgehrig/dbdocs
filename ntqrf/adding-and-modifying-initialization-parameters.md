If you use Advanced Replication, then certain parameter values must be added to the initialization parameter file, and others must be set to recommended values.

Table 5-4  Advanced Replication Initialization Parameters

| Parameter Name             | Recommended Value      | Site              |
|:---------------------------|:-----------------------|:------------------|
| `JAVA_POOL_SIZE`           | 50 MB                  | master            |
| `DISTRIBUTED_LOCK_TIMEOUT` | 300 seconds            | master            |
| `GLOBAL_NAMES`             | TRUE                   | master            |
| `OPEN_LINKS`               | 4                      | master            |
| `PROCESSES`                | Add 9 to current value | master            |
| `JOB_QUEUE-PROCESSES`      | 2                      | master            |
| `JOB_QUEUE_PROCESSES`      | 2                      | materialized view |

### Note

Depends on the number of n-way sites.

**Parent topic:** [About Advanced Replication on Windows](about-advanced-replication-on-windows.md)
