There are various maintenance operations that can be performed on partitions, subpartitions, and index partitions.

The maintenance operations that are supported on partitions, subpartitions, and index partitions are described in the following tables and topics.

- Table 4-1 lists partition maintenance operations that can be performed on partitioned tables and composite partitioned tables

- Table 4-2 lists subpartition maintenance operations that can be performed on composite partitioned tables

- Table 4-3 lists maintenance operations that can be performed on index partitions, and on which type of index (global or local) they can be performed

- Updating Indexes Automatically

- Asynchronous Global Index Maintenance for Dropping and Truncating Partitions

- Modifying a Subpartition Template

- Filtering Maintenance Operations

For each type of partitioning and subpartitioning in Table 4-1 and Table 4-2, the specific clause of the `ALTER TABLE` statement that is used to perform that maintenance operation is listed.

**Note:**

Partition maintenance operations on multiple partitions are not supported on tables with domain indexes.

Table 4-1 ALTER TABLE Maintenance Operations for Table Partitions

| Maintenance Operation                                                                                                    | RangeComposite Range-\*                              | IntervalComposite Interval-\*                        | Hash                                                 | ListComposite List-\*                                | Reference                                                                                                                                                            |
|:-------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------|:-----------------------------------------------------|:-----------------------------------------------------|:-----------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Adding Partitions, refer to [About Adding Partitions and Subpartitions](maintenance-partition-tables-indexes.md)         | `ADD PARTITION`, single and multiple partitions      | N/A                                                  | `ADD PARTITION`                                      | `ADD PARTITION`, single and multiple partitions      | N/A. (These operations cannot be performed on reference-partitioned tables. If performed on a parent table, then these operations cascade to all descendant tables.) |
| Coalescing Partitions, refer to [About Coalescing Partitions and Subpartitions](maintenance-partition-tables-indexes.md) | N/A                                                  | N/A                                                  | `COALESCE PARTITION`                                 | N/A                                                  | N/A (These operations cannot be performed on reference-partitioned tables. If performed on a parent table, then these operations cascade to all descendant tables.)  |
| Dropping Partitions, refer to [About Dropping Partitions and Subpartitions](maintenance-partition-tables-indexes.md)     | `DROP PARTITION`, single and multiple partitions     | `DROP PARTITION`, single and multiple partitions     | N/A                                                  | `DROP PARTITION`, single and multiple partitions     | N/A (These operations cannot be performed on reference-partitioned tables. If performed on a parent table, then these operations cascade to all descendant tables.)  |
| Exchanging Partitions, refer to [About Exchanging Partitions and Subpartitions](maintenance-partition-tables-indexes.md) | `EXCHANGE PARTITION`                                 | `EXCHANGE PARTITION`                                 | `EXCHANGE PARTITION`                                 | `EXCHANGE PARTITION`                                 | `EXCHANGE PARTITION`                                                                                                                                                 |
| Merging Partitions, refer to [About Merging Partitions and Subpartitions](maintenance-partition-tables-indexes.md)       | `MERGE PARTITIONS`, single and multiple partitions   | `MERGE PARTITIONS`, single and multiple partitions   | N/A                                                  | `MERGE PARTITIONS`, single and multiple partitions   | N/A (These operations cannot be performed on reference-partitioned tables. If performed on a parent table, then these operations cascade to all descendant tables.)  |
| [About Modifying Default Attributes](maintenance-partition-tables-indexes.md)                                            | `MODIFY DEFAULT ATTRIBUTES`                          | `MODIFY DEFAULT ATTRIBUTES`                          | `MODIFY DEFAULT ATTRIBUTES`                          | `MODIFY DEFAULT ATTRIBUTES`                          | `MODIFY DEFAULT ATTRIBUTES`                                                                                                                                          |
| [About Modifying Real Attributes of Partitions](maintenance-partition-tables-indexes.md)                                 | `MODIFY PARTITION`                                   | `MODIFY PARTITION`                                   | `MODIFY PARTITION`                                   | `MODIFY PARTITION`                                   | `MODIFY PARTITION`                                                                                                                                                   |
| [About Modifying List Partitions: Adding Values](maintenance-partition-tables-indexes.md)                                | N/A                                                  | N/A                                                  | N/A                                                  | `MODIFY PARTITION ADD VALUES`                        | N/A                                                                                                                                                                  |
| [About Modifying List Partitions: Dropping Values](maintenance-partition-tables-indexes.md)                              | N/A                                                  | N/A                                                  | N/A                                                  | `MODIFY PARTITION DROP VALUES`                       | N/A                                                                                                                                                                  |
| Moving Partitions, refer to [About Moving Partitions and Subpartitions](maintenance-partition-tables-indexes.md)         | `MOVE SUBPARTITION`                                  | `MOVE SUBPARTITION`                                  | `MOVE PARTITION`                                     | `MOVE SUBPARTITION`                                  | `MOVE PARTITION`                                                                                                                                                     |
| Renaming Partitions, refer to [About Renaming Partitions and Subpartitions](maintenance-partition-tables-indexes.md)     | `RENAME PARTITION`                                   | `RENAME PARTITION`                                   | `RENAME PARTITION`                                   | `RENAME PARTITION`                                   | `RENAME PARTITION`                                                                                                                                                   |
| Splitting Partitions, refer to [About Splitting Partitions and Subpartitions](maintenance-partition-tables-indexes.md)   | `SPLIT PARTITION`, single and multiple partitions    | `SPLIT PARTITION`, single and multiple partitions    | N/A                                                  | `SPLIT PARTITION`, single and multiple partitions    | N/A (These operations cannot be performed on reference-partitioned tables. If performed on a parent table, then these operations cascade to all descendant tables.)  |
| Truncating Partitions, refer to [About Truncating Partitions and Subpartitions](maintenance-partition-tables-indexes.md) | `TRUNCATE PARTITION`, single and multiple partitions | `TRUNCATE PARTITION`, single and multiple partitions | `TRUNCATE PARTITION`, single and multiple partitions | `TRUNCATE PARTITION`, single and multiple partitions | `TRUNCATE PARTITION`, single and multiple partitions                                                                                                                 |

