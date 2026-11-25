## 1.267 PARALLEL_DEGREE_LIMIT

`PARALLEL_DEGREE_LIMIT` limits the degree of parallelism used by the optimizer to ensure that parallel server processes do not flood the system.

| Property            | Description                                                 |
|:--------------------|:------------------------------------------------------------|
| Parameter type      | String                                                      |
| Syntax              | `PARALLEL_DEGREE_LIMIT = { CPU | AUTO | IO | ``integer`` }` |
| Default value       | `CPU`                                                       |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`                             |
| Modifiable in a PDB | Yes                                                         |
| Basic               | No                                                          |

With automatic degree of parallelism, Oracle automatically decides whether a statement should execute in parallel and what degree of parallelism the statement should use. The optimizer automatically determines the degree of parallelism for a statement based on the resource requirements of the statement. However, `PARALLEL_DEGREE_LIMIT` enforces the limit for the degree of parallelism used by the optimizer.

### Values

- `CPU`

  The maximum degree of parallelism is limited by the number of CPUs in the system. The formula used to calculate the limit is `PARALLEL_THREADS_PER_CPU` \* `CPU_COUNT` \* the number of instances available (by default, all the opened instances on the cluster but can be constrained using `PARALLEL_INSTANCE_GROUP` or service specification). This is the default.

- `AUTO`

  This value is equivalent to the `CPU` value.

- `IO`

  The maximum degree of parallelism the optimizer can use is limited by the I/O capacity of the system. The value is calculated by dividing the total system throughput by the maximum I/O bandwidth per process. You must run the `DBMS_RESOURCE_MANAGER.CALIBRATE_IO` procedure on the system to use the `IO` setting. This procedure will calculate the total system throughput and the maximum I/O bandwidth per process.

- `integer`

  A numeric value for this parameter specifies the maximum degree of parallelism the optimizer can choose for a SQL statement when automatic degree of parallelism is active. Automatic degree of parallelism is only enabled if `PARALLEL_DEGREE_POLICY` is set to `ADAPTIVE`, `AUTO`, or `LIMITED`.

**See Also:**

- [Oracle Database VLDB and Partitioning Guide](../vldbg/degree-parallel.md) for information about automatic degree of parallelism

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RESOURCE_MANAGER.md) for information on the `DBMS_RESOURCE_MANAGER.CALIBRATE_IO` procedure
