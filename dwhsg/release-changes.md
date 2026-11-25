This preface contains:

- Changes in Oracle Database Release 18c, Version 18.1

- Changes in Oracle Database 12c Release 2 (12.2.0.1)

- Changes in Oracle Database 12c Release 1 (12.1.0.2)

- Changes in Oracle Database 12c Release 1 (12.1.0.1)

### Changes in Oracle Database Release 19c

The following are changes in Oracle Database Data Warehousing Guide for Oracle Database release 19c.

#### New Features

- The `DISTINCT` keyword of the `LISTAGG` function enables you to eliminate duplicates from the specified expression.

  See [LISTAGG Function](sql-analysis-reporting-data-warehouses.md).

- Materialized views can be created based on hybrid partitioned tables. Query rewrite and refresh is supported for materialized views based on hybrid partitioned tables.

  See [Creating Materialized Views Based on Hybird Partitioned Tables](basic-materialized-views.md), [Refreshing Materialized Views Based on Hybrid Partitioned Tables](refreshing-materialized-views.md), and [About Query Rewrite in the Presence of Hybrid Partitioned Tables](advanced-query-rewrite-materialized-views.md).

- The performance of queries that contain `COUNT(DISTINCT)` operations is enhanced by using materialized views with non-additive facts.

  See [Creating a Materialized View Containing Bitmap-based COUNT(DISTINCT) Functions](basic-materialized-views.md) and [Query Rewrite and Materialized Views Based on Bitmap-based COUNT(DISTINCT) Functions](advanced-query-rewrite-materialized-views.md).

### Changes in Oracle Database Release 18c, Version 18.1

The following are changes in Oracle Database Data Warehousing Guide for Oracle Database release 18c, version 18.1.

#### New Features

- Enhancements to approximate query processing

  Business intelligence (BI) applications extensively use aggregate functions, including analytic functions, to provide answers to common business queries. With approximate query processing, you can instantly improve the performance of existing analytic workloads and enable faster ad-hoc data exploration. New approximate SQL functions for rank, sum and count are now available for top N style queries.

  **See Also:**

  [About Approximate Top-N Query Processing](data-warehouse-optimizations-techniques.md)

- Enhancements to parallel partition-wise operations

  Parallel partition-wise SQL operations can improve query performance significantly, leading to better response time. Parallel partition-wise joins are used commonly for processing large joins efficiently and fast. In addition to parallel partition-wise joins, you can also initiate parallel partition-wise execution of SQL operations with SQL windowing clauses.

  **See Also:**

  [Parallel Partition-Wise Operations with Windowing Functions](sql-analysis-reporting-data-warehouses.md)

- Enhancements to analytic views

  - In a `WITH` or `FROM` clause of a `SELECT` statement, a query of an analytic view may now include the `FILTER` `FACT` keywords to filter the data accessed by the analytic view prior to aggregation. Using the new `ADD` `MEASURES` keywords, you can define analytic view calculated measures within a `SELECT` statement, so that an application can now define its own measures dynamically.

    **See Also:**

    [Analytic View Queries with Filtered Facts and Added Measures](analytic-view-objects.md)

  - The `JOIN` `PATH` keywords in the `CREATE` `ATTRIBUTE` `DIMENSION` statement support the use of snowflake-style dimension tables. The `REFERENCES` `DISTINCT` keywords in the `CREATE` `ANALYTIC` `VIEW` statement support the use of a denormalized fact table, in which dimension attributes and fact data are in the same table.

  - Analytic views now support a variety of new functions that you can use in calculated measure expressions. The new functions include `RANK_`\*, `PERCENTILE_`\*, `STATS_`\*, `COVAR_`\*, `HIER_DEPTH`, `HIER_LEVEL`, `HIER_MEMBER_NAME`, `HIER_MEMBER_UNIQUE_NAME`, `HIER_CAPTION`, and `HIER_DESCRIPTION`. Also, you can now use hierarchical attributes in the definition of calculated measures. For example, in a `CASE` statement you can specify different calculation expressions based on the value of an attribute.

### Changes in Oracle Database 12c Release 2 (12.2.0.1)

The following are changes in Oracle Database Data Warehousing Guide for Oracle Database 12c Release 2 (12.2.0.1).

#### New Features

