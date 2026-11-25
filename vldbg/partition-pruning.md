Partition pruning is an essential performance feature for data warehouses.

In partition pruning, the optimizer analyzes `FROM` and `WHERE` clauses in SQL statements to eliminate unneeded partitions when building the partition access list. This functionality enables Oracle Database to perform operations only on those partitions that are relevant to the SQL statement.

The following topics are discussed:

- Benefits of Partition Pruning

- Information That Can Be Used for Partition Pruning

- How to Identify Whether Partition Pruning Has Been Used

- Static Partition Pruning

- Dynamic Partition Pruning

- Partition Pruning with Zone Maps

- Partition Pruning Tips

### 3.1.1 Benefits of Partition Pruning

Partition pruning dramatically reduces the amount of data retrieved from disk and shortens processing time, thus improving query performance and optimizing resource utilization.

If you partition the index and table on different columns (with a global partitioned index), then partition pruning also eliminates index partitions even when the partitions of the underlying table cannot be eliminated.

Depending upon the actual SQL statement, Oracle Database may use static or dynamic pruning. Static pruning occurs at compile-time, with the information about the partitions accessed beforehand. Dynamic pruning occurs at run-time, meaning that the exact partitions to be accessed by a statement are not known beforehand. A sample scenario for static pruning is a SQL statement containing a `WHERE` condition with a constant literal on the partition key column. An example of dynamic pruning is the use of operators or functions in the `WHERE` condition.

Partition pruning affects the statistics of the objects where pruning occurs and also affects the execution plan of a statement.

### 3.1.2 Information That Can Be Used for Partition Pruning

Partition pruning can be performed on partitioning columns.

Oracle Database prunes partitions when you use range, `LIKE`, equality, and `IN`-list predicates on the range or list partitioning columns, and when you use equality and `IN`-list predicates on the hash partitioning columns.

On composite partitioned objects, Oracle Database can prune at both levels using the relevant predicates. For example, see the table `sales_range_hash`, which is partitioned by range on the column `s_saledate` and subpartitioned by hash on the column `s_productid` in Example 3-1.

Oracle uses the predicate on the partitioning columns to perform partition pruning as follows:

- When using range partitioning, Oracle accesses only partitions `sal99q2` and `sal99q3`, representing the partitions for the third and fourth quarters of 1999.

- When using hash subpartitioning, Oracle accesses only the one subpartition in each partition that stores the rows with `s_productid=1200`. The mapping between the subpartition and the predicate is calculated based on Oracle's internal hash distribution function.

A reference-partitioned table can take advantage of partition pruning through the join with the referenced table. Virtual column-based partitioned tables benefit from partition pruning for statements that use the virtual column-defining expression in the SQL statement.

Example 3-1 Creating a table with partition pruning

    CREATE TABLE sales_range_hash(
      s_productid  NUMBER,
      s_saledate   DATE,
      s_custid     NUMBER,
      s_totalprice NUMBER)
    PARTITION BY RANGE (s_saledate)
    SUBPARTITION BY HASH (s_productid) SUBPARTITIONS 8
     (PARTITION sal99q1 VALUES LESS THAN
       (TO_DATE('01-APR-1999', 'DD-MON-YYYY')),
      PARTITION sal99q2 VALUES LESS THAN
       (TO_DATE('01-JUL-1999', 'DD-MON-YYYY')),
      PARTITION sal99q3 VALUES LESS THAN
       (TO_DATE('01-OCT-1999', 'DD-MON-YYYY')),
      PARTITION sal99q4 VALUES LESS THAN
       (TO_DATE('01-JAN-2000', 'DD-MON-YYYY')));

    SELECT * FROM sales_range_hash
    WHERE s_saledate BETWEEN (TO_DATE('01-JUL-1999', 'DD-MON-YYYY'))
      AND (TO_DATE('01-OCT-1999', 'DD-MON-YYYY')) AND s_productid = 1200;

### 3.1.3 How to Identify Whether Partition Pruning Has Been Used

Whether Oracle uses partition pruning is reflected in the execution plan of a statement, either in the plan table for the `EXPLAIN` `PLAN` statement or in the shared SQL area.

The partition pruning information is reflected in the plan columns `PSTART` (`PARTITION_START`) and `PSTOP` (`PARTITION_STOP`). For serial statements, the pruning information is also reflected in the `OPERATION` and `OPTIONS` columns.

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/generating-and-displaying-execution-plans.md) for more information about `EXPLAIN` `PLAN` and how to interpret it

