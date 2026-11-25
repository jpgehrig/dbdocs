Creating a partitioned table or index is very similar to creating a nonpartitioned table or index.

When creating a partitioned table or index, you include a partitioning clause in the `CREATE TABLE` statement. The partitioning clause, and subclauses, that you include depend upon the type of partitioning you want to achieve.

Partitioning is possible on both regular (heap organized) tables and index-organized tables, except for those containing `LONG` or `LONG RAW` columns. You can create nonpartitioned global indexes, range or hash partitioned global indexes, and local indexes on partitioned tables.

When you create (or alter) a partitioned table, a row movement clause (either `ENABLE ROW MOVEMENT` or `DISABLE ROW MOVEMENT`) can be specified. This clause either enables or disables the migration of a row to a new partition if its key is updated. The default is `DISABLE ROW MOVEMENT`.

You can specify up to a total of 1024K-1 partitions for a single-level partitioned tables, or subpartitions for a composite partitioned table.

Creating automatic list composite partitioned tables and interval subpartitions can save space because these methods only create subpartitions in the presence of data. Deferring subpartition segment creation when creating new partitions on demand ensures that a subpartition segment is only created when the first matching row is inserted.

The following topics present details and examples of creating partitions for the various types of partitioned tables and indexes:

- About Creating Range-Partitioned Tables and Global Indexes

- Creating Range-Interval-Partitioned Tables

- About Creating Hash Partitioned Tables and Global Indexes

- About Creating List-Partitioned Tables

- Creating Reference-Partitioned Tables

- Creating Interval-Reference Partitioned Tables

- Creating a Table Using In-Memory Column Store With Partitioning

- Creating a Table with Read-Only Partitions or Subpartitions

- Creating a Partitioned External Table

- Specifying Partitioning on Key Columns

- Using Virtual Column-Based Partitioning

- Using Table Compression with Partitioned Tables

- Using Key Compression with Partitioned Indexes

- Specifying Partitioning with Segments

- Specifying Partitioning When Creating Index-Organized Tables

- Partitioning Restrictions for Multiple Block Sizes

- Partitioning of Collections in XMLType and Objects

**See Also:**

