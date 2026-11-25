## 1.300 RECOVERY_PARALLELISM

`RECOVERY_PARALLELISM` specifies the number of processes to participate in instance or crash recovery.

| Property            | Description                                                                                  |
|:--------------------|:---------------------------------------------------------------------------------------------|
| Parameter type      | Integer                                                                                      |
| Default value       | System-determined parallel recovery                                                          |
| Modifiable          | `ALTER SYSTEM`                                                                               |
| Modifiable in a PDB | No                                                                                           |
| Range of values     | System-determined, but cannot exceed `PARALLEL_MAX_SERVERS` initialization parameter setting |
| Basic               | No                                                                                           |

To force serial crash and instance recovery, set the `RECOVERY_PARALLELISM` parameter to 0 or 1. 0 or 1 disable parallel instance and crash recovery on a system that has multiple CPUs. An alert log displays the degree of parallelism that was chosen when the database instance/recovery starts.

**See Also:**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/managing-backup-and-recovery.md) for information on setting this parameter in an Oracle RAC environment
