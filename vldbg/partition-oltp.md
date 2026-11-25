Partitioning features are very useful for OLTP systems.

Due to the explosive growth of online transaction processing (OLTP) systems and their user populations, partitioning is particularly useful for OLTP systems in addition to data warehousing environments

Partitioning is often used for OLTP systems to reduce contention while supporting a very large user population. It also helps to address regulatory requirements facing OLTP systems, including storing larger amounts of data in a cost-effective manner.

This chapter contains the following sections:

- What Is an Online Transaction Processing System?

- Performance in an Online Transaction Processing Environment

- Manageability in an Online Transaction Processing Environment

### 7.1 What Is an Online Transaction Processing System?

An Online Transaction Processing (OLTP) system is a common data processing system in today's enterprises. Classic examples of OLTP systems are order entry, retail sales, and financial transaction systems.

OLTP systems are primarily characterized through a specific data usage that is different from data warehouse environments, yet some characteristics, such as having large volumes of data and lifecycle-related data usage and importance, are identical.

The main characteristics of an OLTP environment are:

- Short response time

  The nature of OLTP environments is predominantly any kind of interactive ad hoc usage, such as telemarketers entering telephone survey results. OLTP systems require short response times in order for users to remain productive.

- Small transactions

  OLTP systems typically read and manipulate highly selective, small amounts of data; the data processing is mostly simple and complex joins are relatively rare. There is always a mix of queries and DML workload. For example, one of many call center employees retrieves customer details for every call and enters customer complaints while reviewing past communications with the customer.

- Data maintenance operations

  It is not uncommon to have reporting programs and data updating programs that must run either periodically or on an ad hoc basis. These programs, which run in the background while users continue to work on other tasks, may require a large number of data-intensive computations. For example, a university may start batch jobs assigning students to classes while students can still sign up online for classes themselves.

- Large user populations

  OLTP systems can have enormously large user populations where many users are trying to access the same data at the same time. For example, an online auction website can have hundreds of thousands (if not millions) of users accessing data on its website at the same time.

- High concurrency

  Due to the large user population, the short response times, and small transactions, the concurrency in OLTP environments is very high. A requirement for thousands of concurrent users is not uncommon.

- Large data volumes

  Depending on the application type, the user population, and the data retention time, OLTP systems can become very large. For example, every customer of a bank could have access to the online banking system which shows all their transactions for the last 12 months.

- High availability

  The availability requirements for OLTP systems are often extremely high. An unavailable OLTP system can impact a very large user population, and organizations can suffer major losses if OLTP systems are unavailable. For example, a stock exchange system has extremely high availability requirements during trading hours.

- Lifecycle-related data usage

  Similar to data warehousing environments, OLTP systems often experience different data access patterns over time. For example, at the end of the month, monthly interest is calculated for every active account.

The following are benefits of partitioning for OLTP environments:

- Support for bigger databases

  Backup and recovery, as part of a high availability strategy, can be performed on a low level of granularity to efficiently manage the size of the database. OLTP systems usually remain online during backups and users may continue to access the system while the backup is running. The backup process should not introduce major performance degradation for the online users.

  Partitioning helps to reduce the space requirements for the OLTP system because part of a database object can be stored compressed while other parts can remain uncompressed. Update transactions against uncompressed rows are more efficient than updates on compressed data.

  Partitioning can store data transparently on different storage tiers to lower the cost of retaining vast amounts of data.

- Partition maintenance operations for data maintenance (instead of DML)

  For data maintenance operations (purging being the most common operation), you can leverage partition maintenance operations with the Oracle Database capability of online index maintenance. A partition management operation generates less redo than the equivalent DML operations.

- Potential higher concurrency through elimination of hot spots

  A common scenario for OLTP environments is to have monotonically increasing index values that are used to enforce primary key constraints, thus creating areas of high concurrency and potential contention: every new insert tries to update the same set of index blocks. Partitioned indexes, in particular hash partitioned indexes, can help alleviate this situation.

