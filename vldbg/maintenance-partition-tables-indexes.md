There are various maintenance operations that can be performed on partitioned tables and indexes.

The operations to perform partition and subpartition maintenance for both tables and indexes are discussed in the following topics.

- About Adding Partitions and Subpartitions

- About Coalescing Partitions and Subpartitions

- About Dropping Partitions and Subpartitions

- About Exchanging Partitions and Subpartitions

- About Merging Partitions and Subpartitions

- About Modifying Attributes of Tables, Partitions, and Subpartitions

- About Modifying List Partitions

- About Modifying the Partitioning Strategy

- About Moving Partitions and Subpartitions

- About Rebuilding Index Partitions

- About Renaming Partitions and Subpartitions

- About Splitting Partitions and Subpartitions

- About Truncating Partitions and Subpartitions

**Note:**

Where the usability of indexes or index partitions affected by the maintenance operation is discussed, consider the following:

- Only indexes and index partitions that are not empty are candidates for being marked `UNUSABLE`. If they are empty, the `USABLE`/`UNUSABLE` status is left unchanged.

- Only indexes or index partitions with `USABLE` status are updated by subsequent DML.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-tables.md) for information about managing tables

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for the exact syntax of the partitioning clauses for altering partitioned tables and indexes, any restrictions on their use, and specific privileges required for creating and altering tables

### 4.4.1 Restrictions and Special Requirements for Multi-Partition Operations on Tables with Domain Indexes

These constraints apply to multi-partition `ADD`, `MERGE`, `SPLIT`, `DROP`, and `TRUNCATE` operations on a table which has a domain index created on it.

#### About Tables With a Local Domain Index

If a table has a local domain index, then `ADD`, `SPLIT`, and `DROP` operations on multiple partitions or subpartitions in the same statement are not allowed. Each partition or subpartition can be operated on in a separate statement only.

For `MERGE` operations on a table with a local domain index, two partitions are allowed.

If a table has a local domain index, performing `TRUNCATE` on a single partition or the entire table is supported. Truncating multiple partitions in a single `ALTER TABLE` statement is not permitted if a local domain index is present.

#### About Tables With a Global Domain Index

The restrictions on multi-partition operations described above apply to local domain indexes only. For tables with global domain indexes, multi-partition operations are supported.

**Note:**

For a table that has a global index, when you use a single statement to operate on multiple partitions it is important to include an `UPDATE INDEXES` clause in the statement, otherwise the index is rendered unusable.

#### Checking for Indexes

Before performing `ADD`, `SPLIT`, `DROP` or `MERGE` operations on multiple partitions, you can check for indexes through the `ALL_INDEXES` view. For example:

    SELECT owner, index_name FROM SYS.ALL_INDEXES WHERE index_type IN ('DOMAIN', 'FUNCTION-BASED DOMAIN');

The query can be narrowed down by adding specific `TABLE_OWNER` and `TABLE_NAME` predicates. For example:

    SELECT owner, index_name FROM SYS.ALL_INDEXES WHERE index_type IN ('DOMAIN', 'FUNCTION-BASED DOMAIN') WHERE table_owner = 'MY_USER' AND table_name = 'MY_PART_TABLE';

### 4.4.2 About Adding Partitions and Subpartitions

This section introduces how to manually add new partitions to a partitioned table and explains why partitions cannot be specifically added to most partitioned indexes.

This section contains the following topics:

- Adding a Partition to a Range-Partitioned Table

- Adding a Partition to a Hash-Partitioned Table

- Adding a Partition to a List-Partitioned Table

- Adding a Partition to an Interval-Partitioned Table

- About Adding Partitions to a Composite \*-Hash Partitioned Table

- About Adding Partitions to a Composite \*-List Partitioned Table

- About Adding Partitions to a Composite \*-Range Partitioned Table

- About Adding a Partition or Subpartition to a Reference-Partitioned Table

- Adding Index Partitions

- Adding Multiple Partitions

**Note:**

See Restrictions and Special Requirements for Multi-Partition Operations on Tables with Domain Indexes

#### 4.4.2.1 Adding a Partition to a Range-Partitioned Table

You can add a partition after the last existing partition of a table or the beginning of a table or in the middle of a table.

Use the `ALTER` `TABLE` `ADD` `PARTITION` statement to add a new partition to the "high" end (the point after the last existing partition). To add a partition at the beginning or in the middle of a table, use the `SPLIT` `PARTITION` clause.

For example, consider the table, `sales`, which contains data for the current month in addition to the previous 12 months. On January 1, 1999, you add a partition for January, which is stored in tablespace `tsx`.

    ALTER TABLE sales
          ADD PARTITION jan99 VALUES LESS THAN ( '01-FEB-1999' )
          TABLESPACE tsx;

Local and global indexes associated with the range-partitioned table remain usable.

#### 4.4.2.2 Adding a Partition to a Hash-Partitioned Table

When you add a partition to a hash partitioned table, the database populates the new partition with rows rehashed from an existing partition (selected by the database) as determined by the hash function.

Consequently, if the table contains data, then it may take some time to add a hash partition.

The following statements show two ways of adding a hash partition to table `scubagear`. Choosing the first statement adds a new hash partition whose partition name is system generated, and which is placed in the default tablespace. The second statement also adds a new hash partition, but that partition is explicitly named `p_named` and is created in tablespace `gear5`.

    ALTER TABLE scubagear ADD PARTITION;

    ALTER TABLE scubagear
          ADD PARTITION p_named TABLESPACE gear5;

Indexes may be marked `UNUSABLE` as explained in the following table:

| Table Type      | Index Behavior                                                                                                                                                                                                                                                                                                                                                   |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Regular (Heap)  | Unless you specify `UPDATE` `INDEXES` as part of the `ALTER` `TABLE` statement:<br>• The local indexes for the new partition, and for the existing partition from which rows were redistributed, are marked `UNUSABLE` and must be rebuilt.<br>• All global indexes, or all partitions of partitioned global indexes, are marked `UNUSABLE` and must be rebuilt. |
| Index-organized | • For local indexes, the behavior is identical to heap tables.<br>• All global indexes remain usable.                                                                                                                                                                                                                                                            |

#### 4.4.2.3 Adding a Partition to a List-Partitioned Table

The example in this topic shows how to add a partition to a list-partitioned table.

The following statement illustrates how to add a new partition to a list-partitioned table. In this example, physical attributes and `NOLOGGING` are specified for the partition being added.

    ALTER TABLE q1_sales_by_region
       ADD PARTITION q1_nonmainland VALUES ('HI', 'PR')
          STORAGE (INITIAL 20K NEXT 20K) TABLESPACE tbs_3
          NOLOGGING;

Any value in the set of literal values that describe the partition being added must not exist in any of the other partitions of the table.

You cannot add a partition to a list-partitioned table that has a default partition, but you can split the default partition. By doing so, you effectively create a new partition defined by the values that you specify, and a second partition that remains the default partition.

Local and global indexes associated with the list-partitioned table remain usable.

#### 4.4.2.4 Adding a Partition to an Interval-Partitioned Table

You cannot explicitly add a partition to an interval-partitioned table. The database automatically creates a partition for an interval when data for that interval is inserted.

However, exchanging a partition of an interval-partitioned table that has not been materialized in the data dictionary, meaning to have an explicit entry in the data dictionary beyond the interval definition, you must manually materialize the partition using the `ALTER` `TABLE` `LOCK` `PARTITION` command.

To change the interval for future partitions, use the `SET INTERVAL` clause of the `ALTER TABLE` statement. The `SET INTERVAL` clause converts existing interval partitions to range partitions, determines the high value of the defined range partitions, and automatically creates partitions of the specified interval as needed for data that is beyond that high value. As a side effect, an interval-partitioned table does not have the notation of `MAXVALUES`.

You also use the `SET INTERVAL` clause to migrate an existing range partitioned or range-\* composite partitioned table into an interval or interval-\* partitioned table. To disable the creation of future interval partitions, and effectively revert to a range-partitioned table, use an empty value in the `SET INTERVAL` clause. Created interval partitions are transformed into range partitions with their current high values.