### 3.1.4 Static Partition Pruning

Oracle determines when to use static pruning primarily based on static predicates.

For many cases, Oracle determines the partitions to be accessed at compile time. Static partition pruning occurs if you use static predicates, except for the following cases:

- Partition pruning occurs using the result of a subquery.

- The optimizer rewrites the query with a star transformation and pruning occurs after the star transformation.

- The most efficient execution plan is a nested loop.

These three cases result in the use of dynamic pruning.

If at parse time Oracle can identify which contiguous set of partitions is accessed, then the `PSTART` and `PSTOP` columns in the execution plan show the begin and the end values of the partitions being accessed. Any other cases of partition pruning, including dynamic pruning, show the KEY value in `PSTART` and `PSTOP`, optionally with an additional attribute.

The following is an example:

    SQL> explain plan for select * from sales where time_id = to_date('01-jan-2001', 'dd-mon-yyyy');
    Explained.

    SQL> select * from table(dbms_xplan.display);
    PLAN_TABLE_OUTPUT
    ----------------------------------------------------------------------------------------------
    Plan hash value: 3971874201
    ----------------------------------------------------------------------------------------------
    | Id | Operation              | Name  | Rows | Bytes | Cost (%CPU)| Time     | Pstart| Pstop |
    ----------------------------------------------------------------------------------------------
    |  0 | SELECT STATEMENT       |       | 673  | 19517 | 27      (8)| 00:00:01 |       |       |
    |  1 |  PARTITION RANGE SINGLE|       | 673  | 19517 | 27      (8)| 00:00:01 | 17    | 17    |
    |* 2 |   TABLE ACCESS FULL    | SALES | 673  | 19517 | 27      (8)| 00:00:01 | 17    | 17    |
    ----------------------------------------------------------------------------------------------
    Predicate Information (identified by operation id):
    ---------------------------------------------------
       2 - filter("TIME_ID"=TO_DATE('2001-01-01 00:00:00', 'yyyy-mm-dd hh24:mi:ss'))

This plan shows that Oracle accesses partition number 17, as shown in the `PSTART` and `PSTOP` columns. The `OPERATION` column shows `PARTITION RANGE SINGLE`, indicating that only a single partition is being accessed. If `OPERATION` shows `PARTITION RANGE ALL`, then all partitions are being accessed and effectively no pruning takes place. `PSTART` then shows the very first partition of the table and `PSTOP` shows the very last partition.

An execution plan with a full table scan on an interval-partitioned table shows 1 for `PSTART`, and 1048575 for `PSTOP`, regardless of how many interval partitions were created.

### 3.1.5 Dynamic Partition Pruning

Oracle dynamic partition pruning is introduced in this topic.

Dynamic pruning occurs if pruning is possible and static pruning is not possible. The following examples show multiple dynamic pruning cases:

- Dynamic Pruning with Bind Variables

- Dynamic Pruning with Subqueries

- Dynamic Pruning with Star Transformation

- Dynamic Pruning with Nested Loop Joins

#### 3.1.5.1 Dynamic Pruning with Bind Variables

Statements that use bind variables against partition columns result in dynamic pruning.

The following SQL statement is an example.

    SQL> explain plan for select * from sales s where time_id in ( :a, :b, :c, :d);
    Explained.

    SQL> select * from table(dbms_xplan.display);
    PLAN_TABLE_OUTPUT
    ---------------------------------------------------------------------------------------------------
    Plan hash value: 513834092
    ---------------------------------------------------------------------------------------------------
    | Id | Operation                         |    Name |Rows|Bytes|Cost (%CPU)|  Time  | Pstart| Pstop|
    ---------------------------------------------------------------------------------------------------
    |  0 | SELECT STATEMENT                  |         |2517|72993|    292 (0)|00:00:04|       |      |
    |  1 |  INLIST ITERATOR                  |         |    |     |           |        |       |      |
    |  2 |   PARTITION RANGE ITERATOR        |         |2517|72993|    292 (0)|00:00:04|KEY(I) |KEY(I)|
    |  3 |    TABLE ACCESS BY LOCAL INDEX ROWID| SALES |2517|72993|    292 (0)|00:00:04|KEY(I) |KEY(I)|
    |  4 |     BITMAP CONVERSION TO ROWIDS   |         |    |     |           |        |       |      |
    |* 5 |      BITMAP INDEX SINGLE VALUE    |SALES_TIME_BIX| |   |           |        |KEY(I) |KEY(I)|
    ---------------------------------------------------------------------------------------------------
    Predicate Information (identified by operation id):
    ---------------------------------------------------
    5 - access("TIME_ID"=:A OR "TIME_ID"=:B OR "TIME_ID"=:C OR "TIME_ID"=:D)