Table 4-2 ALTER TABLE Maintenance Operations for Table Subpartitions

| Maintenance Operation                                                                                                                         | Composite \*-Range                                                     | Composite \*-Hash                                          | Composite \*-List                                                      |
|:----------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------|:-----------------------------------------------------------|:-----------------------------------------------------------------------|
| Adding Subpartitions, refer to [About Adding Partitions and Subpartitions](maintenance-partition-tables-indexes.md)                           | `MODIFY PARTITION ADD SUBPARTITION`, single and multiple subpartitions | `MODIFY PARTITION ADD SUBPARTITION`                        | `MODIFY PARTITION ADD SUBPARTITION`, single and multiple subpartitions |
| Coalescing Subpartitions, refer to [About Coalescing Partitions and Subpartitions](maintenance-partition-tables-indexes.md)                   | N/A                                                                    | `MODIFY PARTITION COALESCE SUBPARTITION`                   | N/A                                                                    |
| Dropping Subpartitions, refer to [About Dropping Partitions and Subpartitions](maintenance-partition-tables-indexes.md)                       | `DROP SUBPARTITION`, single and multiple subpartitions                 | N/A                                                        | `DROP SUBPARTITION`, single and multiple subpartitions                 |
| Exchanging Subpartitions, refer to [About Exchanging Partitions and Subpartitions](maintenance-partition-tables-indexes.md)                   | `EXCHANGE SUBPARTITION`                                                | N/A                                                        | `EXCHANGE SUBPARTITION`                                                |
| Merging Subpartitions, refer to [About Merging Partitions and Subpartitions](maintenance-partition-tables-indexes.md)                         | `MERGE SUBPARTITIONS`, single and multiple subpartitions               | N/A                                                        | `MERGE SUBPARTITIONS`, single and multiple subpartitions               |
| [About Modifying Default Attributes](maintenance-partition-tables-indexes.md)                                                                 | `MODIFY DEFAULT ATTRIBUTES FOR PARTITION`                              | `MODIFY DEFAULT ATTRIBUTES FOR PARTITION`                  | `MODIFY DEFAULT ATTRIBUTES FOR PARTITION`                              |
| Modifying Real Attributes of Subpartitions, refer to [About Modifying Real Attributes of Partitions](maintenance-partition-tables-indexes.md) | `MODIFY SUBPARTITION`                                                  | `MODIFY SUBPARTITION`                                      | `MODIFY SUBPARTITION`                                                  |
| Modifying List Subpartitions, refer to [About Modifying List Partitions: Adding Values](maintenance-partition-tables-indexes.md)              | N/A                                                                    | N/A                                                        | `MODIFY SUBPARTITION ADD VALUES`                                       |
| Modifying List Subpartitions, refer to [About Modifying List Partitions: Dropping Values](maintenance-partition-tables-indexes.md)            | N/A                                                                    | N/A                                                        | `MODIFY SUBPARTITION DROP VALUES`                                      |
| Modifying a Subpartition Template                                                                                                             | `SET SUBPARTITION TEMPLATE`                                            | `SET SUBPARTITION TEMPLATE`                                | `SET SUBPARTITION TEMPLATE`                                            |
| Moving Subpartitions, refer to [About Moving Partitions and Subpartitions](maintenance-partition-tables-indexes.md)                           | `MOVE SUBPARTITION`                                                    | `MOVE SUBPARTITION`                                        | `MOVE SUBPARTITION`                                                    |
| Renaming Subpartitions, refer to [About Renaming Partitions and Subpartitions](maintenance-partition-tables-indexes.md)                       | `RENAME SUBPARTITION`                                                  | `RENAME SUBPARTITION`                                      | `RENAME SUBPARTITION`                                                  |
| Splitting Subpartitions, refer to [About Splitting Partitions and Subpartitions](maintenance-partition-tables-indexes.md)                     | `SPLIT SUBPARTITION`, single and multiple subpartitions                | N/A                                                        | `SPLIT SUBPARTITION`, single and multiple subpartitions                |
| Truncating Subpartitions, refer to [About Truncating Partitions and Subpartitions](maintenance-partition-tables-indexes.md)                   | `TRUNCATE SUBPARTITION`, single and multiple subpartitions             | `TRUNCATE SUBPARTITION`, single and multiple subpartitions | `TRUNCATE SUBPARTITION`, single and multiple subpartitions             |

