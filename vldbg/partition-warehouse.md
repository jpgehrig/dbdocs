Partitioning features can improve performance in a data warehouse environment.

This chapter describes the partitioning features that significantly enhance data access and improve overall application performance. Improvements with partitioning are especially true for applications that access tables and indexes with millions of rows and many gigabytes of data, as found in a data warehouse environment. Data warehouses often contain large tables and require techniques for managing these large tables and for providing good query performance across these large tables.

This chapter contains the following sections:

- What Is a Data Warehouse?

- Scalability in a Data Warehouse

- Partitioning for Performance in a Data Warehouse

- Manageability in a Data Warehouse

### 6.1 What Is a Data Warehouse?

A data warehouse is a relational database that is designed for query and analysis rather than for transaction processing.

A data warehouse usually contains historical data derived from transaction data, but can include data from other sources. Data warehouses separate analysis workload from transaction workload and enable an organization to consolidate data from several sources.

In addition to a relational database, a data warehouse environment can include an extraction, transformation, and loading (ETL) solution, analytical processing and data mining capabilities, client analysis tools, and other applications that manage the process of gathering data and delivering it to business users.

**See Also:**

[Oracle Database Data Warehousing Guide](../dwhsg/introduction-data-warehouse-concepts.md)

### 6.2 Scalability in a Data Warehouse

Partitioning helps to scale a data warehouse by dividing database objects into smaller pieces, enabling access to smaller, more manageable objects. Having direct access to smaller objects addresses the scalability requirements of data warehouses.

This section contains the following topics:

- Bigger Databases

- Bigger Individual Tables: More Rows in Tables

- More Users Querying the System

- More Complex Queries

#### 6.2.1 Bigger Databases

The ability to split a large database object into smaller pieces transparently simplifies efficient management of very large databases.

You can identify and manipulate individual partitions and subpartitions to manage large database objects. Consider the following advantages of partitioned objects:

- Backup and recovery can be performed on a low level of granularity to manage the size of the database.

- Part of a database object can be placed in compressed storage while other parts can remain uncompressed.

- Partitioning can store data transparently on different storage tiers to lower the cost of retaining vast amounts of data. For more information, refer to [Managing and Maintaining Time-Based Information](time-based-info.md).

#### 6.2.2 Bigger Individual Tables: More Rows in Tables

It takes longer to scan a big table than it takes to scan a small table. Queries against partitioned tables may access one or more partitions that are small in contrast to the total size of the table.

Similarly, queries may take advantage of partition elimination on indexes. It takes less time to read a smaller portion of an index from disk than to read the entire index. Index structures that share the partitioning strategy with the table, such as local partitioned indexes, can be accessed and maintained on a partition-by-partition basis.

The database can take advantage of the distinct data sets in separate partitions if you use parallel execution to speed up queries, DML, and DDL statements. Individual parallel execution servers can work on their own data sets, identified by the partition boundaries.

#### 6.2.3 More Users Querying the System

With partitioning, users are more likely to query on isolated and smaller data sets.

Consequently, the database can return results faster than if all users queried the same and much larger data sets. Data contention is less likely.

#### 6.2.4 More Complex Queries

You can perform complex queries faster using smaller data sets.

If smaller data sets are being accessed, then complex calculations are more likely to be processed in memory, which is beneficial from a performance perspective and reduces the application's I/O requirements. A larger data set may have to be written to the temporary tablespace to complete a query, in which case additional I/O operations against the database storage occurs.

### 6.3 Partitioning for Performance in a Data Warehouse

Good performance is a requirement for a successful data warehouse.

Analyses run against the database should return within a reasonable amount of time, even if the queries access large amounts of data in tables that are terabytes in size. Partitioning increases the speed of data access and application processing, which results in successful data warehouses that are not prohibitively expensive.

This section contains the following topics:

- Partition Pruning in a Data Warehouse

- Partition-Wise Joins in a Data Warehouse

- Indexes and Partitioned Indexes in a Data Warehouse

- Materialized Views and Partitioning in a Data Warehouse

#### 6.3.1 Partition Pruning in a Data Warehouse

Partition pruning is an essential performance feature for data warehouses.

In partition pruning, the optimizer analyzes `FROM` and `WHERE` clauses in SQL statements to eliminate unneeded partitions when building the partition access list. As a result, Oracle Database performs operations only on those partitions that are relevant to the SQL statement.

Partition pruning dramatically reduces the amount of data retrieved from disk and shortens processing time, thus improving query performance and optimizing resource utilization.

This section contains the following topics:

- Basic Partition Pruning Techniques

- Advanced Partition Pruning Techniques

For more information about partition pruning and the difference between static and dynamic partition pruning, refer to [Partitioning for Availability, Manageability, and Performance](partition-availability.md).

##### 6.3.1.1 Basic Partition Pruning Techniques

The optimizer uses a wide variety of predicates for pruning.

The three predicate types, equality, range, and `IN`-list, are the predicates most commonly used for partition pruning. As an example, consider the following query:

    SELECT SUM(amount_sold) day_sales
    FROM sales
    WHERE time_id = TO_DATE('02-JAN-1998', 'DD-MON-YYYY');

