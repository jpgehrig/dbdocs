When creating a composite partitioned table, you use the `PARTITION` and `SUBPARTITION` clauses of the `CREATE TABLE` SQL statement.

To create a composite partitioned table, you start by using the `PARTITION` `BY` {`HASH` \| `RANGE` \[`INTERVAL`\]\| `LIST`} clause of a `CREATE TABLE` statement. Next, you specify a `SUBPARTITION BY` clause that follows similar syntax and rules as the `PARTITION BY` clause.

The following topics are discussed:

- Creating Composite Hash-\* Partitioned Tables

- Creating Composite Interval-\* Partitioned Tables

- Creating Composite List-\* Partitioned Tables

- Creating Composite Range-\* Partitioned Tables

- Specifying Subpartition Templates to Describe Composite Partitioned Tables

### 4.2.1 Creating Composite Hash-\* Partitioned Tables

Composite hash-\* partitioning enables hash partitioning along two dimensions.

The composite hash-hash partitioning strategy has the most business value of the composite hash-\* partitioned tables. This technique is beneficial to enable partition-wise joins along two dimensions.

In the following example, the number of subpartitions is specified when creating a composite hash-hash partitioned table; however, names are not specified. System generated names are assigned to partitions and subpartitions, which are stored in the default tablespace of the table.

**Live SQL:**