For parallel execution plans, only the partition start and stop columns contain the partition pruning information; the operation column contains information for the parallel operation, as shown in the following example:

    SQL> explain plan for select * from sales where time_id in (:a, :b, :c, :d);
    Explained.

    SQL> select * from table(dbms_xplan.display);
    PLAN_TABLE_OUTPUT
    -------------------------------------------------------------------------------------------------
    Plan hash value: 4058105390
    -------------------------------------------------------------------------------------------------
    | Id| Operation          | Name  |Rows|Bytes|Cost(%CP|  Time  |Pstart| Pstop|  TQ |INOUT| PQ Dis|
    -------------------------------------------------------------------------------------------------
    |  0| SELECT STATEMENT   |       |2517|72993|  75(36)|00:00:01|      |      |     |     |       |
    |  1|  PX COORDINATOR    |       |    |     |        |        |      |      |     |     |       |
    |  2|  PX SEND QC(RANDOM)|:TQ10000|2517|72993| 75(36)|00:00:01|      |      |Q1,00| P->S|QC(RAND|
    |  3|   PX BLOCK ITERATOR|       |2517|72993|  75(36)|00:00:01|KEY(I)|KEY(I)|Q1,00| PCWC|       |
    |* 4|   TABLE ACCESS FULL| SALES |2517|72993|  75(36)|00:00:01|KEY(I)|KEY(I)|Q1,00| PCWP|       |
    -------------------------------------------------------------------------------------------------
    Predicate Information (identified by operation id):
    ---------------------------------------------------
      4 - filter("TIME_ID"=:A OR "TIME_ID"=:B OR "TIME_ID"=:C OR "TIME_ID"=:D)

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/generating-and-displaying-execution-plans.md) for more information about `EXPLAIN PLAN` and how to interpret it

#### 3.1.5.2 Dynamic Pruning with Subqueries

Statements that explicitly use subqueries against partition columns result in dynamic pruning.

The following SQL statement is an example.

    SQL> explain plan for select sum(amount_sold) from sales where time_id in
         (select time_id from times where fiscal_year = 2000);
    Explained.

    SQL> select * from table(dbms_xplan.display);
    PLAN_TABLE_OUTPUT
    PLAN_TABLE_OUTPUT
    ----------------------------------------------------------------------------------------------------
    Plan hash value: 3827742054

    ----------------------------------------------------------------------------------------------------
    | Id  | Operation                  | Name  | Rows  | Bytes | Cost (%CPU)| Time     | Pstart| Pstop |
    ----------------------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT           |       |     1 |    25 |   523   (5)| 00:00:07 |       |       |
    |   1 |  SORT AGGREGATE            |       |     1 |    25 |            |          |       |       |
    |*  2 |   HASH JOIN                |       |   191K|  4676K|   523   (5)| 00:00:07 |       |       |
    |*  3 |    TABLE ACCESS FULL       | TIMES |   304 |  3648 |    18   (0)| 00:00:01 |       |       |
    |   4 |    PARTITION RANGE SUBQUERY|       |   918K|    11M|   498   (4)| 00:00:06 |KEY(SQ)|KEY(SQ)|
    |   5 |     TABLE ACCESS FULL      | SALES |   918K|    11M|   498   (4)| 00:00:06 |KEY(SQ)|KEY(SQ)|
    ----------------------------------------------------------------------------------------------------

    Predicate Information (identified by operation id):
    ---------------------------------------------------

       2 - access("TIME_ID"="TIME_ID")
       3 - filter("FISCAL_YEAR"=2000)

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/generating-and-displaying-execution-plans.md) for more information about `EXPLAIN PLAN` and how to interpret it

#### 3.1.5.3 Dynamic Pruning with Star Transformation

Statements that get transformed by the database using the star transformation result in dynamic pruning.

