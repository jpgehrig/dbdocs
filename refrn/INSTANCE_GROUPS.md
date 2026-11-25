## 1.158 INSTANCE_GROUPS

Used with the `PARALLEL_INSTANCE_GROUP` parameter, `INSTANCE_GROUPS` lets you restrict parallel query operations to a limited number of instances.

| Property            | Description                                                |
|:--------------------|:-----------------------------------------------------------|
| Parameter type      | String                                                     |
| Syntax              | `INSTANCE_GROUPS = ``group_name`` [, ``group_name`` ] ...` |
| Default value       | There is no default value.                                 |
| Modifiable          | No                                                         |
| Modifiable in a PDB | No                                                         |
| Range of values     | One or more instance group names, separated by commas      |
| Basic               | No                                                         |
| Oracle RAC          | Multiple instances can have different values.              |

**Note:**

The `INSTANCE_GROUPS` parameter is deprecated. It is retained for backward compatibility only.

`INSTANCE_GROUPS` is an Oracle RAC parameter that you can specify only in parallel mode.

This parameter specifies one or more instance groups and assigns the current instance to those groups. If one of the specified groups is also specified in the `PARALLEL_INSTANCE_GROUP` parameter, then Oracle allocates query processes for a parallel operation from this instance.

**See Also:**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/workload-management-with-dynamic-database-services.md) for more information on parallel query execution in a Real Application Clusters environment

- "[PARALLEL_INSTANCE_GROUP](PARALLEL_INSTANCE_GROUP.md)"