- Attribute dimensions, hierarchies, and analytic views

  Analytic views provide a fast and efficient way to create analytic queries of data stored in existing database tables and views. Attribute dimensions specify dimension table or view columns as attributes and organize the attributes into levels. Hierarchies organize the levels hierarchically. Analytic views reference hierarchies and specify measures that reference data from fact tables and that specify calculations to make using the data.

  See [Overview of Analytic Views](overview-analytic-views.md)

- Real-time materialized views

  Real-time materialized views further improve the availability of materialized views by providing user queries with fresh data even when the materialized view is marked as stale. When queries access a real-time materialized view that is stale, Oracle Database computes the fresh query result on the fly by using the stale data in the materialized view plus the delta information stored in the materialized view logs.

  See [Using Real-time Materialized Views](advanced-materialized-views.md)

- `ON STATEMENT` refresh mode for materialized views

  The `ON STATEMENT` refresh mode refreshes materialized views every time a DML operation is performed on any base table, without the need to commit the transaction. This mode does not require you to maintain materialized view logs on the base tables.

  See [About ON STATEMENT Refresh for Materialized Views](refreshing-materialized-views.md).

- Managing materialized view refresh statistics

  Statistics for materialized view refresh operations are collected and stored in the database. You can use current and historical statistics to analyze materialized view refresh performance over time.

  See [Monitoring Materialized View Refresh Operations](monitoring-materialized-view-refresh.md).

- Support for approximate query processing

  Approximate query processing provides extremely fast responses to explorative queries using SQL functions that return approximate results, with negligible deviation from the exact result. Queries containing SQL functions that return approximate results, or approximate queries, can be used to create materialized views. Materialized views based on approximate queries are eligible for query rewrite and can be fast refreshed.

  See [About Approximate Query Processing](data-warehouse-optimizations-techniques.md).

- `LISTAGG` enhancements

  The `LISTAGG` function now provides control over scenarios where the concatenated string returned by the `LISTAGG` function exceeds the maximum length supported by the `VARCHAR2` data type.

  See [LISTAGG Function](sql-analysis-reporting-data-warehouses.md).

- Improved handling of data errors using SQL functions

  The `CAST` operator can now return a user-specified value when a data type conversion error occurs. The `VALIDATE_CONVERSION` function determines if conversion to a specified data type can succeed.

  See [Handling Data Errors with SQL](loading-transformation-date-warehouses.md).

- Enhanced query performance with the IM column store

  In-Memory Expressions (IM expressions) calculate and populate the results of frequently-evaluated query expressions into the In-Memory Column Store (IM column store). Populating IM expressions into the IM column store ensures that they can be used by subsequent queries to provide faster query response times.

  In-memory virtual columns (IM virtual columns) enable you to populate virtual columns defined on a table into the IM column store. You can populate all or just a subset of virtual columns from a table into memory to improve the performance of analytic queries that access these virtual columns.

  See [About Improving Query Performance Using In-Memory Expressions](data-warehouse-logical-design.md) and [About Using In-Memory Virtual Columns to Improve Query Performance](data-warehouse-logical-design.md).

- Automatic Data Optimization (ADO) support for IM column store

  ADO can be used to manage the contents of the IM column store. ADO uses heat map statistics to ensure that only the elements that benefit most are stored in the IM column store. This enhances the performance benefits of using the IM column store.

  See [About In-Memory Column Store and Automatic Data Optimization](data-warehouse-logical-design.md).

- Optimize the performance of batch updates during table redefinition

  The `EXECUTE_UPDATE` procedure in the `DBMS_REDEFINITION` package can optimize the performance of bulk updates to a table.

  See [About Batch Updates and Online Table Redefinition](loading-transformation-date-warehouses.md).

- Support for materialized view refresh during online table redefinition

  The `DBMS_REDEFINITION` package can be used to incrementally refresh fast refreshable dependent materialized views during online table redefinition.

  See [About Refreshing Dependent Materialized Views During Online Table Redefinition](refreshing-materialized-views.md).

- Support for partitioning of external tables

  Partitioning of external tables extends existing Oracle partitioning to external tables. This allows for better integration with external sources, for example, to align the partitioning of an external table with the partitions of a HIVE table. It also improves query performance for data stored outside of database using existing partition pruning techniques.

  See [Partitioning for Easier Data Access](data-warehouse-optimizations-techniques.md).