**Note:**

The first time you use table compression to introduce a compressed partition into a partitioned table that has bitmap indexes and that currently contains only uncompressed partitions, you must do the following:

- Either drop all existing bitmap indexes and bitmap index partitions, or mark them `UNUSABLE`.

- Set the table compression attribute.

- Rebuild the indexes.

These actions are independent of whether any partitions contain data and of the operation that introduces the compressed partition.

This does not apply to partitioned tables with B-tree indexes or to partitioned index-organized tables.

Table 4-3 lists maintenance operations that can be performed on index partitions, and indicates on which type of index (global or local) they can be performed. The `ALTER INDEX` clause used for the maintenance operation is shown.

Global indexes do not reflect the structure of the underlying table. If partitioned, they can be partitioned by range or hash.

Because local indexes reflect the underlying structure of the table, partitioning is maintained automatically when table partitions and subpartitions are affected by maintenance activity. Therefore, partition maintenance on local indexes is less necessary and there are fewer options.

Table 4-3 ALTER INDEX Maintenance Operations for Index Partitions

| Maintenance Operation                                                                       | Type of Index | Type of Index Partitioning  |                             |                                                                          |
|:--------------------------------------------------------------------------------------------|:--------------|:----------------------------|:----------------------------|:-------------------------------------------------------------------------|
| Range                                                                                       | Hash and List | Composite                   |                             |                                                                          |
| [Adding Index Partitions](maintenance-partition-tables-indexes.md)                          | Global        | `-`                         | `ADD PARTITION` (hash only) | \-                                                                       |
| [Adding Index Partitions](maintenance-partition-tables-indexes.md)                          | Local         | N/A                         | N/A                         | N/A                                                                      |
| [Dropping Index Partitions](maintenance-partition-tables-indexes.md)                        | Global        | `DROP PARTITION`            | \-                          | \-                                                                       |
| [Dropping Index Partitions](maintenance-partition-tables-indexes.md)                        | Local         | N/A                         | N/A                         | N/A                                                                      |
| [Modifying Default Attributes of Index Partitions](maintenance-partition-tables-indexes.md) | Global        | `MODIFY DEFAULT ATTRIBUTES` | \-                          | \-                                                                       |
| [Modifying Default Attributes of Index Partitions](maintenance-partition-tables-indexes.md) | Local         | `MODIFY DEFAULT ATTRIBUTES` | `MODIFY DEFAULT ATTRIBUTES` | `MODIFY DEFAULT ATTRIBUTES`<br>`MODIFY DEFAULT ATTRIBUTES FOR PARTITION` |
| [Modifying Real Attributes of Index Partitions](maintenance-partition-tables-indexes.md)    | Global        | `MODIFY PARTITION`          | \-                          | \-                                                                       |
| [Modifying Real Attributes of Index Partitions](maintenance-partition-tables-indexes.md)    | Local         | `MODIFY PARTITION`          | `MODIFY PARTITION`          | `MODIFY PARTITION`<br>`MODIFY SUBPARTITION`                              |
| [About Rebuilding Index Partitions](maintenance-partition-tables-indexes.md)                | Global        | `REBUILD PARTITION`         | \-                          | \-                                                                       |
| [About Rebuilding Index Partitions](maintenance-partition-tables-indexes.md)                | Local         | `REBUILD PARTITION`         | `REBUILD PARTITION`         | `REBUILD SUBPARTITION`                                                   |
| [About Renaming Index Partitions](maintenance-partition-tables-indexes.md)                  | Global        | `RENAME PARTITION`          | \-                          | \-                                                                       |
| [About Renaming Index Partitions](maintenance-partition-tables-indexes.md)                  | Local         | `RENAME PARTITION`          | `RENAME PARTITION`          | `RENAME PARTITION`<br>`RENAME SUBPARTITION`                              |
| [Splitting Index Partitions](maintenance-partition-tables-indexes.md)                       | Global        | `SPLIT PARTITION`           | \-                          | \-                                                                       |
| [Splitting Index Partitions](maintenance-partition-tables-indexes.md)                       | Local         | N/A                         | N/A                         | N/A                                                                      |

