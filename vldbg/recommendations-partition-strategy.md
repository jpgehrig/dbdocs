Review these recommendations based on performance considerations when choosing a partitioning strategy.

The following topics provide recommendations for choosing a partitioning strategy:

- When to Use Range or Interval Partitioning

- When to Use Hash Partitioning

- When to Use List Partitioning

- When to Use Composite Partitioning

- When to Use Interval Partitioning

- When to Use Reference Partitioning

- When to Partition on Virtual Columns

- Considerations When Using Read-Only Tablespaces

### 3.5.1 When to Use Range or Interval Partitioning

Range and interval partitioning are useful when organizing similar data, especially date and time data.

Range partitioning is a convenient method for partitioning historical data. The boundaries of range partitions define the ordering of the partitions in the tables or indexes.

Interval partitioning is an extension to range partitioning in which, beyond a point in time, partitions are defined by an interval. Interval partitions are automatically created by the database when data is inserted into the partition.

Range or interval partitioning is often used to organize data by time intervals on a column of type `DATE`. Thus, most SQL statements accessing range partitions focus on time frames. An example of this is a SQL statement similar to "select data from a particular period in time". In such a scenario, if each partition represents data for one month, the query "find data of month 06-DEC" must access only the December partition of year 2006. This reduces the amount of data scanned to a fraction of the total data available, an optimization method called partition pruning.

Range partitioning is also ideal when you periodically load new data and purge old data, because it is easy to add or drop partitions. For example, it is common to keep a rolling window of data, keeping the past 36 months' worth of data online. Range partitioning simplifies this process. To add data from a new month, you load it into a separate table, clean it, index it, and then add it to the range-partitioned table using the `EXCHANGE` `PARTITION` statement, all while the original table remains online. After you add the new partition, you can drop the trailing month with the `DROP` `PARTITION` statement. The alternative to using the `DROP` `PARTITION` statement can be to archive the partition and make it read only, but this works only when your partitions are in separate tablespaces. You can also implement a rolling window of data using inserts into the partitioned table.

Interval partitioning provides an easy way for interval partitions to be automatically created as data arrives. Interval partitions can also be used for all other partition maintenance operations.

In conclusion, consider using range or interval partitioning when:

- Very large tables are frequently scanned by a range predicate on a good partitioning column, such as `ORDER_DATE` or `PURCHASE_DATE`. Partitioning the table on that column enables partition pruning.

- You want to maintain a rolling window of data.

- You cannot complete administrative operations, such as backup and restore, on large tables in an allotted time frame, but you can divide them into smaller logical pieces based on the partition range column.

Example 3-5 creates the table `salestable` for a period of two years, 2005 and 2006, and partitions it by range according to the column `s_salesdate` to separate the data into eight quarters, each corresponding to a partition. Future partitions are created automatically through the monthly interval definition. Interval partitions are created in the provided list of tablespaces in a round-robin manner. Analysis of sales figures by a short interval can take advantage of partition pruning. The sales table also supports a rolling window approach.

Example 3-5 Creating a table with range and interval partitioning

    CREATE TABLE salestable
      (s_productid  NUMBER,
       s_saledate   DATE,
       s_custid     NUMBER,
       s_totalprice NUMBER)
    PARTITION BY RANGE(s_saledate)
    INTERVAL(NUMTOYMINTERVAL(1,'MONTH')) STORE IN (tbs1,tbs2,tbs3,tbs4)
     (PARTITION sal05q1 VALUES LESS THAN (TO_DATE('01-APR-2005', 'DD-MON-YYYY')) TABLESPACE tbs1,
      PARTITION sal05q2 VALUES LESS THAN (TO_DATE('01-JUL-2005', 'DD-MON-YYYY')) TABLESPACE tbs2,
      PARTITION sal05q3 VALUES LESS THAN (TO_DATE('01-OCT-2005', 'DD-MON-YYYY')) TABLESPACE tbs3,
      PARTITION sal05q4 VALUES LESS THAN (TO_DATE('01-JAN-2006', 'DD-MON-YYYY')) TABLESPACE tbs4,
      PARTITION sal06q1 VALUES LESS THAN (TO_DATE('01-APR-2006', 'DD-MON-YYYY')) TABLESPACE tbs1,
      PARTITION sal06q2 VALUES LESS THAN (TO_DATE('01-JUL-2006', 'DD-MON-YYYY')) TABLESPACE tbs2,
      PARTITION sal06q3 VALUES LESS THAN (TO_DATE('01-OCT-2006', 'DD-MON-YYYY')) TABLESPACE tbs3,
      PARTITION sal06q4 VALUES LESS THAN (TO_DATE('01-JAN-2007', 'DD-MON-YYYY')) TABLESPACE tbs4);