- [Oracle Database Administrator's Guide](../admin/managing-tables.md) for information about managing tables

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for the exact syntax of the partitioning clauses for creating and altering partitioned tables and indexes, any restrictions on their use, and specific privileges required for creating and altering tables

- [Oracle Database SecureFiles and Large Objects Developer's Guide ](../adlob/LOB-storage-with-applications.md)for information specific to creating partitioned tables containing columns with `LOB`s or other objects stored as `LOB`s

- [Oracle Database Object-Relational Developer's Guide ](../adobj/advanced-topics-for-oracle-objects.md)for information specific to creating tables with object types, nested tables, or VARRAYs

### 4.1.1 About Creating Range-Partitioned Tables and Global Indexes

The `PARTITION BY RANGE` clause of the `CREATE TABLE` statement specifies that the table or index is to be range-partitioned.

The `PARTITION` clauses identify the individual partition ranges, and the optional subclauses of a `PARTITION` clause can specify physical and other attributes specific to a partition segment. If not overridden at the partition level, partitions inherit the attributes of their underlying table.

The following topics are discussed:

- Creating a Range-Partitioned Table

- Creating a Range-Partitioned Table With More Complexity

- Creating a Range-Partitioned Global Index

#### 4.1.1.1 Creating a Range-Partitioned Table

Use the `PARTITION BY RANGE` clause of the `CREATE TABLE` statement to create a range-partitioned table.

Example 4-1 creates a table of four partitions, one for each quarter of sales. `time_id` is the partitioning column, while its values constitute the partitioning key of a specific row. The `VALUES LESS THAN` clause determines the partition bound: rows with partitioning key values that compare less than the ordered list of values specified by the clause are stored in the partition. Each partition is given a name (`sales_q1_2006`, `sales_q2_2006`, `sales_q3_2006`, `sales_q4_2006`), and each partition is contained in a separate tablespace (`tsa`, `tsb`, `tsc`, `tsd`). A row with `time_id=17-MAR-2006` would be stored in partition `sales_q1_2006`.

**Live SQL:**

View and run a related example on Oracle Live SQL at [Oracle Live SQL: Creating a Range Partitioned Table](https://livesql.oracle.com/apex/livesql/docs/vldbg/partitioning/range-partitioning-example.html).

Example 4-1 Creating a range-partitioned table

    CREATE TABLE sales
      ( prod_id       NUMBER(6)
      , cust_id       NUMBER
      , time_id       DATE
      , channel_id    CHAR(1)
      , promo_id      NUMBER(6)
      , quantity_sold NUMBER(3)
      , amount_sold   NUMBER(10,2)
      )
     PARTITION BY RANGE (time_id)
     ( PARTITION sales_q1_2006 VALUES LESS THAN (TO_DATE('01-APR-2006','dd-MON-yyyy'))
        TABLESPACE tsa
     , PARTITION sales_q2_2006 VALUES LESS THAN (TO_DATE('01-JUL-2006','dd-MON-yyyy'))
        TABLESPACE tsb
     , PARTITION sales_q3_2006 VALUES LESS THAN (TO_DATE('01-OCT-2006','dd-MON-yyyy'))
        TABLESPACE tsc
     , PARTITION sales_q4_2006 VALUES LESS THAN (TO_DATE('01-JAN-2007','dd-MON-yyyy'))
        TABLESPACE tsd
     );

#### 4.1.1.2 Creating a Range-Partitioned Table With More Complexity

With attributes and storage parameters, more complexity can be added to the creation of a range-partitioned table.

In Example 4-2, storage parameters and a `LOGGING` attribute are specified at the table level. These replace the corresponding defaults inherited from the tablespace level for the table itself, and are inherited by the range partitions. However, because there was little business in the first quarter, the storage attributes for partition `sales_q1_2006` are made smaller. The `ENABLE ROW MOVEMENT` clause is specified to allow the automatic migration of a row to a new partition if an update to a key value is made that would place the row in a different partition.

Example 4-2 Creating a range-partitioned table with LOGGING and ENABLE ROW MOVEMENT

    CREATE TABLE sales
      ( prod_id       NUMBER(6)
      , cust_id       NUMBER
      , time_id       DATE
      , channel_id    CHAR(1)
      , promo_id      NUMBER(6)
      , quantity_sold NUMBER(3)
      , amount_sold   NUMBER(10,2)
      )
     STORAGE (INITIAL 100K NEXT 50K) LOGGING
     PARTITION BY RANGE (time_id)
     ( PARTITION sales_q1_2006 VALUES LESS THAN (TO_DATE('01-APR-2006','dd-MON-yyyy'))
        TABLESPACE tsa STORAGE (INITIAL 20K NEXT 10K)
     , PARTITION sales_q2_2006 VALUES LESS THAN (TO_DATE('01-JUL-2006','dd-MON-yyyy'))
        TABLESPACE tsb
     , PARTITION sales_q3_2006 VALUES LESS THAN (TO_DATE('01-OCT-2006','dd-MON-yyyy'))
        TABLESPACE tsc
     , PARTITION sales_q4_2006 VALUES LESS THAN (TO_DATE('01-JAN-2007','dd-MON-yyyy'))
        TABLESPACE tsd
     )
     ENABLE ROW MOVEMENT;

#### 4.1.1.3 Creating a Range-Partitioned Global Index

The rules for creating range-partitioned global indexes are similar to those for creating range-partitioned tables.

Example 4-3 creates a range-partitioned global index on `sale_month` for the tables created in the previous examples. Each index partition is named but is stored in the default tablespace for the index.

Example 4-3 Creating a range-partitioned global index table

    CREATE INDEX amount_sold_ix ON sales(amount_sold)
       GLOBAL PARTITION BY RANGE(sale_month)
          ( PARTITION p_100 VALUES LESS THAN (100)
          , PARTITION p_1000 VALUES LESS THAN (1000)
          , PARTITION p_10000 VALUES LESS THAN (10000)
          , PARTITION p_100000 VALUES LESS THAN (100000)
          , PARTITION p_1000000 VALUES LESS THAN (1000000)
          , PARTITION p_greater_than_1000000 VALUES LESS THAN (maxvalue)
          );

**Note:**

If your enterprise has databases using different character sets, use caution when partitioning on character columns, because the sort sequence of characters is not identical in all character sets. For more information, refer to [Oracle Database Globalization Support Guide](../nlspg/overview-of-globalization-support.md)

### 4.1.2 Creating Range-Interval-Partitioned Tables

The `INTERVAL` clause of the `CREATE TABLE` statement establishes interval partitioning for the table.

You must specify at least one range partition using the `PARTITION` clause. The range partitioning key value determines the high value of the range partitions, which is called the transition point, and the database automatically creates interval partitions for data beyond that transition point. The lower boundary of every interval partition is the non-inclusive upper boundary of the previous range or interval partition.

For example, if you create an interval partitioned table with monthly intervals and the transition point is at January 1, 2010, then the lower boundary for the January 2010 interval is January 1, 2010. The lower boundary for the July 2010 interval is July 1, 2010, regardless of whether the June 2010 partition was previously created. Note, however, that using a date where the high or low bound of the partition would be out of the range set for storage causes an error. For example, `TO_DATE('9999-12-01', 'YYYY-MM-DD')` causes the high bound to be 10000-01-01, which would not be storable if 10000 is out of the legal range.

The optional `STORE IN` clause lets you specify one or more tablespaces into which the database stores interval partition data using a round-robin algorithm for subsequently created interval partitions.

For interval partitioning, you can specify only one partitioning key column and the datatype is restricted.

The following example specifies four partitions with varying interval widths. It also specifies that above the transition point of January 1, 2010, partitions are created with an interval width of one month. The high bound of partition `p3` represents the transition point. `p3` and all partitions below it (`p0`, `p1`, and `p2` in this example) are in the range section while all partitions above it fall into the interval section.

    CREATE TABLE interval_sales
        ( prod_id        NUMBER(6)
        , cust_id        NUMBER
        , time_id        DATE
        , channel_id     CHAR(1)
        , promo_id       NUMBER(6)
        , quantity_sold  NUMBER(3)
        , amount_sold    NUMBER(10,2)
        )
      PARTITION BY RANGE (time_id)
      INTERVAL(NUMTOYMINTERVAL(1, 'MONTH'))
        ( PARTITION p0 VALUES LESS THAN (TO_DATE('1-1-2008', 'DD-MM-YYYY')),
          PARTITION p1 VALUES LESS THAN (TO_DATE('1-1-2009', 'DD-MM-YYYY')),
          PARTITION p2 VALUES LESS THAN (TO_DATE('1-7-2009', 'DD-MM-YYYY')),
          PARTITION p3 VALUES LESS THAN (TO_DATE('1-1-2010', 'DD-MM-YYYY')) );

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for restrictions on partitioning keys, the exact syntax of the partitioning clauses for creating and altering partitioned tables and indexes, any restrictions on their use, and specific privileges required for creating and altering tables.

### 4.1.3 About Creating Hash Partitioned Tables and Global Indexes

The `PARTITION BY HASH` clause of the `CREATE TABLE` statement identifies that the table is to be hash partitioned.

The `PARTITIONS` clause can then be used to specify the number of partitions to create, and optionally, the tablespaces to store them in. Alternatively, you can use `PARTITION` clauses to name the individual partitions and their tablespaces.

The only attribute you can specify for hash partitions is `TABLESPACE`. All of the hash partitions of a table must share the same segment attributes (except `TABLESPACE`), which are inherited from the table level.

The following topics are discussed:

- Creating a Hash Partitioned Table

- Creating a Hash Partitioned Global Index

#### 4.1.3.1 Creating a Hash Partitioned Table

The example in this topic shows how to create a hash partitioned table.

The partitioning column is `id`, four partitions are created and assigned system generated names, and they are placed in four named tablespaces (`gear1`, `gear2`, `gear3`, `gear4`).

    CREATE TABLE scubagear
         (id NUMBER,
          name VARCHAR2 (60))
       PARTITION BY HASH (id)
       PARTITIONS 4
       STORE IN (gear1, gear2, gear3, gear4);

In the following example, the number of partitions is specified when creating a hash partitioned table, but system generated names are assigned to them and they are stored in the default tablespace of the table.

    CREATE TABLE departments_hash (department_id NUMBER(4) NOT NULL,
                 department_name VARCHAR2(30))
         PARTITION BY HASH(department_id) PARTITIONS 16;

In the following example, names of individual partitions, and tablespaces in which they are to reside, are specified. The initial extent size for each hash partition (segment) is also explicitly stated at the table level, and all partitions inherit this attribute.

    CREATE TABLE departments_hash (department_id NUMBER(4) NOT NULL,
                 department_name VARCHAR2(30))
         STORAGE (INITIAL 10K)
         PARTITION BY HASH(department_id)
           (PARTITION p1 TABLESPACE ts1, PARTITION p2 TABLESPACE ts2,
            PARTITION p3 TABLESPACE ts1, PARTITION p4 TABLESPACE ts3);

If you create a local index for this table, the database constructs the index so that it is equipartitioned with the underlying table. The database also ensures that the index is maintained automatically when maintenance operations are performed on the underlying table. The following is an example of creating a local index on a table:

    CREATE INDEX loc_dept_ix ON departments_hash(department_id) LOCAL;

You can optionally name the hash partitions and tablespaces into which the local index partitions are to be stored, but if you do not do so, then the database uses the name of the corresponding base partition as the index partition name, and stores the index partition in the same tablespace as the table partition.

**See Also:**

Specifying Partitioning on Key Columns for more information about partitioning on key columns

#### 4.1.3.2 Creating a Hash Partitioned Global Index

Hash partitioned global indexes can improve the performance of indexes where a small number of leaf blocks in the index have high contention in multiuser OLTP environments.

Hash partitioned global indexes can also limit the impact of index skew on monotonously increasing column values. Queries involving the equality and `IN` predicates on the index partitioning key can efficiently use hash partitioned global indexes.

The syntax for creating a hash partitioned global index is similar to that used for a hash partitioned table. For example, the statement in Example 4-4 creates a hash partitioned global index:

Example 4-4 Creating a hash partitioned global index

    CREATE INDEX hgidx ON tab (c1,c2,c3) GLOBAL
         PARTITION BY HASH (c1,c2)
         (PARTITION p1  TABLESPACE tbs_1,
          PARTITION p2  TABLESPACE tbs_2,
          PARTITION p3  TABLESPACE tbs_3,
          PARTITION p4  TABLESPACE tbs_4);

### 4.1.4 About Creating List-Partitioned Tables

The semantics for creating list partitions are very similar to those for creating range partitions.

However, to create list partitions, you specify a `PARTITION BY LIST` clause in the `CREATE TABLE` statement, and the `PARTITION` clauses specify lists of literal values, which are the discrete values of the partitioning columns that qualify rows to be included in the partition. For list partitioning, the partitioning key can be one or multiple column names from the table.

Available only with list partitioning, you can use the keyword `DEFAULT` to describe the value list for a partition. This identifies a partition that accommodates rows that do not map into any of the other partitions.

As with range partitions, optional subclauses of a `PARTITION` clause can specify physical and other attributes specific to a partition segment. If not overridden at the partition level, partitions inherit the attributes of their parent table.

The following topics are discussed:

- Creating a List-Partitioned Table

- Creating a List-Partitioned Table With a Default Partition

- Creating an Automatic List-Partitioned Table

- Creating a Multi-column List-Partitioned Table

#### 4.1.4.1 Creating a List-Partitioned Table

The example in this topic show how to create a list-partitioned table.

Example 4-5creates table `q1_sales_by_region` which is partitioned by regions consisting of groups of US states. A row is mapped to a partition by checking whether the value of the partitioning column for a row matches a value in the value list that describes the partition. For example, the following list describes how some sample rows are inserted into the table.

- (10, 'accounting', 100, 'WA') maps to partition `q1_northwest`

- (20, 'R&D', 150, 'OR') maps to partition `q1_northwest`

- (30, 'sales', 100, 'FL') maps to partition `q1_southeast`

- (40, 'HR', 10, 'TX') maps to partition `q1_southwest`

- (50, 'systems engineering', 10, 'CA') does not map to any partition in the table and raises an error

**Live SQL:**

View and run a related example on Oracle Live SQL at [Oracle Live SQL: Creating a List Partitioned Table](https://livesql.oracle.com/apex/livesql/docs/vldbg/partitioning/list-partitioning-example.html).

Example 4-5 Creating a list-partitioned table

    CREATE TABLE q1_sales_by_region
          (deptno number,
           deptname varchar2(20),
           quarterly_sales number(10, 2),
           state varchar2(2))
       PARTITION BY LIST (state)
          (PARTITION q1_northwest VALUES ('OR', 'WA'),
           PARTITION q1_southwest VALUES ('AZ', 'UT', 'NM'),
           PARTITION q1_northeast VALUES  ('NY', 'VM', 'NJ'),
           PARTITION q1_southeast VALUES ('FL', 'GA'),
           PARTITION q1_northcentral VALUES ('SD', 'WI'),
           PARTITION q1_southcentral VALUES ('OK', 'TX'));

#### 4.1.4.2 Creating a List-Partitioned Table With a Default Partition

Unlike range partitioning, with list partitioning, there is no apparent sense of order between partitions.

You can also specify a default partition into which rows that do not map to any other partition are mapped. If a default partition were specified in the preceding example, the state CA would map to that partition.

Example 4-6 creates table `sales_by_region` and partitions it using the list method. The first two `PARTITION` clauses specify physical attributes, which override the table-level defaults. The remaining `PARTITION` clauses do not specify attributes and those partitions inherit their physical attributes from table-level defaults. A default partition is also specified.

Example 4-6 Creating a list-partitioned table with a default partition

    CREATE TABLE sales_by_region (item# INTEGER, qty INTEGER,
                 store_name VARCHAR(30), state_code VARCHAR(2),
                 sale_date DATE)
         STORAGE(INITIAL 10K NEXT 20K) TABLESPACE tbs5
         PARTITION BY LIST (state_code)
         (
         PARTITION region_east
            VALUES ('MA','NY','CT','NH','ME','MD','VA','PA','NJ')
            STORAGE (INITIAL 8M)
            TABLESPACE tbs8,
         PARTITION region_west
            VALUES ('CA','AZ','NM','OR','WA','UT','NV','CO')
            NOLOGGING,
         PARTITION region_south
            VALUES ('TX','KY','TN','LA','MS','AR','AL','GA'),
         PARTITION region_central
            VALUES ('OH','ND','SD','MO','IL','MI','IA'),
         PARTITION region_null
            VALUES (NULL),
         PARTITION region_unknown
            VALUES (DEFAULT)
         );

#### 4.1.4.3 Creating an Automatic List-Partitioned Table

The automatic list partitioning method enables list partition creation on demand.

An auto-list partitioned table is similar to a regular list partitioned table, except that this partitioned table is easier to manage. You can create an auto-list partitioned table using only the partitioning key values that are known. As data is loaded into the table, the database automatically creates a new partition if the loaded partitioning key value does not correspond to any of the existing partitions. Because partitions are automatically created on demand, the auto-list partitioning method is conceptually similar to the existing interval partitioning method.

Automatic list partitioning on data types whose value changes very frequently are less suitable for this method unless you can adjust the data. For example, a `SALES_DATE` field with a date value, when the format is not stripped, would increase every second. Each of the `SALES_DATE` values, such as `05-22-2016 08:00:00`, `05-22-2016 08:00:01`, and so on, would generate its own partition. To avoid the creation of a very large number of partitions, you must be aware of the data that would be entered and adjust accordingly. As an example, you can truncate the `SALES_DATE` date value to a day or some other time period, depending on the number of partitions required.

The `CREATE` and `ALTER` `TABLE` SQL statements are updated with an additional clause to specify `AUTOMATIC` or `MANUAL` list partitioning. An automatic list-partitioned table must have at least one partition when created. Because new partitions are automatically created for new, and unknown, partition key values, an automatic list partition cannot have a `DEFAULT` partition.

You can check the `AUTOLIST` column of the `*_PART_TABLES` view to determine whether a table is automatic list-partitioned.

**Live SQL:**

View and run a related example on Oracle Live SQL at [Oracle Live SQL: Creating an Automatic List-Partitioned Table](https://livesql.oracle.com/apex/livesql/docs/vldbg/partitioning/create-auto-list-partition.html).

Example 4-7 is an example of the `CREATE` `TABLE` statement using the `AUTOMATIC` keyword for auto-list partitioning on the `sales_state` field. The CREATE TABLE SQL statement creates at least one partition as required. As additional rows are inserted, the number of partitions increases when a new `sales_state` value is added.

Example 4-7 Creating an automatic list partitioned table

    CREATE TABLE sales_auto_list
    (
       salesman_id   NUMBER(5)    NOT NULL,
       salesman_name VARCHAR2(30),
       sales_state   VARCHAR2(20) NOT NULL,
       sales_amount  NUMBER(10),
       sales_date    DATE         NOT NULL
    )
      PARTITION BY LIST (sales_state) AUTOMATIC
     (PARTITION P_CAL VALUES ('CALIFORNIA')
    );

    SELECT TABLE_NAME, PARTITIONING_TYPE, AUTOLIST, PARTITION_COUNT FROM USER_PART_TABLES WHERE TABLE_NAME ='SALES_AUTO_LIST';
    TABLE_NAME        PARTITIONING_TYPE  AUTOLIST  PARTITION_COUNT
    ----------------  -----------------  --------  ---------------
    SALES_AUTO_LIST   LIST               YES                     1

    SELECT TABLE_NAME, PARTITION_NAME, HIGH_VALUE FROM USER_TAB_PARTITIONS WHERE TABLE_NAME ='SALES_AUTO_LIST';

    TABLE_NAME        PARTITION_NAME    HIGH_VALUE
    –---------------  –--------------   –---------------
    SALES_AUTO_LIST     P_CAL           'CALIFORNIA'

    INSERT INTO SALES_AUTO_LIST VALUES(021, 'Mary Smith', 'FLORIDA', 41000, TO_DATE ('21-DEC-2018','DD-MON-YYYY'));
    1 row inserted.

    INSERT INTO SALES_AUTO_LIST VALUES(032, 'Luis Vargas', 'MICHIGAN', 42000, TO_DATE ('31-DEC-2018','DD-MON-YYYY'));
    1 row inserted.

    SELECT TABLE_NAME, PARTITIONING_TYPE, AUTOLIST, PARTITION_COUNT FROM USER_PART_TABLES WHERE TABLE_NAME ='SALES_AUTO_LIST';
    TABLE_NAME        PARTITIONING_TYPE  AUTOLIST  PARTITION_COUNT
    ----------------  -----------------  --------  ---------------
    SALES_AUTO_LIST   LIST               YES                     3

    INSERT INTO SALES_AUTO_LIST VALUES(015, 'Simone Blair', 'CALIFORNIA', 45000, TO_DATE ('11-JAN-2019','DD-MON-YYYY'));
    1 row inserted.

    INSERT INTO SALES_AUTO_LIST VALUES(015, 'Simone Blair', 'OREGON', 38000, TO_DATE ('18-JAN-2019','DD-MON-YYYY'));
    1 row inserted.

    SELECT TABLE_NAME, PARTITIONING_TYPE, AUTOLIST,PARTITION_COUNT FROM USER_PART_TABLES WHERE TABLE_NAME ='SALES_AUTO_LIST';
    TABLE_NAME        PARTITIONING_TYPE  AUTOLIST  PARTITION_COUNT
    ----------------  -----------------  --------  ---------------
    SALES_AUTO_LIST   LIST               YES                     4

    SELECT TABLE_NAME, PARTITION_NAME, HIGH_VALUE FROM USER_TAB_PARTITIONS WHERE TABLE_NAME ='SALES_AUTO_LIST';
    TABLE_NAME        PARTITION_NAME    HIGH_VALUE
    –---------------  –--------------   –---------------
    SALES_AUTO_LIST     P_CAL           'CALIFORNIA'
    SALES_AUTO_LIST     SYS_P478        'FLORIDA'
    SALES_AUTO_LIST     SYS_P479        'MICHIGAN'
    SALES_AUTO_LIST     SYS_P480        'OREGON'

**See Also:**

[Oracle Database Reference](../refrn/static-data-dictionary-views-4.md) for information about `*_PART_TABLES` view

#### 4.1.4.4 Creating a Multi-column List-Partitioned Table

Multi-column list partitioning enables you to partition a table based on list values of multiple columns.

Similar to single-column list partitioning, individual partitions can contain sets containing lists of values.

Multi-column list partitioning is supported on a table using the `PARTITION` `BY` `LIST` clause on multiple columns of a table. For example:

    PARTITION BY LIST (column1,column2)

A multi-column list-partitioned table can only have one `DEFAULT` partition.

**Live SQL:**

View and run a related example on Oracle Live SQL at [Oracle Live SQL: Creating a Multicolumn List-Partitioned Table](https://livesql.oracle.com/apex/livesql/docs/vldbg/partitioning/create-multicolumn-list.html).

The following is an example of the `CREATE TABLE` statement using multi-column partitioning on the `state` and `channel` columns.

Example 4-8 Creating a multicolumn list-partitioned table

    CREATE TABLE sales_by_region_and_channel
     (dept_number      NUMBER NOT NULL,
      dept_name        VARCHAR2(20),
      quarterly_sales  NUMBER(10,2),
      state            VARCHAR2(2),
      channel          VARCHAR2(1)
     )
     PARTITION BY LIST (state, channel)
     (
      PARTITION yearly_west_direct VALUES (('OR','D'),('UT','D'),('WA','D')),
      PARTITION yearly_west_indirect VALUES (('OR','I'),('UT','I'),('WA','I')),
      PARTITION yearly_south_direct VALUES (('AZ','D'),('TX','D'),('GA','D')),
      PARTITION yearly_south_indirect VALUES (('AZ','I'),('TX','I'),('GA','I')),
      PARTITION yearly_east_direct VALUES (('PA','D'), ('NC','D'), ('MA','D')),
      PARTITION yearly_east_indirect VALUES (('PA','I'), ('NC','I'), ('MA','I')),
      PARTITION yearly_north_direct VALUES (('MN','D'),('WI','D'),('MI','D')),
      PARTITION yearly_north_indirect VALUES (('MN','I'),('WI','I'),('MI','I')),
      PARTITION yearly_ny_direct VALUES ('NY','D'),
      PARTITION yearly_ny_indirect VALUES ('NY','I'),
      PARTITION yearly_ca_direct VALUES ('CA','D'),
      PARTITION yearly_ca_indirect VALUES ('CA','I'),
      PARTITION rest VALUES (DEFAULT)
     );

    SELECT PARTITION_NAME, HIGH_VALUE FROM USER_TAB_PARTITIONS WHERE TABLE_NAME ='SALES_BY_REGION_AND_CHANNEL';
    PARTITION_NAME            HIGH_VALUE
    ---------------------     -------------------------------------------
    REST                      DEFAULT
    YEARLY_CA_DIRECT          ( 'CA', 'D' )
    YEARLY_CA_INDIRECT        ( 'CA', 'I' )
    YEARLY_EAST_DIRECT        ( 'PA', 'D' ), ( 'NC', 'D' ), ( 'MA', 'D' )
    YEARLY_EAST_INDIRECT      ( 'PA', 'I' ), ( 'NC', 'I' ), ( 'MA', 'I' )
    YEARLY_NORTH_DIRECT       ( 'MN', 'D' ), ( 'WI', 'D' ), ( 'MI', 'D' )
    YEARLY_NORTH_INDIRECT     ( 'MN', 'I' ), ( 'WI', 'I' ), ( 'MI', 'I' )
    YEARLY_NY_DIRECT          ( 'NY', 'D' )
    YEARLY_NY_INDIRECT        ( 'NY', 'I' )
    YEARLY_SOUTH_DIRECT       ( 'AZ', 'D' ), ( 'TX', 'D' ), ( 'GA', 'D' )
    YEARLY_SOUTH_INDIRECT     ( 'AZ', 'I' ), ( 'TX', 'I' ), ( 'GA', 'I' )
    YEARLY_WEST_DIRECT        ( 'OR', 'D' ), ( 'UT', 'D' ), ( 'WA', 'D' )
    YEARLY_WEST_INDIRECT      ( 'OR', 'I' ), ( 'UT', 'I' ), ( 'WA', 'I' )
    13 rows selected.

    INSERT INTO SALES_BY_REGION_AND_CHANNEL VALUES (005, 'AUTO DIRECT', 701000, 'OR', 'D' );
    INSERT INTO SALES_BY_REGION_AND_CHANNEL VALUES (006, 'AUTO INDIRECT', 1201000, 'OR', 'I' );
    INSERT INTO SALES_BY_REGION_AND_CHANNEL VALUES (005, 'AUTO DIRECT', 625000, 'WA', 'D' );
    INSERT INTO SALES_BY_REGION_AND_CHANNEL VALUES (006, 'AUTO INDIRECT', 945000, 'WA', 'I' );
    INSERT INTO SALES_BY_REGION_AND_CHANNEL VALUES (005, 'AUTO DIRECT', 595000, 'UT', 'D' );
    INSERT INTO SALES_BY_REGION_AND_CHANNEL VALUES (006, 'AUTO INDIRECT', 825000, 'UT', 'I' );
    INSERT INTO SALES_BY_REGION_AND_CHANNEL VALUES (003, 'AUTO DIRECT', 1950000, 'CA', 'D' );
    INSERT INTO SALES_BY_REGION_AND_CHANNEL VALUES (004, 'AUTO INDIRECT', 5725000, 'CA', 'I' );
    INSERT INTO SALES_BY_REGION_AND_CHANNEL VALUES (010, 'AUTO DIRECT', 925000, 'IL', 'D' );
    INSERT INTO SALES_BY_REGION_AND_CHANNEL VALUES (010, 'AUTO INDIRECT', 3250000, 'IL', 'I' );

    SELECT DEPT_NUMBER, DEPT_NAME, QUARTERLY_SALES, STATE, CHANNEL FROM SALES_BY_REGION_AND_CHANNEL PARTITION(yearly_west_direct);
    DEPT_NUMBER DEPT_NAME            QUARTERLY_SALES ST C
    ----------- -------------------- --------------- -- -
              5 AUTO DIRECT                   701000 OR D
              5 AUTO DIRECT                   625000 WA D
              5 AUTO DIRECT                   595000 UT D

    SELECT DEPT_NUMBER, DEPT_NAME, QUARTERLY_SALES, STATE, CHANNEL FROM SALES_BY_REGION_AND_CHANNEL PARTITION(yearly_west_indirect);
    DEPT_NUMBER DEPT_NAME            QUARTERLY_SALES ST C
    ----------- -------------------- --------------- -- -
              6 AUTO INDIRECT                1201000 OR I
              6 AUTO INDIRECT                 945000 WA I
              6 AUTO INDIRECT                 825000 UT I

    SELECT DEPT_NUMBER, DEPT_NAME, QUARTERLY_SALES, STATE, CHANNEL FROM SALES_BY_REGION_AND_CHANNEL PARTITION(yearly_ca_direct);
    DEPT_NUMBER DEPT_NAME            QUARTERLY_SALES ST C
    ----------- -------------------- --------------- -- -
              3 AUTO DIRECT                  1950000 CA D

    SELECT DEPT_NUMBER, DEPT_NAME, QUARTERLY_SALES, STATE, CHANNEL FROM SALES_BY_REGION_AND_CHANNEL PARTITION(yearly_ca_indirect);
    DEPT_NUMBER DEPT_NAME            QUARTERLY_SALES ST C
    ----------- -------------------- --------------- -- -
              4 AUTO INDIRECT                5725000 CA I

    SELECT DEPT_NUMBER, DEPT_NAME, QUARTERLY_SALES, STATE, CHANNEL FROM SALES_BY_REGION_AND_CHANNEL PARTITION(rest);
    DEPT_NUMBER DEPT_NAME            QUARTERLY_SALES ST C
    ----------- -------------------- --------------- -- -
             10 AUTO DIRECT                   925000 IL D
             10 AUTO INDIRECT                3250000 IL I

### 4.1.5 Creating Reference-Partitioned Tables

To create a reference-partitioned table, you specify a `PARTITION BY REFERENCE` clause in the `CREATE TABLE` statement.

The `PARTITION BY REFERENCE` clause specifies the name of a referential constraint and this constraint becomes the partitioning referential constraint that is used as the basis for reference partitioning in the table. The referential constraint must be enabled and enforced.

As with other partitioned tables, you can specify object-level default attributes, and you can optionally specify partition descriptors that override the object-level defaults on a per-partition basis.

Example 4-9 creates a parent table `orders` which is range-partitioned on `order_date`. The reference-partitioned child table `order_items` is created with four partitions, `Q1_2005`, `Q2_2005`, `Q3_2005`, and `Q4_2005`, where each partition contains the `order_items` rows corresponding to orders in the respective parent partition.

If partition descriptors are provided, then the number of partitions described must exactly equal the number of partitions or subpartitions in the referenced table. If the parent table is a composite partitioned table, then the table has one partition for each subpartition of its parent; otherwise the table has one partition for each partition of its parent.

Partition bounds cannot be specified for the partitions of a reference-partitioned table.

The partitions of a reference-partitioned table can be named. If a partition is not explicitly named, then it inherits its name from the corresponding partition in the parent table, unless this inherited name conflicts with an existing explicit name. In this case, the partition has a system-generated name.

Partitions of a reference-partitioned table collocate with the corresponding partition of the parent table, if no explicit tablespace is specified for the reference-partitioned table's partition.

Example 4-9 Creating reference-partitioned tables

    CREATE TABLE orders
        ( order_id           NUMBER(12),
          order_date         DATE,
          order_mode         VARCHAR2(8),
          customer_id        NUMBER(6),
          order_status       NUMBER(2),
          order_total        NUMBER(8,2),
          sales_rep_id       NUMBER(6),
          promotion_id       NUMBER(6),
          CONSTRAINT orders_pk PRIMARY KEY(order_id)
        )
      PARTITION BY RANGE(order_date)
        ( PARTITION Q1_2005 VALUES LESS THAN (TO_DATE('01-APR-2005','DD-MON-YYYY')),
          PARTITION Q2_2005 VALUES LESS THAN (TO_DATE('01-JUL-2005','DD-MON-YYYY')),
          PARTITION Q3_2005 VALUES LESS THAN (TO_DATE('01-OCT-2005','DD-MON-YYYY')),
          PARTITION Q4_2005 VALUES LESS THAN (TO_DATE('01-JAN-2006','DD-MON-YYYY'))
        );

    CREATE TABLE order_items
        ( order_id           NUMBER(12) NOT NULL,
          line_item_id       NUMBER(3)  NOT NULL,
          product_id         NUMBER(6)  NOT NULL,
          unit_price         NUMBER(8,2),
          quantity           NUMBER(8),
          CONSTRAINT order_items_fk
          FOREIGN KEY(order_id) REFERENCES orders(order_id)
        )
        PARTITION BY REFERENCE(order_items_fk);

### 4.1.6 Creating Interval-Reference Partitioned Tables

You can use interval partitioned tables as parent tables for reference partitioning. Partitions in a reference-partitioned table corresponding to interval partitions in the parent table are created when inserting records into the reference partitioned table.

When creating an interval partition in a child table, the partition name is inherited from the associated parent table fragment. If the child table has a table-level default tablespace, then it is used as tablespace for the new interval partition; otherwise, the tablespace is inherited from the parent table fragment.

The SQL `ALTER` `TABLE` `SET` `INTERVAL` statement is not allowed for reference-partitioned tables, but can be run on tables that have reference-partitioned children. In particular, `ALTER` `TABLE` `SET` `INTERVAL` removes the interval property from the targeted table and converts any interval-reference children to ordinary reference-partitioned tables. Also, the SQL `ALTER` `TABLE` `SET` `STORE` `IN` statement is not allowed for reference-partitioned tables, but can be run on tables that have reference-partitioned children.

Operations that transform interval partitions to conventional partitions in the parent table, such as `ALTER` `TABLE` `SPLIT` `PARTITION` on an interval partition, construct the corresponding transformation in the child table, creating partitions in the child table as necessary.

For example, the following SQL statements provides three interval partitions in the parent table and none in the child table:

    CREATE TABLE par(pk INT CONSTRAINT par_pk PRIMARY KEY, i INT)
     PARTITION BY RANGE(i) INTERVAL (10)
     (PARTITION p1 VALUES LESS THAN (10));

    CREATE TABLE chi(fk INT NOT NULL, i INT,
     CONSTRAINT chi_fk FOREIGN KEY(fk) REFERENCES par(pk))
     PARTITION BY REFERENCE(chi_fk);

    INSERT INTO par VALUES(15, 15);
    INSERT INTO par VALUES(25, 25);
    INSERT INTO par VALUES(35, 35);

You can display information about partitions with the `USER_TAB_PARTITIONS` view:

    SELECT table_name, partition_position, high_value, interval
       FROM USER_TAB_PARTITIONS WHERE table_name IN ('PAR', 'CHI')
       ORDER BY 1, 2;

    TABLE_NAME       PARTITION_POSITION HIGH_VALUE INT
    ---------------- ------------------ ---------- ---
    CHI                               1            NO
    PAR                               1         10 NO
    PAR                               2         20 YES
    PAR                               3         30 YES
    PAR                               4         40 YES

If the interval partition is split in the parent table, then some interval partitions are converted to conventional partitions for all tables in the hierarchy, creating conventional partitions in the child table in the process. For example:

    ALTER TABLE par SPLIT PARTITION FOR (25) AT (25)
       INTO (partition x, partition y);

    SELECT table_name, partition_position, high_value, interval
       FROM USER_TAB_PARTITIONS WHERE table_name IN ('PAR', 'CHI')
       ORDER BY 1, 2;

    TABLE_NAME       PARTITION_POSITION HIGH_VALUE INT
    ---------------- ------------------ ---------- ---
    CHI                               1            NO
    CHI                               2            NO
    CHI                               3            NO
    CHI                               4            NO
    PAR                               1         10 NO
    PAR                               2         20 NO
    PAR                               3         25 NO
    PAR                               4         30 NO
    PAR                               5         40 YES

Interval-reference functionality requires that the database compatibility level (Oracle Database `COMPATIBLE` initialization parameter setting) be set to greater than or equal to `12.0.0.0`.

### 4.1.7 Creating a Table Using In-Memory Column Store With Partitioning

You can create a partitioned table using the In-Memory Column Store with the `INMEMORY` clause.

The following example specifies that individual partitions are loaded into the In-Memory Column Store using the `INMEMORY` clause with the partitioning clauses of the `CREATE` `TABLE` SQL statements.

    CREATE TABLE list_customers
       ( customer_id             NUMBER(6)
       , cust_first_name         VARCHAR2(20)
       , cust_last_name          VARCHAR2(20)
       , cust_address            CUST_ADDRESS_TYP
       , nls_territory           VARCHAR2(30)
       , cust_email              VARCHAR2(40))
       PARTITION BY LIST (nls_territory) (
       PARTITION asia VALUES ('CHINA', 'THAILAND')
             INMEMORY MEMCOMPRESS FOR CAPACITY HIGH,
       PARTITION europe VALUES ('GERMANY', 'ITALY', 'SWITZERLAND')
             INMEMORY MEMCOMPRESS FOR CAPACITY LOW,
       PARTITION west VALUES ('AMERICA')
             INMEMORY MEMCOMPRESS FOR CAPACITY LOW,
       PARTITION east VALUES ('INDIA')
             INMEMORY MEMCOMPRESS FOR CAPACITY HIGH,
       PARTITION rest VALUES (DEFAULT);

**See Also:**

- [Oracle Database In-Memory Guide](../inmem/intro-to-in-memory-column-store.md) for overview information about In-Memory Column Store

- [Oracle Database In-Memory Guide](../inmem/populating-objects-in-memory.md) for information about enabling objects for population in the In-Memory Column Store and ADO support

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about SQL syntax related to In-Memory Column Store

### 4.1.8 Creating a Table with Read-Only Partitions or Subpartitions

You can set tables, partitions, and subpartitions to read-only status to protect data from unintentional DML operations by any user or trigger.

Any attempt to update data in a partition or subpartition that is set to read only results in an error, while updating data in partitions or subpartitions that are set to read write succeeds.

The `CREATE` `TABLE` and `ALTER` `TABLE` SQL statements provide a read-only clause for partitions and subpartitions. The values of the read-only clause can be `READ` `ONLY` or `READ` `WRITE`. `READ` `WRITE` is the default value. A higher level setting of the read-only clause is applied to partitions and subpartitions unless the read-only clause has been explicitly set for a partition or subpartition.

The following is an example of a creating a composite range-list partitioned table with both read-only and read-write status. The `orders_read_write_only` is explicitly specified as `READ` `WRITE`, so the default attribute of the table is read write. The default attribute of partition `order_p1` is specified as read only, so the subpartitions `ord_p1_northwest` and `order_p1_southwest` inherit read only status from partition `order_p1`. Subpartitions `ord_p2_southwest` and `order_p3_northwest` are explicitly specified as read only, overriding the default read write status.

Example 4-10 Creating a table with read-only and read-write partitions

    CREATE TABLE orders_read_write_only (
       order_id NUMBER (12),
       order_date DATE CONSTRAINT order_date_nn NOT NULL,
       state VARCHAR2(2)
       ) READ WRITE
         PARTITION BY RANGE (order_date)
         SUBPARTITION BY LIST (state)
         ( PARTITION order_p1 VALUES LESS THAN (TO_DATE ('01-DEC-2015','DD-MON-YYYY')) READ ONLY
         ( SUBPARTITION order_p1_northwest VALUES ('OR', 'WA'),
           SUBPARTITION order_p1_southwest VALUES ('AZ', 'UT', 'NM')
          ),
         PARTITION order_p2 VALUES LESS THAN (TO_DATE ('01-MAR-2016','DD-MON-YYYY'))
         ( SUBPARTITION order_p2_northwest VALUES ('OR', 'WA'),
           SUBPARTITION order_p2_southwest VALUES ('AZ', 'UT', 'NM') READ ONLY
          ),
         PARTITION order_p3 VALUES LESS THAN (TO_DATE ('01-JUL-2016','DD-MON-YYYY'))
         (
         SUBPARTITION order_p3_northwest VALUES ('OR', 'WA') READ ONLY,
         SUBPARTITION order_p3_southwest VALUES ('AZ', 'UT', 'NM')
         )
     );

You can check the read-only status with the `DEF_READ_ONLY` column of the `*_PART_TABLES` view, the `READ_ONLY` column of the `*_TAB_PARTITIONS` view, and the `READ_ONLY` column of the `*_TAB_SUBPARTITIONS` view. Note that only physical segments, partitions for single-level partitioning and subpartitions for composite partitioning, have a status. All other levels are logical and only have a default status.

    SQL> SELECT PARTITION_NAME, READ_ONLY FROM USER_TAB_PARTITIONS WHERE TABLE_NAME ='ORDERS_READ_WRITE_ONLY';
    PARTITION_NAME                  READ
    ------------------------------- ----
    ORDER_P1                        YES
    ORDER_P2                        NONE
    ORDER_P3                        NONE

    SQL> SELECT PARTITION_NAME, SUBPARTITION_NAME, READ_ONLY FROM USER_TAB_SUBPARTITIONS WHERE TABLE_NAME ='ORDERS_READ_WRITE_ONLY';
    PARTITION_NAME                 SUBPARTITION_NAME             REA
    ------------------------------ ----------------------------- ---
    ORDER_P1                       ORDER_P1_NORTHWEST            YES
    ORDER_P1                       ORDER_P1_SOUTHWEST            YES
    ORDER_P2                       ORDER_P2_NORTHWEST            NO
    ORDER_P2                       ORDER_P2_SOUTHWEST            YES
    ORDER_P3                       ORDER_P3_NORTHWEST            YES
    ORDER_P3                       ORDER_P3_SOUTHWEST            NO

**See Also:**

[Oracle Database Reference](../refrn/static-data-dictionary-views-5.md) for information about `*_PART_TABLES`, `*_TAB_PARTITIONS`, and `*_TAB_SUBPARTITIONS` views

### 4.1.9 Creating a Partitioned External Table

You can create partitions for an external table.

The organization external clause identifies the table as external table, followed by the specification and access parameters of the external table. While parameters, such as the default directory; can be overridden on a partition or subpartition level, the external table type and its access parameters are table-level attributes and applicable to all partitions or subpartitions.

The table created in Example 4-11 has three partitions for external data accessed from different locations. Partition `p1` stores customer data for California, located in the default directory of the table. Partition `p2` points to a file storing data for Washington. Partition `p3` does not have a file descriptor and is empty.

Example 4-11 Creating a Partitioned External Table

    CREATE TABLE sales (loc_id number, prod_id number, cust_id number, amount_sold number, quantity_sold number)
     ORGANIZATION EXTERNAL
     (TYPE oracle_loader
      DEFAULT DIRECTORY load_d1
      ACCESS PARAMETERS
      ( RECORDS DELIMITED BY NEWLINE CHARACTERSET US7ASCII
        NOBADFILE
        LOGFILE log_dir:'sales.log'
        FIELDS TERMINATED BY ","
       )
     )
      REJECT LIMIT UNLIMITED
     PARTITION BY RANGE (loc_id)
     (PARTITION p1 VALUES LESS THAN (1000) LOCATION ('california.txt'),
      PARTITION p2 VALUES LESS THAN (2000) DEFAULT DIRECTORY load_d2 LOCATION ('washington.txt'),
      PARTITION p3 VALUES LESS THAN (3000))
    ;

**Note:**

Hive column names should be limited to `[a-zA-Z0-9_]+` on external partitioned tables. If you use any Oracle column names that do not follow this rule, then use the two access parameters `com.oracle.bigdata.fields` and `com.oracle.bigdata.colmap` together to remap the “extended” Oracle column name to a simple Hive identifer.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-tables.md) for information about partitioning external tables

### 4.1.10 Specifying Partitioning on Key Columns

For range-partitioned and hash partitioned tables, you can specify up to 16 partitioning key columns.

Use multicolumn partitioning when the partitioning key is composed of several columns and subsequent columns define a higher granularity than the preceding ones. The most common scenario is a decomposed `DATE` or `TIMESTAMP` key, consisting of separated columns, for year, month, and day.

In evaluating multicolumn partitioning keys, the database uses the second value only if the first value cannot uniquely identify a single target partition, and uses the third value only if the first and second do not determine the correct partition, and so forth. A value cannot determine the correct partition only when a partition bound exactly matches that value and the same bound is defined for the next partition. The n<sup>th</sup> column is investigated only when all previous (n-1) values of the multicolumn key exactly match the (n-1) bounds of a partition. A second column, for example, is evaluated only if the first column exactly matches the partition boundary value. If all column values exactly match all of the bound values for a partition, then the database determines that the row does not fit in this partition and considers the next partition for a match.

For nondeterministic boundary definitions (successive partitions with identical values for at least one column), the partition boundary value becomes an inclusive value, representing a "less than or equal to" boundary. This is in contrast to deterministic boundaries, where the values are always regarded as "less than" boundaries.

The following topics are discussed:

- Creating a Multicolumn Range-Partitioned Table By Date

- Creating a Multicolumn Range-Partitioned Table to Enforce Equal-Sized Partitions

#### 4.1.10.1 Creating a Multicolumn Range-Partitioned Table By Date

The example in this topic shows how to create a multicolumn range-partitioned table by date.

Example 4-12 illustrates the column evaluation for a multicolumn range-partitioned table, storing the actual `DATE` information in three separate columns: `year`, `month`, and `day`. The partitioning granularity is a calendar quarter. The partitioned table being evaluated is created as follows:

The year value for 12-DEC-2000 satisfied the first partition, `before2001`, so no further evaluation is needed:

    SELECT * FROM sales_demo PARTITION(before2001);

          YEAR      MONTH        DAY AMOUNT_SOLD
    ---------- ---------- ---------- -----------
          2000         12         12        1000

The information for 17-MAR-2001 is stored in partition `q1_2001`. The first partitioning key column, `year`, does not by itself determine the correct partition, so the second partitioning key column, `month`, must be evaluated.

    SELECT * FROM sales_demo PARTITION(q1_2001);

          YEAR      MONTH        DAY AMOUNT_SOLD
    ---------- ---------- ---------- -----------
          2001          3         17        2000

Following the same determination rule as for the previous record, the second column, `month`, determines partition `q4_2001` as correct partition for 1-NOV-2001:

    SELECT * FROM sales_demo PARTITION(q4_2001);

          YEAR      MONTH        DAY AMOUNT_SOLD
    ---------- ---------- ---------- -----------
          2001         11          1        5000

The partition for 01-JAN-2002 is determined by evaluating only the `year` column, which indicates the `future` partition:

    SELECT * FROM sales_demo PARTITION(future);

          YEAR      MONTH        DAY AMOUNT_SOLD
    ---------- ---------- ---------- -----------
          2002          1          1        4000

If the database encounters `MAXVALUE` in a partitioning key column, then all other values of subsequent columns become irrelevant. That is, a definition of partition `future` in the preceding example, having a bound of (`MAXVALUE`,0) is equivalent to a bound of (`MAXVALUE`,100) or a bound of (`MAXVALUE`,`MAXVALUE`).

Example 4-12 Creating a multicolumn range-partitioned table

    CREATE TABLE sales_demo (
       year          NUMBER,
       month         NUMBER,
       day           NUMBER,
       amount_sold   NUMBER)
    PARTITION BY RANGE (year,month)
      (PARTITION before2001 VALUES LESS THAN (2001,1),
       PARTITION q1_2001    VALUES LESS THAN (2001,4),
       PARTITION q2_2001    VALUES LESS THAN (2001,7),
       PARTITION q3_2001    VALUES LESS THAN (2001,10),
       PARTITION q4_2001    VALUES LESS THAN (2002,1),
       PARTITION future     VALUES LESS THAN (MAXVALUE,0));

    REM  12-DEC-2000
    INSERT INTO sales_demo VALUES(2000,12,12, 1000);
    REM  17-MAR-2001
    INSERT INTO sales_demo VALUES(2001,3,17, 2000);
    REM  1-NOV-2001
    INSERT INTO sales_demo VALUES(2001,11,1, 5000);
    REM  1-JAN-2002
    INSERT INTO sales_demo VALUES(2002,1,1, 4000);

#### 4.1.10.2 Creating a Multicolumn Range-Partitioned Table to Enforce Equal-Sized Partitions

The example in this topic shows how to create a multicolumn range-partitioned table to enforce equal-sized partitions.

The following example illustrates the use of a multicolumn partitioned approach for table `supplier_parts`, storing the information about which suppliers deliver which parts. To distribute the data in equal-sized partitions, it is not sufficient to partition the table based on the `supplier_id`, because some suppliers might provide hundreds of thousands of parts, while others provide only a few specialty parts. Instead, you partition the table on (`supplier_id`, `partnum`) to manually enforce equal-sized partitions.

Every row with `supplier_id` \< 10 is stored in partition `p1`, regardless of the `partnum` value. The column `partnum` is evaluated only if `supplier_id` =10, and the corresponding rows are inserted into partition `p1`, `p2`, or even into `p3` when `partnum` \>=200. To achieve equal-sized partitions for ranges of `supplier_parts`, you could choose a composite range-hash partitioned table, range partitioned by `supplier_id`, hash subpartitioned by `partnum`.

Defining the partition boundaries for multicolumn partitioned tables must obey some rules. For example, consider a table that is range partitioned on three columns `a`, `b`, and `c`. The individual partitions have range values represented as follows:

    P0(a0, b0, c0)
    P1(a1, b1, c1)
    P2(a2, b2, c2)
    ...
    Pn(an, bn, cn)

The range values you provide for each partition must follow these rules:

- `a0` must be less than or equal to `a1`, and `a1` must be less than or equal to `a2`, and so on.

- If `a0`=`a1`, then `b0` must be less than or equal to `b1`. If `a0` \< `a1`, then `b0` and `b1` can have any values. If `a0`=`a1` and `b0`=`b1`, then `c0` must be less than or equal to `c1`. If `b0`\<`b1`, then `c0` and `c1` can have any values, and so on.

- If `a1`=`a2`, then `b1` must be less than or equal to `b2`. If `a1`\<`a2`, then `b1` and `b2` can have any values. If `a1`=`a2` and `b1`=`b2`, then `c1` must be less than or equal to `c2`. If `b1`\<`b2`, then `c1` and `c2` can have any values, and so on.

<!-- -->

    CREATE TABLE supplier_parts (
       supplier_id      NUMBER,
       partnum          NUMBER,
       price            NUMBER)
    PARTITION BY RANGE (supplier_id, partnum)
      (PARTITION p1 VALUES LESS THAN  (10,100),
       PARTITION p2 VALUES LESS THAN (10,200),
       PARTITION p3 VALUES LESS THAN (MAXVALUE,MAXVALUE));

The following three records are inserted into the table:

    INSERT INTO supplier_parts VALUES (5,5, 1000);
    INSERT INTO supplier_parts VALUES (5,150, 1000);
    INSERT INTO supplier_parts VALUES (10,100, 1000);

The first two records are inserted into partition `p1`, uniquely identified by `supplier_id`. However, the third record is inserted into partition `p2`; it matches all range boundary values of partition `p1` exactly and the database therefore considers the following partition for a match. The value of `partnum` satisfies the criteria \< 200, so it is inserted into partition `p2`.

    SELECT * FROM supplier_parts PARTITION (p1);

    SUPPLIER_ID    PARTNUM      PRICE
    ----------- ---------- ----------
              5          5       1000
              5        150       1000

    SELECT * FROM supplier_parts PARTITION (p2);

    SUPPLIER_ID    PARTNUM      PRICE
    ----------- ---------- ----------
              10       100       1000

### 4.1.11 Using Virtual Column-Based Partitioning

With partitioning, a virtual column can be used as any regular column.

All partition methods are supported when using virtual columns, including interval partitioning and all different combinations of composite partitioning. A virtual column used as the partitioning column cannot use calls to a PL/SQL function.

The following example shows the `sales` table partitioned by range-range using a virtual column for the subpartitioning key. The virtual column calculates the total value of a sale by multiplying `amount_sold` and `quantity_sold`. As the example shows, row movement is also supported with virtual columns. If row movement is enabled, then a row migrates from one partition to another partition if the virtual column evaluates to a value that belongs to another partition.

    CREATE TABLE sales
      ( prod_id       NUMBER(6) NOT NULL
      , cust_id       NUMBER NOT NULL
      , time_id       DATE NOT NULL
      , channel_id    CHAR(1) NOT NULL
      , promo_id      NUMBER(6) NOT NULL
      , quantity_sold NUMBER(3) NOT NULL
      , amount_sold   NUMBER(10,2) NOT NULL
      , total_amount AS (quantity_sold * amount_sold)
      )
     PARTITION BY RANGE (time_id) INTERVAL (NUMTOYMINTERVAL(1,'MONTH'))
     SUBPARTITION BY RANGE(total_amount)
     SUBPARTITION TEMPLATE
       ( SUBPARTITION p_small VALUES LESS THAN (1000)
       , SUBPARTITION p_medium VALUES LESS THAN (5000)
       , SUBPARTITION p_large VALUES LESS THAN (10000)
       , SUBPARTITION p_extreme VALUES LESS THAN (MAXVALUE)
       )
     (PARTITION sales_before_2007 VALUES LESS THAN
            (TO_DATE('01-JAN-2007','dd-MON-yyyy'))
    )
    ENABLE ROW MOVEMENT
    PARALLEL NOLOGGING;

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Pseudocolumns.md) for the syntax on how to create a virtual column

### 4.1.12 Using Table Compression with Partitioned Tables

For heap-organized partitioned tables, you can compress some or all partitions using table compression.

The compression attribute can be declared for a tablespace, a table, or a partition of a table. Whenever the compress attribute is not specified, it is inherited like any other storage attribute.

Example 4-13 creates a range-partitioned table with one compressed partition `costs_old`. The compression attribute for the table and all other partitions is inherited from the tablespace level.

Example 4-13 Creating a range-partitioned table with a compressed partition

    CREATE TABLE costs_demo (
       prod_id     NUMBER(6),    time_id     DATE,
       unit_cost   NUMBER(10,2), unit_price  NUMBER(10,2))
    PARTITION BY RANGE (time_id)
       (PARTITION costs_old
           VALUES LESS THAN (TO_DATE('01-JAN-2003', 'DD-MON-YYYY')) COMPRESS,
        PARTITION costs_q1_2003
           VALUES LESS THAN (TO_DATE('01-APR-2003', 'DD-MON-YYYY')),
        PARTITION costs_q2_2003
           VALUES LESS THAN (TO_DATE('01-JUN-2003', 'DD-MON-YYYY')),
        PARTITION costs_recent VALUES LESS THAN (MAXVALUE));

### 4.1.13 Using Key Compression with Partitioned Indexes

You can compress some or all partitions of a B-tree index using key compression.

Key compression is applicable only to B-tree indexes. Bitmap indexes are stored in a compressed manner by default. An index using key compression eliminates repeated occurrences of key column prefix values, thus saving space and I/O.

The following example creates a local partitioned index with all partitions except the most recent one compressed:

    CREATE INDEX i_cost1 ON costs_demo (prod_id) COMPRESS LOCAL
       (PARTITION costs_old, PARTITION costs_q1_2003,
        PARTITION costs_q2_2003, PARTITION costs_recent NOCOMPRESS);

You cannot specify `COMPRESS` (or `NOCOMPRESS`) explicitly for an index subpartition. All index subpartitions of a given partition inherit the key compression setting from the parent partition.

To modify the key compression attribute for all subpartitions of a given partition, you must first issue an `ALTER INDEX...MODIFY PARTITION` statement and then rebuild all subpartitions. The `MODIFY PARTITION` clause marks all index subpartitions as `UNUSABLE`.

### 4.1.14 Specifying Partitioning with Segments

Partitioning with segments is introduced in this topic.

These topics discuss the functionality when using partitioning with segments.

- Deferred Segment Creation for Partitioning

- Truncating Segments That Are Empty

- Maintenance Procedures for Segment Creation on Demand

#### 4.1.14.1 Deferred Segment Creation for Partitioning

You can defer the creation of segments when creating a partitioned table until the first row is inserted into a partition.

When the first row is inserted, segments are created for the base table partition, LOB columns, all global indexes, and local index partitions. Deferred segment creation can be controlled by the following:

- Setting the `DEFERRED_SEGMENT_CREATION` initialization parameter to `TRUE` or `FALSE` in the initialization parameter file.

- Setting the initialization parameter `DEFERRED_SEGMENT_CREATION` to `TRUE` or `FALSE` with the `ALTER` `SESSION` or `ALTER` `SYSTEM` SQL statements.

- Specifying the keywords `SEGMENT` `CREATION` `IMMEDIATE` or `SEGMENT` `CREATION` `DEFERRED` with the partition clause when issuing the `CREATE` `TABLE` SQL statement.

You can force the creation of segments for an existing created partition with the `ALTER` `TABLE` `MODIFY` `PARTITION` `ALLOCATE` `EXTENT` SQL statement. This statement allocates one extent more than the initial number of extents specified during the `CREATE` `TABLE`.

Serializable transactions are not supported with deferred segment creation. Inserting data into an empty table with no segment created, or into a partition of an interval partitioned table that does not have a segment yet, can cause an error.

**See Also:**

- [Oracle Database Reference](../refrn/DEFERRED_SEGMENT_CREATION.md) for more information about the `DEFERRED_SEGMENT_CREATION` initialization parameter

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-SESSION.md) for more information about the `ALTER` `SESSION` and `ALTER` `SYSTEM` SQL statements

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for more information about the keywords `SEGMENT` `CREATION` `IMMEDIATE` and `SEGMENT` `CREATION` `DEFERRED` of the `CREATE` `TABLE` SQL statement

#### 4.1.14.2 Truncating Segments That Are Empty

You can drop empty segments in tables and table fragments with the `DBMS_SPACE_ADMIN.DROP_EMPTY_SEGMENTS` procedure.

In addition, if a partition or subpartition has a segment, then the truncate feature drops the segment if the `DROP` `ALL` `STORAGE` clause is specified with the `ALTER` `TABLE` `TRUNCATE` `PARTITION` SQL statement.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SPACE_ADMIN.md) for more information about the `DBMS_SPACE_ADMIN` package

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for more information about the `DROP` `ALL` `STORAGE` clause of `ALTER` `TABLE`

#### 4.1.14.3 Maintenance Procedures for Segment Creation on Demand

You can use the `MATERIALIZE_DEFERRED_SEGMENTS` procedure in the `DBMS_SPACE_ADMIN` package to create segments for tables and dependent objects for tables with the deferred segment property.

You can also force the creation of segments for an existing created table and table fragment with the `DBMS_SPACE_ADMIN.MATERIALIZE_DEFERRED_SEGMENTS` procedure. The `MATERIALIZE_DEFERRED_SEGMENTS` procedure differs from the `ALTER` `TABLE` `MODIFY` `PARTITION` `ALLOCATE` `EXTENT` SQL statement because it does not allocate one additional extent for the table or table fragment.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SPACE_ADMIN.md) for more information about the `DBMS_SPACE_ADMIN` package

### 4.1.15 Specifying Partitioning When Creating Index-Organized Tables

For index-organized tables, you can use the range, list, or hash partitioning method.

The semantics for creating partitioned index-organized tables are similar to that for regular tables with these differences:

- When you create the table, you specify the `ORGANIZATION INDEX` clause, and `INCLUDING` and `OVERFLOW` clauses as necessary.

- The `PARTITION` clause can have `OVERFLOW` subclauses that allow you to specify attributes of the overflow segments at the partition level.

Specifying an `OVERFLOW` clause results in the overflow data segments themselves being equipartitioned with the primary key index segments. Thus, for partitioned index-organized tables with overflow, each partition has an index segment and an overflow data segment.

For index-organized tables, the set of partitioning columns must be a subset of the primary key columns. Because rows of an index-organized table are stored in the primary key index for the table, the partitioning criterion affects the availability. By choosing the partitioning key to be a subset of the primary key, an insert operation must only verify uniqueness of the primary key in a single partition, thereby maintaining partition independence.

Support for secondary indexes on index-organized tables is similar to the support for regular tables. Because of the logical nature of the secondary indexes, global indexes on index-organized tables remain usable for certain operations where they would be marked `UNUSABLE` for regular tables.

The following topics are discussed:

- Creating Range-Partitioned Index-Organized Tables

- Creating Hash Partitioned Index-Organized Tables

- Creating List-Partitioned Index-Organized Tables

**See Also:**

- [Maintenance Operations for Partitioned Tables and Indexes](maintenance-partition-tables-indexes.md) for information about maintenance operations on index-organized tables

- [Oracle Database Administrator’s Guide](../admin/managing-tables.md) for more information about managing index-organized tables

- [Oracle Database Concepts](../cncpt/indexes-and-index-organized-tables.md) for more information about index-organized tables

#### 4.1.15.1 Creating Range-Partitioned Index-Organized Tables

You can partition index-organized tables, and their secondary indexes, by the range method.

In Example 4-14, a range-partitioned index-organized table `sales` is created. The `INCLUDING` clause specifies that all columns after `week_no` are to be stored in an overflow segment. There is one overflow segment for each partition, all stored in the same tablespace (`overflow_here`). Optionally, `OVERFLOW TABLESPACE` could be specified at the individual partition level, in which case some or all of the overflow segments could have separate `TABLESPACE` attributes.

Example 4-14 Creating a range-partitioned index-organized table

    CREATE TABLE sales(acct_no NUMBER(5),
                       acct_name CHAR(30),
                       amount_of_sale NUMBER(6),
                       week_no INTEGER,
                       sale_details VARCHAR2(1000),
                 PRIMARY KEY (acct_no, acct_name, week_no))
         ORGANIZATION INDEX
                 INCLUDING week_no
                 OVERFLOW TABLESPACE overflow_here
         PARTITION BY RANGE (week_no)
                (PARTITION VALUES LESS THAN (5)
                       TABLESPACE ts1,
                 PARTITION VALUES LESS THAN (9)
                       TABLESPACE ts2 OVERFLOW TABLESPACE overflow_ts2,
                 ...
                 PARTITION VALUES LESS THAN (MAXVALUE)
                       TABLESPACE ts13);

#### 4.1.15.2 Creating Hash Partitioned Index-Organized Tables

Another option for partitioning index-organized tables is to use the hash method.

In Example 4-15, the `sales` index-organized table is partitioned by the hash method.

**Note:**

A well-designed hash function is intended to distribute rows in a well-balanced fashion among the partitions. Therefore, updating the primary key column(s) of a row is very likely to move that row to a different partition. Oracle recommends that you explicitly specify the `ENABLE ROW MOVEMENT` clause when creating a hash partitioned index-organized table with a changeable partitioning key. The default is that `ENABLE ROW MOVEMENT` is disabled.

Example 4-15 Creating a hash partitioned index-organized table

    CREATE TABLE sales(acct_no NUMBER(5),
                       acct_name CHAR(30),
                       amount_of_sale NUMBER(6),
                       week_no INTEGER,
                       sale_details VARCHAR2(1000),
                 PRIMARY KEY (acct_no, acct_name, week_no))
         ORGANIZATION INDEX
                 INCLUDING week_no
         OVERFLOW
              PARTITION BY HASH (week_no)
                 PARTITIONS 16
                 STORE IN (ts1, ts2, ts3, ts4)
                 OVERFLOW STORE IN (ts3, ts6, ts9);

#### 4.1.15.3 Creating List-Partitioned Index-Organized Tables

The other option for partitioning index-organized tables is to use the list method.

In Example 4-16, the `sales` index-organized table is partitioned by the list method.

Example 4-16 Creating a list-partitioned index-organized table

    CREATE TABLE sales(acct_no NUMBER(5),
                       acct_name CHAR(30),
                       amount_of_sale NUMBER(6),
                       week_no INTEGER,
                       sale_details VARCHAR2(1000),
                 PRIMARY KEY (acct_no, acct_name, week_no))
         ORGANIZATION INDEX
                 INCLUDING week_no
                 OVERFLOW TABLESPACE ts1
         PARTITION BY LIST (week_no)
                (PARTITION VALUES (1, 2, 3, 4)
                       TABLESPACE ts2,
                 PARTITION VALUES (5, 6, 7, 8)
                       TABLESPACE ts3 OVERFLOW TABLESPACE ts4,
                 PARTITION VALUES (DEFAULT)
                       TABLESPACE ts5);

### 4.1.16 Partitioning Restrictions for Multiple Block Sizes

Use caution when creating partitioned objects in a database with tablespaces of different block sizes.

The storage of partitioned objects in such tablespaces is subject to some restrictions. Specifically, all partitions of the following entities must reside in tablespaces of the same block size:

- Conventional tables

- Indexes

- Primary key index segments of index-organized tables

- Overflow segments of index-organized tables

- `LOB` columns stored out of line

Therefore:

- For each conventional table, all partitions of that table must be stored in tablespaces with the same block size.

- For each index-organized table, all primary key index partitions must reside in tablespaces of the same block size, and all overflow partitions of that table must reside in tablespaces of the same block size. However, index partitions and overflow partitions can reside in tablespaces of different block size.

- For each index (global or local), each partition of that index must reside in tablespaces of the same block size. However, partitions of different indexes defined on the same object can reside in tablespaces of different block sizes.

- For each `LOB` column, each partition of that column must be stored in tablespaces of equal block sizes. However, different `LOB` columns can be stored in tablespaces of different block sizes.

When you create or alter a partitioned table or index, all tablespaces you explicitly specify for the partitions and subpartitions of each entity must be of the same block size. If you do not explicitly specify tablespace storage for an entity, then the tablespaces the database uses by default must be of the same block size. Therefore, you must be aware of the default tablespaces at each level of the partitioned object.

### 4.1.17 Partitioning of Collections in XMLType and Objects

Partitioning when using `XMLType` or object tables and columns follows the basic rules for partitioning.

For the purposes of this discussion, the term Collection Tables is used for the following two categories: (1) ordered collection tables inside `XMLType` tables or columns, and (2) nested tables inside object tables or columns.

When you partition Collection Tables, Oracle Database uses the partitioning scheme of the base table. Also, Collection Tables are automatically partitioned when the base table is partitioned. DML against a partitioned nested table behaves in a similar manner to that of a reference partitioned table.

Oracle Database provides a `LOCAL` keyword to equipartition a Collection Table with a partitioned base table. This is the default behavior in this release. The default in earlier releases was not to equipartition the Collection Table with the partitioned base table. Now you must specify the `GLOBAL` keyword to store an unpartitioned Collection Table with a partitioned base table.

Out-of-line (OOL) table partitioning is supported. However, you cannot create two tables of the same XML schema that has out-of-line tables. This restriction means that exchange partitioning cannot be performed for schemas with OOL tables because it is not possible to have two tables of the same schema.

The statement in the following example creates a nested table partition.

    CREATE TABLE print_media_part (
       product_id NUMBER(6),
       ad_id NUMBER(6),
       ad_composite BLOB,
       ad_sourcetext CLOB,
       ad_finaltext CLOB,
       ad_fltextn NCLOB,
       ad_textdocs_ntab TEXTDOC_TAB,
       ad_photo BLOB,
       ad_graphic BFILE,
       ad_header ADHEADER_TYP)
    NESTED TABLE ad_textdocs_ntab STORE AS textdoc_nt
    PARTITION BY RANGE (product_id)
      (PARTITION p1 VALUES LESS THAN (100),
       PARTITION p2 VALUES LESS THAN (200));

**See Also:**

- Performing PMOs on Partitions that Contain Collection Tables and Partitioning of XMLIndex for Binary XML Tables for additional related examples

- [Collection Tables](partition-pruning.md) for an example of issuing a query against a partitioned nested table and using the `EXPLAIN` `PLAN` to improve performance

- [Changing a Nonpartitioned Table into a Partitioned Table](evolve-nopartition-table.md) for information about using online redefinition to convert your existing nonpartitioned collection tables to partitioned tables

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for details about `CREATE` `TABLE` syntax

#### 4.1.17.1 Performing PMOs on Partitions that Contain Collection Tables

Whether a partition contains Collection Tables or not does not significantly affect your ability to perform partition maintenance operations (PMOs).

Usually, maintenance operations on Collection Tables are carried out on the base table. The following example illustrates a typical `ADD` `PARTITION` operation based on the preceding nested table partition:

    ALTER TABLE print_media_part
       ADD PARTITION p4 VALUES LESS THAN (400)
       LOB(ad_photo, ad_composite) STORE AS (TABLESPACE omf_ts1)
       LOB(ad_sourcetext, ad_finaltext) STORE AS (TABLESPACE omf_ts1)
       NESTED TABLE ad_textdocs_ntab STORE AS nt_p3;

The storage table for nested table storage column `ad_textdocs_ntab` is named `nt_p3` and inherits all other attributes from the table-level defaults and then from the tablespace defaults.

You must directly invoke the following partition maintenance operations on the storage table corresponding to the collection column:

- modify partition

- move partition

- rename partition

- modify the default attributes of a partition

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for `ADD` `PARTITION` syntax

- [Maintenance Operations Supported on Partitions](maintenance-partition-can-be-performed.md) for a list of partition maintenance operations that can be performed on partitioned tables and composite partitioned tables

#### 4.1.17.2 Partitioning of XMLIndex for Binary XML Tables

For binary XML tables, XMLIndex is equipartitioned with the base table for range, hash, list, interval, and reference partitions.

In the following example, an XMLIndex is created on a range-partitioned table.

    CREATE TABLE purchase_order
       (id NUMBER, doc XMLTYPE)
        PARTITION BY RANGE (id)
        (PARTITION p1 VALUES LESS THAN (10),
         PARTITION p2 VALUES LESS THAN (MAXVALUE));

    CREATE INDEX purchase_order_idx ON purchase_order(doc)
           INDEXTYPE IS XDB.XMLINDEX LOCAL;

**See Also:**

- [Oracle Database Data Cartridge Developer's Guide](../addci/introduction-to-data-cartridges.md) for information about Oracle XML DB and partitioning of XMLIndex for binary XML tables

- [Oracle XML DB Developer’s Guide](../adxdb/indexes-for-XMLType-data.md) for information about XMLIndex

- [Oracle XML DB Developer’s Guide](../adxdb/XML-Schema-and-query-object-relational-storage.md) for information about partitioning XMLType tables and columns
