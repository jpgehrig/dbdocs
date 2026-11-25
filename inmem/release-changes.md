This preface summarizes the In-Memory features for Oracle Database 19c, Oracle Database 18c, and Oracle Database 12c.

This section contains the following topics:

### Changes in Oracle Database Release 19c, Version 19.20

Oracle Database In-Memory Guide for Oracle Database 19c, version 19.20 includes the new `DBMS_INMEMORY_ADVISE` PL/SQL package.

`DBMS_INMEMORY_ADVISE` contains the `IS_INMEMORY_ELIGIBLE` procedure, which you can run to get a quick assessment about whether or not a database workload can benefit from Database In-Memory.

**See:**

[unresolvable-reference.html#GUID-D1EDC6A8-4187-4B25-8654-CBC0BA8952D9](https://docs.oracle.com/en/database/oracle/oracle-database/19/inmem/unresolvable-reference.html#GUID-D1EDC6A8-4187-4B25-8654-CBC0BA8952D9)

### Changes in Oracle Database Release 19c, Version 19.8

Oracle Database In-Memory Guide for Oracle Database 19c, version 19.8 has the following changes.

#### New Features

The following major features are new in this release.

- Database In-Memory Base Level

  Starting with Oracle Database release 19c, version 19.8, you can enable the Database In-Memory Base Level by setting the `INMEMORY_FORCE` initialization parameter to `BASE_LEVEL`. The Base Level enables you to experiment with In-Memory features without purchasing the Oracle Database In-Memory option.

  When the Base Level is enabled, the IM column store size is limited to 16 GB for a CDB or non-CDB and for every database instance in an Oracle RAC database. Also, the compression level for all objects and columns is set to `QUERY LOW` automatically and transparently, and Automatic In-Memory is disabled.

- Starting with Oracle Database release 19c, version 19.8, you can use the CellMemory feature without enabling the IM column store by setting `INMEMORY_FORCE=CELLMEMORY_LEVEL` and `INMEMORY_SIZE=0`. With these settings, the IM column store is not enabled and queries can use CellMemory to scan objects.

  In previous releases of Oracle Database, in order to use the CellMemory feature, you were required to enable the IM column store, even if you had no intention of using it. This incurred the overhead of enabling the IM column store without any benefit.

**See Also:**

- See "[Enabling the IM Column Store for a Database](enabling-the-im-column-store.md)."

- [Oracle Database Licensing Information User Manual](../dblic/Licensing-Information.md) for details on which features are supported for different editions and services

### Changes in Oracle Database Release 19c, Version 19.1

Oracle Database In-Memory Guide for Oracle Database release 19c, version 19.1 has the following changes.

#### New Features

The following major features are new in this release.

- Database In-Memory Base Level

  Enable the Database In-Memory Base Level by setting the `INMEMORY_FORCE` initialization parameter to `BASE_LEVEL`. The Base Level enables you to experiment with In-Memory features without purchasing the Oracle Database In-Memory option.

  When the Base Level is enabled, the IM column store size is limited to 16 GB for a CDB or non-CDB and for every database instance in an Oracle RAC database. Also, the compression level for all objects and columns is set to `QUERY LOW` automatically and transparently, and Automatic In-Memory is disabled.

  See "[Enabling the IM Column Store for a Database](enabling-the-im-column-store.md)" and [Oracle Database Licensing Information User Manual](../dblic/Licensing-Information.md).

- Database In-Memory wait on populate

  The `DBMS_INMEMORY_ADMIN.POPULATE_WAIT` function initiates population of all `INMEMORY` objects that have a priority greater than or equal to the specified priority, and returns a status value for the population. A user-specified interval specifies the maximum time that the function waits before returning the value to the caller.

  See "[Forcing Initial Population of an In-Memory Object](populating-the-imcs-manually.md)".

- Big Data and performance enhancements for In-Memory external tables

  This release introduces several manageability and performance improvements to the In-Memory external tables feature:

  - The `ORACLE_HIVE` and `ORACLE_BIGDATA` drivers are supported.

  - Parallel query is supported.

  - A full table scan populates an In-Memory external table. In previous releases, population required using the `POPULATE` or `REPOPULATE` procedure of `DBMS_INMEMORY`.

  - The In-Memory background processes, rather than a foreground process, now drop IM segments.

  See "[In-Memory External Tables](populating-objects-in-memory.md)".

- Hybrid partitioned tables

  Partitions can reside in both Oracle Database segments and in external files and sources. This feature significantly enhances partitioning for Big Data SQL, where large portions of a table can reside in external partitions. Only the internal partitions of a hybrid partitioned table inherit the `INMEMORY` attribute.

  See "[In-Memory Tables](populating-objects-in-memory.md)".

- Oracle Database Resource Manager automatically enabled for Database In-Memory

  When `INMEMORY_SIZE` is greater than `0`, the Resource Manager is automatically enabled.

  See "[Interface for IM Dynamic Scans](in-memory-column-store-architecture.md)".

- Oracle Data Guard Multi-Instance Redo Apply supports the IM column store

  Setting the initialization parameter `ENABLE_IMC_WITH_MIRA` to `TRUE` enables the IM column store and Data Guard Multi-Instance Redo Apply at the same time on an Active Data Guard standby database. By default, `ENABLE_IMC_WITH_MIRA` is `FALSE`.

  See [Oracle Database Reference](../refrn/ENABLE_IMC_WITH_MIRA.md) to learn more about `ENABLE_IMC_WITH_MIRA`.

**See Also:**

[Oracle Database Licensing Information User Manual](../dblic/Licensing-Information.md) for details on which features are supported for different editions and services

### Changes in Oracle Database Release 18c, Version 18.1

Oracle Database In-Memory Guide for Oracle Database release 18c, version 18.1 has the following changes.

#### New Features

The following major features are new in this release.

- Automatic In-Memory

  This feature uses segment and column usage statistics to manage the contents of the IM column store automatically. If a populate job fails because the IM column store is full, then Automatic In-Memory evicts inactive segments to make room for active segments.

  See "[Configuring Automatic In-Memory](configuring-memory-management.md)".

- In-Memory Dynamic Scans

  IM dynamic scans automatically and transparently parallelize table scans by using lightweight process threads. Oracle Resource Manager allocates these threads when it perceives that CPU resources are idle and can be leveraged to speed up the query.

  See "[In-Memory Dynamic Scans](in-memory-column-store-architecture.md)".

- IM expressions window capture

  You can define an expression capture window of an arbitrary length, which ensures that only the expressions occurring within this window are considered for In-Memory materialization. This mechanism is especially useful when you know of a small interval that is representative of the entire workload. For example, during the trading window, a brokerage firm can gather the set of expressions, and materialize them in the IM column store to speed-up future query processing for the entire workload.

  See "[Expression Capture Interval](optimizing-in-memory-expressions.md)".

- In-Memory support for external tables

  You can populate external tables into the IM column store. This feature is useful for analytical queries that combine internal and external data.

  See "[In-Memory External Tables](populating-objects-in-memory.md)" and "[Populating an In-Memory External Table Using DBMS_INMEMORY.POPULATE: Example](populating-the-imcs-manually.md)".

- In-Memory Optimized Arithmetic

  For tables compressed with `QUERY LOW`, `NUMBER` columns are encoded using an optimized format that enables native calculations in hardware. SIMD vector processing of aggregations and arithmetic operations that use this format can achieve significant performance gains. The feature is enabled when `INMEMORY_OPTIMIZED_ARITHMETIC` is set to `ENABLE`.

  See "[Optimizing In-Memory Arithmetic](optimizing-in-memory-aggregation.md)".

- Enhanced performance for Large Objects (LOBs)

  In previous releases, although LOBs and LOB pointers were populated in the IM column store, the database satisfied queries by using the buffer cache. In this release, In-Memory queries that apply range predicates to scalar columns or SQL operators to LOB columns benefit from SIMD vector processing.

  The IM column store provides contiguous storage for inline LOBs, which are LOBs less than 4 KB, within the IMCUs. For out-of-line LOBs, the IM column store only stores the LOB locator, which is 40 byes. There is one exception to the preceding rule. An IMEU can allocate up to 32 KB of contiguous storage for JSON columns defined as a LOB data type. The IMEU stores these columns in the OSON (binary JSON) format.

  See "[CPU Architecture: SIMD Vector Processing](in-memory-column-store-architecture.md)".

- In-Memory join group on one column

  You can use the following syntax to create a join group for a self-join on a single column: `CREATE INMEMORY JOIN GROUP ``jg_name``(``table_name``(``column_name``))`.

  See "[Optimizing Joins with Join Groups](optimizing-queries-with-join-groups.md)".

### Changes in Oracle Database 12c Release 2 (12.2.0.1)

Oracle Database In-Memory Guide for Oracle Database 12c Release 2 (12.2.0.1) has the following changes.

#### New Features

The following major features are new in this release:

- In-Memory Column Store (IM column store) dynamic resizing

  You can now dynamically increase the size of the In-Memory Area without reopening the database.

  See "[Increasing the Size of the IM Column Store Dynamically](enabling-the-im-column-store.md)".

- In-Memory Expressions (IM expressions)

  Oracle Database automatically identifies frequently used (“hot”) expressions that are candidates for population in the IM column store. A candidate expression might be `(monthly_sales*12)/52`. IM expressions can greatly improve the performance of analytic queries that use computationally intensive expressions and access large data sets.

  See "[Optimizing Queries with In-Memory Expressions](optimizing-in-memory-expressions.md)".

- In-Memory virtual columns (IM virtual columns)

  IM virtual columns enable the IM column store to materialize some or all virtual columns in a table.

  See "[Enabling and Disabling Columns for In-Memory Tables](populating-objects-in-memory.md)".

- IM FastStart

  IM FastStart optimizes the population of database objects in the IM column store by storing IMCUs directly on disk.

  See "[Managing IM FastStart for the IM Column Store](managing-im-faststart-for-im-column-store.md)".

- Object-level support for services

  For an individual object, the `INMEMORY ... DISTRIBUTE` clause has a `FOR SERVICE` subclause that limits population to the database instance where this service can run. For example, you can configure an `INMEMORY` object to be populated in the IM column store on instance 1 only, or on instance 2 only, or in both instances.

  See "[Object-Level Service Controls](deploying-in-memory-in-oracle-rac.md)".

- IM column store on a standby database

  You can enable an IM column store in an Oracle Active Data Guard standby database. You can populate a completely different set of data in the in-memory column store on the primary and standby databases, effectively doubling the size of the in-memory column store that is available to the application.

  See "[Deploying an IM Column Store with Oracle Active Data Guard](deploying-im-column-store-with-adg.md)".

- ADO support for the IM column store

  You can use Automatic Data Optimization (ADO) policies to evict objects such as tables, partitions, or subpartitions from the IM column store based on Heat Map statistics. Successful policy completion results in setting `NO INMEMORY` for the specified object.

  See "[Enabling ADO for the IM Column Store](configuring-memory-management.md)".

- Join groups

  A join group is a user-created object that lists two columns that can be meaningfully joined. In certain queries, join groups enable the database to eliminate the performance overhead of decompressing and hashing column values. Join groups require an IM column store.

  See "[Optimizing Joins with Join Groups](optimizing-queries-with-join-groups.md)".