Because there is an equality predicate on the partitioning column of `sales`, the query is pruned down to a single predicate and this is reflected in the following execution plan:

    -----------------------------------------------------------------------------------------------
    |  Id | Operation                | Name  | Rows| Bytes | Cost (%CPU)| Time     |Pstart| Pstop |
    -----------------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT         |       |     |       | 21 (100)   |          |      |       |
    |   1 |  SORT AGGREGATE          |       | 1   | 13    |            |          |      |       |
    |   2 |   PARTITION RANGE SINGLE |       | 485 | 6305  | 21 (10)    | 00:00:01 | 5    | 5     |
    | * 3 |    TABLE ACCESS FULL     | SALES | 485 | 6305  | 21 (10)    | 00:00:01 | 5    | 5     |
    -----------------------------------------------------------------------------------------------
    Predicate Information (identified by operation id):
    ---------------------------------------------------
      3 - filter("TIME_ID"=TO_DATE('1998-01-02 00:00:00', 'yyyy-mm-dd hh24:mi:ss'))

Similarly, a range or an `IN`-list predicate on the `time_id` column and the optimizer would be used to prune to a set of partitions. The partitioning type plays a role in which predicates can be used. Range predicates cannot be used for pruning on hash partitioned tables, but they can be used for all other partitioning strategies. However, on list-partitioned tables, range predicates may not map to a contiguous set of partitions. Equality and `IN`-list predicates can prune with all the partitioning methods.

##### 6.3.1.2 Advanced Partition Pruning Techniques

Oracle Database pruning feature effectively handles more complex predicates or SQL statements that involve partitioned tables.

A common situation is when a partitioned table is joined to the subset of another table, limited by a `WHERE` condition. For example, consider the following query:

    SELECT t.day_number_in_month, SUM(s.amount_sold)
      FROM sales s, times t
      WHERE s.time_id = t.time_id
        AND t.calendar_month_desc='2000-12'
      GROUP BY t.day_number_in_month;

If the database performed a nested loop join with `times` table on the right-hand side, then the query would access only the partition corresponding to this row from the `times` table, so pruning would implicitly take place. But, if the database performed a hash or sort merge join, this would not be possible. If the table with the `WHERE` predicate is relatively small compared to the partitioned table, and the expected reduction of records or partitions for the partitioned table is significant, then the database performs dynamic partition pruning using a recursive subquery. The decision whether to invoke subquery pruning is an internal cost-based decision of the optimizer.

A sample execution plan using a hash join operation would look like the following:

    --------------------------------------------------------------------------------------------------
    | Id| Operation                    |  Name |  Rows | Bytes| Cost (%CPU)|  Time  | Pstart | Pstop |
    --------------------------------------------------------------------------------------------------
    |  0| SELECT STATEMENT             |       |       |      | 761 (100)  |        |        |       |
    |  1|  HASH GROUP BY               |       |    20 | 640  | 761 (41)   |00:00:10|        |       |
    |* 2|   HASH JOIN                  |       | 19153 | 598K | 749 (40)   |00:00:09|        |       |
    |* 3|    TABLE ACCESS FULL         | TIMES |    30 |  570 |  17 (6)    |00:00:01|        |       |
    |  4|     PARTITION RANGE SUBQUERY |       |  918K | 11M  |   655 (33) |00:00:08| KEY(SQ)|KEY(SQ)|
    |  5|      TABLE ACCESS FULL       | SALES |   918 | 11M  |   655 (33) |00:00:08| KEY(SQ)|KEY(SQ)|
    --------------------------------------------------------------------------------------------------
    Predicate Information (identified by operation id):
    ---------------------------------------------------
    PLAN_TABLE_OUTPUT
    --------------------------------------------------------------------------------------------------
      2 - access("S"."TIME_ID"="T"."TIME_ID")
      3 - filter("T"."CALENDAR_MONTH_DESC"='2000-12')

This execution plan shows that dynamic partition pruning occurred on the `sales` table using a subquery, as shown by the `KEY(SQ)` value in the `PSTART` and `PSTOP` columns.

The following is an example of advanced pruning using an `OR` predicate.

    SELECT p.promo_name promo_name, (s.profit - p.promo_cost) profit
    FROM
       promotions p,
       ( SELECT
          sales.promo_id,
          SUM(sales.QUANTITY_SOLD * (costs.UNIT_PRICE - costs.UNIT_COST)) profit
       FROM
          sales, costs
       WHERE
          ((sales.time_id BETWEEN TO_DATE('01-JAN-1998','DD-MON-YYYY',
                      'NLS_DATE_LANGUAGE = American') AND
          TO_DATE('01-JAN-1999','DD-MON-YYYY', 'NLS_DATE_LANGUAGE = American')
       OR
          (sales.time_id BETWEEN TO_DATE('01-JAN-2001','DD-MON-YYYY',
                      'NLS_DATE_LANGUAGE = American') AND
          TO_DATE('01-JAN-2002','DD-MON-YYYY', 'NLS_DATE_LANGUAGE = American')))
          AND sales.time_id = costs.time_id
          AND sales.prod_id = costs.prod_id)
       GROUP BY
          sales.promo_id) s
    WHERE s.promo_id = p.promo_id
    ORDER BY profit
    DESC;