To increase the interval for date ranges, you must ensure that you are at a relevant boundary for the new interval. For example, if the highest interval partition boundary in your daily interval partitioned table transactions is January 30, 2007 and you want to change to a monthly partition interval, then the following statement results in an error:

    ALTER TABLE transactions SET INTERVAL (NUMTOYMINTERVAL(1,'MONTH');

    ORA-14767: Cannot specify this interval with existing high bounds

You must create another daily partition with a high bound of February 1, 2007 to successfully change to a monthly interval:

    LOCK TABLE transactions PARTITION FOR(TO_DATE('31-JAN-2007','dd-MON-yyyy')
       IN SHARE MODE;

    ALTER TABLE transactions SET INTERVAL (NUMTOYMINTERVAL(1,'MONTH');

The lower partitions of an interval-partitioned table are range partitions. You can split range partitions to add more partitions in the range portion of the interval-partitioned table.

To disable interval partitioning on the `transactions` table, use:

    ALTER TABLE transactions SET INTERVAL ();

#### 4.4.2.5 About Adding Partitions to a Composite \*-Hash Partitioned Table

Partitions can be added at both the partition level and at the hash subpartition level.

- Adding a Partition to a \*-Hash Partitioned Table

- Adding a Subpartition to a \*-Hash Partitioned Table

##### 4.4.2.5.1 Adding a Partition to a \*-Hash Partitioned Table

The example in this topic shows how to add a new partition to a \[range \| list \| interval\]-hash partitioned table.

For an interval-hash partitioned table, interval partitions are automatically created. You can specify a `SUBPARTITIONS` clause that lets you add a specified number of subpartitions, or a `SUBPARTITION` clause for naming specific subpartitions. If no `SUBPARTITIONS` or `SUBPARTITION` clause is specified, then the partition inherits table level defaults for subpartitions. For an interval-hash partitioned table, you can only add subpartitions to range or interval partitions that have been materialized.

This example adds a range partition `q1_2000` to the range-hash partitioned table `sales`, which is populated with data for the first quarter of the year 2000. There are eight subpartitions stored in tablespace `tbs5`. The subpartitions cannot be set explicitly to use table compression. Subpartitions inherit the compression attribute from the partition level and are stored in a compressed form in this example:

    ALTER TABLE sales ADD PARTITION q1_2000
          VALUES LESS THAN (2000, 04, 01) COMPRESS
          SUBPARTITIONS 8 STORE IN tbs5;

##### 4.4.2.5.2 Adding a Subpartition to a \*-Hash Partitioned Table

Use the `MODIFY` `PARTITION` `ADD` `SUBPARTITION` clause of the `ALTER` `TABLE` statement to add a hash subpartition to a \[range \| list \| interval\]-hash partitioned table.

The newly added subpartition is populated with rows rehashed from other subpartitions of the same partition as determined by the hash function. For an interval-hash partitioned table, you can only add subpartitions to range or interval partitions that have been materialized.

In the following example, a new hash subpartition `us_loc5`, stored in tablespace `us1`, is added to range partition `locations_us` in table `diving`.

    ALTER TABLE diving MODIFY PARTITION locations_us
          ADD SUBPARTITION us_locs5 TABLESPACE us1;

Index subpartitions corresponding to the added and rehashed subpartitions must be rebuilt unless you specify `UPDATE` `INDEXES`.

#### 4.4.2.6 About Adding Partitions to a Composite \*-List Partitioned Table

Partitions can be added at both the partition level and at the list subpartition level.

- Adding a Partition to a \*-List Partitioned Table

- Adding a Subpartition to a \*-List Partitioned Table

##### 4.4.2.6.1 Adding a Partition to a \*-List Partitioned Table

The example in this topic shows how to add a new partition to a \[range \| list \| interval\]-list partitioned table.

The database automatically creates interval partitions as data for a specific interval is inserted. You can specify `SUBPARTITION` clauses for naming and providing value lists for the subpartitions. If no `SUBPARTITION` clauses are specified, then the partition inherits the subpartition template. If there is no subpartition template, then a single default subpartition is created.

The statement in Example 4-28 adds a new partition to the `quarterly_regional_sales` table that is partitioned by the range-list method. Some new physical attributes are specified for this new partition while table-level defaults are inherited for those that are not specified.

Example 4-28 Adding partitions to a range-list partitioned table

    ALTER TABLE quarterly_regional_sales
       ADD PARTITION q1_2000 VALUES LESS THAN (TO_DATE('1-APR-2000','DD-MON-YYYY'))
          STORAGE (INITIAL 20K NEXT 20K) TABLESPACE ts3 NOLOGGING
             (
              SUBPARTITION q1_2000_northwest VALUES ('OR', 'WA'),
              SUBPARTITION q1_2000_southwest VALUES ('AZ', 'UT', 'NM'),
              SUBPARTITION q1_2000_northeast VALUES ('NY', 'VM', 'NJ'),
              SUBPARTITION q1_2000_southeast VALUES ('FL', 'GA'),
              SUBPARTITION q1_2000_northcentral VALUES ('SD', 'WI'),
              SUBPARTITION q1_2000_southcentral VALUES ('OK', 'TX')
             );

##### 4.4.2.6.2 Adding a Subpartition to a \*-List Partitioned Table

Use the `MODIFY` `PARTITION` `ADD` `SUBPARTITION` clause of the `ALTER` `TABLE` statement to add a list subpartition to a \[range \| list \| interval\]-list partitioned table.

For an interval-list partitioned table, you can only add subpartitions to range or interval partitions that have been materialized.

The following statement adds a new subpartition to the existing set of subpartitions in the range-list partitioned table `quarterly_regional_sales`. The new subpartition is created in tablespace `ts2`.

    ALTER TABLE quarterly_regional_sales
       MODIFY PARTITION q1_1999
          ADD SUBPARTITION q1_1999_south
             VALUES ('AR','MS','AL') tablespace ts2;

#### 4.4.2.7 About Adding Partitions to a Composite \*-Range Partitioned Table

Partitions can be added at both the partition level and at the range subpartition level.

- Adding a Partition to a \*-Range Partitioned Table

- Adding a Subpartition to a \*-Range Partitioned Table

##### 4.4.2.7.1 Adding a Partition to a \*-Range Partitioned Table

The example in this topic shows how to add a new partition to a \[range \| list \| interval\]-range partitioned table.

The database automatically creates interval partitions for an interval-range partitioned table when data is inserted in a specific interval. You can specify a `SUBPARTITION` clause for naming and providing ranges for specific subpartitions. If no `SUBPARTITION` clause is specified, then the partition inherits the subpartition template specified at the table level. If there is no subpartition template, then a single subpartition with a maximum value of `MAXVALUE` is created.

Example 4-29 adds a range partition `p_2007_jan` to the range-range partitioned table `shipments`, which is populated with data for the shipments ordered in January 2007. There are three subpartitions. Subpartitions inherit the compression attribute from the partition level and are stored in a compressed form in this example:

Example 4-29 Adding partitions to a range-range partitioned table

    ALTER TABLE shipments
       ADD PARTITION p_2007_jan
          VALUES LESS THAN (TO_DATE('01-FEB-2007','dd-MON-yyyy')) COMPRESS
          ( SUBPARTITION p07_jan_e VALUES LESS THAN (TO_DATE('15-FEB-2007','dd-MON-yyyy'))
          , SUBPARTITION p07_jan_a VALUES LESS THAN (TO_DATE('01-MAR-2007','dd-MON-yyyy'))
          , SUBPARTITION p07_jan_l VALUES LESS THAN (TO_DATE('01-APR-2007','dd-MON-yyyy'))
          ) ;

##### 4.4.2.7.2 Adding a Subpartition to a \*-Range Partitioned Table

You use the `MODIFY` `PARTITION` `ADD` `SUBPARTITION` clause of the `ALTER` `TABLE` statement to add a range subpartition to a \[range \| list \| interval\]-range partitioned table.

For an interval-range partitioned table, you can only add partitions to range or interval partitions that have been materialized.

The following example adds a range subpartition to the `shipments` table that contains all values with an `order_date` in January 2007 and a `delivery_date` on or after April 1, 2007.

    ALTER TABLE shipments
       MODIFY PARTITION p_2007_jan
          ADD SUBPARTITION p07_jan_vl VALUES LESS THAN (MAXVALUE) ;

#### 4.4.2.8 About Adding a Partition or Subpartition to a Reference-Partitioned Table

A partition or subpartition can be added to a parent table in a reference partition definition just as partitions and subpartitions can be added to a range, hash, list, or composite partitioned table.

The add operation automatically cascades to any descendant reference partitioned tables. The `DEPENDENT TABLES` clause can set specific properties for dependent tables when you add partitions or subpartitions to a master table.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md)

#### 4.4.2.9 Adding Index Partitions

You cannot explicitly add a partition to a local index. Instead, a new partition is added to a local index only when you add a partition to the underlying table.

Specifically, when there is a local index defined on a table and you issue the `ALTER` `TABLE` statement to add a partition, a matching partition is also added to the local index. The database assigns names and default physical storage attributes to the new index partitions, but you can rename or alter them after the `ADD` `PARTITION` operation is complete.

You can effectively specify a new tablespace for an index partition in an `ADD` `PARTITION` operation by first modifying the default attributes for the index. For example, assume that a local index, `q1_sales_by_region_locix`, was created for list partitioned table `q1_sales_by_region`. If before adding the new partition `q1_nonmainland`, as shown in Adding a Partition to a List-Partitioned Table, you had issued the following statement, then the corresponding index partition would be created in tablespace `tbs_4`.

    ALTER INDEX q1_sales_by_region_locix
       MODIFY DEFAULT ATTRIBUTES TABLESPACE tbs_4;

Otherwise, it would be necessary for you to use the following statement to move the index partition to `tbs_4` after adding it:

    ALTER INDEX q1_sales_by_region_locix
       REBUILD PARTITION q1_nonmainland TABLESPACE tbs_4;


You can add a partition to a hash partitioned global index using the `ADD` `PARTITION` syntax of `ALTER` `INDEX`. The database adds hash partitions and populates them with index entries rehashed from an existing hash partition of the index, as determined by the hash function. The following statement adds a partition to the index `hgidx` shown in [Creating a Hash Partitioned Global Index](partition-create-tables-indexes.md):

    ALTER INDEX hgidx ADD PARTITION p5;

You cannot add a partition to a range-partitioned global index, because the highest partition always has a partition bound of `MAXVALUE`. To add a new highest partition, use the `ALTER` `INDEX` `SPLIT` `PARTITION` statement.

#### 4.4.2.10 Adding Multiple Partitions

You can add multiple new partitions and subpartitions with the `ADD` `PARTITION` and `ADD` `SUBPARTITION` clauses of the same `ALTER` `TABLE` statement.

When adding multiple partitions, local and global index operations are the same as when adding a single partition. Adding multiple partitions and subpartitions is only supported for range, list, and system partitions and subpartitions.

You can add multiple range partitions that are listed in ascending order of their upper bound values to the high end (after the last existing partition) of a range-partitioned or composite range-partitioned table, provided the `MAXVALUE` partition is not defined. Similarly, you can add multiple list partitions to a table using new sets of partition values if the `DEFAULT` partition does not exist.

Multiple system partitions can be added using a single SQL statement by specifying the individual partitions. For example, the following SQL statement adds multiple partitions to the range-partitioned `sales` table created in [Example 4-1](partition-create-tables-indexes.md):

    ALTER TABLE sales ADD
      PARTITION sales_q1_2007 VALUES LESS THAN (TO_DATE('01-APR-2007','dd-MON-yyyy')),
      PARTITION sales_q2_2007 VALUES LESS THAN (TO_DATE('01-JUL-2007','dd-MON-yyyy')),
      PARTITION sales_q3_2007 VALUES LESS THAN (TO_DATE('01-OCT-2007','dd-MON-yyyy')),
      PARTITION sales_q4_2007 VALUES LESS THAN (TO_DATE('01-JAN-2008','dd-MON-yyyy'))
    ;

You can use the `BEFORE` clause to add multiple new system partitions in relation to only one existing partition. The following SQL statements provide an example of adding multiple individual partitions using the `BEFORE` clause:

    CREATE TABLE system_part_tab1 (number1 integer, number2 integer)
    PARTITION BY SYSTEM
    ( PARTITION p1,
      PARTITION p2,
      PARTITION p3,
      PARTITION p_last);

    ALTER TABLE system_part_tab1 ADD
      PARTITION p4,
      PARTITION p5,
      PARTITION p6
      BEFORE PARTITION p_last;

    SELECT SUBSTR(TABLE_NAME,1,18) table_name, TABLESPACE_NAME,
       SUBSTR(PARTITION_NAME,1,16) partition_name
       FROM USER_TAB_PARTITIONS WHERE TABLE_NAME='SYSTEM_PART_TAB1';
    TABLE_NAME         TABLESPACE_NAME                PARTITION_NAME
    ------------------ ------------------------------ ----------------
    SYSTEM_PART_TAB1   USERS                          P_LAST
    SYSTEM_PART_TAB1   USERS                          P6
    SYSTEM_PART_TAB1   USERS                          P5
    SYSTEM_PART_TAB1   USERS                          P4
    SYSTEM_PART_TAB1   USERS                          P3
    SYSTEM_PART_TAB1   USERS                          P2
    SYSTEM_PART_TAB1   USERS                          P1

**Note:**

See Restrictions and Special Requirements for Multi-Partition Operations on Tables with Domain Indexes

### 4.4.3 About Coalescing Partitions and Subpartitions

Coalescing partitions is a way of reducing the number of partitions in a hash partitioned table or index, or the number of subpartitions in a \*-hash partitioned table.

When a hash partition is coalesced, its contents are redistributed into one or more remaining partitions determined by the hash function. The specific partition that is coalesced is selected by the database, and is dropped after its contents have been redistributed. If you coalesce a hash partition or subpartition in the parent table of a reference-partitioned table definition, then the reference-partitioned table automatically inherits the new partitioning definition.

Index partitions may be marked `UNUSABLE` as explained in the following table:

| Table Type      | Index Behavior                                                                                                                                                                                                                                                                                                                                                                                                       |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Regular (Heap)  | Unless you specify `UPDATE` `INDEXES` as part of the `ALTER` `TABLE` statement:<br>• Any local index partition corresponding to the selected partition is also dropped. Local index partitions corresponding to the one or more absorbing partitions are marked `UNUSABLE` and must be rebuilt.<br>• All global indexes, or all partitions of partitioned global indexes, are marked `UNUSABLE` and must be rebuilt. |
| Index-organized | • Some local indexes are marked `UNUSABLE` as noted for heap indexes.<br>• All global indexes remain usable.                                                                                                                                                                                                                                                                                                         |

This section contains the following topics:

- Coalescing a Partition in a Hash Partitioned Table

- Coalescing a Subpartition in a \*-Hash Partitioned Table

- Coalescing Hash Partitioned Global Indexes

#### 4.4.3.1 Coalescing a Partition in a Hash Partitioned Table

The `ALTER` `TABLE` `COALESCE` `PARTITION` statement is used to coalesce a partition in a hash partitioned table.

The following statement reduces by one the number of partitions in a table by coalescing a partition.

    ALTER TABLE ouu1
         COALESCE PARTITION;

#### 4.4.3.2 Coalescing a Subpartition in a \*-Hash Partitioned Table

The `ALTER` `TABLE` `COALESCE` `SUBPARTITION` statement is used to coalesce a subpartition in a hash partitioned table.

The following statement distributes the contents of a subpartition of partition `us_locations` into one or more remaining subpartitions (determined by the hash function) of the same partition. For an interval-partitioned table, you can only coalesce hash subpartitions of materialized range or interval partitions. Basically, this operation is the inverse of the `MODIFY` `PARTITION` `ADD` `SUBPARTITION` clause discussed in Adding a Subpartition to a \*-Hash Partitioned Table.

    ALTER TABLE diving MODIFY PARTITION us_locations
         COALESCE SUBPARTITION;

#### 4.4.3.3 Coalescing Hash Partitioned Global Indexes

You can instruct the database to reduce by one the number of index partitions in a hash partitioned global index using the `COALESCE` `PARTITION` clause of `ALTER` `INDEX`.

The database selects the partition to coalesce based on the requirements of the hash partition. The following statement reduces by one the number of partitions in the `hgidx` index, created in [Creating a Hash Partitioned Global Index](partition-create-tables-indexes.md):

    ALTER INDEX hgidx COALESCE PARTITION;

### 4.4.4 About Dropping Partitions and Subpartitions

You can drop partitions from range, interval, list, or composite \*-\[range \| list\] partitioned tables.

For interval partitioned tables, you can only drop range or interval partitions that have been materialized. For hash partitioned tables, or hash subpartitions of composite \*-hash partitioned tables, you must perform a coalesce operation instead.

You cannot drop a partition from a reference-partitioned table. Instead, a drop operation on a parent table cascades to all descendant tables.

This section contains the following topics:

- Dropping Table Partitions

- Dropping Interval Partitions

- Dropping Index Partitions

- Dropping Multiple Partitions

#### 4.4.4.1 Dropping Table Partitions

To drop table partitions, use `DROP` `PARTITION` or `DROP` `SUBPARTITION` with the `ALTER` `TABLE` SQL statement.

The following statements drop a table partition or subpartition:

- `ALTER` `TABLE` `DROP` `PARTITION` to drop a table partition

- `ALTER` `TABLE` `DROP` `SUBPARTITION` to drop a subpartition of a composite \*-\[range \| list\] partitioned table

To preserve the data in the partition, use the `MERGE` `PARTITION` statement instead of the `DROP` `PARTITION` statement.

To remove data in the partition without dropping the partition, use the `TRUNCATE` `PARTITION` statement.

If local indexes are defined for the table, then this statement also drops the matching partition or subpartitions from the local index. All global indexes, or all partitions of partitioned global indexes, are marked `UNUSABLE` unless either of the following is true:

- You specify `UPDATE` `INDEXES` (Cannot be specified for index-organized tables. Use `UPDATE` `GLOBAL` `INDEXES` instead.)

- The partition being dropped or its subpartitions are empty.

**Note:**

- If a table contains only one partition, you cannot drop the partition. Instead, you must drop the table.

- You cannot drop the highest range partition in the range-partitioned section of an interval-partitioned or interval-\* composite partitioned table.

- With asynchronous global index maintenance, a drop partition update indexes operation is on metadata only and all global indexes remain valid.

- Dropping a partition does not place the partition in the Oracle Database recycle bin, regardless of the setting of the recycle bin. Dropped partitions are immediately removed from the system.

The following sections contain some scenarios for dropping table partitions.

- Dropping a Partition from a Table that Contains Data and Global Indexes

- Dropping a Partition Containing Data and Referential Integrity Constraints

**See Also:**

- About Merging Partitions and Subpartitions for information about merging a partition

- About Truncating Partitions and Subpartitions for information about truncating a partition

- [Asynchronous Global Index Maintenance for Dropping and Truncating Partitions](maintenance-partition-can-be-performed.md) for information about asynchronous index maintenance for dropping partitions

##### 4.4.4.1.1 Dropping a Partition from a Table that Contains Data and Global Indexes

There are several methods you can use to drop a partition from a table that contains data and global indexes.

If the partition contains data and one or more global indexes are defined on the table, then use one of the following methods (method 1, 2 or 3) to drop the table partition.

##### Method 1

Issue the `ALTER` `TABLE` `DROP` `PARTITION` statement without maintaining global indexes. Afterward, you must rebuild any global indexes (whether partitioned or not) because the index (or index partitions) has been marked `UNUSABLE`. The following statements provide an example of dropping partition `dec98` from the `sales` table, then rebuilding its global nonpartitioned index.

    ALTER TABLE sales DROP PARTITION dec98;
    ALTER INDEX sales_area_ix REBUILD;

If index `sales_area_ix` were a range-partitioned global index, then all partitions of the index would require rebuilding. Further, it is not possible to rebuild all partitions of an index in one statement. You must issue a separate `REBUILD` statement for each partition in the index. The following statements rebuild the index partitions `jan99_ix` to `dec99_ix`.

    ALTER INDEX sales_area_ix REBUILD PARTITION jan99_ix;
    ALTER INDEX sales_area_ix REBUILD PARTITION feb99_ix;
    ALTER INDEX sales_area_ix REBUILD PARTITION mar99_ix;
    ...
    ALTER INDEX sales_area_ix REBUILD PARTITION dec99_ix;

This method is most appropriate for large tables where the partition being dropped contains a significant percentage of the total data in the table. While asynchronous global index maintenance keeps global indexes valid without the need of any index maintenance, you must use the `UPDATE` `INDEXES` clause to enable this new functionality. This behavior ensures backward compatibility.

##### Method 2

Issue the `DELETE` statement to delete all rows from the partition before you issue the `ALTER` `TABLE` `DROP` `PARTITION` statement. The `DELETE` statement updates the global indexes.

For example, to drop the first partition, issue the following statements:

    DELETE FROM sales partition (dec98);
    ALTER TABLE sales DROP PARTITION dec98;

This method is most appropriate for small tables, or for large tables when the partition being dropped contains a small percentage of the total data in the table.

##### Method 3

Specify `UPDATE` `INDEXES` in the `ALTER` `TABLE` statement. Doing so leverages the new asynchronous global index maintenance. Indexes remain valid.

    ALTER TABLE sales DROP PARTITION dec98
         UPDATE INDEXES;

##### 4.4.4.1.2 Dropping a Partition Containing Data and Referential Integrity Constraints

There are several methods you can use to drop a partition containing data and referential integrity constraints.

If a partition contains data and the table has referential integrity constraints, choose either of the following methods (method 1 or 2) to drop the table partition. This table has a local index only, so it is not necessary to rebuild any indexes.

##### Method 1

If there is no data referencing the data in the partition to drop, then you can disable the integrity constraints on the referencing tables, issue the `ALTER` `TABLE` `DROP` `PARTITION` statement, then re-enable the integrity constraints.

This method is most appropriate for large tables where the partition being dropped contains a significant percentage of the total data in the table. If there is still data referencing the data in the partition to be dropped, then ensure the removal of all the referencing data so that you can re-enable the referential integrity constraints.

##### Method 2

If there is data in the referencing tables, then you can issue the `DELETE` statement to delete all rows from the partition before you issue the `ALTER` `TABLE` `DROP` `PARTITION` statement. The `DELETE` statement enforces referential integrity constraints, and also fires triggers and generates redo and undo logs. The delete can succeed if you created the constraints with the `ON DELETE CASCADE` option, deleting all rows from referencing tables as well.

    DELETE FROM sales partition (dec94);
    ALTER TABLE sales DROP PARTITION dec94;

This method is most appropriate for small tables or for large tables when the partition being dropped contains a small percentage of the total data in the table.

#### 4.4.4.2 Dropping Interval Partitions

You can drop interval partitions in an interval-partitioned table.

This operation drops the data for the interval only and leaves the interval definition in tact. If data is inserted in the interval just dropped, then the database again creates an interval partition.

You can also drop range partitions in an interval-partitioned table. The rules for dropping a range partition in an interval-partitioned table follow the rules for dropping a range partition in a range-partitioned table. If you drop a range partition in the middle of a set of range partitions, then the lower boundary for the next range partition shifts to the lower boundary of the range partition you just dropped. You cannot drop the highest range partition in the range-partitioned section of an interval-partitioned table.

The following example drops the September 2007 interval partition from the `sales` table. There are only local indexes so no indexes are invalidated.

    ALTER TABLE sales DROP PARTITION FOR(TO_DATE('01-SEP-2007','dd-MON-yyyy'));

#### 4.4.4.3 Dropping Index Partitions

You cannot explicitly drop a partition of a local index. Instead, local index partitions are dropped only when you drop a partition from the underlying table.

If a global index partition is empty, then you can explicitly drop it by issuing the `ALTER` `INDEX` `DROP` `PARTITION` statement. But, if a global index partition contains data, then dropping the partition causes the next highest partition to be marked `UNUSABLE`. For example, you would like to drop the index partition P1, and P2 is the next highest partition. You must issue the following statements:

    ALTER INDEX npr DROP PARTITION P1;
    ALTER INDEX npr REBUILD PARTITION P2;

**Note:**

You cannot drop the highest partition in a global index.

#### 4.4.4.4 Dropping Multiple Partitions

You can remove multiple partitions or subpartitions from a range or list partitioned table with the `DROP` `PARTITION` and `DROP` `SUBPARTITION` clauses of the SQL `ALTER` `TABLE` statement.

For example, the following SQL statement drops multiple partitions from the range-partitioned table `sales`.

    ALTER TABLE sales DROP PARTITION sales_q1_2008, sales_q2_2008,
         sales_q3_2008, sales_q4_2008;

You cannot drop all the partitions of a table. When dropping multiple partitions, local and global index operations are the same as when dropping a single partition.

**See Also:**

Restrictions and Special Requirements for Multi-Partition Operations on Tables with Domain Indexes.

### 4.4.5 About Exchanging Partitions and Subpartitions

You can convert a partition or subpartition into a nonpartitioned table, and a nonpartitioned table into a partition or subpartition of a partitioned table by exchanging their data segments.

You can also convert a hash partitioned table into a partition of a composite \*-hash partitioned table, or convert the partition of a composite \*-hash partitioned table into a hash partitioned table. Similarly, you can convert a range- or list-partitioned table into a partition of a composite \*-range or -list partitioned table, or convert a partition of the composite \*-range or -list partitioned table into a range- or list-partitioned table.

Exchanging table partitions is useful to get data quickly in or out of a partitioned table. For example, in data warehousing environments, exchanging partitions facilitates high-speed data loading of new, incremental data into an existing partitioned table.

Note that during the exchange process the data from the source is moved to the target and the data from the target is moved to the source.

OLTP and data warehousing environments benefit from exchanging old data partitions out of a partitioned table. The data is purged from the partitioned table without actually being deleted and can be archived separately afterward.

When you exchange partitions, logging attributes are preserved. You can optionally specify if local indexes are also to be exchanged with the `INCLUDING` `INDEXES` clause, and if rows are to be validated for proper mapping with the `WITH` `VALIDATION` clause.

**Note:**

When you specify `WITHOUT` `VALIDATION` for the exchange partition operation, this is normally a fast operation because it involves only data dictionary updates. However, if the table or partitioned table involved in the exchange operation has a primary key or unique constraint enabled, then the exchange operation is performed as if `WITH` `VALIDATION` were specified to maintain the integrity of the constraints.

To avoid the overhead of this validation activity, issue the following statement for each constraint before performing the exchange partition operation:

    ALTER TABLE table_name
         DISABLE CONSTRAINT constraint_name KEEP INDEX

Enable the constraints after the exchange.

If you specify `WITHOUT` `VALIDATION`, then you must ensure that the data to be exchanged belongs in the partition you exchange. You can use the `ORA_PARTITION_VALIDATION` SQL function to help identify those records that have been inserted incorrectly in the wrong partition.

Unless you specify `UPDATE` `INDEXES`, the Oracle Database marks the global indexes or all global index partitions on the table whose partition is being exchanged as `UNUSABLE`. Global indexes or global index partitions on the table being exchanged remain invalidated.

You cannot use `UPDATE` `INDEXES` for index-organized tables. Use `UPDATE` `GLOBAL` `INDEXES` instead.

Incremental statistics on a partitioned table are maintained with a partition exchange operation if the statistics were gathered on the nonpartitioned table when `DBMS_STATS` table preferences `INCREMENTAL` is set to true and `INCREMENTAL_LEVEL` is set to `TABLE`.

**Note:**

In situations where column statistics for virtual columns are out of order, the column statistics are deleted rather than retaining the stale statistics. Information about this deletion is written to the alert log file.

This section contains the following topics:

- Creating a Table for Exchange With a Partitioned Table

- Exchanging a Range, Hash, or List Partition

- Exchanging a Partition of an Interval Partitioned Table

- Exchanging a Partition of a Reference-Partitioned Table

- About Exchanging a Partition of a Table with Virtual Columns

- Exchanging a Hash Partitioned Table with a \*-Hash Partition

- Exchanging a Subpartition of a \*-Hash Partitioned Table

- Exchanging a List-Partitioned Table with a \*-List Partition

- About Exchanging a Subpartition of a \*-List Partitioned Table

- Exchanging a Range-Partitioned Table with a \*-Range Partition

- About Exchanging a Subpartition of a \*-Range Partitioned Table

- About Exchanging a Partition with the Cascade Option

**See Also:**

- [Partitioning Key](partition-concepts.md) for information about validating partition content

- [Viewing Information About Partitioned Tables and Indexes](view-info-partition-tables-indexes.md) for information about using views to monitor details about partitioned tables and indexes

- [Oracle Database SQL Tuning Guide](../tgsql/gathering-optimizer-statistics.md) for more information about incremental statistics

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md) for information about the `DBMS_STATS` package

#### 4.4.5.1 Creating a Table for Exchange With a Partitioned Table

Tables can be created with the `FOR` `EXCHANGE` `WITH` clause to exactly match the shape of a partitioned table and be eligible for a partition exchange command. However, indexes are not created as an operation of this command.

Because the `FOR` `EXCHANGE` `WITH` clause of `CREATE` `TABLE` provides an exact match between a non-partitioned and partitioned table, this is an improvement over the `CREATE` `TABLE` `AS` `SELECT` statement.

The following list is a summary of the effects of the `CREATE` `TABLE` `FOR EXCHANGE WITH` DDL operation:

- The use case of this DDL operation is to facilitate creation of a table to be used for exchange partition DDL.

- The operation creates a clone of the for exchange table in terms of column ordering and column properties.

- Columns cannot be renamed. The table being created inherits the names from the for exchange table.

- The only logical property that can be specified during the DDL operation is the partitioning specification of the table.

  The partitioning clause is only relevant for the exchange with a partition of a composite-partitioned table. In this case, a partition with n subpartitions is exchanged with a partitioned table with n partitions matching the subpartitions. You are responsible for the definition of the partitioning clause for this exchange in this scenario.

  The subpartitioning can be asymmetrical across partitions. The partitioning clause has to match exactly the subpartitioning of the partition to being exchanged.

- The physical properties which can be specified are primarily table segment attributes.

- Column properties copied with this DDL operation include, but are not limited to, the following: unusable columns, invisible columns, virtual expression columns, functional index expression columns, and other internal settings and attributes.

The following is an example of the use of the `CREATE` `TABLE` statement with the `FOR` `EXCHANGE` `WITH` clause to create a table that mimics the shape of an existing table in terms of column ordering and properties.

Example 4-30 Using the FOR EXCHANGE WITH clause of CREATE TABLE

    CREATE TABLE sales_by_year_table
      ( prod_id       NUMBER        NOT NULL,
        cust_id       NUMBER        NOT NULL,
        time_id       DATE          NOT NULL,
        channel_id    NUMBER        NOT NULL,
        promo_id      NUMBER        NOT NULL,
        quantity_sold NUMBER(10,2)  NOT NULL,
        amount_sold   NUMBER(10,2)  NOT NULL
      )
        PARTITION BY RANGE (time_id)
         (PARTITION sales_2016 VALUES LESS THAN (TO_DATE('01-01-2017','dd-mm-yyyy')),
          PARTITION sales_2017 VALUES LESS THAN (TO_DATE('01-01-2018','dd-mm-yyyy')),
          PARTITION sales_2018 VALUES LESS THAN (TO_DATE('01-01-2019','dd-mm-yyyy')),
          PARTITION sales_2019 VALUES LESS THAN (TO_DATE('01-01-2020','dd-mm-yyyy')),
          PARTITION sales_future VALUES LESS THAN (MAXVALUE)
     );

    DESCRIBE sales_by_year_table
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     PROD_ID                                   NOT NULL NUMBER
     CUST_ID                                   NOT NULL NUMBER
     TIME_ID                                   NOT NULL DATE
     CHANNEL_ID                                NOT NULL NUMBER
     PROMO_ID                                  NOT NULL NUMBER
     QUANTITY_SOLD                             NOT NULL NUMBER(10,2)
     AMOUNT_SOLD                               NOT NULL NUMBER(10,2)

    CREATE TABLE sales_later_year_table
      FOR EXCHANGE WITH TABLE sales_by_year_table;

    DESCRIBE sales_later_year_table
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     PROD_ID                                   NOT NULL NUMBER
     CUST_ID                                   NOT NULL NUMBER
     TIME_ID                                   NOT NULL DATE
     CHANNEL_ID                                NOT NULL NUMBER
     PROMO_ID                                  NOT NULL NUMBER
     QUANTITY_SOLD                             NOT NULL NUMBER(10,2)
     AMOUNT_SOLD                               NOT NULL NUMBER(10,2)

#### 4.4.5.2 Exchanging a Range, Hash, or List Partition

To exchange a partition of a range, hash, or list partitioned table with a nonpartitioned table, or the reverse, use the `ALTER` `TABLE` `EXCHANGE` `PARTITION` statement.

The following is an example of exchanging range partitions with a nonpartitioned table.

Example 4-31 Exchanging a Range Partition

    CREATE TABLE sales_future_table
      ( prod_id       NUMBER        NOT NULL,
        cust_id       NUMBER        NOT NULL,
        time_id       DATE          NOT NULL,
        channel_id    NUMBER        NOT NULL,
        promo_id      NUMBER        NOT NULL,
        quantity_sold NUMBER(10,2)  NOT NULL,
        amount_sold   NUMBER(10,2)  NOT NULL
      )
        PARTITION BY RANGE (time_id)
         (PARTITION s_2020 VALUES LESS THAN (TO_DATE('01-01-2021','dd-mm-yyyy')),
          PARTITION s_2021 VALUES LESS THAN (TO_DATE('01-01-2022','dd-mm-yyyy')),
          PARTITION s_2022 VALUES LESS THAN (TO_DATE('01-01-2023','dd-mm-yyyy'))
     );

    CREATE TABLE sales_exchange_table
      FOR EXCHANGE WITH TABLE sales_future_table;

    INSERT INTO sales_exchange_table VALUES (1002,110,TO_DATE('19-02-2020','dd-mm-yyyy'),12,18,150,4800);
    INSERT INTO sales_exchange_table VALUES (1001,100,TO_DATE('12-03-2020','dd-mm-yyyy'),10,15,400,6500);
    INSERT INTO sales_exchange_table VALUES (1001,100,TO_DATE('31-05-2020','dd-mm-yyyy'),10,15,600,8000);
    INSERT INTO sales_exchange_table VALUES (2105,101,TO_DATE('25-06-2020','dd-mm-yyyy'),12,19,100,3000);
    INSERT INTO sales_exchange_table VALUES (1002,120,TO_DATE('31-08-2020','dd-mm-yyyy'),10,15,400,6000);
    INSERT INTO sales_exchange_table VALUES (2105,101,TO_DATE('25-10-2020','dd-mm-yyyy'),12,19,250,7500);

    ALTER TABLE sales_future_table
        EXCHANGE PARTITION s_2020 WITH TABLE sales_exchange_table;

    SELECT * FROM sales_future_table PARTITION(s_2020);
       PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          1002        110 19-FEB-20         12         18           150        4800
          1001        100 12-MAR-20         10         15           400        6500
          1001        100 31-MAY-20         10         15           600        8000
          2105        101 25-JUN-20         12         19           100        3000
          1002        120 31-AUG-20         10         15           400        6000
          2105        101 25-OCT-20         12         19           250        7500
    6 rows selected.

    REM Note that all records have been removed from the sales_exchange_table
    SELECT * FROM sales_exchange_table;
    no rows selected

    INSERT INTO sales_exchange_table VALUES (1002,110,TO_DATE('15-02-2021','dd-mm-yyyy'),12,18,300,9500);
    INSERT INTO sales_exchange_table VALUES (1002,120,TO_DATE('31-03-2021','dd-mm-yyyy'),10,15,200,3000);
    INSERT INTO sales_exchange_table VALUES (2105,101,TO_DATE('25-04-2021','dd-mm-yyyy'),12,19,150,9000);

    ALTER TABLE sales_future_table
        EXCHANGE PARTITION s_2021 WITH TABLE sales_exchange_table;

    SELECT * FROM sales_future_table PARTITION(s_2021);
       PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          1002        110 15-FEB-21         12         18           300        9500
          1002        120 31-MAR-21         10         15           200        3000
          2105        101 25-APR-21         12         19           150        9000
    3 rows selected.

#### 4.4.5.3 Exchanging a Partition of an Interval Partitioned Table

You can exchange interval partitions in an interval-partitioned table. However, you must ensure that the interval partition has been created before you can exchange the partition.

The following example shows a partition exchange for the `interval_sales` table, interval-partitioned using monthly partitions as of January 1, 2007. This example shows how to add data for June 2007 to the table using partition exchange load. Assume there are only local indexes on the `interval_sales` table, and equivalent indexes have been created on the `interval_sales_june_2007` table.

    ALTER TABLE interval_sales
      EXCHANGE PARTITION FOR (TO_DATE('01-JUN-2007','dd-MON-yyyy'))
      WITH TABLE interval_sales_jun_2007
      INCLUDING INDEXES;

Note the use of the `FOR` syntax to identify a partition that was system-generated. You can determine the partition name by querying the `*_TAB_PARTITIONS` data dictionary view to display the system-generated partition name.

#### 4.4.5.4 Exchanging a Partition of a Reference-Partitioned Table

You can exchange partitions in a reference-partitioned table, but you must ensure that the data that you reference is available in the respective partition in the parent table.

Example 4-32 shows a partition exchange load scenario for the range-partitioned `orders` table, and the reference partitioned `order_items` table. The data in the `order_items_2018_dec` table only contains order item data for orders with an `order_date` in December 2018.

You must use the `UPDATE GLOBAL INDEXES` or `UPDATE INDEXES` on the exchange partition of the parent table in order for the primary key index to remain usable. Note also that you must create or enable the foreign key constraint on the `order_items_2018_dec` table in order for the partition exchange on the reference-partitioned table to succeed.

For information and an example using exchanging with the `CASCADE` keyword, refer to About Exchanging a Partition with the Cascade Option.

Example 4-32 Exchanging a partition for a reference-partitioned table

    CREATE TABLE orders (
           order_id number NOT NULL,
           order_date DATE,
           CONSTRAINT order_pk PRIMARY KEY (order_id))
           PARTITION by range (order_date)
           (PARTITION p_2018_dec values less than ('01-JAN-2019'));

    CREATE TABLE order_items  (
           order_item_id NUMBER NOT NULL,
           order_id NUMBER not null,
           order_item VARCHAR2(100),
           CONSTRAINT order_item_pk PRIMARY KEY (order_item_id),
           CONSTRAINT order_item_fk FOREIGN KEY (order_id) references orders(order_id) on delete cascade)
           PARTITION by reference (order_item_fk);

    CREATE TABLE orders_2018_dec (
           order_id NUMBER,
           order_date DATE,
           CONSTRAINT order_2018_dec_pk PRIMARY KEY (order_id));

    INSERT into orders_2018_dec values (1,'01-DEC-2018');
    COMMIT;

    CREATE TABLE order_items_2018_dec (
           order_item_id NUMBER,
           order_id NUMBER NOT NULL,
           order_item VARCHAR2(100),
           CONSTRAINT order_item_2018_dec_pk PRIMARY KEY (order_item_id),
           CONSTRAINT order_item_2018_dec_fk FOREIGN KEY (order_id) references orders_2018_dec (order_id) on delete cascade);

    INSERT into order_items_2018_dec values (1,1,'item A');
    INSERT into order_items_2018_dec values (2,1,'item B');

    REM You must disable or DROP the constraint before the exchange
    ALTER TABLE order_items_2018_dec DROP CONSTRAINT order_item_2018_dec_fk;

    REM ALTER TABLE is successful with disabled PK-FK
    ALTER TABLE orders
      EXCHANGE PARTITION p_2018_dec
      WITH TABLE orders_2018_dec
      UPDATE GLOBAL INDEXES;

    REM You must establish the PK-FK with the future parent prior to this exchange
    ALTER TABLE order_items_2018_dec
      ADD CONSTRAINT order_items_dec_2018_fk
      FOREIGN KEY (order_id)
      REFERENCES orders(order_id) ;

    REM Complete the exchange
    ALTER TABLE order_items
      EXCHANGE PARTITION p_2018_dec
      WITH TABLE order_items_2018_dec;

    REM Display the data
    SELECT * FROM orders;
      ORDER_ID ORDER_DAT
    ---------- ---------
             1 01-DEC-18

    SELECT * FROM order_items;
    ORDER_ITEM_ID   ORDER_ID ORDER_ITEM
    ------------- ---------- ------------
                1          1 item A
                2          1 item B

#### 4.4.5.5 About Exchanging a Partition of a Table with Virtual Columns

You can exchange partitions in the presence of virtual columns.

In order for a partition exchange on a partitioned table with virtual columns to succeed, you must create a table that matches the definition of all non-virtual columns in a single partition of the partitioned table. You do not need to include the virtual column definitions, unless constraints or indexes have been defined on the virtual column.

In this case, you must include the virtual column definition to match the partitioned table's constraint and index definitions. This scenario also applies to virtual column-based partitioned tables.

#### 4.4.5.6 Exchanging a Hash Partitioned Table with a \*-Hash Partition

You can exchange a whole hash partitioned table, with all of its partitions, with the partition of a \*-hash partitioned table and all of its hash subpartitions.

The following example illustrates this concept for a range-hash partitioned table.

First, create a hash partitioned table:

    CREATE TABLE t1 (i NUMBER, j NUMBER)
         PARTITION BY HASH(i)
           (PARTITION p1, PARTITION p2);

Populate the table, then create a range-hash partitioned table as follows:

    CREATE TABLE t2 (i NUMBER, j NUMBER)
         PARTITION BY RANGE(j)
         SUBPARTITION BY HASH(i)
            (PARTITION p1 VALUES LESS THAN (10)
                (SUBPARTITION t2_pls1,
                 SUBPARTITION t2_pls2),
             PARTITION p2 VALUES LESS THAN (20)
                (SUBPARTITION t2_p2s1,
                 SUBPARTITION t2_p2s2)
             );

It is important that the partitioning key in table `t1` equals the subpartitioning key in table `t2`.

To migrate the data in `t1` to `t2`, and validate the rows, use the following statement:

    ALTER TABLE t2 EXCHANGE PARTITION p1 WITH TABLE t1
         WITH VALIDATION;

#### 4.4.5.7 Exchanging a Subpartition of a \*-Hash Partitioned Table

You can use the `ALTER` `TABLE` `EXCHANGE` `SUBPARTITION` statement to convert a hash subpartition of a \*-hash partitioned table into a nonpartitioned table, or the reverse.

The following example converts the subpartition `q3_1999_s1` of table `sales` into the nonpartitioned table `q3_1999`. Local index partitions are exchanged with corresponding indexes on `q3_1999`.

    ALTER TABLE sales EXCHANGE SUBPARTITION q3_1999_s1
          WITH TABLE q3_1999 INCLUDING INDEXES;

#### 4.4.5.8 Exchanging a List-Partitioned Table with a \*-List Partition

You can use the `ALTER` `TABLE` `EXCHANGE` `PARTITION` statement to exchange a list-partitioned table with a \*-list partition.

The semantics are the same as described previously in Exchanging a Hash Partitioned Table with a \*-Hash Partition. The following example shows an exchange partition scenario for a list-list partitioned table.

    CREATE TABLE customers_apac
    ( id            NUMBER
    , name          VARCHAR2(50)
    , email         VARCHAR2(100)
    , region        VARCHAR2(4)
    , credit_rating VARCHAR2(1)
    )
    PARTITION BY LIST (credit_rating)
    ( PARTITION poor VALUES ('P')
    , PARTITION mediocre VALUES ('C')
    , PARTITION good VALUES ('G')
    , PARTITION excellent VALUES ('E')
    );

Populate the table with APAC customers. Then create a list-list partitioned table:

    CREATE TABLE customers
    ( id            NUMBER
    , name          VARCHAR2(50)
    , email         VARCHAR2(100)
    , region        VARCHAR2(4)
    , credit_rating VARCHAR2(1)
    )
    PARTITION BY LIST (region)
    SUBPARTITION BY LIST (credit_rating)
    SUBPARTITION TEMPLATE
    ( SUBPARTITION poor VALUES ('P')
    , SUBPARTITION mediocre VALUES ('C')
    , SUBPARTITION good VALUES ('G')
    , SUBPARTITION excellent VALUES ('E')
    )
    (PARTITION americas VALUES ('AMER')
    , PARTITION emea VALUES ('EMEA')
    , PARTITION apac VALUES ('APAC')
    );

It is important that the partitioning key in the `customers_apac` table matches the subpartitioning key in the `customers` table.

Next, exchange the `apac` partition.

    ALTER TABLE customers
    EXCHANGE PARTITION apac
    WITH TABLE customers_apac
    WITH VALIDATION;

#### 4.4.5.9 About Exchanging a Subpartition of a \*-List Partitioned Table

You can use the `ALTER` `TABLE` `EXCHANGE` `SUBPARTITION` statement to exchange a subpartition of a \*-list partitioned table.

The semantics of the `ALTER` `TABLE``EXCHANGE` `SUBPARTITION` statement are the same as described previously in Exchanging a Subpartition of a \*-Hash Partitioned Table.

#### 4.4.5.10 Exchanging a Range-Partitioned Table with a \*-Range Partition

You can use the `ALTER` `TABLE` `EXCHANGE` `PARTITION` statement to exchange a range-partitioned table with a \*-range partition.

The semantics of the `ALTER` `TABLE` `EXCHANGE` `PARTITION` statement are the same as described previously in Exchanging a Hash Partitioned Table with a \*-Hash Partition. The example below shows the `orders` table, which is interval partitioned by `order_date`, and subpartitioned by range on `order_total`. The example shows how to exchange a single monthly interval with a range-partitioned table.

    CREATE TABLE orders_mar_2007
     ( id          NUMBER
      , cust_id     NUMBER
      , order_date  DATE
      , order_total NUMBER
     )
    PARTITION BY RANGE (order_total)
     ( PARTITION p_small VALUES LESS THAN (1000)
      , PARTITION p_medium VALUES LESS THAN (10000)
      , PARTITION p_large VALUES LESS THAN (100000)
      , PARTITION p_extraordinary VALUES LESS THAN (MAXVALUE)
     );

Populate the table with orders for March 2007. Then create an interval-range partitioned table:

    CREATE TABLE orders
     ( id          NUMBER
      , cust_id     NUMBER
      , order_date  DATE
      , order_total NUMBER
     )
    PARTITION BY RANGE (order_date) INTERVAL (NUMTOYMINTERVAL(1,'MONTH'))
      SUBPARTITION BY RANGE (order_total)
      SUBPARTITION TEMPLATE
      ( SUBPARTITION p_small VALUES LESS THAN (1000)
       , SUBPARTITION p_medium VALUES LESS THAN (10000)
       , SUBPARTITION p_large VALUES LESS THAN (100000)
       , SUBPARTITION p_extraordinary VALUES LESS THAN (MAXVALUE)
      )
     (PARTITION p_before_2007 VALUES LESS THAN (TO_DATE('01-JAN-2007','dd-MON-yyyy')));

It is important that the partitioning key in the `orders_mar_2007` table matches the subpartitioning key in the `orders` table.

Next, exchange the partition.

    ALTER TABLE orders
      EXCHANGE PARTITION
       FOR (TO_DATE('01-MAR-2007','dd-MON-yyyy'))
       WITH TABLE orders_mar_2007
       WITH VALIDATION;

#### 4.4.5.11 About Exchanging a Subpartition of a \*-Range Partitioned Table

You can use the `ALTER` `TABLE` `EXCHANGE` `SUBPARTITION` statement to exchange a subpartition of a \*-range partition.

The semantics of the `ALTER` `TABLE` `EXCHANGE` `SUBPARTITION` are the same as described previously in Exchanging a Subpartition of a \*-Hash Partitioned Table.

#### 4.4.5.12 About Exchanging a Partition with the Cascade Option

You can cascade exchange operations to reference partitioned child tables with the `CASCADE` option of the `ALTER` `TABLE` `EXCHANGE` `PARTITION` and `ALTER` `TABLE` `EXCHANGE` `SUBPARTITION` SQL statements.

Cascading exchange operations require all foreign key constraints to being defined as `ON` `DELETE` `CASCADE`.

When the `CASCADE` option for `ALTER` `TABLE` `EXCHANGE` `PARTITION` and `ALTER` `TABLE` `EXCHANGE` `SUBPARTITION` is specified, the `EXCHANGE` operation cascades to reference partitioned tables that are children of the targeted table. The exchange operation can be targeted at any level in a reference partitioned hierarchy and cascades to child tables starting from the targeted table. Privileges are not required on the child tables, but ordinary restrictions on the exchange operation apply for all tables affected by the operation. The `CASCADE` option is ignored if it is specified for a table that does not have reference partitioned children.

The reference partitioned hierarchy of the targeted table and the reference partitioned hierarchy of the exchange table must match. The `CASCADE` option is not supported if the same parent key is referenced by multiple dependent tables. Having more than one dependent table relying on the same primary key makes it impossible for the kernel to unambiguously identify how to exchange the dependent partitions. Any other options specified for the operation, such as `UPDATE` `INDEXES`, applies for all tables affected by the operation.

The cascade options are off by default so they do not affect Oracle Database compatibility.

The following example shows the use of `CASCADE` when exchanging the a partition of a referenced-partitioned table.

Example 4-33 Exchanging a partition using cascade for a reference-partitioned table

    CREATE TABLE orders (
           order_id number NOT NULL,
           order_date DATE,
           CONSTRAINT order_pk PRIMARY KEY (order_id))
           PARTITION by range (order_date)
           (PARTITION p_2018_dec values less than ('01-JAN-2019'));

    CREATE TABLE order_items  (
           order_item_id NUMBER NOT NULL,
           order_id NUMBER not null,
           order_item VARCHAR2(100),
           CONSTRAINT order_item_pk PRIMARY KEY (order_item_id),
           CONSTRAINT order_item_fk FOREIGN KEY (order_id) references orders(order_id) on delete cascade)
           PARTITION by reference (order_item_fk);

    CREATE TABLE orders_2018_dec (
           order_id NUMBER,
           order_date DATE,
           CONSTRAINT order_2018_dec_pk PRIMARY KEY (order_id));

    INSERT into orders_2018_dec values (1,'01-DEC-2018');

    CREATE TABLE order_items_2018_dec (
           order_item_id NUMBER,
           order_id NUMBER NOT NULL,
           order_item VARCHAR2(100),
           CONSTRAINT order_item_2018_dec_pk PRIMARY KEY (order_item_id),
           CONSTRAINT order_item_2018_dec_fk FOREIGN KEY (order_id) references orders_2018_dec (order_id) on delete cascade);

    INSERT into order_items_2018_dec values (1,1,'item A new');
    INSERT into order_items_2018_dec values (2,1,'item B new');

    REM Display data from reference partitioned tables before exchange
    SELECT * FROM orders;
    no rows selected

    SELECT * FROM order_items;
    no rows selected

    REM ALTER TABLE using cascading exchange
    ALTER TABLE orders
       EXCHANGE PARTITION p_2018_dec
       WITH TABLE orders_2018_dec
        CASCADE
       UPDATE GLOBAL INDEXES;

    REM Display data from reference partitioned tables after exchange
    SELECT * FROM orders;
      ORDER_ID ORDER_DAT
    ---------- ---------
             1 01-DEC-18

    SELECT * FROM order_items;
    ORDER_ITEM_ID   ORDER_ID ORDER_ITEM
    ------------- ---------- ------------
                1          1 item A new
                2          1 item B new

### 4.4.6 About Merging Partitions and Subpartitions

Use the `ALTER` `TABLE` `MERGE` `PARTITION` and `SUBPARTITION` SQL statements to merge the contents of two partitions or subpartitions.

The two original partitions or subpartitions are dropped, as are any corresponding local indexes. You cannot use this statement for a hash partitioned table or for hash subpartitions of a composite \*-hash partitioned table.

You cannot merge partitions for a reference-partitioned table. Instead, a merge operation on a parent table cascades to all descendant tables. However, you can use the `DEPENDENT TABLES` clause to set specific properties for dependent tables when you issue the merge operation on the parent table to merge partitions or subpartitions.

You can use the `ONLINE` keyword with the `ALTER` `TABLE` `MERGE` `PARTITION` and `SUBPARTITION` SQL statements to enable online merge operations for regular (heap-organized) tables. For an example of the use of the `ONLINE` keyword, see Example 4-34.

If the involved partitions or subpartitions contain data, then indexes may be marked `UNUSABLE` as described in the following table:

| Table Type      | Index Behavior                                                                                                                                                                                                                                                                                           |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Regular (Heap)  | Unless you specify `UPDATE` `INDEXES` as part of the `ALTER` `TABLE` statement:<br>• The database marks `UNUSABLE` all resulting corresponding local index partitions or subpartitions.<br>• Global indexes, or all partitions of partitioned global indexes, are marked `UNUSABLE` and must be rebuilt. |
| Index-organized | • The database marks `UNUSABLE` all resulting corresponding local index partitions.<br>• All global indexes remain usable.                                                                                                                                                                               |

This section contains the following topics:

- Merging Range Partitions

- Merging Interval Partitions

- Merging List Partitions

- Merging \*-Hash Partitions

- About Merging \*-List Partitions

- About Merging \*-Range Partitions

- Merging Multiple Partitions

**See Also:**

Restrictions and Special Requirements for Multi-Partition Operations on Tables with Domain Indexes

[Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md)

#### 4.4.6.1 Merging Range Partitions

You can merge the contents of two adjacent range partitions into one partition.

Nonadjacent range partitions cannot be merged. The resulting partition inherits the higher upper bound of the two merged partitions.

One reason for merging range partitions is to keep historical data online in larger partitions. For example, you can have daily partitions, with the oldest partition rolled up into weekly partitions, which can then be rolled up into monthly partitions, and so on.

Example 4-34 shows an example of merging range partitions using the `ONLINE` keyword.

Example 4-34 Merging range partitions

    -- First, create a partitioned table with four partitions, each on its own
    -- tablespace, partitioned by range on the date column
    --
    CREATE TABLE four_seasons
    (       one DATE,
            two VARCHAR2(60),
          three NUMBER
    )
    PARTITION BY RANGE (one)
    (
    PARTITION quarter_one
       VALUES LESS THAN ( TO_DATE('01-APR-2017','dd-mon-yyyy'))
       TABLESPACE quarter_one,
    PARTITION quarter_two
       VALUES LESS THAN ( TO_DATE('01-JUL-2017','dd-mon-yyyy'))
       TABLESPACE quarter_two,
    PARTITION quarter_three
       VALUES LESS THAN ( TO_DATE('01-OCT-2017','dd-mon-yyyy'))
       TABLESPACE quarter_three,
    PARTITION quarter_four
       VALUES LESS THAN ( TO_DATE('01-JAN-2018','dd-mon-yyyy'))
       TABLESPACE quarter_four
    );
    --
    -- Create local PREFIXED indexes on four_seasons
    -- Prefixed because the leftmost columns of the index match the
    -- Partitioning key
    --
    CREATE INDEX i_four_seasons_l ON four_seasons (one,two)
      LOCAL (
      PARTITION i_quarter_one TABLESPACE i_quarter_one,
      PARTITION i_quarter_two TABLESPACE i_quarter_two,
      PARTITION i_quarter_three TABLESPACE i_quarter_three,
      PARTITION i_quarter_four TABLESPACE i_quarter_four
    );

    SELECT TABLE_NAME, PARTITION_NAME FROM USER_TAB_PARTITIONS WHERE TABLE_NAME ='FOUR_SEASONS';
    TABLE_NAME                          PARTITION_NAME
    ----------------------------------- -------------------------
    FOUR_SEASONS                        QUARTER_FOUR
    FOUR_SEASONS                        QUARTER_ONE
    FOUR_SEASONS                        QUARTER_THREE
    FOUR_SEASONS                        QUARTER_TWO

    -- Next, merge the first two partitions
    ALTER TABLE four_seasons
      MERGE PARTITIONS quarter_one, quarter_two INTO PARTITION quarter_two
      UPDATE INDEXES
      ONLINE;

    SELECT TABLE_NAME, PARTITION_NAME FROM USER_TAB_PARTITIONS WHERE TABLE_NAME ='FOUR_SEASONS';
    TABLE_NAME                          PARTITION_NAME
    ----------------------------------- -------------------------
    FOUR_SEASONS                        QUARTER_FOUR
    FOUR_SEASONS                        QUARTER_THREE
    FOUR_SEASONS                        QUARTER_TWO

If you omit the `UPDATE` `INDEXES` clause from the `ALTER` `TABLE` `four_season` statement, then you must rebuild the local index for the affected partition.

    -- Rebuild the index for quarter_two, which has been marked unusable
    -- because it has not had all of the data from quarter_one added to it.
    -- Rebuilding the index corrects this condition.
    --
    ALTER TABLE four_seasons MODIFY PARTITION quarter_two
      REBUILD UNUSABLE LOCAL INDEXES;

#### 4.4.6.2 Merging Interval Partitions

The contents of two adjacent interval partitions can be merged into one partition.

Nonadjacent interval partitions cannot be merged. The first interval partition can also be merged with the highest range partition. The resulting partition inherits the higher upper bound of the two merged partitions.

Merging interval partitions always results in the transition point being moved to the higher upper bound of the two merged partitions. This result is that the range section of the interval-partitioned table is extended to the upper bound of the two merged partitions. Any materialized interval partitions with boundaries lower than the newly merged partition are automatically converted into range partitions, with their upper boundaries defined by the upper boundaries of their intervals.

For example, consider the following interval-partitioned table transactions:

    CREATE TABLE transactions
    ( id               NUMBER
    , transaction_date DATE
    , value            NUMBER
    )
    PARTITION BY RANGE (transaction_date)
    INTERVAL (NUMTODSINTERVAL(1,'DAY'))
    ( PARTITION p_before_2007 VALUES LESS THAN (TO_DATE('01-JAN-2007','dd-MON-yyyy')));

Inserting data into the interval section of the table creates the interval partitions for these days. The data for January 15, 2007 and January 16, 2007 are stored in adjacent interval partitions.

    INSERT INTO transactions VALUES (1,TO_DATE('15-JAN-2007','dd-MON-yyyy'),100);
    INSERT INTO transactions VALUES (2,TO_DATE('16-JAN-2007','dd-MON-yyyy'),600);
    INSERT INTO transactions VALUES (3,TO_DATE('30-JAN-2007','dd-MON-yyyy'),200);

Next, merge the two adjacent interval partitions. The new partition again has a system-generated name.

    ALTER TABLE transactions
    MERGE PARTITIONS FOR(TO_DATE('15-JAN-2007','dd-MON-yyyy'))
    , FOR(TO_DATE('16-JAN-2007','dd-MON-yyyy'));

The transition point for the `transactions` table has now moved to January 17, 2007. The range section of the interval-partitioned table contains two range partitions: values less than January 1, 2007 and values less than January 17, 2007. Values greater than January 17, 2007 fall in the interval portion of the interval-partitioned table.

#### 4.4.6.3 Merging List Partitions

When you merge list partitions, the partitions being merged can be any two partitions.

They do not need to be adjacent, as for range partitions, because list partitioning does not assume any order for partitions. The resulting partition consists of all of the data from the original two partitions. If you merge a default list partition with any other partition, then the resulting partition is the default partition.

The following statement merges two partitions of a table partitioned using the list method into a partition that inherits all of its attributes from the table-level default attributes. `MAXEXTENTS` is specified in the statement.

    ALTER TABLE q1_sales_by_region
       MERGE PARTITIONS q1_northcentral, q1_southcentral
       INTO PARTITION q1_central
          STORAGE(MAXEXTENTS 20);

The value lists for the two original partitions were specified as:

    PARTITION q1_northcentral VALUES ('SD','WI')
    PARTITION q1_southcentral VALUES ('OK','TX')

The resulting `sales_west` partition value list comprises the set that represents the union of these two partition value lists, or specifically:

    ('SD','WI','OK','TX')

#### 4.4.6.4 Merging \*-Hash Partitions

When you merge \*-hash partitions, the subpartitions are rehashed into the number of subpartitions specified by `SUBPARTITIONS` `n` or the `SUBPARTITION` clause. If neither is included, table-level defaults are used.

The inheritance of properties is different when a \*-hash partition is split, as opposed to when two \*-hash partitions are merged. When a partition is split, the new partitions can inherit properties from the original partition because there is only one parent. However, when partitions are merged, properties must be inherited from the table level.

For interval-hash partitioned tables, you can only merge two adjacent interval partitions, or the highest range partition with the first interval partition. The transition point moves when you merge intervals in an interval-hash partitioned table.

The following example merges two range-hash partitions:

    ALTER TABLE all_seasons
       MERGE PARTITIONS quarter_1, quarter_2 INTO PARTITION quarter_2
       SUBPARTITIONS 8;

**See Also:**

- Splitting a \*-Hash Partition for information about splitting a hash partition

- Merging Interval Partitions for information about merging interval partitions

#### 4.4.6.5 About Merging \*-List Partitions

Partitions can be merged at the partition level and subpartitions can be merged at the list subpartition level.

This section contains the following topics.

- Merging Partitions in a \*-List Partitioned Table

- Merging Subpartitions in a \*-List Partitioned Table

##### 4.4.6.5.1 Merging Partitions in a \*-List Partitioned Table

When you merge two \*-list partitions, the resulting new partition inherits the subpartition descriptions from the subpartition template, if a template exists. If no subpartition template exists, then a single default subpartition is created for the new partition.

For interval-list partitioned tables, you can only merge two adjacent interval partitions, or the highest range partition with the first interval partition. The transition point moves when you merge intervals in an interval-list partitioned table.

The following statement merges two partitions in the range-list partitioned `stripe_regional_sales` table. A subpartition template exists for the table.

    ALTER TABLE stripe_regional_sales
       MERGE PARTITIONS q1_1999, q2_1999 INTO PARTITION q1_q2_1999
          STORAGE(MAXEXTENTS 20);

Some new physical attributes are specified for this new partition while table-level defaults are inherited for those that are not specified. The new resulting partition `q1_q2_1999` inherits the high-value bound of the partition `q2_1999` and the subpartition value-list descriptions from the subpartition template description of the table.

The data in the resulting partitions consists of data from both the partitions. However, there may be cases where the database returns an error. This can occur because data may map out of the new partition when both of the following conditions exist:

This error condition can be eliminated by always specifying a default partition in the default subpartition template.

- Some literal values of the merged subpartitions were not included in the subpartition template.

- The subpartition template does not contain a default partition definition.

**See Also:**

- Merging List Partitions for information about merging partitions in a \*-list partitioned table

- Merging Interval Partitions for information about merging interval partitions

##### 4.4.6.5.2 Merging Subpartitions in a \*-List Partitioned Table

You can merge the contents of any two arbitrary list subpartitions belonging to the same partition.

The resulting subpartition value-list descriptor includes all of the literal values in the value lists for the partitions being merged.

The following statement merges two subpartitions of a table partitioned using range-list method into a new subpartition located in tablespace `ts4`:

    ALTER TABLE quarterly_regional_sales
       MERGE SUBPARTITIONS q1_1999_northwest, q1_1999_southwest
          INTO SUBPARTITION q1_1999_west
             TABLESPACE ts4;

The value lists for the original two partitions were:

- Subpartition `q1_1999_northwest` was described as `('WA','OR')`

- Subpartition `q1_1999_southwest` was described as `('AZ','NM','UT')`

The resulting subpartition value list comprises the set that represents the union of these two subpartition value lists:

- Subpartition `q1_1999_west` has a value list described as `('WA','OR','AZ','NM','UT')`

The tablespace in which the resulting subpartition is located and the subpartition attributes are determined by the partition-level default attributes, except for those specified explicitly. If any of the existing subpartition names are being reused, then the new subpartition inherits the subpartition attributes of the subpartition whose name is being reused.

#### 4.4.6.6 About Merging \*-Range Partitions

Partitions can be merged at the partition level and subpartitions can be merged at the range subpartition level.

- Merging Partitions in a \*-Range Partitioned Table

##### 4.4.6.6.1 Merging Partitions in a \*-Range Partitioned Table

When you merge two \*-range partitions, the resulting new partition inherits the subpartition descriptions from the subpartition template, if one exists. If no subpartition template exists, then a single subpartition with an upper boundary `MAXVALUE` is created for the new partition.

For interval-range partitioned tables, you can only merge two adjacent interval partitions, or the highest range partition with the first interval partition. The transition point moves when you merge intervals in an interval-range partitioned table.

The following statement merges two partitions in the monthly interval-range partitioned `orders` table. A subpartition template exists for the table.

    ALTER TABLE orders
    MERGE PARTITIONS FOR(TO_DATE('01-MAR-2007','dd-MON-yyyy')),
    FOR(TO_DATE('01-APR-2007','dd-MON-yyyy'))
    INTO PARTITION p_pre_may_2007;

If the March 2007 and April 2007 partitions were still in the interval section of the interval-range partitioned table, then the merge operation would move the transition point to May 1, 2007.

The subpartitions for partition `p_pre_may_2007` inherit their properties from the subpartition template. The data in the resulting partitions consists of data from both the partitions. However, there may be cases where the database returns an error. This can occur because data may map out of the new partition when both of the following conditions are met:

The error condition can be eliminated by always specifying a subpartition with an upper boundary of `MAXVALUE` in the subpartition template.

- Some range values of the merged subpartitions were not included in the subpartition template.

- The subpartition template does not have a subpartition definition with a `MAXVALUE` upper boundary.

**See Also:**

- Merging Range Partitions for information about merging partitions in a \*-range partitioned table

- Merging Interval Partitions for information about merging interval partitions

#### 4.4.6.7 Merging Multiple Partitions

You can merge the contents of two or more partitions or subpartitions into one new partition or subpartition and then drop the original partitions or subpartitions with the `MERGE` `PARTITIONS` and `MERGE` `SUBPARTITIONS` clauses of the `ALTER` `TABLE` SQL statement.

The `MERGE` `PARTITIONS` and `MERGE` `SUBPARTITIONS` clauses are synonymous with the `MERGE` `PARTITION` and `MERGE` `SUBPARTITION` clauses.

For example, the following SQL statement merges four partitions into one partition and drops the four partitions that were merged.

    ALTER TABLE t1 MERGE PARTITIONS p01, p02, p03, p04 INTO p0;

When merging multiple range partitions, the partitions must be adjacent and specified in the ascending order of their partition bound values. The new partition inherits the partition upper bound of the highest of the original partitions.

You can specify the lowest and the highest partitions to be merged when merging multiple range partitions with the `TO` syntax. All partitions between specified partitions, including those specified, are merged into the target partition. You cannot use this syntax for list and system partitions.

For example, the following SQL statements merges partitions `p01` through `p04` into the partition `p0`.

    ALTER TABLE t1 MERGE PARTITIONS p01 TO p04 INTO p0;

List partitions and system partitions that you want to merge do not need to be adjacent, because no ordering of the partitions is assumed. When merging multiple list partitions, the resulting partition value list are the union of the set of partition value list of all of the partitions to be merged. A `DEFAULT` list partition merged with other list partitions results in a `DEFAULT` partition.

When merging multiple partitions of a composite partitioned table, the resulting new partition inherits the subpartition descriptions from the subpartition template, if one exists. If no subpartition template exists, then Oracle creates one `MAXVALUE` subpartition from range subpartitions or one `DEFAULT` subpartition from list subpartitions for the new partition. When merging multiple subpartitions of a composite partitioned table, the subpartitions to be merged must belong to the same partition.

When merging multiple partitions, local and global index operations and semantics for inheritance of unspecified physical attributes are the same for merging two partitions.

In the following SQL statement, four partitions of the partitioned by range table `sales` are merged. These four partitions that correspond to the four quarters of the oldest year are merged into a single partition containing the entire sales data of the year.

    ALTER TABLE sales
      MERGE PARTITIONS sales_q1_2009, sales_q2_2009, sales_q3_2009, sales_q4_2009
      INTO PARTITION sales_2009;

The previous SQL statement can be rewritten as the following SQL statement to obtain the same result.

    ALTER TABLE sales
      MERGE PARTITIONS sales_q1_2009 TO sales_q4_2009
      INTO PARTITION sales_2009;

**Note:**

See Restrictions and Special Requirements for Multi-Partition Operations on Tables with Domain Indexes

### 4.4.7 About Modifying Attributes of Tables, Partitions, and Subpartitions

The modification of attributes of tables, partitions, and subpartitions is introduced in this topic.

- About Modifying Default Attributes

- About Modifying Real Attributes of Partitions

#### 4.4.7.1 About Modifying Default Attributes

You can modify the default attributes of a table, or for a partition of a composite partitioned table.

When you modify default attributes, the new attributes affect only future partitions, or subpartitions, that are created. The default values can still be specifically overridden when creating a new partition or subpartition. You can modify the default attributes of a reference-partitioned table.

This section contains the following topics:

- Modifying Default Attributes of a Table

- Modifying Default Attributes of a Partition

- Modifying Default Attributes of Index Partitions

##### 4.4.7.1.1 Modifying Default Attributes of a Table

You can modify the default attributes that are inherited for range, hash, list, interval, or reference partitions using the `MODIFY` `DEFAULT` `ATTRIBUTES` clause of `ALTER` `TABLE`.

For hash partitioned tables, only the `TABLESPACE` attribute can be modified.

##### 4.4.7.1.2 Modifying Default Attributes of a Partition

To modify the default attributes inherited when creating subpartitions, use the `ALTER` `TABLE` `MODIFY` `DEFAULT` `ATTRIBUTES` `FOR` `PARTITION`.

The following statement modifies the `TABLESPACE` in which future subpartitions of partition `p1` in the range-hash partitioned table reside.

    ALTER TABLE employees_subpartitions
         MODIFY DEFAULT ATTRIBUTES FOR PARTITION p1 TABLESPACE ts1;

Because all subpartitions of a range-hash partitioned table must share the same attributes, except `TABLESPACE`, it is the only attribute that can be changed.

You cannot modify default attributes of interval partitions that have not yet been created. To change the way in which future subpartitions in an interval-partitioned table are created, you must modify the subpartition template.

##### 4.4.7.1.3 Modifying Default Attributes of Index Partitions

In a similar fashion to table partitions, you can alter the default attributes that are inherited by partitions of a range-partitioned global index, or local index partitions of partitioned tables.

For this you use the `ALTER` `INDEX` `MODIFY` `DEFAULT` `ATTRIBUTES` statement. Use the `ALTER` `INDEX` `MODIFY` `DEFAULT` `ATTRIBUTES` `FOR` `PARTITION` statement if you are altering default attributes to be inherited by subpartitions of a composite partitioned table.

#### 4.4.7.2 About Modifying Real Attributes of Partitions

It is possible to modify attributes of an existing partition of a table or index.

You cannot change the `TABLESPACE` attribute. Use `ALTER` `TABLE` `MOVE` `PARTITION`/`SUBPARTITION` to move a partition or subpartition to a new tablespace.

This section contains the following topics:

- Modifying Real Attributes for a Range or List Partition

- Modifying Real Attributes for a Hash Partition

- Modifying Real Attributes of a Subpartition

- Modifying Real Attributes of Index Partitions

##### 4.4.7.2.1 Modifying Real Attributes for a Range or List Partition

Use the `ALTER` `TABLE` `MODIFY` `PARTITION` statement to modify existing attributes of a range partition or list partition.

You can modify segment attributes (except `TABLESPACE`), or you can allocate and deallocate extents, mark local index partitions `UNUSABLE`, or rebuild local indexes that have been marked `UNUSABLE`.

If this is a range partition of a \*-hash partitioned table, then note the following:

- If you allocate or deallocate an extent, this action is performed for every subpartition of the specified partition.

- Likewise, changing any other attributes results in corresponding changes to those attributes of all the subpartitions for that partition. The partition level default attributes are changed as well. To avoid changing attributes of existing subpartitions, use the `FOR` `PARTITION` clause of the `MODIFY` `DEFAULT` `ATTRIBUTES` statement.

The following are some examples of modifying the real attributes of a partition.

This example modifies the `MAXEXTENTS` storage attribute for the range partition `sales_q1` of table `sales`:

    ALTER TABLE sales MODIFY PARTITION sales_q1
         STORAGE (MAXEXTENTS 10);

All of the local index subpartitions of partition `ts1` in range-hash partitioned table `scubagear` are marked `UNUSABLE` in the following example:

    ALTER TABLE scubagear MODIFY PARTITION ts1 UNUSABLE LOCAL INDEXES;

For an interval-partitioned table you can only modify real attributes of range partitions or interval partitions that have been created.

##### 4.4.7.2.2 Modifying Real Attributes for a Hash Partition

You can use the `ALTER` `TABLE` `MODIFY` `PARTITION` statement to modify attributes of a hash partition.

However, because the physical attributes of individual hash partitions must all be the same (except for `TABLESPACE`), you are restricted to:

- Allocating a new extent

- Deallocating an unused extent

- Marking a local index subpartition `UNUSABLE`

- Rebuilding local index subpartitions that are marked `UNUSABLE `

The following example rebuilds any unusable local index partitions associated with hash partition `p1` of the table:

    ALTER TABLE departments_rebuild_index MODIFY PARTITION p1
         REBUILD UNUSABLE LOCAL INDEXES;

##### 4.4.7.2.3 Modifying Real Attributes of a Subpartition

With the `MODIFY` `SUBPARTITION` clause of `ALTER` `TABLE` you can perform the same actions as listed previously for partitions, but at the specific composite partitioned table subpartition level.

For example:

    ALTER TABLE employees_rebuild_index MODIFY SUBPARTITION p3_s1
         REBUILD UNUSABLE LOCAL INDEXES;

##### 4.4.7.2.4 Modifying Real Attributes of Index Partitions

The `MODIFY` `PARTITION` clause of `ALTER` `INDEX` enables you to modify the real attributes of an index partition or its subpartitions.

The rules are very similar to those for table partitions, but unlike the `MODIFY` `PARTITION` clause for `ALTER` `INDEX`, there is no subclause to rebuild an unusable index partition, but there is a subclause to coalesce an index partition or its subpartitions. In this context, coalesce means to merge index blocks where possible to free them for reuse.

You can also allocate or deallocate storage for a subpartition of a local index, or mark it `UNUSABLE`, using the `MODIFY` `PARTITION` clause.

### 4.4.8 About Modifying List Partitions

The modification of values in list partitions and subpartitions is introduced in this topic.

- About Modifying List Partitions: Adding Values

- About Modifying List Partitions: Dropping Values

#### 4.4.8.1 About Modifying List Partitions: Adding Values

List partitioning enables you to optionally add literal values from the defining value list.

This section contains the following topics:

- Adding Values for a List Partition

- Adding Values for a List Subpartition

##### 4.4.8.1.1 Adding Values for a List Partition

Use the `MODIFY` `PARTITION` `ADD` `VALUES` clause of the `ALTER` `TABLE` statement to extend the value list of an existing partition.

Literal values being added must not have been included in any other partition value list. The partition value list for any corresponding local index partition is correspondingly extended, and any global indexes, or global or local index partitions, remain usable.

The following statement adds a new set of state codes ('`OK`', '`KS`') to an existing partition list.

    ALTER TABLE sales_by_region
       MODIFY PARTITION region_south
          ADD VALUES ('OK', 'KS');

The existence of a default partition can have a performance impact when adding values to other partitions. This is because to add values to a list partition, the database must check that the values being added do not exist in the default partition. If any of the values do exist in the default partition, then an error is displayed.

**Note:**

The database runs a query to check for the existence of rows in the default partition that correspond to the literal values being added. Therefore, it is advisable to create a local prefixed index on the table. This speeds up the execution of the query and the overall operation.

You cannot add values to a default list partition.

##### 4.4.8.1.2 Adding Values for a List Subpartition

Use the `MODIFY` `SUBPARTITION` `ADD` `VALUES` clause of the `ALTER` `TABLE` statement to extend the value list of an existing subpartition.

This operation is essentially the same as described for About Modifying List Partitions: Adding Values, however, you use a `MODIFY` `SUBPARTITION` clause instead of the `MODIFY` `PARTITION` clause. For example, to extend the range of literal values in the value list for subpartition `q1_1999_southeast`, use the following statement:

    ALTER TABLE quarterly_regional_sales
       MODIFY SUBPARTITION q1_1999_southeast
          ADD VALUES ('KS');

Literal values being added must not have been included in any other subpartition value list within the owning partition. However, they can be duplicates of literal values in the subpartition value lists of other partitions within the table.

For an interval-list composite partitioned table, you can only add values to subpartitions of range partitions or interval partitions that have been created. To add values to subpartitions of interval partitions that have not yet been created, you must modify the subpartition template.

#### 4.4.8.2 About Modifying List Partitions: Dropping Values

List partitioning enables you to optionally drop literal values from the defining value list.

This section contains the following topics:

- Dropping Values from a List Partition

- Dropping Values from a List Subpartition

##### 4.4.8.2.1 Dropping Values from a List Partition

Use the `MODIFY` `PARTITION` `DROP` `VALUES` clause of the `ALTER` `TABLE` statement to remove literal values from the value list of an existing partition.

The statement is always executed with validation, meaning that it checks to see if any rows exist in the partition that corresponds to the set of values being dropped. If any such rows are found then the database returns an error message and the operation fails. When necessary, use a `DELETE` statement to delete corresponding rows from the table before attempting to drop values.

**Note:**

You cannot drop all literal values from the value list describing the partition. You must use the `ALTER TABLE DROP PARTITION` statement instead.

The partition value list for any corresponding local index partition reflects the new value list, and any global index, or global or local index partitions, remain usable.

The following statement drops a set of state codes ('`OK`' and '`KS`') from an existing partition value list.

    ALTER TABLE sales_by_region
       MODIFY PARTITION region_south
          DROP VALUES ('OK', 'KS');

**Note:**

The database runs a query to check for the existence of rows in the partition that correspond to the literal values being dropped. Therefore, it is advisable to create a local prefixed index on the table. This speeds up the query and the overall operation.

You cannot drop values from a default list partition.

##### 4.4.8.2.2 Dropping Values from a List Subpartition

Use the `MODIFY` `SUBPARTITION` `DROP` `VALUES` clause of the `ALTER` `TABLE` statement to remove literal values from the value list of an existing subpartition.

This operation is essentially the same as described for About Modifying List Partitions: Dropping Values, however, you use a `MODIFY` `SUBPARTITION` clause instead of the `MODIFY` `PARTITION` clause. For example, to remove a set of literal values in the value list for subpartition `q1_1999_southeast`, use the following statement:

    ALTER TABLE quarterly_regional_sales
       MODIFY SUBPARTITION q1_1999_southeast
          DROP VALUES ('KS');

For an interval-list composite partitioned table, you can only drop values from subpartitions of range partitions or interval partitions that have been created. To drop values from subpartitions of interval partitions that have not yet been created, you must modify the subpartition template.

### 4.4.9 About Modifying the Partitioning Strategy

You can change the partitioning strategy of a regular (heap-organized) table with the `ALTER` `TABLE` `MODIFY` `PARTITION` SQL statement.

Modifying the partitioning strategy, such as hash partitioning to composite range-hash partitioning, can be performed offline or online. When performed in online mode, the conversion does not impact ongoing DML operations. When performed in offline mode, the conversion does not allow concurrent DML operations during the modification.

Indexes are maintained as part of the table modification. When modifying the partitioning strategy, all unspecified indexes whose index columns are a prefix of the new partitioning key are automatically converted to a local partitioned index; otherwise, an index is converted to global index.

The modification operation is not supported with domain indexes. The `UPDATE` `INDEXES` clause cannot change the columns on which the list of indexes was originally defined or the uniqueness property of the index or any other index property.

For information about converting a non-partitioned table to a partitioned table, refer to [Converting a Non-Partitioned Table to a Partitioned Table](evolve-nopartition-table.md).

Example 4-35 shows the use of `ALTER` `TABLE` to convert a range partitioned table to a composite range-hash partitioned table online. During the `ALTER` `TABLE` modification in the example, indexes are updated.

**Live SQL:**

View and run a related example on Oracle Live SQL at [Modifying the Partitioning Strategy of a Table](https://livesql.oracle.com/apex/livesql/docs/vldbg/partitioning/modify-partitioning-strategy.html).

Example 4-35 Modifying the partitioning strategy

    CREATE TABLE mod_sales_partitioning
      ( prod_id       NUMBER        NOT NULL,
        cust_id       NUMBER        NOT NULL,
        time_id       DATE          NOT NULL,
        channel_id    NUMBER        NOT NULL,
        promo_id      NUMBER        NOT NULL,
        quantity_sold NUMBER(10,2)  NOT NULL,
        amount_sold   NUMBER(10,2)  NOT NULL
      )
      PARTITION BY RANGE (time_id)
      (PARTITION sales_q1_2017 VALUES LESS THAN (TO_DATE('01-APR-2017','dd-MON-yyyy')),
       PARTITION sales_q2_2017 VALUES LESS THAN (TO_DATE('01-JUL-2017','dd-MON-yyyy')),
       PARTITION sales_q3_2017 VALUES LESS THAN (TO_DATE('01-OCT-2017','dd-MON-yyyy')),
       PARTITION sales_q4_2017 VALUES LESS THAN (TO_DATE('01-JAN-2018','dd-MON-yyyy'))
     );

    CREATE INDEX i1_cust_id_indx ON mod_sales_partitioning (cust_id) LOCAL;
    CREATE INDEX i2_time_id_indx ON mod_sales_partitioning (time_id);
    CREATE INDEX i3_prod_id_indx ON mod_sales_partitioning (prod_id);

    SELECT TABLE_NAME, PARTITIONING_TYPE FROM USER_PART_TABLES WHERE TABLE_NAME ='MOD_SALES_PARTITIONING';
    TABLE_NAME                PARTITION_NAME
    ------------------------- --------------
    MOD_SALES_PARTITIONING    RANGE

    SELECT TABLE_NAME, PARTITION_NAME FROM USER_TAB_PARTITIONS WHERE TABLE_NAME ='MOD_SALES_PARTITIONING';
    TABLE_NAME                PARTITION_NAME
    ------------------------- --------------
    MOD_SALES_PARTITIONING    SALES_Q1_2017
    MOD_SALES_PARTITIONING    SALES_Q2_2017
    MOD_SALES_PARTITIONING    SALES_Q3_2017
    MOD_SALES_PARTITIONING    SALES_Q4_2017
    ...

    ALTER TABLE mod_sales_partitioning
     MODIFY
     PARTITION BY RANGE (time_id) SUBPARTITION BY HASH (cust_id)
      SUBPARTITIONS 8
     ( PARTITION  sales_q1_2017 VALUES LESS THAN (TO_DATE('01-APR-2017','dd-MON-yyyy')),
        PARTITION sales_q2_2017 VALUES LESS THAN (TO_DATE('01-JUL-2017','dd-MON-yyyy')),
        PARTITION sales_q3_2017 VALUES LESS THAN (TO_DATE('01-OCT-2017','dd-MON-yyyy')),
        PARTITION sales_q4_2017 VALUES LESS THAN (TO_DATE('01-JAN-2018','dd-MON-yyyy')))
        ONLINE
      UPDATE INDEXES
       ( i1_cust_id_indx LOCAL,
         i2_time_id_indx GLOBAL PARTITION BY RANGE (time_id)
         (PARTITION ip1_indx VALUES LESS THAN (MAXVALUE) ) );

    SELECT TABLE_NAME, PARTITIONING_TYPE, SUBPARTITIONING_TYPE FROM USER_PART_TABLES WHERE TABLE_NAME ='MOD_SALES_PARTITIONING';
    TABLE_NAME                  PARTITION      SUBPARTIT
    --------------------------- -------------- ----------
    MOD_SALES_PARTITIONING      RANGE          HASH

    SELECT TABLE_NAME, PARTITION_NAME, SUBPARTITION_NAME FROM USER_TAB_SUBPARTITIONS WHERE TABLE_NAME ='MOD_SALES_PARTITIONING';
    TABLE_NAME                  PARTITION_NAME     SUBPARTITION_NAME
    --------------------------- ------------------ ------------------
    MOD_SALES_PARTITIONING      SALES_Q1_2017      SYS_SUBP567
    MOD_SALES_PARTITIONING      SALES_Q1_2017      SYS_SUBP568
    MOD_SALES_PARTITIONING      SALES_Q1_2017      SYS_SUBP569
    MOD_SALES_PARTITIONING      SALES_Q1_2017      SYS_SUBP570
    ...

### 4.4.10 About Moving Partitions and Subpartitions

Use the `MOVE` `PARTITION` clause of the `ALTER` `TABLE` statement to change the physical storage attributes of a partition.

With the `MOVE` `PARTITION` clause of the `ALTER` `TABLE` statement, you can:

- Re-cluster data and reduce fragmentation

- Move a partition to another tablespace

- Modify create-time attributes

- Store the data in compressed format using table compression

Typically, you can change the physical storage attributes of a partition in a single step using an `ALTER` `TABLE`/`INDEX` `MODIFY` `PARTITION` statement. However, there are some physical attributes, such as `TABLESPACE`, that you cannot modify using `MODIFY` `PARTITION`. In these cases, use the `MOVE` `PARTITION` clause. Modifying some other attributes, such as table compression, affects only future storage, but not existing data.

If the partition being moved contains any data, then indexes may be marked `UNUSABLE` according to the following table:

| Table Type      | Index Behavior                                                                                                                                                                                                                                                                                                                   |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Regular (Heap)  | Unless you specify `UPDATE` `INDEXES` as part of the `ALTER` `TABLE` statement:<br>• The matching partition in each local index is marked `UNUSABLE`. You must rebuild these index partitions after issuing `MOVE` `PARTITION`.<br>• Any global indexes, or all partitions of partitioned global indexes, are marked `UNUSABLE`. |
| Index-organized | Any local or global indexes defined for the partition being moved remain usable because they are primary-key based logical rowids. However, the guess information for these rowids becomes incorrect.                                                                                                                            |

This section contains the following topics:

- Moving Table Partitions

- Moving Subpartitions

- Moving Index Partitions

**see Also:**

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for information the `ALTER` `TABLE` `MOVE` statement

- [Oracle Database Administrator’s Guide](../admin/managing-tables.md) for information moving tables and partitions

#### 4.4.10.1 Moving Table Partitions

Use the `MOVE` `PARTITION` clause to move a partition.

For example, to move the most active partition to a tablespace that resides on its own set of disks (to balance I/O), not log the action, and compress the data, issue the following statement:

    ALTER TABLE parts MOVE PARTITION depot2
         TABLESPACE ts094 NOLOGGING COMPRESS;

This statement always drops the old partition segment and creates a new segment, even if you do not specify a new tablespace.

If you are moving a partition of a partitioned index-organized table, then you can specify the `MAPPING` `TABLE` clause as part of the `MOVE` `PARTITION` clause, and the mapping table partition are moved to the new location along with the table partition.

For an interval or interval-\* partitioned table, you can only move range partitions or interval partitions that have been materialized. A partition move operation does not move the transition point in an interval or interval-\* partitioned table.

You can move a partition in a reference-partitioned table independent of the partition in the master table.

#### 4.4.10.2 Moving Subpartitions

Use the `MOVE` `SUBPARTITION` clause to move a subpartition.

The following statement shows how to move data in a subpartition of a table. In this example, a `PARALLEL` clause has also been specified.

    ALTER TABLE scuba_gear MOVE SUBPARTITION bcd_types
         TABLESPACE tbs23 PARALLEL (DEGREE 2);

You can move a subpartition in a reference-partitioned table independent of the subpartition in the master table.

#### 4.4.10.3 Moving Index Partitions

The `ALTER` `TABLE` `MOVE` `PARTITION` statement for regular tables marks all partitions of a global index `UNUSABLE`.

You can rebuild the entire index by rebuilding each partition individually using the `ALTER` `INDEX` `REBUILD` `PARTITION` statement. You can perform these rebuilds concurrently.

You can also simply drop the index and re-create it.

### 4.4.11 About Rebuilding Index Partitions

Rebuilding an index provides several advantages.

Some reasons for rebuilding index partitions include:

- To recover space and improve performance

- To repair a damaged index partition caused by media failure

- To rebuild a local index partition after loading the underlying table partition with SQL\*Loader or an import utility

- To rebuild index partitions that have been marked `UNUSABLE`

- To enable key compression for B-tree indexes

The following sections discuss options for rebuilding index partitions and subpartitions.

This section contains the following topics:

- About Rebuilding Global Index Partitions

- About Rebuilding Local Index Partitions

#### 4.4.11.1 About Rebuilding Global Index Partitions

You can rebuild global index partitions with several methods.

- Rebuild each partition by issuing the `ALTER` `INDEX` `REBUILD` `PARTITION` statement (you can run the rebuilds concurrently).

- Drop the entire global index and re-create it. This method is more efficient because the table is scanned only one time.

For most maintenance operations on partitioned tables with indexes, you can optionally avoid the need to rebuild the index by specifying `UPDATE` `INDEXES` on your DDL statement.

#### 4.4.11.2 About Rebuilding Local Index Partitions

You can rebuild local index partitions with several methods.

Rebuild local indexes using either `ALTER` `INDEX` or `ALTER` `TABLE` as follows:

- `ALTER` `INDEX` `REBUILD` `PARTITION`/`SUBPARTITION`

  This statement rebuilds an index partition or subpartition unconditionally.

- `ALTER` `TABLE` `MODIFY` `PARTITION`/`SUBPARTITION` `REBUILD` `UNUSABLE` `LOCAL` `INDEXES`

  This statement finds all of the unusable indexes for the given table partition or subpartition and rebuilds them. It only rebuilds an index partition if it has been marked `UNUSABLE`.

The following sections contain examples about rebuilding indexes.

- Using ALTER INDEX to Rebuild a Partition

- Using ALTER TABLE to Rebuild an Index Partition

##### 4.4.11.2.1 Using ALTER INDEX to Rebuild a Partition

The `ALTER` `INDEX` `REBUILD` `PARTITION` statement rebuilds one partition of an index.

It cannot be used for composite-partitioned tables. Only real physical segments can be rebuilt with this command. When you re-create the index, you can also choose to move the partition to a new tablespace or change attributes.

For composite-partitioned tables, use `ALTER` `INDEX` `REBUILD` `SUBPARTITION` to rebuild a subpartition of an index. You can move the subpartition to another tablespace or specify a parallel clause. The following statement rebuilds a subpartition of a local index on a table and moves the index subpartition to another tablespace.

    ALTER INDEX scuba
       REBUILD SUBPARTITION bcd_types
       TABLESPACE tbs23 PARALLEL (DEGREE 2);

##### 4.4.11.2.2 Using ALTER TABLE to Rebuild an Index Partition

The `REBUILD` `UNUSABLE` `LOCAL` `INDEXES` clause of `ALTER` `TABLE` `MODIFY` `PARTITION` enables you to rebuild an unusable index partition.

However, the statement does not allow you to specify any new attributes for the rebuilt index partition. The following example finds and rebuilds any unusable local index partitions for table `scubagear`, partition `p1`.

    ALTER TABLE scubagear
       MODIFY PARTITION p1 REBUILD UNUSABLE LOCAL INDEXES;

The `ALTER` `TABLE` `MODIFY` `SUBPARTITION` is the clause for rebuilding unusable local index subpartitions.

### 4.4.12 About Renaming Partitions and Subpartitions

You can rename partitions and subpartitions of both tables and indexes.

One reason for renaming a partition might be to assign a meaningful name, as opposed to a default system name that was assigned to the partition in another maintenance operation.

All partitioning methods support the `FOR(``value``)` method to identify a partition. You can use this method to rename a system-generated partition name into a more meaningful name. This is particularly useful in interval or interval-\* partitioned tables.

You can independently rename partitions and subpartitions for reference-partitioned master and child tables. The rename operation on the master table is not cascaded to descendant tables.

This section contains the following topics:

- Renaming a Table Partition

- Renaming a Table Subpartition

- About Renaming Index Partitions

#### 4.4.12.1 Renaming a Table Partition

You can rename a range, hash, or list partition, using the `ALTER` `TABLE` `RENAME` `PARTITION` statement.

For example:

    ALTER TABLE scubagear RENAME PARTITION sys_p636 TO tanks;

#### 4.4.12.2 Renaming a Table Subpartition

You can assign new names to subpartitions of a table.

In this case, you would use the `ALTER` `TABLE` `RENAME` `SUBPARTITION` syntax.

#### 4.4.12.3 About Renaming Index Partitions

You can rename index partitions and subpartitions with the `ALTER` `INDEX` statement.

- Renaming an Index Partition

- Renaming an Index Subpartition

##### 4.4.12.3.1 Renaming an Index Partition

Use the `ALTER` `INDEX` `RENAME` `PARTITION` statement to rename an index partition.

The `ALTER INDEX` statement does not support the use of `FOR(``value``)` to identify a partition. You must use the original partition name in the rename operation.

##### 4.4.12.3.2 Renaming an Index Subpartition

Use the `ALTER` `INDEX` `RENAME` `SUBPARTITION` statement to rename an index subpartition.

The following statement simply shows how to rename a subpartition that has a system generated name that was a consequence of adding a partition to an underlying table:

    ALTER INDEX scuba RENAME SUBPARTITION sys_subp3254 TO bcd_types;

### 4.4.13 About Splitting Partitions and Subpartitions

You can split the contents of a partition into two new partitions.

The `SPLIT` `PARTITION` clause of the `ALTER` `TABLE` or `ALTER` `INDEX` statement is used to redistribute the contents of a partition into two new partitions. Consider doing this when a partition becomes too large and causes backup, recovery, or maintenance operations to take a long time to complete or it is felt that there is simply too much data in the partition. You can also use the `SPLIT` `PARTITION` clause to redistribute the I/O load. This clause cannot be used for hash partitions or subpartitions.

If the partition you are splitting contains any data, then indexes may be marked `UNUSABLE` as explained in the following table:

| Table Type      | Index Behavior                                                                                                                                                                                                                                                                                  |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Regular (Heap)  | Unless you specify `UPDATE` `INDEXES` as part of the `ALTER` `TABLE` statement:<br>• The database marks `UNUSABLE` the new partitions (there are two) in each local index.<br>• Any global indexes, or all partitions of partitioned global indexes, are marked `UNUSABLE` and must be rebuilt. |
| Index-organized | • The database marks `UNUSABLE` the new partitions (there are two) in each local index.<br>• All global indexes remain usable.                                                                                                                                                                  |

You cannot split partitions or subpartitions in a reference-partitioned table except for the parent table. When you split partitions or subpartitions in the parent table then the split is cascaded to all descendant tables. However, you can use the `DEPENDENT TABLES` clause to set specific properties for dependent tables when you issue the `SPLIT` statement on the parent table to split partitions or subpartitions.

Partition maintenance with `SPLIT` operations are supported as online operations with the keyword `ONLINE` for heap organized tables, enabling concurrent DML operations while a partition maintenance operation is ongoing.

For `ONLINE` operations, split indexes are always updated by default, regardless whether you specify the `UPDATE` `INDEXES` clause.

For an example of the use of the keyword `ONLINE` with a `SPLIT` operation, see Example 4-37.

This section contains the following topics:

- Splitting a Partition of a Range-Partitioned Table

- Splitting a Partition of a List-Partitioned Table

- Splitting a Partition of an Interval-Partitioned Table

- Splitting a \*-Hash Partition

- Splitting Partitions in a \*-List Partitioned Table

- Splitting a \*-Range Partition

- Splitting Index Partitions

- Splitting into Multiple Partitions

- Fast SPLIT PARTITION and SPLIT SUBPARTITION Operations

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md)

#### 4.4.13.1 Splitting a Partition of a Range-Partitioned Table

You can split a range partition using the `ALTER` `TABLE` `SPLIT` `PARTITION` statement.

In the SQL statement, you must specify values of the partitioning key column within the range of the partition at which to split the partition.

You can optionally specify new attributes for the partitions resulting from the split. If there are local indexes defined on the table, this statement also splits the matching partition in each local index.

If you do not specify new partition names, then the database assigns names of the form `SYS_P``n`. You can examine the data dictionary to locate the names assigned to the new local index partitions. You may want to rename them. Any attributes that you do not specify are inherited from the original partition.

Example 4-36 Splitting a partition of a range-partitioned table and rebuilding indexes

In this example `fee_katy` is a partition in the table `vet_cats`, which has a local index, `jaf1`. There is also a global index, `vet` on the table. `vet` contains two partitions, `vet_parta`, and `vet_partb`. The first of the resulting two new partitions includes all rows in the original partition whose partitioning key column values map lower than the specified value. The second partition contains all rows whose partitioning key column values map greater than or equal to the specified value. The following SQL statement split the partition `fee_katy`, and rebuild the index partitions.

    ALTER TABLE vet_cats SPLIT PARTITION
          fee_katy at (100) INTO ( PARTITION
          fee_katy1, PARTITION fee_katy2);
    ALTER INDEX JAF1 REBUILD PARTITION fee_katy1;
    ALTER INDEX JAF1 REBUILD PARTITION fee_katy2;
    ALTER INDEX VET REBUILD PARTITION vet_parta;
    ALTER INDEX VET REBUILD PARTITION vet_partb;

Example 4-37 Splitting a partition of a range-partitioned table online

In this example, the `sales_q4_2016` partition of the`ORDERS` table is split into separate partitions for each month. The `ONLINE` keyword is specified to enable concurrent DML operations while a partition maintenance operation is ongoing.

If there were any indexes on the `ORDERS` table, then those would be maintained automatically as part of the online split.

    CREATE TABLE orders
     (prod_id       NUMBER(6),
      cust_id       NUMBER,
      time_id       DATE,
      channel_id    CHAR(1),
      promo_id      NUMBER(6),
      quantity_sold NUMBER(3),
      amount_sold   NUMBER(10,2)
      )
      PARTITION BY RANGE (time_id)
      (PARTITION sales_q1_2016 VALUES LESS THAN (TO_DATE('01-APR-2016','dd-MON-yyyy')),
       PARTITION sales_q2_2016 VALUES LESS THAN (TO_DATE('01-JUL-2016','dd-MON-yyyy')),
       PARTITION sales_q3_2016 VALUES LESS THAN (TO_DATE('01-OCT-2016','dd-MON-yyyy')),
       PARTITION sales_q4_2016 VALUES LESS THAN (TO_DATE('01-JAN-2017','dd-MON-yyyy'))
       );

    ALTER TABLE orders
      SPLIT PARTITION sales_q4_2016 INTO
      (PARTITION sales_oct_2016 VALUES LESS THAN (TO_DATE('01-NOV-2016','dd-MON-yyyy')),
       PARTITION sales_nov_2016 VALUES LESS THAN (TO_DATE('01-DEC-2016','dd-MON-yyyy')),
       PARTITION sales_dec_2016
       )
      ONLINE;

#### 4.4.13.2 Splitting a Partition of a List-Partitioned Table

You can split a list partition with the `ALTER` `TABLE` `SPLIT` `PARTITION` statement.

The `SPLIT` `PARTITION` clause enables you to specify a list of literal values that define a partition into which rows with corresponding partitioning key values are inserted. The remaining rows of the original partition are inserted into a second partition whose value list contains the remaining values from the original partition. You can optionally specify new attributes for the two partitions that result from the split.

The following statement splits the partition `region_east` into two partitions:

    ALTER TABLE sales_by_region
       SPLIT PARTITION region_east VALUES ('CT', 'MA', 'MD')
       INTO
        ( PARTITION region_east_1
             TABLESPACE tbs2,
          PARTITION region_east_2
            STORAGE (INITIAL 8M))
       PARALLEL 5;

The literal value list for the original `region_east` partition was specified as:

    PARTITION region_east VALUES ('MA','NY','CT','NH','ME','MD','VA','PA','NJ')

The two new partitions are:

- `region_east_1` with a literal value list of `('CT','MA','MD')`

- `region_east_2` inheriting the remaining literal value list of `('NY','NH','ME','VA','PA','NJ')`

The individual partitions have new physical attributes specified at the partition level. The operation is executed with parallelism of degree 5.

You can split a default list partition just like you split any other list partition. This is also the only means of adding a new partition to a list-partitioned table that contains a default partition. When you split the default partition, you create a new partition defined by the values that you specify, and a second partition that remains the default partition.

**Live SQL:**

View and run a related example on Oracle Live SQL at [Oracle Live SQL: Splitting the DEFAULT Partition of a List-Partitioned Table](https://livesql.oracle.com/apex/livesql/docs/vldbg/partitioning/split-list-partition.html).

Example 4-38 Splitting the default partition of a list-partitioned table

This example splits the default partition of `sales_by_region`, creating new partitions.

    CREATE TABLE sales_by_region
         (dept_number         NUMBER NOT NULL,
          dept_name           VARCHAR2(20),
          quarterly_sales     NUMBER(10,2),
          state               VARCHAR2(2)
     )
     PARTITION BY LIST (state)
     (
      PARTITION yearly_north VALUES ('MN','WI','MI'),
      PARTITION yearly_south VALUES ('NM','TX','GA'),
      PARTITION yearly_east VALUES  ('MA','NY','NC'),
      PARTITION yearly_west VALUES  ('CA','OR','WA'),
      PARTITION unknown VALUES (DEFAULT)
     );

    SELECT PARTITION_NAME, HIGH_VALUE FROM USER_TAB_PARTITIONS WHERE TABLE_NAME ='SALES_BY_REGION';
    PARTITION_NAME       HIGH_VALUE
    --------------       ---------------
    UNKNOWN              DEFAULT
    YEARLY_EAST          'MA', 'NY', 'NC'
    YEARLY_NORTH         'MN', 'WI', 'MI'
    YEARLY_SOUTH         'NM', 'TX', 'GA'
    YEARLY_WEST          'CA', 'OR', 'WA
    5 rows selected.

    INSERT INTO SALES_BY_REGION VALUES (002, 'AUTO NORTH', 450000, 'MN');
    INSERT INTO SALES_BY_REGION VALUES (002, 'AUTO NORTH', 495000, 'WI');
    INSERT INTO SALES_BY_REGION VALUES (002, 'AUTO NORTH', 850000, 'MI');

    INSERT INTO SALES_BY_REGION VALUES (004, 'AUTO SOUTH',  595000, 'NM');
    INSERT INTO SALES_BY_REGION VALUES (004, 'AUTO SOUTH', 4825000, 'TX');
    INSERT INTO SALES_BY_REGION VALUES (004, 'AUTO SOUTH',  945000, 'GA');

    INSERT INTO SALES_BY_REGION VALUES (006, 'AUTO EAST', 2125000, 'MA');
    INSERT INTO SALES_BY_REGION VALUES (006, 'AUTO EAST', 6101000, 'NY');
    INSERT INTO SALES_BY_REGION VALUES (006, 'AUTO EAST',  741000, 'NC');

    INSERT INTO SALES_BY_REGION VALUES (008, 'AUTO WEST', 7201000, 'CA');
    INSERT INTO SALES_BY_REGION VALUES (008, 'AUTO WEST',  901000, 'OR');
    INSERT INTO SALES_BY_REGION VALUES (008, 'AUTO WEST', 1125000, 'WA');

    INSERT INTO SALES_BY_REGION VALUES (009, 'AUTO MIDWEST', 1950000, 'AZ');
    INSERT INTO SALES_BY_REGION VALUES (009, 'AUTO MIDWEST', 5725000, 'UT');

    SELECT DEPT_NUMBER, DEPT_NAME, QUARTERLY_SALES, STATE FROM SALES_BY_REGION PARTITION(yearly_north);
    DEPT_NUMBER DEPT_NAME            QUARTERLY_SALES ST
    ----------- -------------------- --------------- --
    2           AUTO NORTH                    450000 MN
    2           AUTO NORTH                    495000 WI
    2           AUTO NORTH                    850000 MI

    SELECT DEPT_NUMBER, DEPT_NAME, QUARTERLY_SALES, STATE FROM SALES_BY_REGION PARTITION(yearly_south);
    DEPT_NUMBER DEPT_NAME            QUARTERLY_SALES ST
    ----------- -------------------- --------------- --
    4           AUTO SOUTH                    595000 NM
    4           AUTO SOUTH                   4825000 TX
    4           AUTO SOUTH                    945000 GA

    …

    SELECT DEPT_NUMBER, DEPT_NAME, QUARTERLY_SALES, STATE FROM SALES_BY_REGION PARTITION(unknown);
    DEPT_NUMBER DEPT_NAME            QUARTERLY_SALES ST
    ----------- -------------------- --------------- --
    9           AUTO MIDWEST                 1950000 AZ
    9           AUTO MIDWEST                 5725000 UT

    REM Note that the following ADD PARTITION statement fails. This action fails because
    REM all undefined values are automatically included in the DEFAULT partition.
    ALTER TABLE sales_by_region ADD PARTITION yearly_midwest VALUES ('AZ', 'UT');
    ORA-14323: cannot add partition when DEFAULT partition exists

    REM You must SPLIT the DEFAULT partition to add a new partition.
    ALTER TABLE sales_by_region
       SPLIT PARTITION unknown VALUES ('AZ', 'UT')
       INTO
        ( PARTITION yearly_midwest,
          PARTITION unknown);

    SELECT PARTITION_NAME, HIGH_VALUE FROM USER_TAB_PARTITIONS WHERE TABLE_NAME ='SALES_BY_REGION';
    PARTITION_NAME       HIGH_VALUE
    --------------       ---------------
    UNKNOWN              DEFAULT
    YEARLY_EAST          'MA', 'NY', 'NC'
    YEARLY_MIDWEST       'AZ', 'UT'
    YEARLY_NORTH         'MN', 'WI', 'MI'
    YEARLY_SOUTH         'NM', 'TX', 'GA'
    YEARLY_WEST          'CA', 'OR', 'WA'
    6 Rows selected.

    SELECT DEPT_NUMBER, DEPT_NAME, QUARTERLY_SALES, STATE FROM SALES_BY_REGION PARTITION(yearly_midwest);
    DEPT_NUMBER DEPT_NAME            QUARTERLY_SALES ST
    ----------- -------------------- --------------- --
              9 AUTO MIDWEST                 1950000 AZ
              9 AUTO MIDWEST                 5725000 UT

    SELECT DEPT_NUMBER, DEPT_NAME, QUARTERLY_SALES, STATE FROM SALES_BY_REGION PARTITION(unknown);
    no rows selected

    REM Split the DEFAULT partition again to add a new 'yearly_mideast' partition.
    ALTER TABLE sales_by_region
       SPLIT PARTITION unknown VALUES ('OH', 'IL')
       INTO
        ( PARTITION yearly_mideast,
          PARTITION unknown);
    Table altered.

    SELECT PARTITION_NAME, HIGH_VALUE FROM USER_TAB_PARTITIONS WHERE TABLE_NAME ='SALES_BY_REGION';
    PARTITION_NAME      HIGH_VALUE
    ------------------  ------------------
    UNKNOWN             DEFAULT
    YEARLY_EAST         'MA', 'NY', 'NC'
    YEARLY_MIDEAST      'OH', 'IL'
    YEARLY_MIDWEST      'AZ', 'UT'
    YEARLY_NORTH        'MN', 'WI', 'MI'
    YEARLY_SOUTH        'NM', 'TX', 'GA'
    YEARLY_WEST         'CA', 'OR', 'WA'
    7 rows selected.

    INSERT INTO SALES_BY_REGION VALUES (007, 'AUTO MIDEAST',  925000, 'OH');
    INSERT INTO SALES_BY_REGION VALUES (007, 'AUTO MIDEAST', 1325000, 'IL');

    SELECT DEPT_NUMBER, DEPT_NAME, QUARTERLY_SALES, STATE FROM SALES_BY_REGION PARTITION(yearly_mideast);
    DEPT_NUMBER DEPT_NAME            QUARTERLY_SALES ST
    ----------- -------------------- --------------- --
              7 AUTO MIDEAST                  925000 OH
              7 AUTO MIDEAST                 1325000 IL

    SELECT DEPT_NUMBER, DEPT_NAME, QUARTERLY_SALES, STATE FROM SALES_BY_REGION PARTITION(unknown);
    no rows selected

#### 4.4.13.3 Splitting a Partition of an Interval-Partitioned Table

You can split a range or a materialized interval partition with the `ALTER` `TABLE` `SPLIT` `PARTITION` statement in an interval-partitioned table.

Splitting a range partition in the interval-partitioned table is described in Splitting a Partition of a Range-Partitioned Table.

To split a materialized interval partition, you specify a value of the partitioning key column within the interval partition at which to split the partition. The first of the resulting two new partitions includes all rows in the original partition whose partitioning key column values map lower than the specified value. The second partition contains all rows whose partitioning key column values map greater than or equal to the specified value. The split partition operation moves the transition point up to the higher boundary of the partition you just split, and all materialized interval partitions lower than the newly split partitions are implicitly converted into range partitions, with their upper boundaries defined by the upper boundaries of the intervals.

You can optionally specify new attributes for the two range partitions resulting from the split. If there are local indexes defined on the table, then this statement also splits the matching partition in each local index. You cannot split interval partitions that have not yet been created.

The following example shows splitting the May 2007 partition in the monthly interval partitioned table `transactions`.

    ALTER TABLE transactions
        SPLIT PARTITION FOR(TO_DATE('01-MAY-2007','dd-MON-yyyy'))
        AT (TO_DATE('15-MAY-2007','dd-MON-yyyy'));

#### 4.4.13.4 Splitting a \*-Hash Partition

You can split a hash partition with the `ALTER` `TABLE` `SPLIT` `PARTITION` statement.

This is the opposite of merging \*-hash partitions. When you split \*-hash partitions, the new subpartitions are rehashed into either the number of subpartitions specified in a `SUBPARTITIONS` or `SUBPARTITION` clause. Or, if no such clause is included, the new partitions inherit the number of subpartitions (and tablespaces) from the partition being split.

The inheritance of properties is different when a \*-hash partition is split, versus when two \*-hash partitions are merged. When a partition is split, the new partitions can inherit properties from the original partition because there is only one parent. However, when partitions are merged, properties must be inherited from table level defaults because there are two parents and the new partition cannot inherit from either at the expense of the other.

The following example splits a range-hash partition:

    ALTER TABLE all_seasons SPLIT PARTITION quarter_1
         AT (TO_DATE('16-dec-1997','dd-mon-yyyy'))
         INTO (PARTITION q1_1997_1 SUBPARTITIONS 4 STORE IN (ts1,ts3),
               PARTITION q1_1997­_2);

The rules for splitting an interval-hash partitioned table follow the rules for splitting an interval-partitioned table. As described in Splitting a Partition of an Interval-Partitioned Table, the transition point is changed to the higher boundary of the split partition.

#### 4.4.13.5 Splitting Partitions in a \*-List Partitioned Table

Partitions can be split at both the partition level and at the subpartition level in a list partitioned table..

- Splitting a \*-List Partition

- Splitting a \*-List Subpartition

##### 4.4.13.5.1 Splitting a \*-List Partition

You can split a list partition with the `ALTER` `TABLE` `SPLIT` `PARTITION` statement.

Splitting a partition of a \*-list partitioned table is similar to the description in Splitting a Partition of a List-Partitioned Table. No subpartition literal value list can be specified for either of the new partitions. The new partitions inherit the subpartition descriptions from the original partition being split.

The following example splits the `q1_1999` partition of the `quarterly_regional_sales` table:

    ALTER TABLE quarterly_regional_sales SPLIT PARTITION q1_1999
       AT (TO_DATE('15-Feb-1999','dd-mon-yyyy'))
       INTO ( PARTITION q1_1999_jan_feb
                 TABLESPACE ts1,
              PARTITION q1_1999_feb_mar
                 STORAGE (INITIAL 8M) TABLESPACE ts2)
       PARALLEL 5;

This operation splits the partition `q1_1999` into two resulting partitions: `q1_1999_jan_feb` and `q1_1999_feb_mar`. Both partitions inherit their subpartition descriptions from the original partition. The individual partitions have new physical attributes, including tablespaces, specified at the partition level. These new attributes become the default attributes of the new partitions. This operation is run with parallelism of degree 5.

The `ALTER` `TABLE` `SPLIT` `PARTITION` statement provides no means of specifically naming subpartitions resulting from the split of a partition in a composite partitioned table. However, for those subpartitions in the parent partition with names of the form `partition name_subpartition name`, the database generates corresponding names in the newly created subpartitions using the new partition names. All other subpartitions are assigned system generated names of the form `SYS_SUBP``n`. System generated names are also assigned for the subpartitions of any partition resulting from the split for which a name is not specified. Unnamed partitions are assigned a system generated partition name of the form `SYS_P``n`.

The following query displays the subpartition names resulting from the previous split partition operation on table `quarterly_regional_sales`. It also reflects the results of other operations performed on this table in preceding sections of this chapter since its creation in [About Creating Composite Range-List Partitioned Tables](create-composite-partition-table.md).

    SELECT PARTITION_NAME, SUBPARTITION_NAME, TABLESPACE_NAME
      FROM DBA_TAB_SUBPARTITIONS
      WHERE TABLE_NAME='QUARTERLY_REGIONAL_SALES'
      ORDER BY PARTITION_NAME;

    PARTITION_NAME       SUBPARTITION_NAME              TABLESPACE_NAME
    -------------------- ------------------------------ ---------------
    Q1_1999_FEB_MAR      Q1_1999_FEB_MAR_WEST           TS2
    Q1_1999_FEB_MAR      Q1_1999_FEB_MAR_NORTHEAST      TS2
    Q1_1999_FEB_MAR      Q1_1999_FEB_MAR_SOUTHEAST      TS2
    Q1_1999_FEB_MAR      Q1_1999_FEB_MAR_NORTHCENTRAL   TS2
    Q1_1999_FEB_MAR      Q1_1999_FEB_MAR_SOUTHCENTRAL   TS2
    Q1_1999_FEB_MAR      Q1_1999_FEB_MAR_SOUTH          TS2
    Q1_1999_JAN_FEB      Q1_1999_JAN_FEB_WEST           TS1
    Q1_1999_JAN_FEB      Q1_1999_JAN_FEB_NORTHEAST      TS1
    Q1_1999_JAN_FEB      Q1_1999_JAN_FEB_SOUTHEAST      TS1
    Q1_1999_JAN_FEB      Q1_1999_JAN_FEB_NORTHCENTRAL   TS1
    Q1_1999_JAN_FEB      Q1_1999_JAN_FEB_SOUTHCENTRAL   TS1
    Q1_1999_JAN_FEB      Q1_1999_JAN_FEB_SOUTH          TS1
    Q1_2000              Q1_2000_NORTHWEST              TS3
    Q1_2000              Q1_2000_SOUTHWEST              TS3
    Q1_2000              Q1_2000_NORTHEAST              TS3
    Q1_2000              Q1_2000_SOUTHEAST              TS3
    Q1_2000              Q1_2000_NORTHCENTRAL           TS3
    Q1_2000              Q1_2000_SOUTHCENTRAL           TS3
    Q2_1999              Q2_1999_NORTHWEST              TS4
    Q2_1999              Q2_1999_SOUTHWEST              TS4
    Q2_1999              Q2_1999_NORTHEAST              TS4
    Q2_1999              Q2_1999_SOUTHEAST              TS4
    Q2_1999              Q2_1999_NORTHCENTRAL           TS4
    Q2_1999              Q2_1999_SOUTHCENTRAL           TS4
    Q3_1999              Q3_1999_NORTHWEST              TS4
    Q3_1999              Q3_1999_SOUTHWEST              TS4
    Q3_1999              Q3_1999_NORTHEAST              TS4
    Q3_1999              Q3_1999_SOUTHEAST              TS4
    Q3_1999              Q3_1999_NORTHCENTRAL           TS4
    Q3_1999              Q3_1999_SOUTHCENTRAL           TS4
    Q4_1999              Q4_1999_NORTHWEST              TS4
    Q4_1999              Q4_1999_SOUTHWEST              TS4
    Q4_1999              Q4_1999_NORTHEAST              TS4
    Q4_1999              Q4_1999_SOUTHEAST              TS4
    Q4_1999              Q4_1999_NORTHCENTRAL           TS4
    Q4_1999              Q4_1999_SOUTHCENTRAL           TS4

    36 rows selected.

##### 4.4.13.5.2 Splitting a \*-List Subpartition

You can split a list subpartition with the `ALTER` `TABLE` `SPLIT` `SUBPARTITION` statement.

Splitting a list subpartition of a \*-list partitioned table is similar to the description in Splitting a Partition of a List-Partitioned Table, but the syntax is that of `SUBPARTITION` rather than `PARTITION`. For example, the following statement splits a subpartition of the `quarterly_regional_sales` table:

    ALTER TABLE quarterly_regional_sales SPLIT SUBPARTITION q2_1999_southwest
       VALUES ('UT') INTO
          ( SUBPARTITION q2_1999_utah
               TABLESPACE ts2,
            SUBPARTITION q2_1999_southwest
               TABLESPACE ts3
          )
       PARALLEL;

This operation splits the subpartition `q2_1999_southwest` into two subpartitions:

- `q2_1999_utah` with literal value list of `('UT')`

- `q2_1999_southwest` which inherits the remaining literal value list of `('AZ','NM')`

The individual subpartitions have new physical attributes that are inherited from the subpartition being split.

You can only split subpartitions in an interval-list partitioned table for range partitions or materialized interval partitions. To change subpartition values for future interval partitions, you must modify the subpartition template.

#### 4.4.13.6 Splitting a \*-Range Partition

You can split a range partition using the `ALTER` `TABLE` `SPLIT` `PARTITION` statement.

Splitting a partition of a \*-range partitioned table is similar to the description in Splitting a Partition of a Range-Partitioned Table. No subpartition range values can be specified for either of the new partitions. The new partitions inherit the subpartition descriptions from the original partition being split.

The following example splits the May 2007 interval partition of the interval-range partitioned `orders` table:

    ALTER TABLE orders
        SPLIT PARTITION FOR(TO_DATE('01-MAY-2007','dd-MON-yyyy'))
        AT (TO_DATE('15-MAY-2007','dd-MON-yyyy'))
        INTO (PARTITION p_fh_may07,PARTITION p_sh_may2007);

This operation splits the interval partition `FOR('01-MAY-2007')` into two resulting partitions: `p_fh_may07` and `p_sh_may_2007`. Both partitions inherit their subpartition descriptions from the original partition. Any interval partitions before the June 2007 partition have been converted into range partitions, as described in Merging Interval Partitions.

The `ALTER TABLE SPLIT PARTITION` statement provides no means of specifically naming subpartitions resulting from the split of a partition in a composite partitioned table. However, for those subpartitions in the parent partition with names of the form `partition name``_``subpartition name`, the database generates corresponding names in the newly created subpartitions using the new partition names. All other subpartitions are assigned system generated names of the form `SYS_SUBP``n`. System generated names are also assigned for the subpartitions of any partition resulting from the split for which a name is not specified. Unnamed partitions are assigned a system generated partition name of the form `SYS_P``n`.

The following query displays the subpartition names and high values resulting from the previous split partition operation on table `orders`. It also reflects the results of other operations performed on this table in preceding sections of this chapter since its creation.

    BREAK ON partition_name

    SELECT partition_name, subpartition_name, high_value
    FROM user_tab_subpartitions
    WHERE table_name = 'ORCERS'
    ORDER BY partition_name, subpartition_position;

    PARTITION_NAME            SUBPARTITION_NAME              HIGH_VALUE
    ------------------------- ------------------------------ ---------------
    P_BEFORE_2007             P_BEFORE_2007_P_SMALL          1000
                              P_BEFORE_2007_P_MEDIUM         10000
                              P_BEFORE_2007_P_LARGE          100000
                              P_BEFORE_2007_P_EXTRAORDINARY  MAXVALUE
    P_FH_MAY07                SYS_SUBP2985                   1000
                              SYS_SUBP2986                   10000
                              SYS_SUBP2987                   100000
                              SYS_SUBP2988                   MAXVALUE
    P_PRE_MAY_2007            P_PRE_MAY_2007_P_SMALL         1000
                              P_PRE_MAY_2007_P_MEDIUM        10000
                              P_PRE_MAY_2007_P_LARGE         100000
                              P_PRE_MAY_2007_P_EXTRAORDINARY MAXVALUE
    P_SH_MAY2007              SYS_SUBP2989                   1000
                              SYS_SUBP2990                   10000
                              SYS_SUBP2991                   100000
                              SYS_SUBP2992                   MAXVALUE

##### 4.4.13.6.1 Splitting a \*-Range Subpartition

You can split a range subpartition using the `ALTER` `TABLE` `SPLIT` `SUBPARTITION` statement.

Splitting a range subpartition of a \*-range partitioned table is similar to the description in Splitting a Partition of a Range-Partitioned Table, but the syntax is that of `SUBPARTITION` rather than `PARTITION`. For example, the following statement splits a subpartition of the `orders` table:

    ALTER TABLE orders
    SPLIT SUBPARTITION p_pre_may_2007_p_large AT (50000)
    INTO (SUBPARTITION p_pre_may_2007_med_large TABLESPACE TS4
         , SUBPARTITION p_pre_may_2007_large_large TABLESPACE TS5
         );

This operation splits the subpartition `p_pre_may_2007_p_large` into two subpartitions:

- `p_pre_may_2007_med_large` with values between 10000 and 50000

- `p_pre_may_2007_large_large` with values between 50000 and 100000

The individual subpartitions have new physical attributes that are inherited from the subpartition being split.

You can only split subpartitions in an interval-range partitioned table for range partitions or materialized interval partitions. To change subpartition boundaries for future interval partitions, you must modify the subpartition template.

#### 4.4.13.7 Splitting Index Partitions

You cannot explicitly split a partition in a local index. A local index partition is split only when you split a partition in the underlying table.

However, you can split a global index partition as is done in the following example:

    ALTER INDEX quon1 SPLIT
        PARTITION canada AT ( 100 ) INTO
        PARTITION canada1 ..., PARTITION canada2 ...);
    ALTER INDEX quon1 REBUILD PARTITION canada1;
    ALTER INDEX quon1 REBUILD PARTITION canada2;

The index being split can contain index data, and the resulting partitions do not require rebuilding, unless the original partition was previously marked `UNUSABLE`.

#### 4.4.13.8 Splitting into Multiple Partitions

You can redistribute the contents of one partition or subpartition into multiple partitions or subpartitions with the `SPLIT` `PARTITION` and `SPLIT` `SUBPARTITION` clauses of the `ALTER` `TABLE` statement.

When splitting multiple partitions, the segment associated with the current partition is discarded. Each new partitions obtains a new segment and inherits all unspecified physical attributes from the current source partition. Fast split optimization is applied to multipartition split operations when required conditions are met.

You can use the extended split syntax to specify a list of new partition descriptions similar to the create partitioned table SQL statements, rather than specifying the `AT` or `VALUES` clause. Additionally, the range or list values clause for the last new partition description is derived based on the high bound of the source partition and the bound values specified for the first (N-1) new partitions resulting from the split.

The following SQL statements are examples of splitting a partition into multiple partitions.

    ALTER TABLE SPLIT PARTITION p0 INTO
      (PARTITION p01 VALUES LESS THAN (25),
       PARTITION p02 VALUES LESS THAN (50),
       PARTITION p03 VALUES LESS THAN (75),
       PARTITION p04);

    ALTER TABLE SPLIT PARTITION p0 INTO
      (PARTITION p01 VALUES LESS THAN (25),
       PARTITION p02);

In the second SQL example, partition `p02` has the high bound of the original partition `p0`.

To split a range partition into N partitions, (N-1) values of the partitioning key column must be specified within the range of the partition at which to split the partition. The new non-inclusive upper bound values specified must be in ascending order. The high bound of Nth new partition is assigned the value of the high bound of the partition being split. The names and physical attributes of the N new partitions resulting from the split can be optionally specified.

To split a list partition into N partitions, (N-1) lists of literal values must be specified, each of which defines the first (N-1) partitions into which rows with corresponding partitioning key values are inserted. The remaining rows of the original partition are inserted into the Nth new partition whose value list contains the remaining literal values from the original partition. No two value lists can contain the same partition value. The (N-1) value lists that are specified cannot contain all of the partition values of the current partition because the Nth new partition would be empty. Also, the (N-1) value lists cannot contain any partition values that do not exist for the current partition.

When splitting a `DEFAULT` list partition or a `MAXVALUE` range partition into multiple partitions, the first (N-1) new partitions are created using the literal value lists or high bound values specified, while the Nth new partition resulting from the split have the `DEFAULT` value or `MAXVALUE`. Splitting a partition of a composite partitioned table into multiple partitions assumes the existing behavior with respect to inheritance of the number, names, bounds and physical properties of the subpartitions of the new partitions resulting from the split. The `SPLIT_TABLE_SUBPARTITION` clause is extended similarly to allow split of a range or list subpartition into N new subpartitions.

The behavior of the SQL statement with respect to local and global indexes remains unchanged. Corresponding local index partition are split into multiple partitions. If the partitioned table contains LOB columns, then existing semantics for the `SPLIT` `PARTITION` clause apply with the extended syntax; that is, LOB data and index segments is dropped for current partition and new segments are created for each LOB column for each new partition. Fast split optimization is applied to multipartition split operations when required conditions are met.

For example, the following SQL statement splits the `sales_Q4_2007` partition of the partitioned by range table `sales` splits into five partitions corresponding to the quarters of the next year. In this example, the partition `sales_Q4_2008` implicitly becomes the high bound of the split partition.

    ALTER TABLE sales SPLIT PARTITION sales_Q4_2007 INTO
    ( PARTITION sales_Q4_2007 VALUES LESS THAN (TO_DATE('01-JAN-2008','dd-MON-yyyy')),
      PARTITION sales_Q1_2008 VALUES LESS THAN (TO_DATE('01-APR-2008','dd-MON-yyyy')),
      PARTITION sales_Q2_2008 VALUES LESS THAN (TO_DATE('01-JUL-2008','dd-MON-yyyy')),
      PARTITION sales_Q3_2008 VALUES LESS THAN (TO_DATE('01-OCT-2008','dd-MON-yyyy')),
      PARTITION sales_Q4_2008);

For the sample table `customers` partitioned by list, the following statement splits the partition Europe into three partitions.

    ALTER TABLE list_customers SPLIT PARTITION Europe INTO
      (PARTITION western-europe VALUES ('GERMANY', 'FRANCE'),
       PARTITION southern-europe VALUES ('ITALY'),
       PARTITION rest-europe);

**See Also:**

Restrictions and Special Requirements for Multi-Partition Operations on Tables with Domain Indexes

#### 4.4.13.9 Fast SPLIT PARTITION and SPLIT SUBPARTITION Operations

Oracle Database implements a `SPLIT` `PARTITION` operation by creating two or more new partitions and redistributing the rows from the partition being split into the new partitions.

This is a time-consuming operation because it is necessary to scan all the rows of the partition being split and then insert them one-by-one into the new partitions. Further if you do not use the `UPDATE` `INDEXES` clause, then both local and global indexes also require rebuilding.

Sometimes after a split operation, one new partition contains all of the rows from the partition being split, while the other partitions contain no rows. This is often the case when splitting the first or last partition of a table. The database can detect such situations and can optimize the split operation. This optimization results in a fast split operation that behaves like an add partition operation.

Specifically, the database can optimize and speed up `SPLIT` `PARTITION` operations if all of the following conditions are met:

- One of the resulting partitions contains all of the rows.

- The non-empty resulting partition must have storage characteristics identical to those of the partition being split. Specifically:

  - If the partition being split is composite, then the storage characteristics of each subpartition in the new resulting partition must be identical to those of the subpartitions of the partition being split.

  - If the partition being split contains a `LOB` column, then the storage characteristics of each `LOB` (sub)partition in the new non-empty resulting partition must be identical to those of the `LOB` (sub)partitions of the partition being split.

  - If a partition of an index-organized table with overflow is being split, then the storage characteristics of each overflow (sub)partition in the new nonempty resulting partition must be identical to those of the overflow (sub)partitions of the partition being split.

  - If a partition of an index-organized table with mapping table is being split, then the storage characteristics of each mapping table (sub)partition in the new nonempty resulting partition must be identical to those of the mapping table (sub)partitions of the partition being split.

If these conditions are met after the split, then all global indexes remain usable, even if you did not specify the `UPDATE` `INDEXES` clause. Local index (sub)partitions associated with the resulting partitions remain usable if they were usable before the split. Local index (sub)partitions corresponding to the non-empty resulting partition are identical to the local index (sub)partitions of the partition that was split. The same optimization holds for `SPLIT` `SUBPARTITION` operations.

### 4.4.14 About Truncating Partitions and Subpartitions

Truncating a partition is similar to dropping a partition, except that the partition is emptied of its data, but not physically dropped.

Use the `ALTER` `TABLE` `TRUNCATE` `PARTITION` statement to remove all rows from a table partition. You cannot truncate an index partition. However, if local indexes are defined for the table, the `ALTER` `TABLE` `TRUNCATE` `PARTITION` statement truncates the matching partition in each local index. Unless you specify `UPDATE` `INDEXES`, any global indexes are marked `UNUSABLE` and must be rebuilt. You cannot use `UPDATE` `INDEXES` for index-organized tables. Use `UPDATE` `GLOBAL` `INDEXES` instead.

This section contains the following topics:

- About Truncating a Table Partition

- Truncating Multiple Partitions

- Truncating Subpartitions

- Truncating a Partition with the Cascade Option

**See Also:**

- [Asynchronous Global Index Maintenance for Dropping and Truncating Partitions](maintenance-partition-can-be-performed.md) for information about asynchronous index maintenance for truncating partitions

- About Dropping Partitions and Subpartitions for information about dropping a partition

#### 4.4.14.1 About Truncating a Table Partition

Use the `ALTER` `TABLE` `TRUNCATE` `PARTITION` statement to remove all rows from a table partition, with or without reclaiming space.

Truncating a partition in an interval-partitioned table does not move the transition point. You can truncate partitions and subpartitions in a reference-partitioned table.

- Truncating Table Partitions Containing Data and Global Indexes

- Truncating a Partition Containing Data and Referential Integrity Constraints

##### 4.4.14.1.1 Truncating Table Partitions Containing Data and Global Indexes

When truncating a table partition that contains data and global indexes, you can use one of several methods.

If the partition contains data and global indexes, use one of the following methods (method 1, 2, or 3) to truncate the table partition.

##### Method 1

Leave the global indexes in place during the `ALTER` `TABLE` `TRUNCATE` `PARTITION` statement. In this example, table `sales` has a global index `sales_area_ix`, which is rebuilt.

    ALTER TABLE sales TRUNCATE PARTITION dec98;
    ALTER INDEX sales_area_ix REBUILD;

This method is most appropriate for large tables where the partition being truncated contains a significant percentage of the total data in the table.

##### Method 2

Run the `DELETE` statement to delete all rows from the partition before you issue the `ALTER` `TABLE` `TRUNCATE` `PARTITION` statement. The `DELETE` statement updates the global indexes, and also fires triggers and generates redo and undo logs.

For example, to truncate the first partition, run the following statements:

    DELETE FROM sales PARTITION (dec98);
    ALTER TABLE sales TRUNCATE PARTITION dec98;

This method is most appropriate for small tables, or for large tables when the partition being truncated contains a small percentage of the total data in the table.

##### Method 3

Specify `UPDATE` `INDEXES` in the `ALTER TABLE` statement. This causes the global index to be truncated at the time the partition is truncated.

    ALTER TABLE sales TRUNCATE PARTITION dec98
         UPDATE INDEXES;

With asynchronous global index maintenance, this operation is a metadata-only operation.

##### 4.4.14.1.2 Truncating a Partition Containing Data and Referential Integrity Constraints

If a partition contains data and has referential integrity constraints, then you cannot truncate the partition. However, if no other data is referencing any data in the partition to remove, then you can use one of several methods.

Choose either of the following methods (method 1 or 2) to truncate the table partition.

##### Method 1

Disable the integrity constraints, run the `ALTER` `TABLE` `TRUNCATE` `PARTITION` statement, then re-enable the integrity constraints. This method is most appropriate for large tables where the partition being truncated contains a significant percentage of the total data in the table. If there is still referencing data in other tables, then you must remove that data to be able to re-enable the integrity constraints.

##### Method 2

Issue the `DELETE` statement to delete all rows from the partition before you issue the `ALTER` `TABLE` `TRUNCATE` `PARTITION` statement. The `DELETE` statement enforces referential integrity constraints, and also fires triggers and generates redo and undo logs. Data in referencing tables is deleted if the foreign key constraints were created with the `ON DELETE CASCADE` option.

    DELETE FROM sales partition (dec94);
    ALTER TABLE sales TRUNCATE PARTITION dec94;

This method is most appropriate for small tables, or for large tables when the partition being truncated contains a small percentage of the total data in the table.

#### 4.4.14.2 Truncating Multiple Partitions

You can truncate multiple partitions from a range or list partitioned table with the `TRUNCATE` `PARTITION` clause of the `ALTER` `TABLE` statement.

The corresponding partitions of local indexes are truncated in the operation. Global indexes must be rebuilt unless `UPDATE` `INDEXES` is specified.

In the following example, the `ALTER` `TABLE` SQL statement truncates multiple partitions in a table. Note that the data is truncated, but the partitions are not dropped.

**Live SQL:**

View and run a related example on Oracle Live SQL at [Oracle Live SQL: Truncating a Range-Partitioned Table](https://livesql.oracle.com/apex/livesql/docs/vldbg/partitioning/truncate-partitions.html).

Example 4-39 Truncating Multiple Partitions

    CREATE TABLE sales_partition_truncate
      ( product_id       NUMBER(6) NOT NULL,
        customer_id      NUMBER    NOT NULL,
        channel_id       CHAR(1),
        promo_id         NUMBER(6),
        sales_date       DATE,
        quantity_sold    INTEGER,
        amount_sold      NUMBER(10,2)
      )
     PARTITION BY RANGE (sales_date)
     SUBPARTITION BY LIST (channel_id)
    (  PARTITION q3_2018 VALUES LESS THAN (TO_DATE('1-OCT-2018','DD-MON-YYYY'))
       ( SUBPARTITION q3_2018_p_catalog VALUES ('C'),
         SUBPARTITION q3_2018_p_internet VALUES ('I'),
         SUBPARTITION q3_2018_p_partners VALUES ('P'),
         SUBPARTITION q3_2018_p_direct_sales VALUES ('S'),
         SUBPARTITION q3_2018_p_tele_sales VALUES ('T')
       ),
      PARTITION q4_2018 VALUES LESS THAN (TO_DATE('1-JAN-2019','DD-MON-YYYY'))
       ( SUBPARTITION q4_2018_p_catalog VALUES ('C'),
         SUBPARTITION q4_2018_p_internet VALUES ('I'),
         SUBPARTITION q4_2018_p_partners VALUES ('P'),
         SUBPARTITION q4_2018_p_direct_sales VALUES ('S'),
         SUBPARTITION q4_2018_p_tele_sales VALUES ('T')
       ),
      PARTITION q1_2019 VALUES LESS THAN (TO_DATE('1-APR-2019','DD-MON-YYYY'))
       ( SUBPARTITION q1_2019_p_catalog VALUES ('C')
       , SUBPARTITION q1_2019_p_internet VALUES ('I')
       , SUBPARTITION q1_2019_p_partners VALUES ('P')
       , SUBPARTITION q1_2019_p_direct_sales VALUES ('S')
       , SUBPARTITION q1_2019_p_tele_sales VALUES ('T')
       ),
      PARTITION q2_2019 VALUES LESS THAN (TO_DATE('1-JUL-2019','DD-MON-YYYY'))
       ( SUBPARTITION q2_2019_p_catalog VALUES ('C'),
         SUBPARTITION q2_2019_p_internet VALUES ('I'),
         SUBPARTITION q2_2019_p_partners VALUES ('P'),
         SUBPARTITION q2_2019_p_direct_sales VALUES ('S'),
         SUBPARTITION q2_2019_p_tele_sales VALUES ('T')
       ),
      PARTITION q3_2019 VALUES LESS THAN (TO_DATE('1-OCT-2019','DD-MON-YYYY'))
       ( SUBPARTITION q3_2019_p_catalog VALUES ('C'),
         SUBPARTITION q3_2019_p_internet VALUES ('I'),
         SUBPARTITION q3_2019_p_partners VALUES ('P'),
         SUBPARTITION q3_2019_p_direct_sales VALUES ('S'),
         SUBPARTITION q3_2019_p_tele_sales VALUES ('T')
       ),
      PARTITION q4_2019 VALUES LESS THAN (TO_DATE('1-JAN-2020','DD-MON-YYYY'))
       ( SUBPARTITION q4_2019_p_catalog VALUES ('C'),
         SUBPARTITION q4_2019_p_internet VALUES ('I'),
         SUBPARTITION q4_2019_p_partners VALUES ('P'),
         SUBPARTITION q4_2019_p_direct_sales VALUES ('S'),
         SUBPARTITION q4_2019_p_tele_sales VALUES ('T')
       )
      );

    SELECT TABLE_NAME, PARTITION_NAME, SUBPARTITION_NAME FROM USER_TAB_SUBPARTITIONS
           WHERE TABLE_NAME ='SALES_PARTITION_TRUNCATE';
    TABLE_NAME                  PARTITION_NAME    SUBPARTITION_NAME
    –------------------------   –--------------   –------------------
    SALES_PARTITION_TRUNCATE    Q1_2019           Q1_2019_P_CATALOG
    SALES_PARTITION_TRUNCATE    Q1_2019           Q1_2019_P_DIRECT_SALES
    ...
    30 rows selected.

    INSERT INTO sales_partition_truncate VALUES (1001,100,'C',150,'10-SEP-2018',500,2000);
    INSERT INTO sales_partition_truncate VALUES (1021,200,'C',160,'16-NOV-2018',100,1500);
    INSERT INTO sales_partition_truncate VALUES (1001,100,'C',150,'10-FEB-2019',500,2000);
    INSERT INTO sales_partition_truncate VALUES (1021,200,'S',160,'16-FEB-2019',100,1500);
    INSERT INTO sales_partition_truncate VALUES (1002,110,'I',180,'15-JUN-2019',100,1000);
    INSERT INTO sales_partition_truncate VALUES (5010,150,'P',200,'20-AUG-2019',1000,10000);
    INSERT INTO sales_partition_truncate VALUES (1001,100,'T',150,'12-OCT-2019',500,2000);

    SELECT * FROM sales_partition_truncate;
    PRODUCT_ID CUSTOMER_ID C   PROMO_ID SALES_DAT QUANTITY_SOLD AMOUNT_SOLD
    ---------- ----------- - ---------- --------- ------------- -----------
          1001         100 C        150 10-SEP-18           500        2000
          1021         200 C        160 16-NOV-18           100        1500
          1001         100 C        150 10-FEB-19           500        2000
          1021         200 S        160 16-FEB-19           100        1500
          1002         110 I        180 15-JUN-19           100        1000
          5010         150 P        200 20-AUG-19          1000       10000
          1001         100 T        150 12-OCT-19           500        2000
    7 rows selected.

    ALTER TABLE sales_partition_truncate
       TRUNCATE PARTITIONS q3_2018, q4_2018;

    SELECT * FROM sales_partition_truncate;
    PRODUCT_ID CUSTOMER_ID C   PROMO_ID SALES_DAT QUANTITY_SOLD AMOUNT_SOLD
    ---------- ----------- - ---------- --------- ------------- -----------
          1001         100 C        150 10-FEB-19           500        2000
          1021         200 S        160 16-FEB-19           100        1500
          1002         110 I        180 15-JUN-19           100        1000
          5010         150 P        200 20-AUG-19          1000       10000
          1001         100 T        150 12-OCT-19           500        2000
    5 rows selected.

    SELECT TABLE_NAME, PARTITION_NAME, SUBPARTITION_NAME FROM USER_TAB_SUBPARTITIONS
           WHERE TABLE_NAME ='SALES_PARTITION_TRUNCATE';
    TABLE_NAME                  PARTITION_NAME    SUBPARTITION_NAME
    –------------------------   –--------------   –------------------
    SALES_PARTITION_TRUNCATE    Q1_2019           Q1_2019_P_CATALOG
    SALES_PARTITION_TRUNCATE    Q1_2019           Q1_2019_P_DIRECT_SALES
    ...
    SALES_PARTITION_TRUNCATE    Q3_2018           Q3_2018_P_CATALOG
    SALES_PARTITION_TRUNCATE    Q3_2018           Q3_2018_P_DIRECT_SALES
    SALES_PARTITION_TRUNCATE    Q3_2018           Q3_2018_P_INTERNET
    SALES_PARTITION_TRUNCATE    Q3_2018           Q3_2018_P_PARTNERS
    SALES_PARTITION_TRUNCATE    Q3_2018           Q3_2018_P_TELE_SALES
    ...
    SALES_PARTITION_TRUNCATE    Q4_2018           Q4_2018_P_CATALOG
    SALES_PARTITION_TRUNCATE    Q4_2018           Q4_2018_P_DIRECT_SALES
    SALES_PARTITION_TRUNCATE    Q4_2018           Q4_2018_P_INTERNET
    SALES_PARTITION_TRUNCATE    Q4_2018           Q4_2018_P_PARTNERS
    SALES_PARTITION_TRUNCATE    Q4_2018           Q4_2018_P_TELE_SALES
    ...
    30 rows selected.

**Note:**

If a table has a local domain index, truncating a single partition or the entire table is supported. Truncating multiple partitions in a single `ALTER TABLE` statement is not permitted if a local index is present.

**See Also:**

Restrictions and Special Requirements for Multi-Partition Operations on Tables with Domain Indexes

#### 4.4.14.3 Truncating Subpartitions

Use the `ALTER` `TABLE` `TRUNCATE` `SUBPARTITION` statement to remove all rows from a subpartition of a composite partitioned table.

When truncating a subpartition, corresponding local index subpartitions are also truncated.

In the following example, the `ALTER` `TABLE` statement truncates data in subpartitions of a table. In this example, the space occupied by the deleted rows is made available for use by other schema objects in the tablespace with the `DROP` `STORAGE` clause. Note that the data is truncated, but the subpartitions are not dropped.

Example 4-40 Truncating Multiple Subpartitions

    CREATE TABLE sales_partition_truncate
      ( product_id       NUMBER(6) NOT NULL,
        customer_id      NUMBER    NOT NULL,
        channel_id       CHAR(1),
        promo_id         NUMBER(6),
        sales_date       DATE,
        quantity_sold    INTEGER,
        amount_sold      NUMBER(10,2)
      )
     PARTITION BY RANGE (sales_date)
     SUBPARTITION BY LIST (channel_id)
    (  PARTITION q3_2018 VALUES LESS THAN (TO_DATE('1-OCT-2018','DD-MON-YYYY'))
       ( SUBPARTITION q3_2018_p_catalog VALUES ('C'),
         SUBPARTITION q3_2018_p_internet VALUES ('I'),
         SUBPARTITION q3_2018_p_partners VALUES ('P'),
         SUBPARTITION q3_2018_p_direct_sales VALUES ('S'),
         SUBPARTITION q3_2018_p_tele_sales VALUES ('T')
       ),
      PARTITION q4_2018 VALUES LESS THAN (TO_DATE('1-JAN-2019','DD-MON-YYYY'))
       ( SUBPARTITION q4_2018_p_catalog VALUES ('C'),
         SUBPARTITION q4_2018_p_internet VALUES ('I'),
         SUBPARTITION q4_2018_p_partners VALUES ('P'),
         SUBPARTITION q4_2018_p_direct_sales VALUES ('S'),
         SUBPARTITION q4_2018_p_tele_sales VALUES ('T')
       ),
      PARTITION q1_2019 VALUES LESS THAN (TO_DATE('1-APR-2019','DD-MON-YYYY'))
       ( SUBPARTITION q1_2019_p_catalog VALUES ('C')
       , SUBPARTITION q1_2019_p_internet VALUES ('I')
       , SUBPARTITION q1_2019_p_partners VALUES ('P')
       , SUBPARTITION q1_2019_p_direct_sales VALUES ('S')
       , SUBPARTITION q1_2019_p_tele_sales VALUES ('T')
       ),
      PARTITION q2_2019 VALUES LESS THAN (TO_DATE('1-JUL-2019','DD-MON-YYYY'))
       ( SUBPARTITION q2_2019_p_catalog VALUES ('C'),
         SUBPARTITION q2_2019_p_internet VALUES ('I'),
         SUBPARTITION q2_2019_p_partners VALUES ('P'),
         SUBPARTITION q2_2019_p_direct_sales VALUES ('S'),
         SUBPARTITION q2_2019_p_tele_sales VALUES ('T')
       ),
      PARTITION q3_2019 VALUES LESS THAN (TO_DATE('1-OCT-2019','DD-MON-YYYY'))
       ( SUBPARTITION q3_2019_p_catalog VALUES ('C'),
         SUBPARTITION q3_2019_p_internet VALUES ('I'),
         SUBPARTITION q3_2019_p_partners VALUES ('P'),
         SUBPARTITION q3_2019_p_direct_sales VALUES ('S'),
         SUBPARTITION q3_2019_p_tele_sales VALUES ('T')
       ),
      PARTITION q4_2019 VALUES LESS THAN (TO_DATE('1-JAN-2020','DD-MON-YYYY'))
       ( SUBPARTITION q4_2019_p_catalog VALUES ('C'),
         SUBPARTITION q4_2019_p_internet VALUES ('I'),
         SUBPARTITION q4_2019_p_partners VALUES ('P'),
         SUBPARTITION q4_2019_p_direct_sales VALUES ('S'),
         SUBPARTITION q4_2019_p_tele_sales VALUES ('T')
       )
      );

    SELECT TABLE_NAME, PARTITION_NAME, SUBPARTITION_NAME FROM USER_TAB_SUBPARTITIONS
           WHERE TABLE_NAME ='SALES_PARTITION_TRUNCATE';
    TABLE_NAME                  PARTITION_NAME    SUBPARTITION_NAME
    –------------------------   –--------------   –------------------
    SALES_PARTITION_TRUNCATE    Q1_2019           Q1_2019_P_CATALOG
    SALES_PARTITION_TRUNCATE    Q1_2019           Q1_2019_P_DIRECT_SALES
    ...
    30 rows selected.

    INSERT INTO sales_partition_truncate VALUES (1001,100,'C',150,'10-SEP-2018',500,2000);
    INSERT INTO sales_partition_truncate VALUES (1021,200,'C',160,'16-NOV-2018',100,1500);
    INSERT INTO sales_partition_truncate VALUES (1001,100,'C',150,'10-FEB-2019',500,2000);
    INSERT INTO sales_partition_truncate VALUES (1021,200,'S',160,'16-FEB-2019',100,1500);
    INSERT INTO sales_partition_truncate VALUES (1002,110,'I',180,'15-JUN-2019',100,1000);
    INSERT INTO sales_partition_truncate VALUES (5010,150,'P',200,'20-AUG-2019',1000,10000);
    INSERT INTO sales_partition_truncate VALUES (1001,100,'T',150,'12-OCT-2019',500,2000);

    SELECT * FROM sales_partition_truncate;
    PRODUCT_ID CUSTOMER_ID C   PROMO_ID SALES_DAT QUANTITY_SOLD AMOUNT_SOLD
    ---------- ----------- - ---------- --------- ------------- -----------
          1001         100 C        150 10-SEP-18           500        2000
          1021         200 C        160 16-NOV-18           100        1500
          1001         100 C        150 10-FEB-19           500        2000
          1021         200 S        160 16-FEB-19           100        1500
          1002         110 I        180 15-JUN-19           100        1000
          5010         150 P        200 20-AUG-19          1000       10000
          1001         100 T        150 12-OCT-19           500        2000
    7 rows selected.

    ALTER TABLE sales_subpartition_truncate
       TRUNCATE SUBPARTITIONS q3_2018_p_catalog, q4_2018_p_catalog, q1_2019_p_catalog,
                              q2_2019_p_catalog, q3_2019_p_catalog, q4_2019_p_catalog
            DROP STORAGE;

    SELECT * FROM sales_partition_truncate;
    PRODUCT_ID CUSTOMER_ID C   PROMO_ID SALES_DAT QUANTITY_SOLD AMOUNT_SOLD
    ---------- ----------- - ---------- --------- ------------- -----------
          1021         200 S        160 16-FEB-19           100        1500
          1002         110 I        180 15-JUN-19           100        1000
          5010         150 P        200 20-AUG-19          1000       10000
          1001         100 T        150 12-OCT-19           500        2000
    4 rows selected.

    SELECT TABLE_NAME, PARTITION_NAME, SUBPARTITION_NAME FROM USER_TAB_SUBPARTITIONS
           WHERE TABLE_NAME ='SALES_PARTITION_TRUNCATE';
    TABLE_NAME                  PARTITION_NAME    SUBPARTITION_NAME
    –------------------------   –--------------   –------------------
    SALES_PARTITION_TRUNCATE    Q1_2019           Q1_2019_P_CATALOG
    SALES_PARTITION_TRUNCATE    Q1_2019           Q1_2019_P_DIRECT_SALES
    ...
    30 rows selected.

#### 4.4.14.4 Truncating a Partition with the Cascade Option

You can use cascade truncate operations to a reference partitioned child table with the `CASCADE` option of `TRUNCATE` `TABLE`, `ALTER` `TABLE` `TRUNCATE` `PARTITION`, and `ALTER` `TABLE` `TRUNCATE` `SUBPARTITION` SQL statements.

When the `CASCADE` option is specified for `TRUNCATE` `TABLE`, the truncate table operation also truncates child tables that reference the targeted table through an enabled referential constraint that has `ON` `DELETE` `CASCADE` enabled. This cascading action applies recursively to grandchildren, great-grandchildren, and so on. After determining the set of tables to be truncated based on the enabled `ON` `DELETE` `CASCADE` referential constraints, an error is raised if any table in this set is referenced through an enabled constraint from a child outside of the set. If a parent and child are connected by multiple referential constraints, a `TRUNCATE` `TABLE` `CASCADE` operation targeting the parent succeeds if at least one constraint has `ON` `DELETE` `CASCADE` enabled.

Privileges are required on all tables affected by the operation. Any other options specified for the operation, such as `DROP` `STORAGE` or `PURGE` `MATERIALIZED` `VIEW` `LOG`, apply for all tables affected by the operation.

When the `CASCADE` option is specified, the `TRUNCATE` `PARTITION` and `TRUNCATE` `SUBPARTITION` operations cascade to reference partitioned tables that are children of the targeted table. The `TRUNCATE` can be targeted at any level in a reference partitioned hierarchy and cascades to child tables starting from the targeted table. Privileges are not required on the child tables, but the usual restrictions on the `TRUNCATE` operation, such as the table cannot be referenced by an enabled referential constraint that is not a partitioning constraint, apply for all tables affected by the operation.

The `CASCADE` option is ignored if it is specified for a table that does not have reference partitioned children. Any other options specified for the operation, such as `DROP` `STORAGE` or `UPDATE` `INDEXES`, apply to all tables affected by the operation.

The cascade options are off by default so they do not affect Oracle Database compatibility.

    ALTER TABLE sales
         TRUNCATE PARTITION dec2016
         DROP STORAGE
         CASCADE
         UPDATE INDEXES;