**See Also:**

[Partition Administration](partition-admin.md) for more information about the partition maintenance operations on interval partitions

### 3.5.2 When to Use Hash Partitioning

Hash partitioning is useful for randomly distributing data across partitions based on a hashing algorithm, rather than grouping similar data.

There are times when it is not obvious in which partition data should reside, although the partitioning key can be identified. Rather than group similar data, there are times when it is desirable to distribute data such that it does not correspond to a business or a logical view of the data, as it does in range partitioning. With hash partitioning, a row is placed into a partition based on the result of passing the partitioning key into a hashing algorithm.

Using this approach, data is randomly distributed across the partitions rather than grouped. This is a good approach for some data, but may not be an effective way to manage historical data. However, hash partitions share some performance characteristics with range partitions. For example, partition pruning is limited to equality predicates. You can also use partition-wise joins, parallel index access, and parallel DML.

As a general rule, use hash partitioning for the following purposes:

- To enable partial or full parallel partition-wise joins with likely equisized partitions.

- To distribute data evenly among the nodes of an MPP platform that uses Oracle Real Application Clusters. Consequently, you can minimize interconnect traffic when processing internode parallel statements.

- To use partition pruning and partition-wise joins according to a partitioning key that is mostly constrained by a distinct value or value list.

- To randomly distribute data to avoid I/O bottlenecks if you do not use a storage management technique that stripes and mirrors across all available devices.

**Note:**

With hash partitioning, only equality or `IN`-list predicates are supported for partition pruning.

For optimal data distribution, the following requirements should be satisfied:

- Choose a column or combination of columns that is unique or almost unique.

- Create multiple partitions and subpartitions for each partition that is a power of two. For example, 2, 4, 8, 16, 32, 64, 128, and so on.

Example 3-6 creates four hash partitions for the table `sales_hash` using the column `s_productid` as the partitioning key. Parallel joins with the products table can take advantage of partial or full partition-wise joins. Queries accessing sales figures for only a single product or a list of products benefit from partition pruning.

If you do not explicitly specify partition names, but instead you specify the number of hash partitions, then Oracle automatically generates internal names for the partitions. Also, you can use the `STORE` `IN` clause to assign hash partitions to tablespaces in a round-robin manner.

Example 3-6 Creating a table with hash partitioning

    CREATE TABLE sales_hash
      (s_productid  NUMBER,
       s_saledate   DATE,
       s_custid     NUMBER,
       s_totalprice NUMBER)
    PARTITION BY HASH(s_productid)
    ( PARTITION p1 TABLESPACE tbs1
    , PARTITION p2 TABLESPACE tbs2
    , PARTITION p3 TABLESPACE tbs3
    , PARTITION p4 TABLESPACE tbs4
    );

**See Also:**

- [Partition-Wise Operations](partition-wise-joins.md) for information about part-wise joins

- [Storage Management for VLDBs](vldb-storage.md) for more information about managing storage for VLDBs

- [Partition Administration](partition-admin.md) for more examples on creating hash-partitioned tables

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for partitioning syntax

### 3.5.3 When to Use List Partitioning

List partitioning is useful to explicitly map rows to partitions based on discrete values.

In Example 3-7, all the customers for states Oregon and Washington are stored in one partition and customers in other states are stored in different partitions. Account managers who analyze their accounts by region can take advantage of partition pruning.

