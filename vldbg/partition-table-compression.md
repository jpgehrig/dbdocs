Compression can be performed on several partitions or a complete partitioned heap-organized table.

You can do this compression by either defining a complete partitioned table as being compressed, or by defining it on a per-partition level. Partitions without a specific declaration inherit the attribute from the table definition or, if nothing is specified on table level, from the tablespace definition.

The decision whether a partition should be compressed or uncompressed adheres to the same rules as a nonpartitioned table. However, due to partitioning to separate data logically into distinct partitions, such a partitioned table is an ideal candidate for compressing parts of the data (partitions). For example, it is beneficial in all rolling window operations as a intermediate stage before aging out old data. With data segment compression, you can keep more old data online, minimizing the burden of additional storage consumption.

You can also change any existing uncompressed table partition later on, add new compressed and uncompressed partitions, or change the compression attribute as part of any partition maintenance operation that requires data movement, such as `MERGE` `PARTITION`, `SPLIT` `PARTITION`, or `MOVE` `PARTITION`. The partitions can contain data or can be empty.

The access and maintenance of a partially or fully compressed partitioned table are the same as for a fully uncompressed partitioned table. Everything that applies to fully uncompressed partitioned tables is also valid for partially or fully compressed partitioned tables.

The following topics are discussed:

- Table Compression and Bitmap Indexes

- Example of Table Compression and Partitioning

**See Also:**

- [Oracle Database Data Warehousing Guide](../dwhsg/data-warehouse-optimizations-techniques.md) for a generic discussion of data warehousing optimizations and techniques

- [Oracle Database Administrator’s Guide](../admin/managing-tables.md) for information about guidelines for managing tables

- [Oracle Database Performance Tuning Guide](../tgdba/configuring-database-for-performance.md) for estimating the compression factor

### 3.4.1 Table Compression and Bitmap Indexes

There are several necessary steps before using compression on partitioned tables with bitmap indexes.

To use table compression on partitioned tables with bitmap indexes, you must do the following before you introduce the compression attribute for the first time:

1.  Mark bitmap indexes unusable.

2.  Set the compression attribute.

3.  Rebuild the indexes.

The first time you make a compressed partition part of an existing, fully uncompressed partitioned table, you must either drop all existing bitmap indexes or mark them `UNUSABLE` before adding a compressed partition. This must be done irrespective of whether any partition contains any data. It is also independent of the operation that causes one or more compressed partitions to become part of the table. This does not apply to a partitioned table having B-tree indexes only.

This rebuilding of the bitmap index structures is necessary to accommodate the potentially higher number of rows stored for each data block with table compression enabled. Enabling table compression must be done only for the first time. All subsequent operations, whether they affect compressed or uncompressed partitions, or change the compression attribute, behave identically for uncompressed, partially compressed, or fully compressed partitioned tables.

To avoid the recreation of any bitmap index structure, Oracle recommends creating every partitioned table with at least one compressed partition whenever you plan to partially or fully compress the partitioned table in the future. This compressed partition can stay empty or even can be dropped after the partition table creation.

Having a partitioned table with compressed partitions can lead to slightly larger bitmap index structures for the uncompressed partitions. The bitmap index structures for the compressed partitions, however, are usually smaller than the appropriate bitmap index structure before table compression. This highly depends on the achieved compression rates.

**Note:**

Oracle Database raises an error if compression is introduced to an object for the first time and there are usable bitmap index segments.

### 3.4.2 Example of Table Compression and Partitioning

Examples of table compression with partitioned tables are described in this topic.

The following statement moves and compresses an existing partition `sales_q1_1998` of table `sales`:

    ALTER TABLE sales
      MOVE PARTITION sales_q1_1998 TABLESPACE ts_arch_q1_1998 COMPRESS;

Alternatively, you could choose Hybrid Columnar Compression (HCC), as in the following:

    ALTER TABLE sales
      MOVE PARTITION sales_q1_1998 TABLESPACE ts_arch_q1_1998
      COMPRESS FOR ARCHIVE LOW;

If you use the `MOVE` statement, then the local indexes for partition `sales_q1_1998` become unusable. You must rebuild them afterward, as follows:

    ALTER TABLE sales
      MODIFY PARTITION sales_q1_1998 REBUILD UNUSABLE LOCAL INDEXES;

You can also include the `UPDATE INDEXES` clause in the `MOVE` statement in order for the entire operation to be completed automatically without any negative effect on users accessing the table.

The following statement merges two existing partitions into a new, compressed partition, residing in a separate tablespace. The local bitmap indexes have to be rebuilt afterward, as in the following:

    ALTER TABLE sales MERGE PARTITIONS sales_q1_1998, sales_q2_1998
      INTO PARTITION sales_1_1998 TABLESPACE ts_arch_1_1998
      COMPRESS FOR OLTP UPDATE INDEXES;

**See Also:**

- [Partition Administration](partition-admin.md) for more details and examples about partition management operations

- [Oracle Database Performance Tuning Guide](../tgdba/configuring-database-for-performance.md) for details regarding how to estimate the compression ratio when using table compression

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for the SQL syntax

- [Oracle Database Concepts](../cncpt/tables-and-table-clusters.md) for more information about Hybrid Columnar Compression. Hybrid Columnar Compression is a feature of certain Oracle storage systems.