### 4.3.1 Updating Indexes Automatically

Before discussing the individual maintenance operations for partitioned tables and indexes, it is important to discuss the effects of the `UPDATE` `INDEXES` clause that can be specified in the `ALTER` `TABLE` statement.

By default, many table maintenance operations on partitioned tables invalidate (mark `UNUSABLE`) the corresponding indexes or index partitions. You must then rebuild the entire index or, for a global index, each of its partitions. The database lets you override this default behavior if you specify `UPDATE` `INDEXES` in your `ALTER` `TABLE` statement for the maintenance operation. Specifying this clause tells the database to update the indexes at the time it executes the maintenance operation DDL statement. This provides the following benefits:

- The indexes are updated with the base table operation. You are not required to update later and independently rebuild the indexes.

- The global indexes are more highly available, because they are not marked `UNUSABLE`. These indexes remain available even while the partition DDL is executing and can access unaffected partitions in the table.

- You need not look up the names of all invalid indexes to rebuild them.

Optional clauses for local indexes let you specify physical and storage characteristics for updated local indexes and their partitions.

- You can specify physical attributes, tablespace storage, and logging for each partition of each local index. Alternatively, you can specify only the `PARTITION` keyword and let the database update the partition attributes as follows:

  - For operations on a single table partition (such as `MOVE` `PARTITION` and `SPLIT` `PARTITION`), the corresponding index partition inherits the attributes of the affected table partition. The database does not generate names for new index partitions, so any new index partitions resulting from this operation inherit their names from the corresponding new table partition.

  - For `MERGE` `PARTITION` operations, the resulting local index partition inherits its name from the resulting table partition and inherits its attributes from the local index.