View and run a related example on Oracle Live SQL at [Oracle Live SQL: Creating a Composite Hash-Hash Partition Table](https://livesql.oracle.com/apex/livesql/docs/vldbg/partitioning/composite-hash-hash-partitioning-example.html).

Example 4-17 Creating a composite hash-hash partitioned table

    CREATE TABLE departments_courses_hash (
                 department_id NUMBER(4) NOT NULL,
                 department_name VARCHAR2(30),
                 course_id NUMBER(4) NOT NULL)
         PARTITION BY HASH(department_id)
         SUBPARTITION BY HASH (course_id) SUBPARTITIONS 32 PARTITIONS 16;

**See Also:**

Specifying Subpartition Templates to Describe Composite Partitioned Tables to learn how using a subpartition template can simplify the specification of a composite partitioned table

### 4.2.2 Creating Composite Interval-\* Partitioned Tables

The concepts of interval-\* composite partitioning are similar to the concepts for range-\* partitioning.

However, you extend the `PARTITION BY RANGE` clause to include the `INTERVAL` definition. You must specify at least one range partition using the `PARTITION` clause. The range partitioning key value determines the high value of the range partitions, which is called the transition point, and the database automatically creates interval partitions for data beyond that transition point.

The subpartitions for intervals in an interval-\* partitioned table are created when the database creates the interval. You can specify the definition of future subpartitions only with a subpartition template.

The following topics show examples for the different interval-\* composite partitioning methods.

- Creating Composite Interval-Hash Partitioned Tables

- Creating Composite Interval-List Partitioned Tables

- Creating Composite Interval-Range Partitioned Tables

**See Also:**

Specifying Subpartition Templates to Describe Composite Partitioned Tables to learn how using a subpartition template can simplify the specification of a composite partitioned table

#### 4.2.2.1 Creating Composite Interval-Hash Partitioned Tables

You can create an interval-hash partitioned table with multiple hash partitions by specifying multiple hash partitions in the `PARTITION` clause or by using a subpartition template.

If you do not use either of these methods, then future interval partitions get only a single hash subpartition.

The following example shows the `sales` table, interval partitioned using monthly intervals on `time_id`, with hash subpartitions by `cust_id`. This example specifies multiple hash partitions, without any specific tablespace assignment to the individual hash partitions.

**Live SQL:**

View and run a related example on Oracle Live SQL at [Oracle Live SQL: Creating a Composite Interval-Hash Partitioned Table](https://livesql.oracle.com/apex/livesql/docs/vldbg/partitioning/composite-interval-hash-partitioning-example.html).

    CREATE TABLE sales
      ( prod_id       NUMBER(6)
      , cust_id       NUMBER
      , time_id       DATE
      , channel_id    CHAR(1)
      , promo_id      NUMBER(6)
      , quantity_sold NUMBER(3)
      , amount_sold   NUMBER(10,2)
      )
     PARTITION BY RANGE (time_id) INTERVAL (NUMTOYMINTERVAL(1,'MONTH'))
     SUBPARTITION BY HASH (cust_id) SUBPARTITIONS 4
     (PARTITION before_2000 VALUES LESS THAN (TO_DATE('01-JAN-2000','dd-MON-yyyy'))
      )
    PARALLEL;

This next example shows the same `sales` table, interval partitioned using monthly intervals on `time_id`, again with hash subpartitions by `cust_id`. This time, however, individual hash partitions are stored in separate tablespaces. The subpartition template is used to define the tablespace assignment for future hash subpartitions.

    CREATE TABLE sales
      ( prod_id       NUMBER(6)
      , cust_id       NUMBER
      , time_id       DATE
      , channel_id    CHAR(1)
      , promo_id      NUMBER(6)
      , quantity_sold NUMBER(3)
      , amount_sold   NUMBER(10,2)
      )
     PARTITION BY RANGE (time_id) INTERVAL (NUMTOYMINTERVAL(1,'MONTH'))
     SUBPARTITION BY hash(cust_id)
       SUBPARTITION template
       ( SUBPARTITION p1 TABLESPACE ts1
       , SUBPARTITION p2 TABLESPACE ts2
       , SUBPARTITION p3 TABLESPACE ts3
       , SUBPARTITION P4 TABLESPACE ts4
       )
     (PARTITION before_2000 VALUES LESS THAN (TO_DATE('01-JAN-2000','dd-MON-yyyy'))
      )
    PARALLEL;

#### 4.2.2.2 Creating Composite Interval-List Partitioned Tables

To define list subpartitions for future interval-list partitions, you must use the subpartition template.

If you do not use the subpartitioning template, then the only subpartition that are created for every interval partition is a `DEFAULT` subpartition.

Example 4-18 shows the `sales_interval_list` table, interval partitioned using monthly intervals on `sales_date`, with list subpartitions by `channel_id`.

Example 4-18 Creating a composite interval-list partitioned table

    CREATE TABLE sales_interval_list
      ( product_id       NUMBER(6)
      , customer_id      NUMBER
      , channel_id       CHAR(1)
      , promo_id         NUMBER(6)
      , sales_date       DATE
      , quantity_sold    INTEGER
      , amount_sold      NUMBER(10,2)
      )
     PARTITION BY RANGE (sales_date) INTERVAL (NUMTOYMINTERVAL(1,'MONTH'))
     SUBPARTITION BY LIST (channel_id)
       SUBPARTITION TEMPLATE
       ( SUBPARTITION p_catalog VALUES ('C')
       , SUBPARTITION p_internet VALUES ('I')
       , SUBPARTITION p_partners VALUES ('P')
       , SUBPARTITION p_direct_sales VALUES ('S')
       , SUBPARTITION p_tele_sales VALUES ('T')
       )
     (PARTITION before_2017 VALUES LESS THAN (TO_DATE('01-JAN-2017','dd-MON-yyyy'))
      )
    PARALLEL;

    SELECT TABLE_NAME, PARTITION_NAME, SUBPARTITION_NAME FROM USER_TAB_SUBPARTITIONS WHERE TABLE_NAME ='SALES_INTERVAL_LIST';

#### 4.2.2.3 Creating Composite Interval-Range Partitioned Tables

To define range subpartitions for future interval-range partitions, you must use the subpartition template.

If you do not use the subpartition template, then the only subpartition that is created for every interval partition is a range subpartition with the `MAXVALUE` upper boundary.

Example 4-19 shows the `sales` table, interval partitioned using daily intervals on `time_id`, with range subpartitions by `amount_sold`.

Example 4-19 Creating a composite interval-range partitioned table

    CREATE TABLE sales
      ( prod_id       NUMBER(6)
      , cust_id       NUMBER
      , time_id       DATE
      , channel_id    CHAR(1)
      , promo_id      NUMBER(6)
      , quantity_sold NUMBER(3)
      , amount_sold   NUMBER(10,2)
      )
     PARTITION BY RANGE (time_id) INTERVAL (NUMTODSINTERVAL(1,'DAY'))
    SUBPARTITION BY RANGE(amount_sold)
       SUBPARTITION TEMPLATE
       ( SUBPARTITION p_low VALUES LESS THAN (1000)
       , SUBPARTITION p_medium VALUES LESS THAN (4000)
       , SUBPARTITION p_high VALUES LESS THAN (8000)
       , SUBPARTITION p_ultimate VALUES LESS THAN (maxvalue)
       )
     (PARTITION before_2000 VALUES LESS THAN (TO_DATE('01-JAN-2000','dd-MON-yyyy'))
      )
    PARALLEL;

### 4.2.3 Creating Composite List-\* Partitioned Tables

The concepts of list-hash, list-list, and list-range composite partitioning are similar to the concepts for range-hash, range-list, and range-range partitioning.

However, for list-\* composite partitioning you specify `PARTITION BY LIST` to define the partitioning strategy.

The list partitions of a list-\* composite partitioned table are similar to non-composite range partitioned tables. This organization enables optional subclauses of a `PARTITION` clause to specify physical and other attributes, including tablespace, specific to a partition segment. If not overridden at the partition level, then partitions inherit the attributes of their underlying table.

The subpartition descriptions, in the `SUBPARTITION` or `SUBPARTITIONS` clauses, are similar to range-\* composite partitioning methods.

The following topics show examples for the different list-\* composite partitioning methods.

- Creating Composite List-Hash Partitioned Tables

- Creating Composite List-List Partitioned Tables

- Creating Composite List-Range Partitioned Tables

**See Also:**

- Specifying Subpartition Templates to Describe Composite Partitioned Tables to learn how using a subpartition template can simplify the specification of a composite partitioned table

- About Creating Composite Range-Hash Partitioned Tables for more information about the subpartition definition of a list-hash composite partitioning method

- About Creating Composite Range-List Partitioned Tables for more information about the subpartition definition of a list-list composite partitioning method

- Creating Composite Range-Range Partitioned Tables for more information about the subpartition definition of a list-range composite partitioning method

#### 4.2.3.1 Creating Composite List-Hash Partitioned Tables

The example in this topic shows how to create a composite list-hash partitioned table.

Example 4-20 shows an `accounts` table that is list partitioned by region and subpartitioned using hash by customer identifier.

Example 4-20 Creating a composite list-hash partitioned table

    CREATE TABLE accounts
    ( id             NUMBER
     , account_number NUMBER
     , customer_id    NUMBER
     , balance        NUMBER
     , branch_id      NUMBER
     , region         VARCHAR(2)
     , status         VARCHAR2(1)
    )
    PARTITION BY LIST (region)
    SUBPARTITION BY HASH (customer_id) SUBPARTITIONS 8
    ( PARTITION p_northwest VALUES ('OR', 'WA')
     , PARTITION p_southwest VALUES ('AZ', 'UT', 'NM')
     , PARTITION p_northeast VALUES ('NY', 'VM', 'NJ')
     , PARTITION p_southeast VALUES ('FL', 'GA')
     , PARTITION p_northcentral VALUES ('SD', 'WI')
     , PARTITION p_southcentral VALUES ('OK', 'TX')
    );

#### 4.2.3.2 Creating Composite List-List Partitioned Tables

The example in this topic shows how to create a composite list-list partitioned table.

Example 4-21 shows an `accounts` table that is list partitioned by region and subpartitioned using list by account status.

**Live SQL:**

View and run a related example on Oracle Live SQL at [Oracle Live SQL: Creating a Composite List-List Partitioned Table](https://livesql.oracle.com/apex/livesql/docs/vldbg/partitioning/composite-list-list-partitioning-example.html).

Example 4-21 Creating a composite list-list partitioned table

    CREATE TABLE accounts
    ( id             NUMBER
    , account_number NUMBER
    , customer_id    NUMBER
    , balance        NUMBER
    , branch_id      NUMBER
    , region         VARCHAR(2)
    , status         VARCHAR2(1)
    )
    PARTITION BY LIST (region)
    SUBPARTITION BY LIST (status)
    ( PARTITION p_northwest VALUES ('OR', 'WA')
      ( SUBPARTITION p_nw_bad VALUES ('B')
      , SUBPARTITION p_nw_average VALUES ('A')
      , SUBPARTITION p_nw_good VALUES ('G')
      )
    , PARTITION p_southwest VALUES ('AZ', 'UT', 'NM')
      ( SUBPARTITION p_sw_bad VALUES ('B')
      , SUBPARTITION p_sw_average VALUES ('A')
      , SUBPARTITION p_sw_good VALUES ('G')
      )
    , PARTITION p_northeast VALUES ('NY', 'VM', 'NJ')
      ( SUBPARTITION p_ne_bad VALUES ('B')
      , SUBPARTITION p_ne_average VALUES ('A')
      , SUBPARTITION p_ne_good VALUES ('G')
      )
    , PARTITION p_southeast VALUES ('FL', 'GA')
      ( SUBPARTITION p_se_bad VALUES ('B')
      , SUBPARTITION p_se_average VALUES ('A')
      , SUBPARTITION p_se_good VALUES ('G')
      )
    , PARTITION p_northcentral VALUES ('SD', 'WI')
      ( SUBPARTITION p_nc_bad VALUES ('B')
      , SUBPARTITION p_nc_average VALUES ('A')
      , SUBPARTITION p_nc_good VALUES ('G')
      )
    , PARTITION p_southcentral VALUES ('OK', 'TX')
      ( SUBPARTITION p_sc_bad VALUES ('B')
      , SUBPARTITION p_sc_average VALUES ('A')
      , SUBPARTITION p_sc_good VALUES ('G')
      )
    );

#### 4.2.3.3 Creating Composite List-Range Partitioned Tables

The example in this topic shows how to create a composite list-range partitioned table.

Example 4-22 shows an `accounts` table that is list partitioned by region and subpartitioned using range by account balance, and row movement is enabled. Subpartitions for different list partitions could have different ranges specified.

Example 4-22 Creating a composite list-range partitioned table

    CREATE TABLE accounts
    ( id             NUMBER
    , account_number NUMBER
    , customer_id    NUMBER
    , balance        NUMBER
    , branch_id      NUMBER
    , region         VARCHAR(2)
    , status         VARCHAR2(1)
    )
    PARTITION BY LIST (region)
    SUBPARTITION BY RANGE (balance)
    ( PARTITION p_northwest VALUES ('OR', 'WA')
      ( SUBPARTITION p_nw_low VALUES LESS THAN (1000)
      , SUBPARTITION p_nw_average VALUES LESS THAN (10000)
      , SUBPARTITION p_nw_high VALUES LESS THAN (100000)
      , SUBPARTITION p_nw_extraordinary VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_southwest VALUES ('AZ', 'UT', 'NM')
      ( SUBPARTITION p_sw_low VALUES LESS THAN (1000)
      , SUBPARTITION p_sw_average VALUES LESS THAN (10000)
      , SUBPARTITION p_sw_high VALUES LESS THAN (100000)
      , SUBPARTITION p_sw_extraordinary VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_northeast VALUES ('NY', 'VM', 'NJ')
      ( SUBPARTITION p_ne_low VALUES LESS THAN (1000)
      , SUBPARTITION p_ne_average VALUES LESS THAN (10000)
      , SUBPARTITION p_ne_high VALUES LESS THAN (100000)
      , SUBPARTITION p_ne_extraordinary VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_southeast VALUES ('FL', 'GA')
      ( SUBPARTITION p_se_low VALUES LESS THAN (1000)
      , SUBPARTITION p_se_average VALUES LESS THAN (10000)
      , SUBPARTITION p_se_high VALUES LESS THAN (100000)
      , SUBPARTITION p_se_extraordinary VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_northcentral VALUES ('SD', 'WI')
      ( SUBPARTITION p_nc_low VALUES LESS THAN (1000)
      , SUBPARTITION p_nc_average VALUES LESS THAN (10000)
      , SUBPARTITION p_nc_high VALUES LESS THAN (100000)
      , SUBPARTITION p_nc_extraordinary VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_southcentral VALUES ('OK', 'TX')
      ( SUBPARTITION p_sc_low VALUES LESS THAN (1000)
      , SUBPARTITION p_sc_average VALUES LESS THAN (10000)
      , SUBPARTITION p_sc_high VALUES LESS THAN (100000)
      , SUBPARTITION p_sc_extraordinary VALUES LESS THAN (MAXVALUE)
      )
    ) ENABLE ROW MOVEMENT;

### 4.2.4 Creating Composite Range-\* Partitioned Tables

The methods for creating composite range-\* partitioned tables are introduced in this topic.

The following topics show examples of the different range-\* composite partitioning methods.

- About Creating Composite Range-Hash Partitioned Tables

- About Creating Composite Range-List Partitioned Tables

- Creating Composite Range-Range Partitioned Tables

**See Also:**

Specifying Subpartition Templates to Describe Composite Partitioned Tables to learn how using a subpartition template can simplify the specification of a composite partitioned table

#### 4.2.4.1 About Creating Composite Range-Hash Partitioned Tables

The partitions of a range-hash partitioned table are logical structures only, because their data is stored in the segments of their subpartitions.

As with partitions, these subpartitions share the same logical attributes. Unlike range partitions in a range-partitioned table, the subpartitions cannot have different physical attributes from the owning partition, although they are not required to reside in the same tablespace.

The following topics are discussed:

- Creating a Composite Range-Hash Partitioned Table With the Same Tablespaces

- Creating a Composite Range-Hash Partitioned Table With Varying Tablespaces

- Creating a Local Index Across Multiple Tablespaces

**See Also:**

Specifying Subpartition Templates to Describe Composite Partitioned Tables to learn how using a subpartition template can simplify the specification of a composite partitioned table

##### 4.2.4.1.1 Creating a Composite Range-Hash Partitioned Table With the Same Tablespaces

The example in this topic shows how to create a composite range-hash partitioned table using the same tablespaces.

The statement in Example 4-23 creates a range-hash partitioned table. Four range partitions are created, each containing eight subpartitions. Because the subpartitions are not named, system generated names are assigned, but the `STORE IN` clause distributes them across the 4 specified tablespaces (`ts1`, `ts2`, `ts3`,`ts4`).

Example 4-23 Creating a composite range-hash partitioned table using one STORE IN clause

    CREATE TABLE sales
      ( prod_id       NUMBER(6)
      , cust_id       NUMBER
      , time_id       DATE
      , channel_id    CHAR(1)
      , promo_id      NUMBER(6)
      , quantity_sold NUMBER(3)
      , amount_sold   NUMBER(10,2)
      )
     PARTITION BY RANGE (time_id) SUBPARTITION BY HASH (cust_id)
      SUBPARTITIONS 8 STORE IN (ts1, ts2, ts3, ts4)
     ( PARTITION sales_q1_2006 VALUES LESS THAN (TO_DATE('01-APR-2006','dd-MON-yyyy'))
      , PARTITION sales_q2_2006 VALUES LESS THAN (TO_DATE('01-JUL-2006','dd-MON-yyyy'))
      , PARTITION sales_q3_2006 VALUES LESS THAN (TO_DATE('01-OCT-2006','dd-MON-yyyy'))
      , PARTITION sales_q4_2006 VALUES LESS THAN (TO_DATE('01-JAN-2007','dd-MON-yyyy'))
     );

##### 4.2.4.1.2 Creating a Composite Range-Hash Partitioned Table With Varying Tablespaces

The example in this topic shows how to create a composite range-hash partitioned table using varying tablespaces.

Attributes specified for a range partition apply to all subpartitions of that partition. You can specify different attributes for each range partition, and you can specify a `STORE IN` clause at the partition level if the list of tablespaces across which the subpartitions of that partition should be spread is different from those of other partitions. This is illustrated in the following example.

    CREATE TABLE employees_range_hash
             (department_id NUMBER(4) NOT NULL,
              last_name VARCHAR2(25),
              job_id VARCHAR2(10))
         PARTITION BY RANGE(department_id) SUBPARTITION BY HASH(last_name)
            SUBPARTITIONS 8 STORE IN (ts1, ts3, ts5, ts7)
        (PARTITION p1 VALUES LESS THAN (1000),
         PARTITION p2 VALUES LESS THAN (2000)
            STORE IN (ts2, ts4, ts6, ts8),
         PARTITION p3 VALUES LESS THAN (MAXVALUE)
           (SUBPARTITION p3_s1 TABLESPACE ts4,
            SUBPARTITION p3_s2 TABLESPACE ts5));

##### 4.2.4.1.3 Creating a Local Index Across Multiple Tablespaces

The example in this topic shows how to create a local index across multiple tablespaces.

The following statement is an example of creating a local index on a table where the index segments are spread across tablespaces `ts7`, `ts8`, and `ts9`.

    CREATE INDEX employee_ix ON employees_range_hash(department_id)
         LOCAL STORE IN (ts7, ts8, ts9);

This local index is equipartitioned with the base table so that it consists of as many partitions as the base table. Each index partition consists of as many subpartitions as the corresponding base table partition. Index entries for rows in a given subpartition of the base table are stored in the corresponding subpartition of the index.

#### 4.2.4.2 About Creating Composite Range-List Partitioned Tables

The range partitions of a range-list composite partitioned table are described as the same for non-composite range partitioned tables.

This organization enables optional subclauses of a `PARTITION` clause to specify physical and other attributes, including tablespace, specific to a partition segment. If not overridden at the partition level, partitions inherit the attributes of their underlying table.

The list subpartition descriptions, in the `SUBPARTITION` clauses, are described as for non-composite list partitions, except the only physical attribute that can be specified is a tablespace (optional). Subpartitions inherit all other physical attributes from the partition description.

The following topics are discussed:

- Creating a Composite Range-List Partitioned Table

- Creating a Composite Range-List Partitioned Table Specifying Tablespaces

**See Also:**

Specifying Subpartition Templates to Describe Composite Partitioned Tables to learn how using a subpartition template can simplify the specification of a composite partitioned table

##### 4.2.4.2.1 Creating a Composite Range-List Partitioned Table

The example in this topic shows how to create a composite range-list partitioned table.

Example 4-24 illustrates how range-list partitioning might be used. The example tracks sales data of products by quarters and within each quarter, groups it by specified states.

A row is mapped to a partition by checking whether the value of the partitioning column for a row falls within a specific partition range. The row is then mapped to a subpartition within that partition by identifying the subpartition whose descriptor value list contains a value matching the subpartition column value. For example, the following list describes how some sample rows are inserted.

- (10, 4532130, '23-Jan-1999', 8934.10, 'WA') maps to subpartition `q1_1999_northwest`

- (20, 5671621, '15-May-1999', 49021.21, 'OR') maps to subpartition `q2_1999_northwest`

- (30, 9977612, '07-Sep-1999', 30987.90, 'FL') maps to subpartition `q3_1999_southeast`

- (40, 9977612, '29-Nov-1999', 67891.45, 'TX') maps to subpartition `q4_1999_southcentral`

- (40, 4532130, '5-Jan-2000', 897231.55, 'TX') does not map to any partition in the table and displays an error

- (50, 5671621, '17-Dec-1999', 76123.35, 'CA') does not map to any subpartition in the table and displays an error

**Live SQL:**

View and run a related example on Oracle Live SQL at [Oracle Live SQL: Creating a Composite Range-List Partitioned Table](https://livesql.oracle.com/apex/livesql/docs/vldbg/partitioning/composite-range-list-partitioning-example.html).

Example 4-24 Creating a composite range-list partitioned table

    CREATE TABLE quarterly_regional_sales
          (deptno number, item_no varchar2(20),
           txn_date date, txn_amount number, state varchar2(2))
      TABLESPACE ts4
      PARTITION BY RANGE (txn_date)
        SUBPARTITION BY LIST (state)
          (PARTITION q1_1999 VALUES LESS THAN (TO_DATE('1-APR-1999','DD-MON-YYYY'))
             (SUBPARTITION q1_1999_northwest VALUES ('OR', 'WA'),
              SUBPARTITION q1_1999_southwest VALUES ('AZ', 'UT', 'NM'),
              SUBPARTITION q1_1999_northeast VALUES ('NY', 'VM', 'NJ'),
              SUBPARTITION q1_1999_southeast VALUES ('FL', 'GA'),
              SUBPARTITION q1_1999_northcentral VALUES ('SD', 'WI'),
              SUBPARTITION q1_1999_southcentral VALUES ('OK', 'TX')
             ),
           PARTITION q2_1999 VALUES LESS THAN ( TO_DATE('1-JUL-1999','DD-MON-YYYY'))
             (SUBPARTITION q2_1999_northwest VALUES ('OR', 'WA'),
              SUBPARTITION q2_1999_southwest VALUES ('AZ', 'UT', 'NM'),
              SUBPARTITION q2_1999_northeast VALUES ('NY', 'VM', 'NJ'),
              SUBPARTITION q2_1999_southeast VALUES ('FL', 'GA'),
              SUBPARTITION q2_1999_northcentral VALUES ('SD', 'WI'),
              SUBPARTITION q2_1999_southcentral VALUES ('OK', 'TX')
             ),
           PARTITION q3_1999 VALUES LESS THAN (TO_DATE('1-OCT-1999','DD-MON-YYYY'))
             (SUBPARTITION q3_1999_northwest VALUES ('OR', 'WA'),
              SUBPARTITION q3_1999_southwest VALUES ('AZ', 'UT', 'NM'),
              SUBPARTITION q3_1999_northeast VALUES ('NY', 'VM', 'NJ'),
              SUBPARTITION q3_1999_southeast VALUES ('FL', 'GA'),
              SUBPARTITION q3_1999_northcentral VALUES ('SD', 'WI'),
              SUBPARTITION q3_1999_southcentral VALUES ('OK', 'TX')
             ),
           PARTITION q4_1999 VALUES LESS THAN ( TO_DATE('1-JAN-2000','DD-MON-YYYY'))
             (SUBPARTITION q4_1999_northwest VALUES ('OR', 'WA'),
              SUBPARTITION q4_1999_southwest VALUES ('AZ', 'UT', 'NM'),
              SUBPARTITION q4_1999_northeast VALUES ('NY', 'VM', 'NJ'),
              SUBPARTITION q4_1999_southeast VALUES ('FL', 'GA'),
              SUBPARTITION q4_1999_northcentral VALUES ('SD', 'WI'),
              SUBPARTITION q4_1999_southcentral VALUES ('OK', 'TX')
             )
          );

##### 4.2.4.2.2 Creating a Composite Range-List Partitioned Table Specifying Tablespaces

The example in this topic shows how to create a composite range-list partitioned table while specifying tablespaces.

The partitions of a range-list partitioned table are logical structures only, because their data is stored in the segments of their subpartitions. The list subpartitions have the same characteristics as list partitions. You can specify a default subpartition, just as you specify a default partition for list partitioning.

The following example creates a table that specifies a tablespace at the partition and subpartition levels. The number of subpartitions within each partition varies, and default subpartitions are specified. This example results in the following subpartition descriptions:

- All subpartitions inherit their physical attributes, other than tablespace, from tablespace level defaults. This is because the only physical attribute that has been specified for partitions or subpartitions is tablespace. There are no table level physical attributes specified, thus tablespace level defaults are inherited at all levels.

- The first 4 subpartitions of partition `q1_1999` are all contained in `tbs_1`, except for the subpartition `q1_others`, which is stored in `tbs_4` and contains all rows that do not map to any of the other partitions.

- The 6 subpartitions of partition `q2_1999` are all stored in `tbs_2`.

- The first 2 subpartitions of partition `q3_1999` are all contained in `tbs_3`, except for the subpartition `q3_others`, which is stored in `tbs_4` and contains all rows that do not map to any of the other partitions.

- There is no subpartition description for partition `q4_1999`. This results in one default subpartition being created and stored in `tbs_4`. The subpartition name is system generated in the form `SYS_SUBP``n`.

<!-- -->

    CREATE TABLE sample_regional_sales
          (deptno number, item_no varchar2(20),
           txn_date date, txn_amount number, state varchar2(2))
      PARTITION BY RANGE (txn_date)
        SUBPARTITION BY LIST (state)
          (PARTITION q1_1999 VALUES LESS THAN (TO_DATE('1-APR-1999','DD-MON-YYYY'))
              TABLESPACE tbs_1
             (SUBPARTITION q1_1999_northwest VALUES ('OR', 'WA'),
              SUBPARTITION q1_1999_southwest VALUES ('AZ', 'UT', 'NM'),
              SUBPARTITION q1_1999_northeast VALUES ('NY', 'VM', 'NJ'),
              SUBPARTITION q1_1999_southeast VALUES ('FL', 'GA'),
              SUBPARTITION q1_others VALUES (DEFAULT) TABLESPACE tbs_4
             ),
           PARTITION q2_1999 VALUES LESS THAN ( TO_DATE('1-JUL-1999','DD-MON-YYYY'))
              TABLESPACE tbs_2
             (SUBPARTITION q2_1999_northwest VALUES ('OR', 'WA'),
              SUBPARTITION q2_1999_southwest VALUES ('AZ', 'UT', 'NM'),
              SUBPARTITION q2_1999_northeast VALUES ('NY', 'VM', 'NJ'),
              SUBPARTITION q2_1999_southeast VALUES ('FL', 'GA'),
              SUBPARTITION q2_1999_northcentral VALUES ('SD', 'WI'),
              SUBPARTITION q2_1999_southcentral VALUES ('OK', 'TX')
             ),
           PARTITION q3_1999 VALUES LESS THAN (TO_DATE('1-OCT-1999','DD-MON-YYYY'))
              TABLESPACE tbs_3
             (SUBPARTITION q3_1999_northwest VALUES ('OR', 'WA'),
              SUBPARTITION q3_1999_southwest VALUES ('AZ', 'UT', 'NM'),
              SUBPARTITION q3_others VALUES (DEFAULT) TABLESPACE tbs_4
             ),
           PARTITION q4_1999 VALUES LESS THAN ( TO_DATE('1-JAN-2000','DD-MON-YYYY'))
              TABLESPACE tbs_4
          );

#### 4.2.4.3 Creating Composite Range-Range Partitioned Tables

The range partitions of a range-range composite partitioned table are similar to non-composite range partitioned tables.

This organization enables optional subclauses of a `PARTITION` clause to specify physical and other attributes, including tablespace, specific to a partition segment. If not overridden at the partition level, then partitions inherit the attributes of their underlying table.

The range subpartition descriptions, in the `SUBPARTITION` clauses, are similar to non-composite range partitions, except the only physical attribute that can be specified is an optional tablespace. Subpartitions inherit all other physical attributes from the partition description.

The following example illustrates how range-range partitioning might be used. The example tracks shipments. The service level agreement with the customer states that every order is delivered in the calendar month after the order was placed. The following types of orders are identified:

A row is mapped to a partition by checking whether the value of the partitioning column for a row falls within a specific partition range. The row is then mapped to a subpartition within that partition by identifying whether the value of the subpartitioning column falls within a specific range. For example, a shipment with an order date in September 2006 and a delivery date of October 28, 2006 falls in partition `p06_oct_a`.

- E (EARLY): orders that are delivered before the middle of the next month after the order was placed. These orders likely exceed customers' expectations.

- A (AGREED): orders that are delivered in the calendar month after the order was placed (but not early orders).

- L (LATE): orders that were only delivered starting the second calendar month after the order was placed.

<!-- -->

    CREATE TABLE shipments
    ( order_id      NUMBER NOT NULL
    , order_date    DATE NOT NULL
    , delivery_date DATE NOT NULL
    , customer_id   NUMBER NOT NULL
    , sales_amount  NUMBER NOT NULL
    )
    PARTITION BY RANGE (order_date)
    SUBPARTITION BY RANGE (delivery_date)
    ( PARTITION p_2006_jul VALUES LESS THAN (TO_DATE('01-AUG-2006','dd-MON-yyyy'))
      ( SUBPARTITION p06_jul_e VALUES LESS THAN (TO_DATE('15-AUG-2006','dd-MON-yyyy'))
      , SUBPARTITION p06_jul_a VALUES LESS THAN (TO_DATE('01-SEP-2006','dd-MON-yyyy'))
      , SUBPARTITION p06_jul_l VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_2006_aug VALUES LESS THAN (TO_DATE('01-SEP-2006','dd-MON-yyyy'))
      ( SUBPARTITION p06_aug_e VALUES LESS THAN (TO_DATE('15-SEP-2006','dd-MON-yyyy'))
      , SUBPARTITION p06_aug_a VALUES LESS THAN (TO_DATE('01-OCT-2006','dd-MON-yyyy'))
      , SUBPARTITION p06_aug_l VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_2006_sep VALUES LESS THAN (TO_DATE('01-OCT-2006','dd-MON-yyyy'))
      ( SUBPARTITION p06_sep_e VALUES LESS THAN (TO_DATE('15-OCT-2006','dd-MON-yyyy'))
      , SUBPARTITION p06_sep_a VALUES LESS THAN (TO_DATE('01-NOV-2006','dd-MON-yyyy'))
      , SUBPARTITION p06_sep_l VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_2006_oct VALUES LESS THAN (TO_DATE('01-NOV-2006','dd-MON-yyyy'))
      ( SUBPARTITION p06_oct_e VALUES LESS THAN (TO_DATE('15-NOV-2006','dd-MON-yyyy'))
      , SUBPARTITION p06_oct_a VALUES LESS THAN (TO_DATE('01-DEC-2006','dd-MON-yyyy'))
      , SUBPARTITION p06_oct_l VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_2006_nov VALUES LESS THAN (TO_DATE('01-DEC-2006','dd-MON-yyyy'))
      ( SUBPARTITION p06_nov_e VALUES LESS THAN (TO_DATE('15-DEC-2006','dd-MON-yyyy'))
      , SUBPARTITION p06_nov_a VALUES LESS THAN (TO_DATE('01-JAN-2007','dd-MON-yyyy'))
      , SUBPARTITION p06_nov_l VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_2006_dec VALUES LESS THAN (TO_DATE('01-JAN-2007','dd-MON-yyyy'))
      ( SUBPARTITION p06_dec_e VALUES LESS THAN (TO_DATE('15-JAN-2007','dd-MON-yyyy'))
      , SUBPARTITION p06_dec_a VALUES LESS THAN (TO_DATE('01-FEB-2007','dd-MON-yyyy'))
      , SUBPARTITION p06_dec_l VALUES LESS THAN (MAXVALUE)
      )
    );

**See Also:**

Specifying Subpartition Templates to Describe Composite Partitioned Tables to learn how using a subpartition template can simplify the specification of a composite partitioned table

### 4.2.5 Specifying Subpartition Templates to Describe Composite Partitioned Tables

You can create subpartitions in a composite partitioned table using a subpartition template.

A subpartition template simplifies the specification of subpartitions by not requiring that a subpartition descriptor be specified for every partition in the table. Instead, you describe subpartitions only one time in a template, then apply that subpartition template to every partition in the table. For interval-\* composite partitioned tables, the subpartition template is the only way to define subpartitions for interval partitions.

The subpartition template is used whenever a subpartition descriptor is not specified for a partition. If a subpartition descriptor is specified, then it is used instead of the subpartition template for that partition. If no subpartition template is specified, and no subpartition descriptor is supplied for a partition, then a single default subpartition is created.

The following topics are discussed:

- Specifying a Subpartition Template for a \*-Hash Partitioned Table

- Specifying a Subpartition Template for a \*-List Partitioned Table

#### 4.2.5.1 Specifying a Subpartition Template for a \*-Hash Partitioned Table

For range-hash, interval-hash, and list-hash partitioned tables, the subpartition template can describe the subpartitions in detail, or it can specify just the number of hash subpartitions.

Example 4-25 creates a range-hash partitioned table using a subpartition template and displays the subpartition names and tablespaces.

The example produces a table with the following description.

- Every partition has four subpartitions as described in the subpartition template.

- Each subpartition has a tablespace specified. It is required that if a tablespace is specified for one subpartition in a subpartition template, then one must be specified for all.

- The names of the subpartitions, unless you use interval-\* subpartitioning, are generated by concatenating the partition name with the subpartition name in the form:

  partition name\_subpartition name

  For interval-\* subpartitioning, the subpartition names are system-generated in the form:

  `SYS_SUBP``n`

Example 4-25 Creating a range-hash partitioned table with a subpartition template

    CREATE TABLE employees_sub_template (department_id NUMBER(4) NOT NULL,
                 last_name VARCHAR2(25), job_id VARCHAR2(10))
         PARTITION BY RANGE(department_id) SUBPARTITION BY HASH(last_name)
         SUBPARTITION TEMPLATE
             (SUBPARTITION a TABLESPACE ts1,
              SUBPARTITION b TABLESPACE ts2,
              SUBPARTITION c TABLESPACE ts3,
              SUBPARTITION d TABLESPACE ts4
             )
        (PARTITION p1 VALUES LESS THAN (1000),
         PARTITION p2 VALUES LESS THAN (2000),
         PARTITION p3 VALUES LESS THAN (MAXVALUE)
        );

    SQL> SELECT TABLESPACE_NAME, PARTITION_NAME, SUBPARTITION_NAME
      2  FROM DBA_TAB_SUBPARTITIONS WHERE TABLE_NAME='EMPLOYEEES_SUB_TEMPLATE'
      3  ORDER BY TABLESPACE_NAME;

    TABLESPACE_NAME PARTITION_NAME  SUBPARTITION_NAME
    --------------- --------------- ------------------
    TS1             P1              P1_A
    TS1             P2              P2_A
    TS1             P3              P3_A
    TS2             P1              P1_B
    TS2             P2              P2_B
    TS2             P3              P3_B
    TS3             P1              P1_C
    TS3             P2              P2_C
    TS3             P3              P3_C
    TS4             P1              P1_D
    TS4             P2              P2_D
    TS4             P3              P3_D

    12 rows selected.

#### 4.2.5.2 Specifying a Subpartition Template for a \*-List Partitioned Table

For -list partitioned tables, the subpartition template can describe the subpartitions in detail.

Example 4-26, for a range-list partitioned table, illustrates how using a subpartition template can help you stripe data across tablespaces. In this example, a table is created where the table subpartitions are vertically striped, meaning that subpartition n from every partition is in the same tablespace.

If you specified the tablespaces at the partition level (for example, `tbs_1` for partition `q1_1999`, `tbs_2` for partition `q2_1999`, `tbs_3` for partition `q3_1999`, and `tbs_4` for partition `q4_1999`) and not in the subpartition template, then the table would be horizontally striped. All subpartitions would be in the tablespace of the owning partition.

Example 4-26 Creating a range-list partitioned table with a subpartition template

    CREATE TABLE stripe_regional_sales
                ( deptno number, item_no varchar2(20),
                  txn_date date, txn_amount number, state varchar2(2))
       PARTITION BY RANGE (txn_date)
       SUBPARTITION BY LIST (state)
       SUBPARTITION TEMPLATE
          (SUBPARTITION northwest VALUES ('OR', 'WA') TABLESPACE tbs_1,
           SUBPARTITION southwest VALUES ('AZ', 'UT', 'NM') TABLESPACE tbs_2,
           SUBPARTITION northeast VALUES ('NY', 'VM', 'NJ') TABLESPACE tbs_3,
           SUBPARTITION southeast VALUES ('FL', 'GA') TABLESPACE tbs_4,
           SUBPARTITION midwest VALUES ('SD', 'WI') TABLESPACE tbs_5,
           SUBPARTITION south VALUES ('AL', 'AK') TABLESPACE tbs_6,
           SUBPARTITION others VALUES (DEFAULT ) TABLESPACE tbs_7
          )
      (PARTITION q1_1999 VALUES LESS THAN ( TO_DATE('01-APR-1999','DD-MON-YYYY')),
       PARTITION q2_1999 VALUES LESS THAN ( TO_DATE('01-JUL-1999','DD-MON-YYYY')),
       PARTITION q3_1999 VALUES LESS THAN ( TO_DATE('01-OCT-1999','DD-MON-YYYY')),
       PARTITION q4_1999 VALUES LESS THAN ( TO_DATE('1-JAN-2000','DD-MON-YYYY'))
      );
