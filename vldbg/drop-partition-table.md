Dropping partitioned tables is similar to dropping nonpartitioned tables.

Oracle Database processes a `DROP` `TABLE` statement for a partitioned table in the same way that it processes the statement for a nonpartitioned table. One exception is when you use the `PURGE` keyword.

To avoid running into resource constraints, the `DROP` `TABLE`...`PURGE` statement for a partitioned table drops the table in multiple transactions, where each transaction drops a subset of the partitions or subpartitions and then commits. The table is dropped at the conclusion of the final transaction.

This behavior comes with some changes to the `DROP` `TABLE` statement. First, if the `DROP` `TABLE`...`PURGE` statement fails, then you can take corrective action, if any, and then reissue the statement. The statement resumes at the point where it failed. Second, while the `DROP` `TABLE`...`PURGE` statement is in progress, the table is marked as unusable by setting the `STATUS` column to the value `UNUSABLE` in the following data dictionary views:

- `USER_TABLES`, `ALL_TABLES`, `DBA_TABLES`

- `USER_PART_TABLES`, `ALL_PART_TABLES`, `DBA_PART_TABLES`

- `USER_OBJECT_TABLES`, `ALL_OBJECT_TABLES`, `DBA_OBJECT_TABLES`

You can list all `UNUSABLE` partitioned tables by querying the `STATUS` column of these views.

Queries against other data dictionary views pertaining to partitioning, such as `DBA_TAB_PARTITIONS` and `DBA_TAB_SUBPARTITIONS`, exclude rows belonging to an `UNUSABLE` table.

After a table is marked `UNUSABLE`, the only statement that can be issued against it is another `DROP` `TABLE`...`PURGE` statement, and only if the previous `DROP` `TABLE`...`PURGE` statement failed. Any other statement issued against an `UNUSABLE` table results in an error. The table remains in the `UNUSABLE` state until the drop operation is complete.

**See Also:**

- [Viewing Information About Partitioned Tables and Indexes](view-info-partition-tables-indexes.md) for a list of these views that contain information related to partitioning

- [Oracle Database SQL Language Reference](../sqlrf/DROP-TABLE.md) for the syntax of the `DROP TABLE` statement

- [Oracle Database Reference](../refrn/about-static-data-dictionary-views.md) for a description of the data dictionary views mentioned in this section