The following SQL statement is an example.

    SQL> explain plan for select p.prod_name, t.time_id, sum(s.amount_sold)
         from sales s, times t, products p
         where s.time_id = t.time_id and s.prod_id = p.prod_id and t.fiscal_year = 2000
         and t.fiscal_week_number = 3 and p.prod_category = 'Hardware'
         group by t.time_id, p.prod_name;
    Explained.

    SQL> select * from table(dbms_xplan.display);
    PLAN_TABLE_OUTPUT
    ------------------------------------------------------------------------------------------------------
    Plan hash value: 4020965003

    ------------------------------------------------------------------------------------------------------
    | Id  | Operation                             | Name                 | Rows  | Bytes | Pstart| Pstop |
    ------------------------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT                      |                      |     1 |    79 |       |       |
    |   1 |  HASH GROUP BY                        |                      |     1 |    79 |       |       |
    |*  2 |   HASH JOIN                           |                      |     1 |    79 |       |       |
    |*  3 |    HASH JOIN                          |                      |     2 |    64 |       |       |
    |*  4 |     TABLE ACCESS FULL                 | TIMES                |     6 |    90 |       |       |
    |   5 |     PARTITION RANGE SUBQUERY          |                      |   587 |  9979 |KEY(SQ)|KEY(SQ)|
    |   6 |      TABLE ACCESS BY LOCAL INDEX ROWID| SALES                |   587 |  9979 |KEY(SQ)|KEY(SQ)|
    |   7 |       BITMAP CONVERSION TO ROWIDS     |                      |       |       |       |       |
    |   8 |        BITMAP AND                     |                      |       |       |       |       |
    |   9 |         BITMAP MERGE                  |                      |       |       |       |       |
    |  10 |          BITMAP KEY ITERATION         |                      |       |       |       |       |
    |  11 |           BUFFER SORT                 |                      |       |       |       |       |
    |* 12 |            TABLE ACCESS FULL          | TIMES                |     6 |    90 |       |       |
    |* 13 |           BITMAP INDEX RANGE SCAN     | SALES_TIME_BIX       |       |       |KEY(SQ)|KEY(SQ)|
    |  14 |         BITMAP MERGE                  |                      |       |       |       |       |
    |  15 |          BITMAP KEY ITERATION         |                      |       |       |       |       |
    |  16 |           BUFFER SORT                 |                      |       |       |       |       |
    |  17 |            TABLE ACCESS BY INDEX ROWID| PRODUCTS             |    14 |   658 |       |       |
    |* 18 |             INDEX RANGE SCAN          | PRODUCTS_PROD_CAT_IX |    14 |       |       |       |
    |* 19 |           BITMAP INDEX RANGE SCAN     | SALES_PROD_BIX       |       |       |KEY(SQ)|KEY(SQ)|
    |  20 |    TABLE ACCESS BY INDEX ROWID        | PRODUCTS             |    14 |   658 |       |       |
    |* 21 |     INDEX RANGE SCAN                  | PRODUCTS_PROD_CAT_IX |    14 |       |       |       |
    ------------------------------------------------------------------------------------------------------

    Predicate Information (identified by operation id):
    ---------------------------------------------------

       2 - access("S"."PROD_ID"="P"."PROD_ID")
       3 - access("S"."TIME_ID"="T"."TIME_ID")
       4 - filter("T"."FISCAL_WEEK_NUMBER"=3 AND "T"."FISCAL_YEAR"=2000)
      12 - filter("T"."FISCAL_WEEK_NUMBER"=3 AND "T"."FISCAL_YEAR"=2000)
      13 - access("S"."TIME_ID"="T"."TIME_ID")
      18 - access("P"."PROD_CATEGORY"='Hardware')
      19 - access("S"."PROD_ID"="P"."PROD_ID")
      21 - access("P"."PROD_CATEGORY"='Hardware')

    Note
    -----
       - star transformation used for this statement

**Note:**

The `Cost (%CPU)` and `Time` columns were removed from the plan table output in this example.

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/generating-and-displaying-execution-plans.md) for more information about `EXPLAIN PLAN` and how to interpret it

#### 3.1.5.4 Dynamic Pruning with Nested Loop Joins

Statements that are most efficiently executed using a nested loop join use dynamic pruning.