This query joins the `sales` and `costs` tables. The `sales` table is partitioned by range on the column `time_id`. One condition in the query is two predicates on `time_id`, which are combined with an `OR` operator. This `OR` predicate is used to prune the partitions in the `sales` table and a single join between the `sales` and `costs` table is performed. The execution plan is as follows:

    --------------------------------------------------------------------------------------------------
    | Id| Operation               |  Name    |Rows |Bytes |TmpSp|Cost(%CPU)| Time    | Pstart| Pstop |
    --------------------------------------------------------------------------------------------------
    |  0| SELECT STATEMENT        |          | 4   |  200 |     | 3556 (14)| 00:00:43|       |       |
    |  1|  SORT ORDER BY          |          | 4   |  200 |     | 3556 (14)| 00:00:43|       |       |
    |* 2|   HASH JOIN             |          | 4   |  200 |     | 3555 (14)| 00:00:43|       |       |
    |  3|    TABLE ACCESS FULL    |PROMOTIONS| 503 | 16599|     |    16 (0)| 00:00:01|       |       |
    |  4|    VIEW                 |          |   4 |   68 |     | 3538 (14)| 00:00:43|       |       |
    |  5|     HASH GROUP BY       |          |   4 |  164 |     | 3538 (14)| 00:00:43|       |       |
    |  6|      PARTITION RANGE OR |          | 314K|   12M|     |  3321 (9)| 00:00:40|KEY(OR)|KEY(OR)|
    |* 7|       HASH JOIN         |          | 314K|   12M| 440K|  3321 (9)| 00:00:40|       |       |
    |* 8|        TABLE ACCESS FULL| SALES    | 402K| 7467K|     |  400 (39)| 00:00:05|KEY(OR)|KEY(OR)|
    |  9| TABLE ACCESS FULL       | COSTS    |82112| 1764K|     |   77 (24)| 00:00:01|KEY(OR)|KEY(OR)|
    --------------------------------------------------------------------------------------------------
    Predicate Information (identified by operation id):
    ---------------------------------------------------
      2 - access("S"."PROMO_ID"="P"."PROMO_ID")
      7 - access("SALES"."TIME_ID"="COSTS"."TIME_ID" AND "SALES"."PROD_ID"="COSTS"."PROD_ID")
      8 - filter("SALES"."TIME_ID"<=TO_DATE('1999-01-01 00:00:00', 'yyyy-mm-dd hh24:mi:ss') AND
          "SALES"."TIME_ID">=TO_DATE('1998-01-01 00:00:00', 'yyyy-mm-dd hh24:mi:ss') OR
          "SALES"."TIME_ID">=TO_DATE('2001-01-01 00:00:00', 'yyyy-mm-dd hh24:mi:ss') AND
          "SALES"."TIME_ID"<=TO_DATE('2002-01-01 00:00:00', 'yyyy-mm-dd hh24:mi:ss'))

The database also does additional pruning when a column is range-partitioned on multiple columns. As long as the database can guarantee that a particular predicate cannot be satisfied in a particular partition, the partition is skipped. This allows the database to optimize cases where there are range predicates on multiple columns or in the case where there are no predicates on a prefix of the partitioning columns.

For tips on partition pruning, refer to [Partition Pruning Tips](partition-pruning.md).

#### 6.3.2 Partition-Wise Joins in a Data Warehouse

Partition-wise joins reduce query response time by minimizing the amount of data exchanged among parallel execution servers when joins execute in parallel.

Using partition-wise joins significantly reduces response time and improves the use of both CPU and memory resources. Parallel partition-wise joins are used commonly for processing large joins efficiently and fast. Partition-wise joins can be full or partial. Oracle Database decides which type of join to use.

In addition to parallel partition-wise joins, queries using the `SELECT` `DISTINCT` clause and SQL window functions can perform parallel partition-wise operations.

This section contains the following topics:

- Full Partition-Wise Joins

- Partial Partition-Wise Joins

- Benefits of Partition-Wise Joins

- Performance Considerations for Parallel Partition-Wise Joins

**See Also:**

- [Partition-Wise Operations](partition-wise-joins.md) for additional information about partition-wise operations

- [Oracle Database Data Warehousing Guide](../dwhsg/data-warehouse-optimizations-techniques.md) for information about data warehousing and optimization techniques

##### 6.3.2.1 Full Partition-Wise Joins

Full partition-wise joins can occur if two tables that are co-partitioned on the same key are joined in a query.

The tables can be co-partitioned at the partition level, or at the subpartition level, or at a combination of partition and subpartition levels. Reference partitioning is an easy way to guarantee co-partitioning. Full partition-wise joins can be executed serially and in parallel.

For more information about partition-wise joins, refer to [Partitioning for Availability, Manageability, and Performance](partition-availability.md).