Example 3-7 Creating a table with list partitioning

    CREATE TABLE accounts
    ( id             NUMBER
    , account_number NUMBER
    , customer_id    NUMBER
    , branch_id      NUMBER
    , region         VARCHAR(2)
    , status         VARCHAR2(1)
    )
    PARTITION BY LIST (region)
    ( PARTITION p_northwest VALUES ('OR', 'WA')
    , PARTITION p_southwest VALUES ('AZ', 'UT', 'NM')
    , PARTITION p_northeast VALUES ('NY', 'VM', 'NJ')
    , PARTITION p_southeast VALUES ('FL', 'GA')
    , PARTITION p_northcentral VALUES ('SD', 'WI')
    , PARTITION p_southcentral VALUES ('OK', 'TX')
    );

### 3.5.4 When to Use Composite Partitioning

Composite partitioning offers the benefits of partitioning on multiple dimensions.

From a performance perspective you can take advantage of partition pruning on one or two dimensions depending on the SQL statement, and you can take advantage of the use of full or partial partition-wise joins on either dimension.

You can take advantage of parallel backup and recovery of a single table. Composite partitioning also increases the number of partitions significantly, which may be beneficial for efficient parallel execution. From a manageability perspective, you can implement a rolling window to support historical data and still partition on another dimension if many statements can benefit from partition pruning or partition-wise joins.

You can split backups of your tables and you can decide to store data differently based on identification by a partitioning key. For example, you may decide to store data for a specific product type in a read-only, compressed format, and keep other product type data uncompressed.

The database stores every subpartition in a composite partitioned table as a separate segment. Thus, the subpartitions may have properties that differ from the properties of the table or from the partition to which the subpartitions belong.

The following topics are discussed:

- When to Use Range or Interval Partitioning

- When to Use Hash Partitioning

- When to Use List Partitioning

- When to Use Composite Partitioning

- When to Use Interval Partitioning

- When to Use Reference Partitioning

- When to Partition on Virtual Columns

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for details regarding syntax and restrictions

#### 3.5.4.1 When to Use Composite Range-Hash Partitioning

Composite range-hash partitioning is particularly common for tables that store history, are very large consequently, and are frequently joined with other large tables.

For these types of tables (typical of data warehouse systems), composite range-hash partitioning provides the benefit of partition pruning at the range level with the opportunity to perform parallel full or partial partition-wise joins at the hash level. Specific cases can benefit from partition pruning on both dimensions for specific SQL statements.

Composite range-hash partitioning can also be used for tables that traditionally use hash partitioning, but also use a rolling window approach. Over time, data can be moved from one storage tier to another storage tier, compressed, stored in a read-only tablespace, and eventually purged. Information Lifecycle Management (ILM) scenarios often use range partitions to implement a tiered storage approach.

Example 3-8 is an example of a range hash partitioned `page_history` table of an Internet service provider. The table definition is optimized for historical analysis for either specific `client_ip` values (in which case queries benefit from partition pruning) or for analysis across many IP addresses, in which case queries can take advantage of full or partial partition-wise joins.

This example shows the use of interval partitioning. You can use interval partitioning in addition to range partitioning so that interval partitions are created automatically as data is inserted into the table.

Example 3-8 Creating a table with composite range-hash partitioning

    CREATE TABLE page_history
    ( id                NUMBER NOT NULL
    , url               VARCHAR2(300) NOT NULL
    , view_date         DATE NOT NULL
    , client_ip         VARCHAR2(23) NOT NULL
    , from_url          VARCHAR2(300)
    , to_url            VARCHAR2(300)
    , timing_in_seconds NUMBER
    ) PARTITION BY RANGE(view_date) INTERVAL (NUMTODSINTERVAL(1,'DAY'))
    SUBPARTITION BY HASH(client_ip)
    SUBPARTITIONS 32
    (PARTITION p0 VALUES LESS THAN (TO_DATE('01-JAN-2006','dd-MON-yyyy')))
    PARALLEL 32 COMPRESS;

**See Also:**

[Managing and Maintaining Time-Based Information](time-based-info.md) for more detail on Information Lifecycle Management (ILM) and implementing tiered storage using partitioning

#### 3.5.4.2 When to Use Composite Range-List Partitioning