- Database operation monitoring

  Extraction, Transformation, and Loading (ETL) jobs that are performing suboptimally can be monitored to help identify performance bottlenecks.

  See [Overview of Monitoring ETL Operations](loading-transformation-date-warehouses.md).

### Changes in Oracle Database 12c Release 1 (12.1.0.2)

The following are the changes in Oracle Database Data Warehousing Guide for Oracle Database 12c Release 1 (12.1.0.2).

#### New Features

- Oracle In-Memory Column Store

  The Oracle In-Memory Column Store (IM column store) in an optional area in the SGA that stores tables, table partitions, and individual columns in a compressed columnar format. The IM column store is a supplement to rather than a replacement for the database buffer cache.

  The IM column store primarily improves the performance of table scans and the application of `WHERE` clause predicates. Faster table scans make it more likely that the optimizer will choose bloom filters and `VECTOR GROUP BY` transformations.

- Attribute clustering

  Attribute clustering of tables enables you to store data in close proximity on disk in a ordered way that is based on the values of certain columns in the table. I/O and CPU costs of table scans and table data lookup through indexes are reduced because pruning though table zone maps becomes more effective.

  **See Also:**

  "[Attribute Clustering](attribute-clustering.md)"

- Zone maps

  Zone maps enable natural pruning of data based on physical location of the data on disk. Accessing only the relevant data blocks during full table scans and accessing only the relevant data rows during index scans reduces I/O and CPU costs of data access.

  **See Also:**

  "[Using Zone Maps](using-zone-maps.md) "

- In-memory aggregation

  The `VECTOR GROUP BY` operation improves the performance of queries that join one or more relatively small tables to a larger table and aggregate data. In the context of data warehousing, `VECTOR GROUP BY` aggregation will often be chosen for star queries that select data from the IM column store.

  `VECTOR GROUP BY` aggregation minimizes the processing involved in joining multiple dimension tables to one fact table. It uses the infrastructure related to parallel query and blends it with CPU-efficient algorithms that maximize performance.

- Automatic Big Table Caching

  Automatic big table caching improves in-memory query performance for large tables that do not fit completely in the buffer cache. Such tables can be stored in the big table cache, an optional, configurable portion of the database buffer cache.

  **See Also:**

  "[Automatic Big Table Caching to Improve the Performance of In-Memory Parallel Queries](data-warehouse-logical-design.md)"

### Changes in Oracle Database 12c Release 1 (12.1.0.1)

The following are changes in Oracle Database Data Warehousing Guide for Oracle Database 12c Release 1 (12.1.0.1).

#### New Features

- Pattern Matching

  SQL has been extended to support pattern matching, which makes it easy to detect various patterns over sequences. Pattern matching is useful in many commercial applications, such as stock monitoring, network intrusion detection, and e-commerce purchase tracking.

  **See Also:**

  " [SQL for Pattern Matching](sql-pattern-matching-data-warehouses.md) " for more information

- Native SQL Support for Top-N Queries

  The new `row_limiting_clause` enables you to limit the rows returned by a query. You can specify an offset, and number of rows or percentage of rows to return. This enables you to implement top-N reporting.

  **See Also:**

  "[Limiting SQL Rows](sql-analysis-reporting-data-warehouses.md)" for more information

- Online Statistics Gathering for Bulk Load Operations

  Starting in Oracle Database 12c, the database automatically gathers table statistics as part of bulk load operations.

- Synchronous Refresh

  A new type of refresh called synchronous refresh enables you to keep a set of tables and materialized views defined on them to always be in sync. It is well suited for data warehouses where the loading of incremental data is tightly controlled and occurs at periodic intervals.

  **See Also:**

  "[Synchronous Refresh](synchronous-refresh.md)" for more information

- Out-of-Place Refresh

  A new type of refresh is available to improve materialized view refresh performance and availability. This refresh, called out-of-place refresh because it uses outside tables during refresh, is particularly effective when handling situations with large amounts of data changes, where conventional DML statements do not scale well.

  **See Also:**

  "[Refreshing Materialized Views](refreshing-materialized-views.md)" for more information

#### Desupported Features

Some features previously described in this document are desupported in Oracle Database 12c Release 1. See [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md) for a list of desupported features.