The following example shows a full partition-wise join on the `orders` and `order_items` tables, in which the `order_items` table is reference-partitioned.

    CREATE TABLE orders
    ( order_id     NUMBER(12) NOT NULL
    , order_date   DATE NOT NULL
    , order_mode   VARCHAR2(8)
    , order_status VARCHAR2(1)
    , CONSTRAINT orders_pk PRIMARY KEY (order_id)
    )
    PARTITION BY RANGE (order_date)
    ( PARTITION p_before_jan_2006 VALUES LESS THAN (TO_DATE('01-JAN-2006','dd-MON-yyyy'))
    , PARTITION p_2006_jan VALUES LESS THAN (TO_DATE('01-FEB-2006','dd-MON-yyyy'))
    , PARTITION p_2006_feb VALUES LESS THAN (TO_DATE('01-MAR-2006','dd-MON-yyyy'))
    , PARTITION p_2006_mar VALUES LESS THAN (TO_DATE('01-APR-2006','dd-MON-yyyy'))
    , PARTITION p_2006_apr VALUES LESS THAN (TO_DATE('01-MAY-2006','dd-MON-yyyy'))
    , PARTITION p_2006_may VALUES LESS THAN (TO_DATE('01-JUN-2006','dd-MON-yyyy'))
    , PARTITION p_2006_jun VALUES LESS THAN (TO_DATE('01-JUL-2006','dd-MON-yyyy'))
    , PARTITION p_2006_jul VALUES LESS THAN (TO_DATE('01-AUG-2006','dd-MON-yyyy'))
    , PARTITION p_2006_aug VALUES LESS THAN (TO_DATE('01-SEP-2006','dd-MON-yyyy'))
    , PARTITION p_2006_sep VALUES LESS THAN (TO_DATE('01-OCT-2006','dd-MON-yyyy'))
    , PARTITION p_2006_oct VALUES LESS THAN (TO_DATE('01-NOV-2006','dd-MON-yyyy'))
    , PARTITION p_2006_nov VALUES LESS THAN (TO_DATE('01-DEC-2006','dd-MON-yyyy'))
    , PARTITION p_2006_dec VALUES LESS THAN (TO_DATE('01-JAN-2007','dd-MON-yyyy'))
    )
    PARALLEL;

    CREATE TABLE order_items
    ( order_id NUMBER(12) NOT NULL
    , product_id NUMBER NOT NULL
    , quantity NUMBER NOT NULL
    , sales_amount NUMBER NOT NULL
    , CONSTRAINT order_items_orders_fk FOREIGN KEY (order_id) REFERENCES
    orders(order_id)
    )
    PARTITION BY REFERENCE (order_items_orders_fk)
    PARALLEL;

A typical data warehouse query would scan a large amount of data. In the underlying execution plan, the columns `Rows`, `Bytes`, `Cost (%CPU)`, `Time`, and `TQ` have been removed.

    EXPLAIN PLAN FOR
    SELECT o.order_date
    , sum(oi.sales_amount) sum_sales
    FROM orders o
    , order_items oi
    WHERE o.order_id = oi.order_id
    AND o.order_date BETWEEN TO_DATE('01-FEB-2006','DD-MON-YYYY')
                         AND TO_DATE('31-MAY-2006','DD-MON-YYYY')
    GROUP BY o.order_id
    , o.order_date
    ORDER BY o.order_date;

    ---------------------------------------------------------------------------------------------
    | Id  | Operation                         | Name        | Pstart| Pstop |IN-OUT| PQ Distrib |
    ---------------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT                  |             |       |       |      |            |
    |   1 |  PX COORDINATOR                   |             |       |       |      |            |
    |   2 |   PX SEND QC (ORDER)              | :TQ10001    |       |       | P->S | QC (ORDER) |
    |   3 |    SORT GROUP BY                  |             |       |       | PCWP |            |
    |   4 |     PX RECEIVE                    |             |       |       | PCWP |            |
    |   5 |      PX SEND RANGE                | :TQ10000    |       |       | P->P | RANGE      |
    |   6 |       SORT GROUP BY               |             |       |       | PCWP |            |
    |   7 |        PX PARTITION RANGE ITERATOR|             |     3 |     6 | PCWC |            |
    |*  8 |         HASH JOIN                 |             |       |       | PCWP |            |
    |*  9 |          TABLE ACCESS FULL        | ORDERS      |     3 |     6 | PCWP |            |
    |  10 |          TABLE ACCESS FULL        | ORDER_ITEMS |     3 |     6 | PCWP |            |
    ---------------------------------------------------------------------------------------------

    Predicate Information (identified by operation id):
    ---------------------------------------------------

       8 - access("O"."ORDER_ID"="OI"."ORDER_ID")
       9 - filter("O"."ORDER_DATE"<=TO_DATE(' 2006-05-31 00:00:00', 'syyyy-mm-dd hh24:mi:ss'))

##### 6.3.2.2 Partial Partition-Wise Joins

Oracle Database can perform partial partition-wise joins only in parallel.

Unlike full partition-wise joins, partial partition-wise joins require you to partition only one table on the join key, not both tables. The partitioned table is referred to as the reference table. The other table may or may not be partitioned. Partial partition-wise joins are more common than full partition-wise joins.

To execute a partial partition-wise join, the database dynamically partitions or repartitions the other table based on the partitioning of the reference table. After the other table is repartitioned, the execution is similar to a full partition-wise join.

The following example shows a call detail records table, `cdrs`, in a typical data warehouse scenario. The table is interval-hash partitioned.

    CREATE TABLE cdrs
    ( id                 NUMBER
    , cust_id            NUMBER
    , from_number        VARCHAR2(20)
    , to_number          VARCHAR2(20)
    , date_of_call       DATE
    , distance           VARCHAR2(1)
    , call_duration_in_s NUMBER(4)
    ) PARTITION BY RANGE(date_of_call)
    INTERVAL (NUMTODSINTERVAL(1,'DAY'))
    SUBPARTITION BY HASH(cust_id)
    SUBPARTITIONS 16
    (PARTITION p0 VALUES LESS THAN (TO_DATE('01-JAN-2005','dd-MON-yyyy')))
    PARALLEL;

