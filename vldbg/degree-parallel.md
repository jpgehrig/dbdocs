The degree of parallelism (DOP) is the number of parallel execution servers associated with a single operation.

Parallel execution is designed to effectively use multiple CPUs. Oracle Database parallel execution framework enables you to either explicitly choose a specific degree of parallelism or to rely on Oracle Database to automatically control it.

This section contains the following topics:

- Manually Specifying the Degree of Parallelism

- Default Degree of Parallelism

- Automatic Degree of Parallelism

- Determining Degree of Parallelism in Auto DOP

- Controlling Automatic Degree of Parallelism

- Adaptive Parallelism

### 8.2.1 Manually Specifying the Degree of Parallelism

A specific degree of parallelism (DOP) can be requested from Oracle Database for both tables and indexes.

For example, you can set a fixed DOP at a table level with the following:

    ALTER TABLE sales PARALLEL 8;
    ALTER TABLE customers PARALLEL 4;

In this example, queries accessing just the `sales` table request a DOP of 8 and queries accessing the `customers` table request a DOP of 4. A query accessing both the `sales` and the `customers` tables is processed with a DOP of 8 and potentially allocates 16 parallel execution servers (because of the producer/consumer model). Whenever different DOPs are specified, Oracle Database uses the higher DOP.

You can also request a specific DOP by using statement level or object level parallel hints.

The DOP specified in the `PARALLEL` clause of a table or an index takes effect only when `PARALLEL_DEGREE_POLICY` is set to `MANUAL` or `LIMITED`.

The actual runtime DOP of a statement can be limited by Oracle Database Resource Manager.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/Comments.md) for information about hints for parallel processing

- [Oracle Database Administrator’s Guide](../admin/managing-resources-with-oracle-database-resource-manager.md) for more information about Oracle Database Resource Manager

### 8.2.2 Default Degree of Parallelism

If the `PARALLEL` clause is specified but no degree of parallelism (DOP) is listed, then the object gets the default DOP.

For example, you can set a table to the default DOP with the following SQL statement.

    ALTER TABLE sales PARALLEL;

Default parallelism uses a formula to determine the DOP based on the system configuration, as in the following:

- For a single instance, DOP = `PARALLEL_THREADS_PER_CPU x CPU_COUNT`

- For an Oracle RAC configuration, DOP = `PARALLEL_THREADS_PER_CPU x sum(CPU_COUNT)`

By default, `sum(CPU_COUNT)` is the total number of CPUs in the cluster. However, if you have used Oracle RAC services to limit the number of nodes across which a parallel operation can execute, then `sum(CPU_COUNT)` is the total number of CPUs across the nodes belonging to that service. For example, on a 4-node Oracle RAC cluster, with each node having 8 CPU cores and no Oracle RAC services, the default DOP would be 2 x (8+8+8+8) = 64.

You can also request the default DOP by using statement level or object level parallel hints.

The default DOP specified in the `PARALLEL` clause of a table or an index takes effect only when `PARALLEL_DEGREE_POLICY` is set to `MANUAL`.

The default DOP algorithm is designed to use maximum resources and assumes that the operation finishes faster if it can use more resources. Default DOP targets the single-user workload and it is not recommended in a multiuser environment.

The actual runtime DOP of a SQL statement can be limited by Oracle Database Resource Manager.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/Comments.md) for information about hints for parallel processing

- [Oracle Database Administrator’s Guide](../admin/managing-resources-with-oracle-database-resource-manager.md) for more information about Oracle Database Resource Manager

### 8.2.3 Automatic Degree of Parallelism

Automatic Degree of Parallelism (Auto DOP) enables Oracle Database to automatically decide if a statement should execute in parallel and what DOP it should use.

The following is a summary of parallel statement processing when Auto DOP is enabled.

1.  A SQL statement is issued.

2.  The statement is parsed and the optimizer determines the execution plan.

3.  The threshold limit specified by the `PARALLEL_MIN_TIME_THRESHOLD` initialization parameter is checked.

    1.  If the expected execution time is less than the threshold limit, the SQL statement is run serially.

    2.  If the expected execution time is greater than the threshold limit, the statement is run in parallel based on the DOP that the optimizer calculates, including factoring for any defined resource limitations.