Composite range-list partitioning is commonly used for large tables that store historical data and are commonly accessed on multiple dimensions.

Often the historical view of the data is one access path, but certain business cases add another categorization to the access path. For example, regional account managers are very interested in how many new customers they signed up in their region in a specific time period. ILM and its tiered storage approach is a common reason to create range-list partitioned tables so that older data can be moved and compressed, but partition pruning on the list dimension is still available.

Example 3-9 creates a range-list partitioned `call_detail_records` table. A telecommunication company can use this table to analyze specific types of calls over time. The table uses local indexes on `from_number` and `to_number`.

This example shows the use of interval partitioning. You can use interval partitioning in addition to range partitioning so that interval partitions are created automatically as data is inserted into the table.

Example 3-9 Creating a table with composite range-list partitioning

    CREATE TABLE call_detail_records
    ( id NUMBER
    , from_number        VARCHAR2(20)
    , to_number          VARCHAR2(20)
    , date_of_call       DATE
    , distance           VARCHAR2(1)
    , call_duration_in_s NUMBER(4)
    ) PARTITION BY RANGE(date_of_call)
    INTERVAL (NUMTODSINTERVAL(1,'DAY'))
    SUBPARTITION BY LIST(distance)
    SUBPARTITION TEMPLATE
    ( SUBPARTITION local VALUES('L') TABLESPACE tbs1
    , SUBPARTITION medium_long VALUES ('M') TABLESPACE tbs2
    , SUBPARTITION long_distance VALUES ('D') TABLESPACE tbs3
    , SUBPARTITION international VALUES ('I') TABLESPACE tbs4
    )
    (PARTITION p0 VALUES LESS THAN (TO_DATE('01-JAN-2005','dd-MON-yyyy')))
    PARALLEL;

    CREATE INDEX from_number_ix ON call_detail_records(from_number)
    LOCAL PARALLEL NOLOGGING;

    CREATE INDEX to_number_ix ON call_detail_records(to_number)
    LOCAL PARALLEL NOLOGGING;

#### 3.5.4.3 When to Use Composite Range-Range Partitioning

Composite range-range partitioning is useful for applications that store time-dependent data on multiple time dimensions.

Often these applications do not use one particular time dimension to access the data, but rather another time dimension, or sometimes both at the same time. For example, a web retailer wants to analyze its sales data based on when orders were placed, and when orders were shipped (handed over to the shipping company).

Other business cases for composite range-range partitioning include ILM scenarios, and applications that store historical data and want to categorize its data by range on another dimension.

Example 3-10 shows a range-range partitioned table `account_balance_history`. A bank may use access to individual subpartitions to contact its customers for low-balance reminders or specific promotions relevant to a certain category of customers.

This example shows the use of interval partitioning. You can use interval partitioning in addition to range partitioning so that interval partitions are created automatically as data is inserted into the table. In this case 7-day (weekly) intervals are created, starting Monday, January 1, 2007.

Example 3-10 Creating a table with composite range-range partitioning

    CREATE TABLE account_balance_history
    ( id                 NUMBER NOT NULL
    , account_number     NUMBER NOT NULL
    , customer_id        NUMBER NOT NULL
    , transaction_date   DATE NOT NULL
    , amount_credited    NUMBER
    , amount_debited     NUMBER
    , end_of_day_balance NUMBER NOT NULL
    ) PARTITION BY RANGE(transaction_date)
    INTERVAL (NUMTODSINTERVAL(7,'DAY'))
    SUBPARTITION BY RANGE(end_of_day_balance)
    SUBPARTITION TEMPLATE
    ( SUBPARTITION unacceptable VALUES LESS THAN (-1000)
    , SUBPARTITION credit VALUES LESS THAN (0)
    , SUBPARTITION low VALUES LESS THAN (500)
    , SUBPARTITION normal VALUES LESS THAN (5000)
    , SUBPARTITION high VALUES LESS THAN (20000)
    , SUBPARTITION extraordinary VALUES LESS THAN (MAXVALUE)
    )
    (PARTITION p0 VALUES LESS THAN (TO_DATE('01-JAN-2007','dd-MON-yyyy')));