The `cdrs` table is joined with the nonpartitioned `callers` table on the `cust_id` column to rank the customers who spent the most time making calls.

    EXPLAIN PLAN FOR
    SELECT c.cust_id
    ,      c.cust_last_name
    ,      c.cust_first_name
    ,      AVG(call_duration_in_s)
    ,      COUNT(1)
    ,      DENSE_RANK() OVER
           (ORDER BY (AVG(call_duration_in_s) * COUNT(1)) DESC) ranking
    FROM   callers c
    ,      cdrs    cdr
    WHERE cdr.cust_id = c.cust_id
    AND cdr.date_of_call BETWEEN TO_DATE('01-JAN-2006','dd-MON-yyyy')
                             AND TO_DATE('31-DEC-2006','dd-MON-yyyy')
    GROUP BY c.cust_id
    , c.cust_last_name
    , c.cust_first_name
    ORDER BY ranking;

The execution plans shows a partial partition-wise join. In the plan, the columns `Rows`, `Bytes`, `Cost (%CPU)`, `Time`, and `TQ` have been removed.

    --------------------------------------------------------------------------------------------
    | Id  | Operation                           | Name     | Pstart| Pstop |IN-OUT| PQ Distrib |
    --------------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT                    |          |       |       |      |            |
    |   1 |  WINDOW NOSORT                      |          |       |       |      |            |
    |   2 |   PX COORDINATOR                    |          |       |       |      |            |
    |   3 |    PX SEND QC (ORDER)               | :TQ10002 |       |       | P->S | QC (ORDER) |
    |   4 |     SORT ORDER BY                   |          |       |       | PCWP |            |
    |   5 |      PX RECEIVE                     |          |       |       | PCWP |            |
    |   6 |       PX SEND RANGE                 | :TQ10001 |       |       | P->P | RANGE      |
    |   7 |        HASH GROUP BY                |          |       |       | PCWP |            |
    |*  8 |         HASH JOIN                   |          |       |       | PCWP |            |
    |   9 |          PART JOIN FILTER CREATE    | :BF0000  |       |       | PCWP |            |
    |  10 |           BUFFER SORT               |          |       |       | PCWC |            |
    |  11 |            PX RECEIVE               |          |       |       | PCWP |            |
    |  12 |             PX SEND PARTITION (KEY) | :TQ10000 |       |       | S->P | PART (KEY) |
    |  13 |              TABLE ACCESS FULL      | CALLERS  |       |       |      |            |
    |  14 |          PX PARTITION RANGE ITERATOR|          |   367 |   731 | PCWC |            |
    |  15 |           PX PARTITION HASH ALL     |          |     1 |    16 | PCWC |            |
    |* 16 |            TABLE ACCESS FULL        | CDRS     |  5857 | 11696 | PCWP |            |
    --------------------------------------------------------------------------------------------

    Predicate Information (identified by operation id):
    ---------------------------------------------------

       8 - access("CDR"."CUST_ID"="C"."CUST_ID")
      16 - filter("CDR"."DATE_OF_CALL">=TO_DATE(' 2006-01-01 00:00:00', 'syyyy-mm-dd
    hh24:mi:ss') AND "CDR"."DATE_OF_CALL"<=TO_DATE('
                  2006-12-31 00:00:00', 'syyyy-mm-dd hh24:mi:ss'))

##### 6.3.2.3 Benefits of Partition-Wise Joins

Partition-wise joins offers several benefits.

These benefits are described in the following topics:

- Reduction of Communications Overhead

- Reduction of Memory Requirements

###### 6.3.2.3.1 Reduction of Communications Overhead

When executed in parallel, partition-wise joins reduce communications overhead.

This reduction, in the default case, occurs because parallel execution of a join operation by a set of parallel execution servers requires the redistribution of each table on the join column into disjoint subsets of rows. These disjoint subsets of rows are then joined pair-wise by a single parallel execution server.

The database can avoid redistributing the partitions because the two tables are partitioned on the join column. This functionality enables each parallel execution server to join a pair of matching partitions. This improved performance from using parallel execution is even more noticeable in Oracle Real Application Clusters configurations with internode parallel execution.

Partition-wise joins dramatically reduce interconnect traffic. Using this feature is key for large decision support systems (DSS) configurations that use Oracle Real Application Clusters. Currently, most Oracle Real Application Clusters platforms, such as massively parallel processing (MPP) and symmetric multiprocessing (SMP) clusters, provide limited interconnect bandwidths compared to their processing powers. Ideally, interconnect bandwidth should be comparable to disk bandwidth, but this is seldom the case. Consequently, most join operations in Oracle Real Application Clusters experience high interconnect latencies without parallel execution of partition-wise joins.

###### 6.3.2.3.2 Reduction of Memory Requirements

Partition-wise joins require less memory than the equivalent join operation of the complete data set of the tables being joined.

For serial joins, the join is performed at the same time on a pair of matching partitions. If data is evenly distributed across partitions, then the memory requirement is divided by the number of partitions and there is no skew to the data distribution among the parallel servers.

For parallel joins, memory requirements depend on the number of partition pairs that are joined in parallel. For example, if the degree of parallelism is 20 and the number of partitions is 100, then 5 times less memory is required because only 20 joins of two partitions each are performed at the same time. The fact that partition-wise joins require less memory has a direct beneficial effect on performance. For example, the join probably does not need to write blocks to disk during the build phase of a hash join.

##### 6.3.2.4 Performance Considerations for Parallel Partition-Wise Joins

The optimizer weighs the advantages and disadvantages when deciding whether to use partition-wise joins.

The optimizer chooses whether to use partition-wise joins based on the following:

- In range partitioning where partition sizes differ, data skew increases response time; some parallel execution servers take longer than others to finish their joins. Oracle recommends the use of hash partitioning and subpartitioning to enable partition-wise joins because hash partitioning, if the number of partitions is a power of two, limits the risk of skew. Ideally, the hash partitioning key is unique to minimize the risk of skew.

- The number of partitions used for partition-wise joins should, if possible, be a multiple of the number of query servers. With a degree of parallelism of 16, for example, you can have 16, 32, or even 64 partitions. If there is an odd number of partitions, then some parallel execution servers are used less than others. For example, if there are 17 evenly distributed partition pairs, only one pair works on the last join, while the other pair has to wait. This is because, in the beginning of the execution, each parallel execution server works on a different partition pair. After this first phase, only one pair remains. Thus, a single parallel execution server joins this remaining pair while all other parallel execution servers are idle.

In some situations, parallel joins can cause remote I/O operations. For example, on Oracle Real Application Clusters environments running on MPP configurations, if a pair of matching partitions is not collocated on the same node, a partition-wise join requires extra internode communication due to remote I/O. This is because Oracle Database must transfer at least one partition to the node where the join is performed. In this case, it is better to explicitly redistribute the data than to use a partition-wise join.

#### 6.3.3 Indexes and Partitioned Indexes in a Data Warehouse

Indexes are optional structures associated with tables that allow SQL statements to execute more quickly against a table.

Even though table scans are very common in many data warehouses, indexes can often speed up queries.

Both B-tree and bitmap indexes can be created as local indexes on a partitioned table, in which case they inherit the table's partitioning strategy. B-tree indexes can be created as global partitioned indexes on partitioned and nonpartitioned tables.

This section contains the following topics:

- Local Partitioned Indexes

- Nonpartitioned Indexes

- Global Partitioned Indexes

For more information about partitioned indexes, refer to [Partitioning for Availability, Manageability, and Performance](partition-availability.md).

##### 6.3.3.1 Local Partitioned Indexes

In a local index, all keys in a particular index partition refer only to rows stored in a single underlying table partition.

A local index is equipartitioned with the underlying table. Oracle Database partitions the index on the same columns as the underlying table, creates the same number of partitions or subpartitions, and gives them the same partition boundaries as corresponding partitions of the underlying table.

Oracle Database also maintains the index partitioning automatically when partitions in the underlying table are added, dropped, merged, or split, or when hash partitions or subpartitions are added or coalesced. This ensures that the index remains equipartitioned with the table.

For data warehouse applications, local nonprefixed indexes can improve performance because many index partitions can be scanned in parallel by range queries on the index key. The following example creates a local B-tree index on a partitioned `customers_dw` table:

    CREATE INDEX cust_last_name_ix
     ON customers_dw(last_name) LOCAL
     PARALLEL NOLOGGING ;

Bitmap indexes use a very efficient storage mechanism for low cardinality columns. Bitmap indexes are used in data warehouses, and especially common in data warehouses that implement star schemas. A single star schema consists of a central large fact table and multiple smaller dimension tables that describe the data in the fact table.

For example, consider a `sales` table that is a fact table, described by dimension tables `customers`, `products`, `promotions`, `times`, and `channels`. Bitmap indexes enable the star transformation, an optimization for fast query retrieval against star or star look-a-like schemas.

Fact table foreign key columns are ideal candidates for bitmap indexes, because generally there are few distinct values relative to the total number of rows. Fact tables are often range or range-\* partitioned, in which case you must create local bitmap indexes. Global bitmap indexes on partitioned tables are not supported.

The following example creates a local partitioned bitmap index on the `sales` table:

    CREATE BITMAP INDEX prod_id_ix
    ON sales(prod_id) LOCAL
    PARALLEL NOLOGGING;

**See Also:**

[Oracle Database Data Warehousing Guide](../dwhsg/data-warehouse-optimizations-techniques.md) for more information about the star transformation

##### 6.3.3.2 Nonpartitioned Indexes

You can create nonpartitioned indexes on nonpartitioned and partitioned tables.

Nonpartitioned indexes are primarily used on nonpartitioned tables in data warehouse environments and in general to enforce uniqueness if the status of a unique constraint is required to be enforced in a data warehousing environment. You can use a nonpartitioned global index on a partitioned table to enforce a primary or unique key. A nonpartitioned (global) index can be useful for queries that commonly retrieve very few rows based on equality predicates or `IN`-list on a column or set of columns that is not included in the partitioning key. In those cases, it can be faster to scan a single index than to scan many index partitions to find all matching rows.

Unique indexes on columns other than the partitioning columns must be global because unique local nonprefixed indexes whose keys do not contain the partitioning keys are not supported. Unique keys are not always enforced in data warehouses due to the controlled data load processes and the performance cost of enforcing the unique constraint. Global indexes can grow very large on tables with billions of rows.

The following example creates a global unique index on the `sales` table:

    CREATE UNIQUE INDEX sales_unique_ix
      ON sales(cust_id, prod_id, promo_id, channel_id, time_id)
      PARALLEL NOLOGGING;

Very few queries benefit from this index. In systems with a very limited data load window, consider not creating and maintaining it.

##### 6.3.3.3 Global Partitioned Indexes

You can create global partitioned indexes on nonpartitioned and partitioned tables.

In a global partitioned index, the keys in a particular index partition may refer to rows stored in multiple underlying table partitions or subpartitions. A global index can be range or hash partitioned, though it can be defined on any type of partitioned table.

A global index is created by specifying the `GLOBAL` attribute. The database administrator is responsible for defining the initial partitioning of a global index at creation and for maintaining the partitioning over time. Index partitions can be merged or split as necessary.

Global indexes can be useful if there is a class of queries that uses an access path to the table to retrieve a few rows through an index, and by partitioning the index you can eliminate large portions of the index for the majority of its queries. On a partitioned table, you would consider a global partitioned index if the column or columns included to achieve partition pruning do not include the table partitioning key.

The following example creates a global hash partitioned index on the `sales` table:

    CREATE INDEX cust_id_prod_id_global_ix
    ON sales(cust_id,prod_id)
    GLOBAL PARTITION BY HASH (cust_id)
    ( PARTITION p1 TABLESPACE tbs1
    , PARTITION p2 TABLESPACE tbs2
    , PARTITION p3 TABLESPACE tbs3
    , PARTITION p4 TABLESPACE tbs4
    )
    PARALLEL NOLOGGING;

#### 6.3.4 Materialized Views and Partitioning in a Data Warehouse

One technique employed in data warehouses to improve performance is the creation of summaries. Summaries are special types of aggregate views that improve query execution times by precalculating expensive joins and aggregation operations before execution and storing the results in a table in the database.

For example, you can create a summary table to contain the sums of sales by region and by product.

The summaries or aggregates that are referred to in this guide and in literature on data warehousing are created in Oracle Database using a schema object called a materialized view. Materialized views in a data warehouse speed up query performance.

The database supports transparent rewrites against materialized views, so that you do not need to modify the original queries to take advantage of precalculated results in materialized views. Instead of executing the query, the database retrieves precalculated results from one or more materialized views, performs any necessary additional operations on the data, and returns the query results.

**See Also:**

[Oracle Database Data Warehousing Guide](../dwhsg/basic-materialized-views.md) for information about data warehousing and materialized views

##### 6.3.4.1 Partitioned Materialized Views

The underlying storage for a materialized view is a table structure. You can partition materialized views like you can partition tables.

When the database rewrites a query to run against materialized views, the query can take advantage of the same performance features from which queries running against tables directly benefit. The rewritten query may eliminate materialized view partitions. If joins back to tables or with other materialized views are necessary to retrieve the query result, then the rewritten query can take advantage of partition-wise joins.

Example 6-1 shows how to create a compressed partitioned materialized view that aggregates sales results to country level. This materialized view benefits from queries that summarize sales numbers by country level or higher to subregion or region level.

Example 6-1 Creating a compressed partitioned materialized view

    CREATE MATERIALIZED VIEW country_sales
    PARTITION BY HASH (country_id)
    PARTITIONS 16
    COMPRESS FOR OLTP
    PARALLEL NOLOGGING
    ENABLE QUERY REWRITE
    AS SELECT co.country_id
    , co.country_name
    , co.country_subregion
    , co.country_region
    , sum(sa.quantity_sold) country_quantity_sold
    , sum(sa.amount_sold) country_amount_sold
    FROM sales sa
    , customers cu
    , countries co
    WHERE sa.cust_id = cu.cust_id
    AND cu.country_id = co.country_id
    GROUP BY co.country_id
    , co.country_name
    , co.country_subregion
    , co.country_region;

**See Also:**

[Oracle Database Data Warehousing Guide](../dwhsg/basic-materialized-views.md) for information about data warehousing and materialized views

### 6.4 Manageability in a Data Warehouse

Data warehouses store historical data. Important parts of a data warehouse are the data loading and purging. Partitioning is powerful technology that can help data management for data warehouses.

This section contains the following topics:

- Partition Exchange Load

- Partitioning and Indexes

- Removing Data from Tables

- Partitioning and Data Compression

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/optimizer-statistics.md) for information about collecting and managing statistics on partitioned indexes, exchanges, and tables

#### 6.4.1 Partition Exchange Load

Partitions can be added using partition exchange load (PEL).

When you use PEL, you create a separate table that looks exactly like a single partition, including the same indexes and constraints, if any. If you use a composite partitioned table, then your separate table must use a partitioning strategy that matches the subpartitioning strategy of your composite partitioned table. You can then exchange an existing table partition with this separate table. In a data load scenario, data can be loaded into the separate table. Build indexes and implement constraints on the separate table, without impacting the table users query. Then perform the PEL, which is a very low-impact transaction compared to the data load. Daily loads, with a range partition strategy by day, are common in data warehouse environments.

The following example shows a partition exchange load for the `sales` table:

    ALTER TABLE sales ADD PARTITION p_sales_jun_2007
    VALUES LESS THAN (TO_DATE('01-FEB-2007','dd-MON-yyyy'));

    CREATE TABLE sales_jun_2007 COMPRESS FOR OLTP
    AS SELECT * FROM sales WHERE 1=0;

Next, populate table `sales_jun_2007` with sales numbers for June 2007, and create the equivalent bitmap indexes and constraints that have been implemented on the `sales` table:

    CREATE BITMAP INDEX time_id_jun_2007_bix ON sales_jun_2007(time_id) NOLOGGING;
    CREATE BITMAP INDEX cust_id_jun_2007_bix ON sales_jun_2007(cust_id) NOLOGGING;
    CREATE BITMAP INDEX prod_id_jun_2007_bix ON sales_jun_2007(prod_id) NOLOGGING;
    CREATE BITMAP INDEX promo_id_jun_2007_bix ON sales_jun_2007(promo_id) NOLOGGING;
    CREATE BITMAP INDEX channel_id_jun_2007_bix ON sales_jun_2007(channel_id) NOLOGGING;

    ALTER TABLE sales_jun_2007 ADD CONSTRAINT prod_id_fk FOREIGN KEY (prod_id) REFERENCES products(prod_id);
    ALTER TABLE sales_jun_2007 ADD CONSTRAINT cust_id_fk FOREIGN KEY (cust_id) REFERENCES customers(cust_id);
    ALTER TABLE sales_jun_2007 ADD CONSTRAINT promo_id_fk FOREIGN KEY (promo_id) REFERENCES promotions(promo_id);
    ALTER TABLE sales_jun_2007 ADD CONSTRAINT time_id_fk FOREIGN KEY (time_id) REFERENCES times(time_id);
    ALTER TABLE sales_jun_2007 ADD CONSTRAINT channel_id_fk FOREIGN KEY (channel_id) REFERENCES channels(channel_id);

Next, exchange the partition:

    ALTER TABLE sales
    EXCHANGE PARTITION p_sales_jun_2007
    WITH TABLE sales_jun_2007
    INCLUDING INDEXES;

For more information about partition exchange load, refer to [Partition Administration](partition-admin.md).

#### 6.4.2 Partitioning and Indexes

Partition maintenance operations are most easily performed on local indexes.

Local indexes do not invalidate a global index when partition management takes place. Use `INCLUDING INDEXES` in the PEL statement to exchange the local indexes with the equivalent indexes on the separate table so that no index partitions get invalidated. For PEL, you can update global indexes as part of the load. Use the `UPDATE GLOBAL INDEXES` extension to the PEL statement. If an index requires updating, then the PEL takes much longer.

#### 6.4.3 Removing Data from Tables

Data warehouses commonly keep a time window of data. For example, three years of historical data is stored.

Partitioning makes it very easy to purge data from a table. You can use the `DROP PARTITION` or `TRUNCATE PARTITION` statements to purge data. Common strategies also include using a partition exchange load to unload the data from the table and replacing the partition with an empty table before dropping the partition. Archive the separate table you exchanged before emptying or dropping it.

A drop or truncate operation would invalidate a global index or a global partitioned index. Local indexes remain valid. The local index partition is dropped when you drop the table partition.

The following example shows how to drop partition `sales_1995` from the `sales` table:

    ALTER TABLE sales
     DROP PARTITION sales_1995
     UPDATE GLOBAL INDEXES PARALLEL;

#### 6.4.4 Partitioning and Data Compression

Data in a partitioned table can be compressed on a partition-by-partition basis.

Using compressed data is most efficient for data that does not change frequently. Common data warehouse scenarios often see few data changes as data ages and other scenarios only insert data. Using the partition management features, you can compress data on a partition-by-partition basis. Although Oracle Database supports compression for all DML operations, it is still more efficient to modify data in a noncompressed table.

Altering a partition to enable compression applies only to future data to be inserted into the partition. To compress the existing data in the partition, you must move the partition. Enabling compression and moving a partition can be done in a single operation.

To use table compression on partitioned tables with bitmap indexes, you must do the following before you introduce the compression attribute for the first time:

1.  Mark bitmap indexes `UNUSABLE`.

2.  Set the compression attribute.

3.  Rebuild the indexes.

The first time you make a compressed partition part of an existing, fully uncompressed partitioned table, you must either drop all existing bitmap indexes or mark them `UNUSABLE` before adding a compressed partition. This must be done regardless of whether any partition contains data. It is also independent of the operation that causes one or more compressed partitions to become part of the table. This does not apply to a partitioned table having only B-tree indexes.

The following example shows how to compress the `SALES_1995` partition in the `sales` table:

    ALTER TABLE sales
     MOVE PARTITION sales_1995
     COMPRESS FOR OLTP
     PARALLEL NOLOGGING;

If a table or a partition takes less space on disk, then the performance of large table scans in an I/O-constraint environment may improve.