### 8.2.4 Determining Degree of Parallelism in Auto DOP

With automatic degree of parallelism (DOP), the optimizer automatically determines the DOP for a statement based on the resource requirements of that statement.

The optimizer uses the cost of all scan operations, such as a full table scan or index fast full scan, and the cost of all CPU operations in the execution plan to determine the necessary DOP.

However, the optimizer limits the actual maximum DOP to ensure parallel execution servers do not overwhelm the system. This limit is set by the parameter `PARALLEL_DEGREE_LIMIT`. The default value for this parameter is `CPU`, which means the DOP is limited by the number of CPUs on the system (`PARALLEL_THREADS_PER_CPU` \* `sum(CPU_COUNT)`) also known as the default DOP. This default DOP ensures that a single user operation cannot overwhelm the system. By adjusting this parameter setting, you can control the maximum DOP the optimizer can choose for a SQL statement. The optimizer can further limit the maximum DOP that can be chosen if Oracle Database Resource Manager is used to limit the DOP.

**Note:**

The value `AUTO` for `PARALLEL_DEGREE_LIMIT` has the same functionality as the value `CPU`.

To calculate the cost of operations for a SQL statement, Auto DOP uses information about the hardware characteristics of the system. The hardware characteristics include I/O calibration statistics so these statistics should be gathered.

If I/O calibration is not run to gather the required statistics, a default calibration value is used to calculate the cost of operations and the DOP.

I/O calibration statistics can be gathered with the PL/SQL DBMS_RESOURCE_MANAGER.CALIBRATE_IO procedure. I/O calibration is a one-time action if the physical hardware does not change.

The DOP determined by the optimizer is shown in the notes section of an explain plan output, as shown in the following explain plan output, visible either using the explain plan statement or `V$SQL_PLAN`.

    EXPLAIN PLAN FOR
    SELECT SUM(AMOUNT_SOLD) FROM SH.SALES;

    PLAN TABLE OUTPUT
    Plan hash value: 1763145153

    ----------------------------------------------------------------------------------------------------------------------
    |Id| Operation              | Name     | Rows | Bytes| Cost (%CPU)| Time     | Pstart| Pstop|    TQ |IN-OUT| PQ Distrib |
    ------------------------------------------------------------------------------------------------------------------------
    | 0| SELECT STATEMENT       |          |     1|     4|     2   (0)| 00:00:01 |       |       |      |      |           |
    | 1|  SORT AGGREGATE        |          |     1|     4|            |          |       |      |       |      |           |
    | 2|   PX COORDINATOR       |          |      |      |            |          |       |      |       |      |           |
    | 3|    PX SEND QC (RANDOM) | :TQ10000 |     1|     4|            |          |       |      |  Q1,00| P->S | QC (RAND) |
    | 4|     SORT AGGREGATE     |          |     1|     4|            |          |       |      |  Q1,00| PCWP |           |
    | 5|      PX BLOCK ITERATOR |          |   960|  3840|     2   (0)| 00:00:01 |     1 |    16|  Q1,00| PCWC |           |
    | 6|       TABLE ACCESS FULL| SALES    |   960|  3840|     2   (0)| 00:00:01 |     1 |    16|  Q1,00| PCWP |           |
    ------------------------------------------------------------------------------------------------------------------------
    Note
    -----
       - automatic DOP: Computed Degree of Parallelism is 4

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RESOURCE_MANAGER.md) for information about the DBMS_RESOURCE_MANAGER package

### 8.2.5 Controlling Automatic Degree of Parallelism

There are several initialization parameters that control automatic degree of parallelism (auto DOP). These initialization parameters include `PARALLEL_DEGREE_POLICY`, `PARALLEL_DEGREE_LIMIT`, `PARALLEL_MIN_TIME_THRESHOLD`, and `PARALLEL_MIN_DEGREE`.

The initialization parameter `PARALLEL_DEGREE_POLICY` controls whether Auto DOP, parallel statement queuing, and in-memory parallel execution are enabled. This parameter has the following possible values:

- `MANUAL`

  This setting disables Auto DOP, parallel statement queuing and in-memory parallel execution. It reverts the behavior of parallel execution to what it was previous to Oracle Database 11g Release 2 (11.2), which is the default.

  With the default setting of `MANUAL` for `PARALLEL_DEGREE_POLICY`, the system only uses parallel execution when a DOP has been explicitly set on an object or if a parallel hint is specified in the SQL statement. The DOP used is exactly what was specified. No parallel statement queuing and in-memory parallel execution occurs.

- `LIMITED`

  This setting enables Auto DOP for some statements but parallel statement queuing and in-memory parallel execution are disabled. Automatic DOP is applied only to statements that access tables or indexes declared explicitly with the `PARALLEL` clause without an explicit DOP specified. Tables and indexes that have a DOP specified use that explicit DOP setting.

  If you want Oracle Database to automatically decide the DOP only for a subset of SQL statements that touch a specific subset of objects, then set `PARALLEL_DEGREE_POLICY` to `LIMITED` and set the parallel property without specifying an explicit DOP on that subset of objects.

- `AUTO`

  This setting enables Auto DOP for all statements, also enables parallel statement queuing and in-memory parallel execution.

  If you want Oracle Database to automatically decide the DOP for all SQL statements, then set `PARALLEL_DEGREE_POLICY` to `AUTO`.

- `ADAPTIVE`

  This setting enables Auto DOP, parallel statement queuing, and in-memory parallel execution, similar to the `AUTO` value. In addition, performance feedback is enabled.

The `PARALLEL_DEGREE_LIMIT` initialization parameter specifies the maximum DOP that Auto DOP can use systemwide. For a more fine grained control of the maximum DOP, you can use Oracle Database Resource Manager.

The `PARALLEL_MIN_TIME_THRESHOLD` initialization parameter specifies the minimum estimated execution time for a statement to be considered for Auto DOP. First the optimizer calculates a serial execution plan for the SQL statement. If the estimated execution time is greater than the value of `PARALLEL_MIN_TIME_THRESHOLD`, the statement becomes a candidate for Auto DOP.

The `PARALLEL_MIN_ DEGREE` initialization parameter controls the minimum degree of parallelism computed by automatic degree of parallelism. However, `PARALLEL_MIN_DEGREE` has no impact if the value of `PARALLEL_MIN_DEGREE` is greater than the value of `CPU_COUNT` or if an object is Oracle-owned, such as a dictionary table or view created on a dictionary table.

You can also request Auto DOP by specifying the appropriate statement level or object level SQL hints.

**See Also:**

- Automatic Degree of Parallelism for additional information about Auto DOP

- [Parallel Statement Queuing](about-parallel-queuing.md) for information about parallel statement queuing

- [In-Memory Parallel Execution](inmemory-parallel-exec.md) for information about in-memory parallel execution

- [Tips for Tuning Parallel Execution](parallel-exec-tips.md) for information about other techniques that you can use to control parallelism

- [Oracle Database Reference](../refrn/PARALLEL_DEGREE_POLICY.md) for information about settings for the `PARALLEL_DEGREE_POLICY` initialization parameter

- [Oracle Database SQL Language Reference](../sqlrf/Comments.md) for information about the `PARALLEL` hint

### 8.2.6 Adaptive Parallelism

The adaptive multiuser algorithm reduces the degree of parallelism as the load on the system increases.

When using Oracle Database adaptive parallelism capabilities, the database uses an algorithm at SQL execution time to determine whether a parallel operation should receive the requested DOP or have its DOP lower to ensure the system is not overloaded.

In a system that makes aggressive use of parallel execution by using a high DOP, the adaptive algorithm adjusts the DOP down when only a few operations are running in parallel. While the algorithm still ensures optimal resource utilization, users may experience inconsistent response times. Using solely the adaptive parallelism capabilities in an environment that requires deterministic response times is not advised. Adaptive parallelism is controlled through the database initialization parameter `PARALLEL_ADAPTIVE_MULTI_USER`.

**Note:**

Because the initialization parameter `PARALLEL_ADAPTIVE_MULTI_USER` is deprecated in Oracle Database 12c Release 2 (12.2.0.1) and to be desupported in a future release, Oracle recommends using parallel statement queuing instead.