- For a composite-partitioned index, you can specify tablespace storage for each subpartition.

The following operations support the `UPDATE` `INDEXES` clause:

- `ADD` `PARTITION` \| `SUBPARTITION`

- `COALESCE` `PARTITION` \| `SUBPARTITION`

- `DROP` `PARTITION` \| `SUBPARTITION`

- `EXCHANGE` `PARTITION` \| `SUBPARTITION`

- `MERGE` `PARTITION` \| `SUBPARTITION`

- `MOVE` `PARTITION` \| `SUBPARTITION`

- `SPLIT` `PARTITION` \| `SUBPARTITION`

- `TRUNCATE` `PARTITION` \| `SUBPARTITION`

#### SKIP_UNUSABLE_INDEXES Initialization Parameter

`SKIP_UNUSABLE_INDEXES` is an initialization parameter with a default value of `TRUE`. This setting disables error reporting of indexes and index partitions marked `UNUSABLE`. If you do not want the database to choose an alternative execution plan to avoid the unusable elements, then you should set this parameter to `FALSE`.

#### Considerations when Updating Indexes Automatically

The following implications are worth noting when you specify `UPDATE` `INDEXES`:

- The partition DDL statement can take longer to execute, because indexes that were previously marked `UNUSABLE` are updated. However, you must compare this increase with the time it takes to execute DDL without updating indexes, and then rebuild all indexes. A rule of thumb is that it is faster to update indexes if the size of the partition is less that 5% of the size of the table.

- The `EXCHANGE` operation is no longer a fast operation. Again, you must compare the time it takes to do the DDL and then rebuild all indexes.

- When you update a table with a global index:

  - The index is updated in place. The updates to the index are logged, and redo and undo records are generated. In contrast, if you rebuild an entire global index, you can do so in `NOLOGGING` mode.

  - Rebuilding the entire index manually creates a more efficient index, because it is more compact with better space utilization.

- The `UPDATE INDEXES` clause is not supported for index-organized tables. However, the `UPDATE GLOBAL INDEXES` clause may be used with `DROP` `PARTITION`, `TRUNCATE` `PARTITION`, and `EXCHANGE` `PARTITION` operations to keep the global indexes on index-organized tables usable. For the remaining operations in the above list, global indexes on index-organized tables remain usable. In addition, local index partitions on index-organized tables remain usable after a `MOVE` `PARTITION` operation.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for information about the `update_all_indexes_clause` of `ALTER TABLE` in for the syntax for updating indexes

### 4.3.2 Asynchronous Global Index Maintenance for Dropping and Truncating Partitions

The partition maintenance operations `DROP` `PARTITION` and `TRUNCATE` `PARTITION` are optimized by making the index maintenance for metadata only.

Asynchronous global index maintenance for `DROP` and `TRUNCATE` is performed by default; however, the `UPDATE` `INDEXES` clause is still required for backward compatibility.

The following list summarizes the limitations of asynchronous global index maintenance:

- Only performed on heap tables

- No support for tables with object types

- No support for tables with domain indexes

- Not performed for the user SYS

Maintenance operations on indexes can be performed with the automatic scheduler job `SYS.PMO_DEFERRED_GIDX_MAINT_JOB` to clean up all global indexes. This job is scheduled to run on a regular basis by default. You can run this job at any time using `DBMS_SCHEDULER.RUN_JOB` if you want to proactively clean up the indexes. You can also modify the job to run with a schedule based on your specific requirements. Oracle recommends that you do not drop the job.