### 7.2 Performance in an Online Transaction Processing Environment

Performance in OLTP environments heavily relies on efficient index access, thus the choice of the most appropriate index strategy becomes crucial.

The following sections discuss best practices for deciding whether to partition indexes in an OLTP environment.

- Deciding Whether to Partition Indexes

- How to Use Partitioning on Index-Organized Tables

#### 7.2.1 Deciding Whether to Partition Indexes

Due to the selectivity of queries and high concurrency of OLTP applications, the choice of the right index strategy is indisputably an important decision for the use of partitioning in an OLTP environment. With less contention, the application can support a larger user population.

The following basic rules explain the main benefits and trade-offs for the various possible index structures:

- A nonpartitioned index, while larger than individual partitioned index segments, always leads to a single index probe (or scan) if an index access path is chosen; there is only one segment for a table. The data access time and number of blocks being accessed are identical for both a partitioned and a nonpartitioned table.

  A nonpartitioned index does not provide partition autonomy and requires an index maintenance operation for every partition maintenance operation that affects rowids (for example, drop, truncate, move, merge, coalesce, or split operations).

- With partitioned indexes, there are always multiple segments. Whenever Oracle Database cannot prune down to a single index segment, the database has to access multiple segments. This potentially leads to higher I/O requirements (n index segment probes compared with one probe for a nonpartitioned index) and can have an impact (measurable or not) on the run-time performance. This is true for all partitioned indexes.

  Partitioned indexes can either be local partitioned indexes or global partitioned indexes. Local partitioned indexes always inherit the partitioning key from the table and are fully aligned with the table partitions. Consequently, any kind of partition maintenance operation requires little to no index maintenance work. For example, dropping or truncating a partition does not incur any measurable overhead for index maintenance; the local index partitions are either dropped or truncated.

  Partitioned indexes that are not aligned with the table are called global partitioned indexes. Unlike local indexes, there is no relation between a table and an index partition. Global partitioned indexes give the flexibility to choose a partitioning key that is optimal for an efficient partition index access. Partition maintenance operations normally affect more (if not all) partitions of a global partitioned index, depending on the operation and partitioning key of the index.

- Under some circumstances, having multiple segments for an index can be beneficial for performance. It is very common in OLTP environments to use sequences to create artificial keys. Consequently, you create key values that are monotonically increasing, which results in many insertion processes competing for the same index blocks. Introducing a global partitioned index (for example, using global hash partitioning on the key column) can alleviate this situation. If you have, for example, four hash partitions for such an index, then you now have four index segments into which you are inserting data, reducing the concurrency on these segments by a factor of four for the insertion processes.

Enforcing uniqueness is important database functionality for OLTP environments. Uniqueness can be enforced with nonpartitioned and partitioned indexes. However, because partitioned indexes provide partition autonomy, the following requirements must be met to implement unique indexes:

- A nonpartitioned index can enforce uniqueness for any given column or combination of columns. The behavior of a nonpartitioned index is no different for a partitioned table compared to a nonpartitioned table.

- Each partition of a partitioned index is considered an autonomous segment. To enforce the autonomy of these segments, you always have to include the partitioning key columns as a subset of the unique key definition.

  - Global partitioned indexes must always be prefixed with at least the first leading column of the index column (the partitioning column of the partitioned global index).

  - Unique local indexes must have the partitioning key of the table as a subset of the unique key definition.

Example 7-1 shows the creation of a unique index on the `order_id` column of the `orders_oltp` table. The `order_id` in the OLTP application is filled using a sequence number. The unique index uses hash partitioning to reduce contention for the monotonically increasing `order_id` values. The unique key is then used to create the primary key constraint.

