## 1.44 CLUSTER_DATABASE_INSTANCES

`CLUSTER_DATABASE_INSTANCES` is an Oracle RAC parameter that specifies the number of instances that are configured as part of the cluster database.

| Property            | Description                                                                                                                                |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | Integer                                                                                                                                    |
| Default value       | If `CLUSTER_DATABASE` is set to `false`, then `1`<br>If `CLUSTER_DATABASE` is set to `true`, the number of configured Oracle RAC instances |
| Modifiable          | No                                                                                                                                         |
| Modifiable in a PDB | No                                                                                                                                         |
| Range of values     | Any nonzero value                                                                                                                          |
| Basic               | No                                                                                                                                         |
| Oracle RAC          | Multiple instances should have the same value.                                                                                             |

You must set this parameter for every instance. Normally you should set this parameter to the number of instances in your Oracle RAC environment. A proper setting for this parameter can improve memory use.

**Note:**

The `CLUSTER_DATABASE_INSTANCES` parameter is deprecated in Oracle Database 19c, and may be desupported in a future release. Starting with Oracle Database 19c, the number of configurable Oracle RAC instances is derived from Oracle Clusterware.

**See Also:**

- [Oracle Database SQL Tuning Guide](../tgsql/generating-and-displaying-execution-plans.md) for more information about parallel execution

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/introduction-to-oracle-rac.md) for information on Oracle Real Application Clusters