#### 3.5.4.4 When to Use Composite List-Hash Partitioning

Composite list-hash partitioning is useful for large tables that are usually accessed on one dimension, but (due to their size) still must take advantage of parallel full or partial partition-wise joins on another dimension in joins with other large tables.

Example 3-11 shows a `credit_card_accounts` table. The table is list-partitioned on region in order for account managers to quickly access accounts in their region. The subpartitioning strategy is hash on `customer_id` so that queries against the transactions table, which is subpartitioned on `customer_id`, can take advantage of full partition-wise joins. Joins with the hash partitioned customers table can also benefit from full partition-wise joins. The table has a local bitmap index on the `is_active` column.

Example 3-11 Creating a table with composite list-hash partitioning

    CREATE TABLE credit_card_accounts
    ( account_number  NUMBER(16) NOT NULL
    , customer_id     NUMBER NOT NULL
    , customer_region VARCHAR2(2) NOT NULL
    , is_active       VARCHAR2(1) NOT NULL
    , date_opened     DATE NOT NULL
    ) PARTITION BY LIST (customer_region)
    SUBPARTITION BY HASH (customer_id)
    SUBPARTITIONS 16
    ( PARTITION emea VALUES ('EU','ME','AF')
    , PARTITION amer VALUES ('NA','LA')
    , PARTITION apac VALUES ('SA','AU','NZ','IN','CH')
    ) PARALLEL;

    CREATE BITMAP INDEX is_active_bix ON credit_card_accounts(is_active)
    LOCAL PARALLEL NOLOGGING;

#### 3.5.4.5 When to Use Composite List-List Partitioning

Composite list-list partitioning is useful for large tables that are often accessed on different dimensions.

You can specifically map rows to partitions on those dimensions based on discrete values.

Example 3-12 shows an example of a very frequently accessed `current_inventory` table. The table is constantly updated with the current inventory in the supermarket supplier's local warehouses. Potentially perishable foods are supplied from those warehouses to supermarkets, and it is important to optimize supplies and deliveries. The table has local indexes on `warehouse_id` and `product_id`.

Example 3-12 Creating a table with composite list-list partitioning

    CREATE TABLE current_inventory
    ( warehouse_id      NUMBER
    , warehouse_region  VARCHAR2(2)
    , product_id        NUMBER
    , product_category  VARCHAR2(12)
    , amount_in_stock   NUMBER
    , unit_of_shipping  VARCHAR2(20)
    , products_per_unit NUMBER
    , last_updated      DATE
    ) PARTITION BY LIST (warehouse_region)
    SUBPARTITION BY LIST (product_category)
    SUBPARTITION TEMPLATE
    ( SUBPARTITION perishable VALUES ('DAIRY','PRODUCE','MEAT','BREAD')
    , SUBPARTITION non_perishable VALUES ('CANNED','PACKAGED')
    , SUBPARTITION durable VALUES ('TOYS','KITCHENWARE')
    )
    ( PARTITION p_northwest VALUES ('OR', 'WA')
    , PARTITION p_southwest VALUES ('AZ', 'UT', 'NM')
    , PARTITION p_northeast VALUES ('NY', 'VM', 'NJ')
    , PARTITION p_southeast VALUES ('FL', 'GA')
    , PARTITION p_northcentral VALUES ('SD', 'WI')
    , PARTITION p_southcentral VALUES ('OK', 'TX')
    );

    CREATE INDEX warehouse_id_ix ON current_inventory(warehouse_id)
    LOCAL PARALLEL NOLOGGING;

    CREATE INDEX product_id_ix ON current_inventory(product_id)
    LOCAL PARALLEL NOLOGGING;

#### 3.5.4.6 When to Use Composite List-Range Partitioning

Composite list-range partitioning is useful for large tables that are accessed on different dimensions.

For the most commonly used dimension, you can specifically map rows to partitions on discrete values. List-range partitioning is commonly used for tables that use range values within a list partition, whereas range-list partitioning is commonly used for a discrete list values within a range partition. List-range partitioning is less commonly used to store historical data, even though equivalent scenarios are all suitable. Range-list partitioning can be implemented using interval-list partitioning, whereas list-range partitioning does not support interval partitioning.