You can also force cleanup of an index needing maintenance using one of the following options:

- `DBMS_PART.CLEANUP_GIDX` - This PL/SQL procedure gathers the list of global indexes in the system that may require cleanup and runs the operations necessary to restore the indexes to a clean state.

- `ALTER` `INDEX` `REBUILD` \[`PARTITION`\] – This SQL statement rebuilds the entire index or index partition as is done in releases previous to Oracle Database 12c Release 1 (12.1). The resulting index (partition) does not contain any stale entries.

- `ALTER` `INDEX` \[`PARTITION`\] `COALESCE` `CLEANUP` – This SQL statement cleans up any orphaned entries in index blocks.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/scheduling-jobs-with-oracle-scheduler.md) for information about managing jobs with Oracle Scheduler

### 4.3.3 Modifying a Subpartition Template

You can modify a subpartition template of a composite partitioned table by replacing it with a new subpartition template.

Any subsequent operations that use the subpartition template (such as `ADD` `PARTITION` or `MERGE` `PARTITIONS`) now use the new subpartition template. Existing subpartitions remain unchanged.

If you modify a subpartition template of an interval-\* composite partitioned table, then interval partitions that have not yet been created use the new subpartition template.

Use the `ALTER` `TABLE` `SET` `SUBPARTITION` `TEMPLATE` statement to specify a new subpartition template. For example:

    ALTER TABLE employees_sub_template
       SET SUBPARTITION TEMPLATE
             (SUBPARTITION e TABLESPACE ts1,
              SUBPARTITION f TABLESPACE ts2,
              SUBPARTITION g TABLESPACE ts3,
              SUBPARTITION h TABLESPACE ts4
             );

You can drop a subpartition template by specifying an empty list:

    ALTER TABLE employees_sub_template
       SET SUBPARTITION TEMPLATE ( );

### 4.3.4 Filtering Maintenance Operations

Partition maintenance operations support the addition of data filtering, enabling the combination of partition and data maintenance.

A filtered partition maintenance operation only preserves the data satisfying the data filtering as part of the partition maintenance. The capability of data filtering applies to `MOVE` `PARTITION`, `MERGE` `PARTITION`, and `SPLIT` `PARTITION` .

Example 4-27 shows the use of the `ALTER TABLE` statement to move a partition while removing all orders that are not open (closed orders).

The filtering predicate must be on the partitioned table. All partition maintenance operations that can be performed online (`MOVE` and `SPLIT`) can also be performed as filtered partition maintenance operations. With `ONLINE` specified, DML operations on the partitions being maintained are allowed.

Filtered partition maintenance operations performed in online mode do not enforce the filter predicate on concurrent ongoing DML operations. The filter condition is only applied one time at the beginning of the partition maintenance operation. Consequently, any subsequent DML succeeds, but is ignored from a filtering perspective. Records that do not match the filter condition when the partition maintenance started are not preserved, regardless of any DML operation. Newly inserted records are inserted if they match the partition key criteria, regardless of whether they satisfy the filter condition of the partition maintenance operation. Filter conditions are limited to the partitioned table itself and do not allow any reference to other tables, such as a join or subquery expression.

Consider the following scenarios when the keyword `ONLINE` is specified in the SQL statement of Example 4-27.

- An existing order record in partition `q1_2016` that is updated to `status='open'` after the partition maintenance operation has started is not be preserved in the partition.

- A new order record with `status='closed'` can be inserted in partition `q1_2016` after the partition maintenance operation has started and while the partition maintenance operation is ongoing.

Example 4-27 Using a filtering clause when performing maintenance operations

    ALTER TABLE orders_move_part
      MOVE PARTITION q1_2016 TABLESPACE open_orders COMPRESS ONLINE
      INCLUDING ROWS WHERE order_state = 'open';

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for the exact syntax of the partitioning clauses for creating and altering partitioned tables and indexes, any restrictions on their use, and specific privileges required for creating and altering tables