Example 7-1 Creating a unique index and primary key constraint

    CREATE UNIQUE INDEX orders_pk
      ON orders_oltp(order_id)
      GLOBAL PARTITION BY HASH (order_id)
      ( PARTITION p1 TABLESPACE tbs1
       , PARTITION p2 TABLESPACE tbs2
       , PARTITION p3 TABLESPACE tbs3
       , PARTITION p4 TABLESPACE tbs4
      ) NOLOGGING;

    ALTER TABLE orders_oltp ADD CONSTRAINT orders_pk
      PRIMARY KEY (order_id)
      USING INDEX;

#### 7.2.2 How to Use Partitioning on Index-Organized Tables

When your workload fits the use of index-organized tables, then you must consider how to use partitioning on your index-organized table and on any secondary indexes.

You must decide whether to partition secondary indexes on index-organized tables based on the same considerations as indexes on regular heap tables. You can partition an index-organized table, but the partitioning key must be a subset of the primary key. A common reason to partition an index-organized table is to reduce contention; this is typically achieved using hash partitioning.

Another reason to partition an index-organized table is to be able to physically separate data sets based on a primary key column. For example, an application-hosting company can physically separate application instances for different customers by list partitioning on the company identifier. Queries in such a scenario can often take advantage of index partition pruning, shortening the time for the index scan. ILM scenarios with index-organized tables and partitioning are less common because they require a date column to be part of the primary key.

For more information about how to create partitioned index-organized tables, refer to [Partition Administration](partition-admin.md).

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-tables.md) for more information about index-organized tables

### 7.3 Manageability in an Online Transaction Processing Environment

In addition to the performance benefits, partitioning also enables the optimal data management for large objects in an OLTP environment.

Every partition maintenance operation in Oracle Database can be extended to atomically include global and local index maintenance, enabling the execution of any partition maintenance operation without affecting the 24x7 availability of an OLTP environment.

Partition maintenance operations in OLTP systems occur often because of ILM scenarios. In these scenarios, \[range \| interval\] partitioned tables, or \[range \| interval\]-\* composite partitioned tables, are common.

Some business cases for partition maintenance operations include scenarios surrounding the separation of application data. For example, a retail company runs the same application for multiple branches in a single schema. Depending on the branch revenues, the application (as separate partitions) is stored on more efficient storage. List partitioning, or list-\* composite partitioning, is a common partitioning strategy for this type of business case.

You can use hash partitioning, or hash subpartitioning for tables, in OLTP systems to obtain similar performance benefits to the performance benefits achieved in data warehouse environments. The majority of the daily OLTP workload consists of relatively small operations, executed serially. Periodic batch operations, however, may execute in parallel and benefit from the distribution improvements that hash partitioning and subpartitioning can provide for partition-wise joins. For example, end-of-the-month interest calculations may be executed in parallel to complete within a nightly batch window.

This section contains the following topics:

- Impact of a Partition Maintenance Operation on a Partitioned Table with Local Indexes

- Impact of a Partition Maintenance Operation on Global Indexes

- Common Partition Maintenance Operations in OLTP Environments

For more information about the performance benefits of partitioning, refer to [Partitioning for Availability, Manageability, and Performance](partition-availability.md).

#### 7.3.1 Impact of a Partition Maintenance Operation on a Partitioned Table with Local Indexes

When a partition maintenance operation takes place, Oracle Database locks the affected table partitions for any DML operation, except in the case of an `ONLINE` `MOVE`.

Data in the affected partitions, except a `DROP` or `TRUNCATE` operation, is still fully accessible for any `SELECT` operation. Because local indexes are logically coupled with the table (data) partitions, only the local index partitions of the affected table partitions have to be maintained as part of a partition maintenance operation, enabling optimal processing for the index maintenance.

For example, when you move an older partition from a high-end storage tier to a low-cost storage tier using the `ALTER` `TABLE` `MOVE` `ONLINE` functionality, the data and the index are always available for `SELECT` and DML operations; the necessary index maintenance is to update the existing index partition to reflect the new physical location of the data. If you drop an older partition after you have archived it, then its local index partitions get dropped as well, and for global indexes the orphaned entries for the removed partitions get marked, enabling a split-second partition maintenance operation that affects only the data dictionary.