Example 3-13 shows a `donations` table that stores donations in different currencies. The donations are categorized into small, medium, and high, depending on the amount. Due to currency differences, the ranges are different.

Example 3-13 Creating a table with composite list-range partitioning

    CREATE TABLE donations
    ( id             NUMBER
    , name           VARCHAR2(60)
    , beneficiary    VARCHAR2(80)
    , payment_method VARCHAR2(30)
    , currency       VARCHAR2(3)
    , amount         NUMBER
    ) PARTITION BY LIST (currency)
    SUBPARTITION BY RANGE (amount)
    ( PARTITION p_eur VALUES ('EUR')
      ( SUBPARTITION p_eur_small VALUES LESS THAN (8)
      , SUBPARTITION p_eur_medium VALUES LESS THAN (80)
      , SUBPARTITION p_eur_high VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_gbp VALUES ('GBP')
      ( SUBPARTITION p_gbp_small VALUES LESS THAN (5)
      , SUBPARTITION p_gbp_medium VALUES LESS THAN (50)
      , SUBPARTITION p_gbp_high VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_aud_nzd_chf VALUES ('AUD','NZD','CHF')
      ( SUBPARTITION p_aud_nzd_chf_small VALUES LESS THAN (12)
      , SUBPARTITION p_aud_nzd_chf_medium VALUES LESS THAN (120)
      , SUBPARTITION p_aud_nzd_chf_high VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_jpy VALUES ('JPY')
      ( SUBPARTITION p_jpy_small VALUES LESS THAN (1200)
      , SUBPARTITION p_jpy_medium VALUES LESS THAN (12000)
      , SUBPARTITION p_jpy_high VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_inr VALUES ('INR')
      ( SUBPARTITION p_inr_small VALUES LESS THAN (400)
      , SUBPARTITION p_inr_medium VALUES LESS THAN (4000)
      , SUBPARTITION p_inr_high VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_zar VALUES ('ZAR')
      ( SUBPARTITION p_zar_small VALUES LESS THAN (70)
      , SUBPARTITION p_zar_medium VALUES LESS THAN (700)
      , SUBPARTITION p_zar_high VALUES LESS THAN (MAXVALUE)
      )
    , PARTITION p_default VALUES (DEFAULT)
      ( SUBPARTITION p_default_small VALUES LESS THAN (10)
      , SUBPARTITION p_default_medium VALUES LESS THAN (100)
      , SUBPARTITION p_default_high VALUES LESS THAN (MAXVALUE)
      )
    ) ENABLE ROW MOVEMENT;

### 3.5.5 When to Use Interval Partitioning

Interval partitioning can be used for almost every table that is range partitioned and uses fixed intervals for new partitions.

The database automatically creates interval partitions as data for that partition is inserted. Until this happens, the interval partition exists but no segment is created for the partition.

The benefit of interval partitioning is that you do not need to create your range partitions explicitly. You should consider using interval partitioning unless you create range partitions with different intervals, or if you always set specific partition attributes when you create range partitions. You can specify a list of tablespaces in the interval definition. The database creates interval partitions in the provided list of tablespaces in a round-robin manner.

If you upgrade your application and you use range partitioning or composite range-\* partitioning, then you can easily change your existing table definition to use interval partitioning. You cannot manually add partitions to an interval-partitioned table. If you have automated the creation of new partitions, then in the future you must change your application code to prevent the explicit creation of range partitions.

The following SQL statement initiates a change from range partitioning to using monthly interval partitioning on the `sales` table.

    ALTER TABLE sales SET INTERVAL (NUMTOYMINTERVAL(1,'MONTH'));

You cannot use interval partitioning with reference partitioned tables.

Serializable transactions do not work with interval partitioning. Inserting data into a partition of an interval partitioned table that does not have a segment yet causes an error.

### 3.5.6 When to Use Reference Partitioning

Reference partitioning is useful in certain situations.

Reference partitioning is useful in the following scenarios:

- If you have denormalized, or would denormalize, a column from a master table into a child table to get partition pruning benefits on both tables.

  For example, your `orders` table stores the `order_date`, but the `order_items` table, which stores one or more items for each order, does not. To get good performance for historical analysis of orders data, you would traditionally duplicate the `order_date` column in the `order_items` table to use partition pruning on the `order_items` table.

  You should consider reference partitioning in such a scenario and avoid having to duplicate the `order_date` column. Queries that join both tables and use a predicate on `order_date` automatically benefit from partition pruning on both tables.

- If two large tables are joined frequently, then the tables are not partitioned on the join key, but you want to take advantage of partition-wise joins.

  Reference partitioning implicitly enables full partition-wise joins.

- If data in multiple tables has a related life cycle, then reference partitioning can provide significant manageability benefits.

  Partition management operations against the master table are automatically cascaded to its descendents. For example, when you add a partition to the master table, that addition is automatically propagated to all its descendents.

  To use reference partitioning, you must enable and enforce the foreign key relationship between the master table and the reference table in place. You can cascade reference-partitioned tables.

  The primary key-foreign key relationship must be enabled all the time and cannot be disabled. Also the relationship cannot be declared as deferred. These are mandatory requirements because the enabled primary key-foreign relationship is required to determine the data placement for the child tables.

### 3.5.7 When to Partition on Virtual Columns

Partitioning on virtual columns provides more flexibility to partition on a derived column.

Virtual column partitioning enables you to partition on an expression, which may use data from other columns, and perform calculations with these columns. PL/SQL function calls are not supported in virtual column definitions that are to be used as a partitioning key.

Virtual column partitioning supports all partitioning methods, plus performance and manageability features. To get partition pruning benefits, consider using virtual columns if tables are frequently accessed using a predicate that is not directly captured in a column, but can be derived. Traditionally, to get partition pruning benefits, you would have to add a separate column to capture and calculate the correct value and ensure the column is always populated correctly to ensure correct query retrieval.

Example 3-14 shows a `car_rentals` table. The customer's confirmation number contains a two-character country name as the location where the rental car is picked up. Rental car analyses usually evaluate regional patterns, so it makes sense to partition by country.

In this example, the column `country` is defined as a virtual column derived from the confirmation number. The virtual column does not require any storage. As the example illustrates, row movement is supported with virtual columns. The database migrates a row to a different partition if the virtual column evaluates to a different value in another partition.

Example 3-14 Creating a table with virtual columns for partitioning

    CREATE TABLE car_rentals
    ( id                  NUMBER NOT NULL
     , customer_id         NUMBER NOT NULL
     , confirmation_number VARCHAR2(12) NOT NULL
     , car_id              NUMBER
     , car_type            VARCHAR2(10)
     , requested_car_type  VARCHAR2(10) NOT NULL
     , reservation_date    DATE NOT NULL
     , start_date          DATE NOT NULL
     , end_date            DATE
     , country as (substr(confirmation_number,9,2))
    ) PARTITION BY LIST (country)
    SUBPARTITION BY HASH (customer_id)
    SUBPARTITIONS 16
    ( PARTITION north_america VALUES ('US','CA','MX')
     , PARTITION south_america VALUES ('BR','AR','PE')
     , PARTITION europe VALUES ('GB','DE','NL','BE','FR','ES','IT','CH')
     , PARTITION apac VALUES ('NZ','AU','IN','CN')
    ) ENABLE ROW MOVEMENT;

### 3.5.8 Considerations When Using Read-Only Tablespaces

Review these considerations when using read-only tables.

When a referential integrity constraint is defined between parent and child tables, an index is defined on the foreign key, and the tablespace in which that index resides is made read-only, then the integrity check for the constraint is implemented in SQL and not through consistent read buffer access.

The implication of this is if the child is partitioned and if only some child partitions have their indexes in read-only tablespaces and if an insert is made into one nonread-only child segment, then a TM enqueue is acquired on the child table in SX mode.

SX mode is incompatible with S requests, so that if you try to insert into the parent, it is blocked because that insert attempts to acquire an S TM enqueue against the child.