The following SQL statement is an example.

    SQL> explain plan for select t.time_id, sum(s.amount_sold)
         from sales s, times t
         where s.time_id = t.time_id and t.fiscal_year = 2000 and t.fiscal_week_number = 3
         group by t.time_id;
    Explained.

    SQL> select * from table(dbms_xplan.display);
    PLAN_TABLE_OUTPUT
    ----------------------------------------------------------------------------------------------------
    Plan hash value: 50737729

    ----------------------------------------------------------------------------------------------------
    | Id  | Operation                  | Name  | Rows  | Bytes | Cost (%CPU)| Time     | Pstart| Pstop |
    ----------------------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT           |       |     6 |   168 |   126   (4)| 00:00:02 |       |       |
    |   1 |  HASH GROUP BY             |       |     6 |   168 |   126   (4)| 00:00:02 |       |       |
    |   2 |   NESTED LOOPS             |       |  3683 |   100K|   125   (4)| 00:00:02 |       |       |
    |*  3 |    TABLE ACCESS FULL       | TIMES |     6 |    90 |    18   (0)| 00:00:01 |       |       |
    |   4 |    PARTITION RANGE ITERATOR|       |   629 |  8177 |    18   (6)| 00:00:01 |   KEY |   KEY |
    |*  5 |     TABLE ACCESS FULL      | SALES |   629 |  8177 |    18   (6)| 00:00:01 |   KEY |   KEY |
    ----------------------------------------------------------------------------------------------------

    Predicate Information (identified by operation id):
    ---------------------------------------------------

       3 - filter("T"."FISCAL_WEEK_NUMBER"=3 AND "T"."FISCAL_YEAR"=2000)
       5 - filter("S"."TIME_ID"="T"."TIME_ID")

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/generating-and-displaying-execution-plans.md) for more information about `EXPLAIN PLAN` and how to interpret it

### 3.1.6 Partition Pruning with Zone Maps

Partition pruning is enhanced to take advantage of zone maps for pruning of complete partitions. Providing enhanced pruning capabilities provides better performance with less resource consumption and shorter time-to-information.

A zone map is a independent access structure that can be built for a table. During table scans, zone maps enable you to prune disk blocks of a table and partitions of a partitioned table based on predicates on the table columns. Zone maps have no correlation to the partition key columns of a partitioned table, so statements on partitioned tables with zone maps can prune partitions based on non-partition key columns.

**See Also:**

[Oracle Database Data Warehousing Guide](../dwhsg/attribute-clustering.md) for information about zone maps and attribute clustering

Partition pruning with zone maps is especially effective when the zone map column values correlate with partition key column values. For example, the correlation can be between columns of the partitioned table itself, such as a shipping date that has a correlation to the partition key column order date in the same partitioned table, or within the join zone map columns and the partitioned table, such as a join zone map column month description from a dimension table times that correlates with the partition key column day of the partitioned table.

Example 3-2 illustrates partition pruning with zone maps for correlated columns of a partitioned table. Column `s_shipdate` in the partitioned table `sales_range` correlates with the partition key column `order_date` because orders are normally shipped within a couple of days after an order was received.

Due to the correlation of `s_shipdate` and the partition key column any selective predicate on this column has a high likelihood to enable partition pruning for the partitioned table `sales_range`, without having the column as part of the partitioning key.

The following `SELECT` statement looks for all orders that were shipped in the first quarter of 1999:

    SELECT * FROM sales_range
          WHERE s_shipdate BETWEEN to_date('01/01/1999','dd/mm/yyyy')
          AND to_date('03/01/1999','mm/dd/yyyy');

In the following execution plan for the previous `SELECT` statement, zone maps are used for partition pruning and also to prune blocks from the partitions that have to be accessed.

Partition pruning with zone maps is identified by having `KEY(ZM)` in the `PSTART` and `PSTOP` columns of the execution plan. The block level pruning of all accessed partitions is identified by the filter predicate at table access time (`id 2`).

Example 3-2 Partitioned table sales_range with attribute clustering and a zone map on a correlated column

    CREATE TABLE sales_range(
      s_productid      NUMBER,
      s_saledate       DATE,
      s_shipdate       DATE,
      s_custid         NUMBER,
      s_totalprice     NUMBER)
    CLUSTERING BY (s_shipdate)
    WITH MATERIALIZED ZONEMAP
    PARTITION BY RANGE (s_saledate)
     (PARTITION sal99q1 VALUES LESS THAN
       (TO_DATE('01-APR-1999', 'DD-MON-YYYY')),
      PARTITION sal99q2 VALUES LESS THAN
       (TO_DATE('01-JUL-1999', 'DD-MON-YYYY')),
      PARTITION sal99q3 VALUES LESS THAN
       (TO_DATE('01-OCT-1999', 'DD-MON-YYYY')),
      PARTITION sal99q4 VALUES LESS THAN
       (TO_DATE('01-JAN-2000', 'DD-MON-YYYY')));

