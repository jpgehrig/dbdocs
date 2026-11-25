This chapter describes changes to Oracle Database VLDB and Partitioning Guide.

- Changes for VLDB and Partitioning in Oracle Database 19c

- Changes for VLDB and Partitioning in Oracle Database Release 18c

**See Also:**

- [Oracle Database Licensing Information User Manual](../dblic/index.md) to determine whether a feature is available on your edition of Oracle Database

- [Oracle Database New Features Guide](../newft/index.md) for a complete description of the new features in this release

- [Oracle Database Upgrade Guide](../upgrd/index.md) for a complete description of the deprecated and desupported features in this release

### Changes for VLDB and Partitioning in Oracle Database 19c

The following are changes in Very Large Databases and Partitioning for Oracle Database release 19c, version 19.1.

#### New Features

These are the new features in Oracle Database release 19c, version 19.1, to support very large databases:

- Oracle Hybrid Partitioned Tables

  Oracle hybrid partitioned tables combine classical internal partitioned tables with external partitioned tables into a more general partitioning called hybrid partitioned tables. This feature enables you to easily integrate internal partitions and external partitions (those residing on sources outside the database) into a single partition table. Using this feature also enables you to easily move non-active partitions to external files for a cheaper storage solution.

  Partitions of hybrid partitioned tables can reside on both Oracle tablespaces and external sources, such as Linux files with comma-separated values (CSV) records or files on Hadoop Distributed File System (HDFS) with Java server. Hybrid partitioned tables support all existing external table types for external partitions: `ORACLE_DATAPUMP`, `ORACLE_LOADER`, `ORACLE_HDFS`, `ORACLE_HIVE`.

  **See Also:**

  - [Hybrid Partitioned Tables](partition-concepts.md) for an overview of hybrid partitioned tables

  - [Managing Hybrid Partitioned Tables](manage_hypt.md) for information about administering hybrid partitioned tables

  - [Oracle Database Administrator’s Guide](../admin/managing-tables.md) for information about hybrid partitioned external tables

  - [Oracle Database Concepts](../cncpt/partitions-views-and-other-schema-objects.md) for conceptual information about partitioned tables

  - [Oracle Database In-Memory Guide](../inmem/concepts-for-the-im-column-store.md) for information about the In-Memory Column Store and hybrid partition tables

  - [Oracle Database SQL Tuning Guide](../tgsql/sql-performance-fundamentals.md) for information about optimizations for hybrid partitioned tables

  - [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about creating and altering hybrid partitioned tables with the `CREATE` `TABLE` and `ALTER` `TABLE` SQL commands

  - Oracle Database Utilities for information about [using SQL\*Loader with hybrid partitioned tables](../sutil/oracle-sql-loader-concepts.md), [using Oracle Data Pump with hybrid partitioned tables](../sutil/oracle-data-pump-overview.md), and [managing external tables](../sutil/oracle-external-tables-concepts.md)

  - [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_HADOOP.md) for information about the using PL/SQL procedures with hybrid partitioned tables, including the `CREATE_HYBRID_PARTNED_TABLE` procedure in the DBMS_HADOOP package

  - [Oracle Database Reference](../refrn/static-data-dictionary-views.md) for information about hybrid partition tables in data dictionary views, including the USER_TABLES, USER_ALL_TABLES, ALL_TABLES, ALL_ALL_TABLES, DBA_TABLES and DBA_ALL_TABLES views

  - [Oracle Database Data Warehousing Guide](../dwhsg/part-optimizing-dw.md) for information about materialized views and hybrid partitioned tables

### Changes for VLDB and Partitioning in Oracle Database Release 18c

The following are changes in Very Large Databases and Partitioning for Oracle Database release 18c, version 18.1.

- New Features

#### New Features

These are the new features in Oracle Database release 18c, version 18.1, to support very large databases:

- Enhanced Parallel Partition-wise Operations

  Parallel partition-wise SQL operations can improve query performance significantly, leading to better response time. Parallel partition-wise joins are used commonly for processing large joins efficiently and fast.

  In addition to parallel partition-wise joins, queries using the `SELECT` `DISTINCT` clause and SQL window functions can perform parallel partition-wise operations.

  **See Also:**

  - [Partition-Wise Operations](partition-wise-joins.md)

  - [Partition-Wise Joins in a Data Warehouse](partition-warehouse.md)

  - [Oracle Database Data Warehousing Guide](../dwhsg/data-warehouse-optimizations-techniques.md) for information about data warehousing and optimization techniques

- Modifying the Partitioning Strategy

  You can change the partitioning strategy of a regular (heap-organized) table with the `ALTER` `TABLE` `MODIFY` `PARTITION` SQL statement. Modifying the partitioning strategy, such as hash partitioning to range partitioning, can be performed offline or online. Indexes are maintained as part of the table modification. When performed in online mode, the conversion has no impact on ongoing DML operations.

  This functionality enables partitioned tables to evolve without manually recreating the tables. Changing an existing partitioning strategy of a table online enables applications to adjust partitioning for new business requirements without application downtime.

  **See Also:**

  - [About Modifying the Partitioning Strategy](maintenance-partition-tables-indexes.md)

- Online Merging of Partitions and Subpartitions

  You can use the `ONLINE` keyword with the `ALTER` `TABLE` `MERGE` `PARTITION` and `SUBPARTITION` SQL statements to enable online merge operations for regular (heap-organized) tables, providing concurrent data manipulation language (DML) operations with the ongoing partition merge operation.

  Enabling partition maintenance operations online enables you to schedule and execute all of the operations as needed, without the necessity to plan around periods of query-only windows. This capability both increases application availability and simplifies application development.

  **See Also:**

  - [About Merging Partitions and Subpartitions](maintenance-partition-tables-indexes.md)

- Automatic In-Memory Management With Heat Map Data

  Heat Map data can assist Automatic Data Optimization (ADO) to automatically manage the contents of the In-Memory column store (IM column store). Using Heat Map data, which includes column statistics and other relevant statistics, the IM column store can determine when it is almost full (under memory pressure). If the determination is almost full, then inactive segments can be evicted if there are more frequently accessed segments that would benefit from population in the IM column store.

  **See Also:**

  - [Using Heat Map](ilm-strategy-heatmap-ado.md)

  - [Oracle Database In-Memory Guide](../inmem/enabling-the-im-column-store.md) for information about enabling and sizing the In-Memory Column Store

- Enhancements to Multitenant Parallel Statement Queuing

  Parallel execution has been enhanced to work more effectively in a multitenant database. With these enhancements, such as updates to the `PARALLEL_MAX_SERVERS` and `PARALLEL_SERVERS_TARGET` initialization parameters, parallel statement queuing in a multitenant environment can perform as effectively as in a non-PDB multitenant.

  **See Also:**

  [Oracle Multitenant Administrator's Guide](../multi/using-oracle-resource-manager-for-pdbs-with-sql-plus.md) for information about parallel execution (PX) servers and utilization limits for CDBs and PDBs

- Timeout and Dequeue Actions for Parallel Statement Queuing

  You can specify queue timeout and dequeue actions for parallel statement with enhanced functionality to the `PARALLEL_QUEUE_TIMEOUT_ACTION` resource manager directive and the `DBMS_RESOURCE_MANAGER.DEQUEUE_PARALLEL_STATEMENT` PL/SQL procedure.

  **See Also:**

  - [About Managing Parallel Statement Queuing with Oracle Database Resource Manager](about-parallel-queuing.md)

  - [Specifying a Parallel Statement Queue Timeout for Each Consumer Group](about-parallel-queuing.md)

  - [About Managing the Order of the Parallel Statement Queue](about-parallel-queuing.md)

- `PARALLEL_MIN_DEGREE` Initialization Parameter

  **See Also:**

  - [Controlling Automatic Degree of Parallelism](degree-parallel.md)

  - [Oracle Database Reference](../refrn/PARALLEL_MIN_DEGREE.md) for information about `PARALLEL_MIN_DEGREE`