#### 7.3.2 Impact of a Partition Maintenance Operation on Global Indexes

Whenever a global index is defined on a partitioned or nonpartitioned table, there is no correlation between a distinct table partition and the index. Consequently, any partition maintenance operation affects all global indexes or index partitions.

The partitions of tables containing local indexes are locked to prevent DML operations against the affect table partitions, except for an `ONLINE` `MOVE` operation. However, unlike the index maintenance for local indexes, any global index is still fully available for DML operations and does not affect the online availability of the OLTP system.

Conceptually and technically, the index maintenance for global indexes for a partition maintenance operation is comparable to the index maintenance that would become necessary for a semantically identical DML operation, except for `DROP` and `TRUNCATE` where the global index maintenance gets delayed to a later point in time. For more information about managing global indexes, refer to [Management of Global Partitioned Indexes](index-partitioning.md).

For example, dropping an old partition is semantically equivalent to deleting all the records of the old partition using the SQL `DELETE` statement. In the DML case, all index entries of the deleted data set have to be removed from any global index as a standard index maintenance operation, which does not affect the availability of an index for `SELECT` and DML operations.

The `DROP` `PARTITION` also does not affect the index availability, but enables you to decouple the necessary index maintenance from the initial data removal without affecting the availability of the global indexes. In this scenario, a drop operation represents the optimal approach: data is removed without the overhead of a conventional `DELETE` operation and the global indexes are maintained in a nonintrusive manner.

#### 7.3.3 Common Partition Maintenance Operations in OLTP Environments

The two most common partition maintenance operations are the removal of data and the relocation of data onto lower-cost storage tier devices.

- Removing (Purging) Old Data

- Moving or Merging Older Partitions to a Low-Cost Storage Tier Device

##### 7.3.3.1 Removing (Purging) Old Data

Using either a `DROP` or `TRUNCATE` operation removes older data based on the partitioning key criteria.

The drop operation removes the data and the partition metadata, while a `TRUNCATE` operation removes only the data but preserve the metadata. All local index partitions are dropped respectively, and truncated. Asynchronous global index maintenance is done for partitioned or nonpartitioned global indexes and is fully available for select and DML operations.

The following example drops all data older than January 2006 from the `orders_oltp` table. As part of the drop statement, an `UPDATE GLOBAL INDEXES` statement is executed, so that the global index remains usable throughout the maintenance operation. Any local index partitions are dropped as part of this operation.

    ALTER TABLE orders_oltp DROP PARTITION p_before_jan_2006
     UPDATE GLOBAL INDEXES;

##### 7.3.3.2 Moving or Merging Older Partitions to a Low-Cost Storage Tier Device

Using a `MOVE` or `MERGE` operation as part of an Information Lifecycle Management (ILM) strategy, you can relocate older partitions to the most cost-effective storage tier.

Using the `ALTER` `TABLE` `ONLINE` `MOVE` functionality enables the data to be available for both queries and DML operations. Local indexes are maintained and likely relocated as part of the merge or move operation. The standard index maintenance is done for partitioned or nonpartitioned global indexes and is fully available for select and DML operations.

The following example shows how to merge the January 2006 and February 2006 partitions in the `orders_oltp` table, and store them in a different tablespace. Any local index partitions are also moved to the `ts_low_cost` tablespace as part of this operation. The `UPDATE INDEXES` clause ensures that all indexes remain usable throughout and after the operation, without additional rebuilds.

    ALTER TABLE orders_oltp
      MERGE PARTITIONS p_2006_jan,p_2006_feb
      INTO PARTITION p_before_mar_2006 COMPRESS
      TABLESPACE ts_low_cost
      UPDATE INDEXES;

For more information about the benefits of partition maintenance operations for Information Lifecycle Management, see [Managing and Maintaining Time-Based Information](time-based-info.md).