Example 3-3 Execution plan for partition pruning with zone maps

    ---------------------------------------------------------------------------------------------------------------
    | Id  | Operation                       | Name        | Rows  | Bytes | Cost (%CPU)| Time     | Pstart| Pstop |
    ---------------------------------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT                |             |       |       |     3 (100)|          |       |       |
    |   1 |  PARTITION RANGE ITERATOR       |             |    58 |  3306 |     3   (0)| 00:00:01 |KEY(ZM)|KEY(ZM)|
    |*  2 |   TABLE ACCESS FULL WITH ZONEMAP| SALES_RANGE |    58 |  3306 |     3   (0)| 00:00:01 |KEY(ZM)|KEY(ZM)|
    ---------------------------------------------------------------------------------------------------------------

    Predicate Information (identified by operation id):
    ---------------------------------------------------

    2 - filter((SYS_ZMAP_FILTER('/* ZM_PRUNING */ SELECT "ZONE_ID$", CASE WHEN
     BITAND(zm."ZONE_STATE$",1)=1 THEN 1 ELSE CASE WHEN (zm."MAX_1_S_SHIPDATE" < :1 OR
     zm."MIN_1_S_SHIPDATE" > :2) THEN 3 ELSE 2 END END FROM "SH"."ZMAP$_SALES_RANGE" zm WHERE
     zm."ZONE_LEVEL$"=0 ORDER BY zm."ZONE_ID$"',SYS_OP_ZONE_ID(ROWID),TO_DATE(' 1999-01-01 00:00:00',
     'syyyy-mm-dd hh24:mi:ss'),TO_DATE(' 1999-03-01 00:00:00', 'syyyy-mm-dd hh24:mi:ss'))<3 AND
     "S_SHIPDATE">=TO_DATE(' 1999-01-01 00:00:00','syyyy-mm-dd hh24:mi:ss') AND "S_SHIPDATE"<=TO_DATE('
      1999-03-01 00:00:00', 'syyyy-mm-dd hh24:mi:ss')))

### 3.1.7 Partition Pruning Tips

Tips for partition pruning are introduced in this topic.

When using partition pruning, you should consider the following:

- Data Type Conversions

- Function Calls

- Collection Tables

**Note:**

When you manipulate a partition column with any function or transformation, such as `CAST` or `TRUNC`, partition pruning is not taking place.

#### 3.1.7.1 Data Type Conversions

To get the maximum performance benefit from partition pruning, you should avoid constructs that require the database to convert the data type you specify.

Data type conversions typically result in dynamic pruning when static pruning would have otherwise been possible. SQL statements that benefit from static pruning perform better than statements that benefit from dynamic pruning.

A common case of data type conversions occurs when using the Oracle `DATE` data type. An Oracle `DATE` data type is not a character string but is only represented as such when querying the database; the format of the representation is defined by the NLS setting of the instance or the session. Consequently, the same reverse conversion has to happen when inserting data into a `DATE` field or when specifying a predicate on such a field.

A conversion can either happen implicitly or explicitly by specifying a `TO_DATE` conversion. Only a properly applied `TO_DATE` function guarantees that the database can uniquely determine the date value and using it potentially for static pruning, which is especially beneficial for single partition access.

Consider the following example that runs against the `sales` table. You would like to know the total revenue number for the year 2000. There are multiple ways you can retrieve the answer to the query, but not every method is equally efficient.

    explain plan for SELECT SUM(amount_sold) total_revenue
    FROM sales,
    WHERE time_id between '01-JAN-00' and '31-DEC-00';

The plan should now be similar to the following:

    ----------------------------------------------------------------------------------------------------
    | Id  | Operation                  | Name  | Rows  | Bytes | Cost (%CPU)| Time     | Pstart| Pstop |
    ----------------------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT           |       |     1 |    13 |   525   (8)| 00:00:07 |       |       |
    |   1 |  SORT AGGREGATE            |       |     1 |    13 |            |          |       |       |
    |*  2 |   FILTER                   |       |       |       |            |          |       |       |
    |   3 |    PARTITION RANGE ITERATOR|       |   230K|  2932K|   525   (8)| 00:00:07 |   KEY |   KEY |
    |*  4 |     TABLE ACCESS FULL      | SALES |   230K|  2932K|   525   (8)| 00:00:07 |   KEY |   KEY |
    ----------------------------------------------------------------------------------------------------

    Predicate Information (identified by operation id):
    ---------------------------------------------------

       2 - filter(TO_DATE('01-JAN-00')<=TO_DATE('31-DEC-00'))
       4 - filter("TIME_ID">='01-JAN-00' AND "TIME_ID"<='31-DEC-00')

In this case, the keyword `KEY` for both `PSTART` and `PSTOP` means that dynamic partition pruning occurs at run-time. Consider the following case.

    explain plan for select sum(amount_sold)
    from sales
    where time_id between '01-JAN-2000' and '31-DEC-2000' ;

The execution plan now shows the following:

    ----------------------------------------------------------------------------------------
    | Id  | Operation                 | Name  | Rows  | Bytes | Cost (%CPU)| Pstart| Pstop |
    ----------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT          |       |     1 |    13 |   127   (4)|       |       |
    |   1 |  SORT AGGREGATE           |       |     1 |    13 |            |       |       |
    |   2 |   PARTITION RANGE ITERATOR|       |   230K|  2932K|   127   (4)|    13 |    16 |
    |*  3 |    TABLE ACCESS FULL      | SALES |   230K|  2932K|   127   (4)|    13 |    16 |
    ----------------------------------------------------------------------------------------
    Predicate Information (identified by operation id):
    ---------------------------------------------------

       3 - filter("TIME_ID"<=TO_DATE(' 2000-12-31 00:00:00', "syyyy-mm-dd hh24:mi:ss'))

**Note:**

The `Time` column was removed from the execution plan.

The execution plan shows static partition pruning. The query accesses a contiguous list of partitions 13 to 16. In this particular case, the way the date format was specified matches the NLS date format setting. Though this example shows the most efficient execution plan, you cannot rely on the NLS date format setting to define a certain format.

    alter session set nls_date_format='fmdd Month yyyy';

    explain plan for select sum(amount_sold)
    from sales
    where time_id between '01-JAN-2000' and '31-DEC-2000' ;

The execution plan now shows the following:

    -----------------------------------------------------------------------------------------
    | Id  | Operation                  | Name  | Rows  | Bytes | Cost (%CPU)| Pstart| Pstop |
    -----------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT           |       |     1 |    13 |   525   (8)|       |       |
    |   1 |  SORT AGGREGATE            |       |     1 |    13 |            |       |       |
    |*  2 |   FILTER                   |       |       |       |            |       |       |
    |   3 |    PARTITION RANGE ITERATOR|       |   230K|  2932K|   525   (8)|   KEY |   KEY |
    |*  4 |     TABLE ACCESS FULL      | SALES |   230K|  2932K|   525   (8)|   KEY |   KEY |
    -----------------------------------------------------------------------------------------

    Predicate Information (identified by operation id):
    ---------------------------------------------------

       2 - filter(TO_DATE('01-JAN-2000')<=TO_DATE('31-DEC-2000'))
       4 - filter("TIME_ID">='01-JAN-2000' AND "TIME_ID"<='31-DEC-2000')

**Note:**

The `Time` column was removed from the execution plan.

This plan, which uses dynamic pruning, again is less efficient than the static pruning execution plan. To guarantee a static partition pruning plan, you should explicitly convert data types to match the partition column data type. For example:

    explain plan for select sum(amount_sold)
    from sales
    where time_id between to_date('01-JAN-2000','dd-MON-yyyy')
      and to_date('31-DEC-2000','dd-MON-yyyy') ;

    ----------------------------------------------------------------------------------------
    | Id  | Operation                 | Name  | Rows  | Bytes | Cost (%CPU)| Pstart| Pstop |
    ----------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT          |       |     1 |    13 |   127   (4)|       |       |
    |   1 |  SORT AGGREGATE           |       |     1 |    13 |            |       |       |
    |   2 |   PARTITION RANGE ITERATOR|       |   230K|  2932K|   127   (4)|    13 |    16 |
    |*  3 |    TABLE ACCESS FULL      | SALES |   230K|  2932K|   127   (4)|    13 |    16 |
    ----------------------------------------------------------------------------------------

    Predicate Information (identified by operation id):
    ---------------------------------------------------

       3 - filter("TIME_ID"<=TO_DATE(' 2000-12-31 00:00:00', 'syyyy-mm-dd hh24:mi:ss'))

**Note:**

The `Time` column was removed from the execution plan.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for details about the `DATE` data type

- [Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for details about NLS settings and globalization issues

#### 3.1.7.2 Function Calls

Functions can limit the ability of the optimizer to perform pruning.

There are several cases when the optimizer cannot perform pruning. One common reasons is when an operator is used on top of a partitioning column. This could be an explicit operator (for example, a function) or even an implicit operator introduced by Oracle as part of the necessary data type conversion for executing the statement. For example, consider the following query:

    EXPLAIN PLAN FOR
    SELECT SUM(quantity_sold)
    FROM sales
    WHERE time_id = TO_TIMESTAMP('1-jan-2000', 'dd-mon-yyyy');

Because `time_id` is of type `DATE` and Oracle must promote it to the `TIMESTAMP` type to get the same data type, this predicate is internally rewritten as:

    TO_TIMESTAMP(time_id) = TO_TIMESTAMP('1-jan-2000', 'dd-mon-yyyy')

The execution plan for this statement is as follows:

    --------------------------------------------------------------------------------------------
    |Id | Operation            | Name  | Rows  | Bytes | Cost (%CPU)| Time     | Pstart| Pstop |
    --------------------------------------------------------------------------------------------
    | 0 | SELECT STATEMENT     |       |     1 |    11 |     6  (17)| 00:00:01 |       |       |
    | 1 |  SORT AGGREGATE      |       |     1 |    11 |            |          |       |       |
    | 2 |   PARTITION RANGE ALL|       |    10 |   110 |     6  (17)| 00:00:01 |     1 |    16 |
    |*3 |    TABLE ACCESS FULL | SALES |    10 |   110 |     6  (17)| 00:00:01 |     1 |    16 |
    --------------------------------------------------------------------------------------------

    Predicate Information (identified by operation id):
    ---------------------------------------------------
    3 - filter(INTERNAL_FUNCTION("TIME_ID")=TO_TIMESTAMP('1-jan-2000',:B1))

    15 rows selected

The `SELECT` statement accesses all partitions even though pruning down to a single partition could have taken place. Consider the example to find the total sales revenue number for 2000. Another way to construct the query would be:

    EXPLAIN PLAN FOR
    SELECT SUM(amount_sold)
    FROM sales
    WHERE TO_CHAR(time_id,'yyyy') = '2000';

This query applies a function call to the partition key column, which generally disables partition pruning. The execution plan shows a full table scan with no partition pruning:

    ----------------------------------------------------------------------------------------------
    | Id  | Operation            | Name  | Rows  | Bytes | Cost (%CPU)| Time     | Pstart| Pstop |
    ----------------------------------------------------------------------------------------------
    |   0 | SELECT STATEMENT     |       |     1 |    13 |   527   (9)| 00:00:07 |       |       |
    |   1 |  SORT AGGREGATE      |       |     1 |    13 |            |          |       |       |
    |   2 |   PARTITION RANGE ALL|       |  9188 |   116K|   527   (9)| 00:00:07 |     1 |    28 |
    |*  3 |    TABLE ACCESS FULL | SALES |  9188 |   116K|   527   (9)| 00:00:07 |     1 |    28 |
    ----------------------------------------------------------------------------------------------

    Predicate Information (identified by operation id):
    ---------------------------------------------------

       3 - filter(TO_CHAR(INTERNAL_FUNCTION("TIME_ID"),'yyyy')='2000')

Avoid using implicit or explicit functions on the partition columns. If your queries commonly use function calls, then consider using a virtual column and virtual column partitioning to benefit from partition pruning in these cases.

#### 3.1.7.3 Collection Tables

Collection tables can limit the ability of the optimizer to perform pruning.

The following example illustrates what an `EXPLAIN` `PLAN` statement might look like when it contains Collection Tables, which, for the purposes of this discussion, are ordered collection tables or nested tables. A full table access is not performed because it is constrained to just the partition in question.

    EXPLAIN PLAN FOR
    SELECT p.ad_textdocs_ntab
    FROM print_media_part p;

    Explained.

    PLAN_TABLE_OUTPUT
    -----------------------------------------------------------------------
    Plan hash value: 2207588228

    -----------------------------------------------------------------------
    | Id  | Operation                  | Name             | Pstart| Pstop |
    -----------------------------------------------------------------------
    |   0 | SELECT STATEMENT           |                  |       |       |
    |   1 |  PARTITION REFERENCE SINGLE|                  |   KEY |   KEY |
    |   2 |   TABLE ACCESS FULL        | TEXTDOC_NT       |   KEY |   KEY |
    |   3 |  PARTITION RANGE ALL       |                  |     1 |     2 |
    |   4 |   TABLE ACCESS FULL        | PRINT_MEDIA_PART |     1 |     2 |
    -----------------------------------------------------------------------

    Note
    -----
      - dynamic sampling used for this statement

**See Also:**

[Partitioning of Collections in XMLType and Objects](partition-create-tables-indexes.md) for an example of the `CREATE` `TABLE` statement on which the `EXPLAIN` `PLAN` is based
