This chapter discusses advanced topics in using materialized views. It contains the following topics:

- About Partitioning and Materialized Views

- About Materialized Views in Analytic Processing Environments

- About Materialized Views and Models

- About Security Issues with Materialized Views

- Invalidating Materialized Views

- Altering Materialized Views

- Using Real-time Materialized Views

### 6.1 About Partitioning and Materialized Views

Because of the large volume of data held in a data warehouse, partitioning is an extremely useful option when designing a database. Partitioning the fact tables improves scalability, simplifies system administration, and makes it possible to define local indexes that can be efficiently rebuilt. Partitioning the fact tables also improves the opportunity of fast refreshing the materialized view because this may enable partition change tracking (PCT) refresh on the materialized view. Partitioning a materialized view also has benefits for refresh, because the refresh procedure can then use parallel DML in more scenarios and PCT-based refresh can use truncate partition to efficiently maintain the materialized view.

**See Also:**

[Oracle Database VLDB and Partitioning Guide](../vldbg/partition-concepts.md) for further details about partitioning

This section contains the following topics:

- About Partition Change Tracking

- Partitioning a Materialized View

- Partitioning a Prebuilt Table

- Rolling Materialized Views

#### 6.1.1 About Partition Change Tracking

It is possible and advantageous to track freshness to a finer grain than the entire materialized view. You can achieve this through [partition change tracking (PCT)](glossary.md), which is a method to identify which rows in a materialized view are affected by a certain detail table partition. When one or more of the detail tables are partitioned, it may be possible to identify the specific rows in the materialized view that correspond to a modified detail partition(s); those rows become stale when a partition is modified while all other rows remain fresh.

You can use PCT to identify which materialized view rows correspond to a particular partition. PCT is also used to support fast refresh after partition maintenance operations on detail tables. For instance, if a detail table partition is truncated or dropped, the affected rows in the materialized view are identified and deleted.

Identifying which materialized view rows are fresh or stale, rather than considering the entire materialized view as stale, allows query rewrite to use those rows that are fresh while in `QUERY_REWRITE_INTEGRITY `= `ENFORCED` or `TRUSTED` modes. Several views, such as `DBA_MVIEW_DETAIL_PARTITION`, detail which partitions are stale or fresh. Oracle does not rewrite against partial stale materialized views if partition change tracking on the changed table is enabled by the presence of join dependent expressions in the materialized view.

**See Also:**

"About Join Dependent Expression and Partition Change Tracking" for more information

Note that, while partition change tracking tracks the staleness on a partition and subpartition level (for composite partitioned tables), the level of granularity for PCT refresh is only the top-level partitioning strategy. Consequently, any change to data in one of the subpartitions of a composite partitioned-table will only mark the single impacted subpartition as stale and have the rest of the table available for rewrite, but the PCT refresh will refresh the whole partition that contains the impacted subpartition.

To support PCT, a materialized view must satisfy the following requirements:

- At least one of the detail tables referenced by the materialized view must be partitioned.

- Partitioned tables must use either range, list or composite partitioning with range or list as the top-level partitioning strategy.

- The top level partition key must consist of only a single column.

- The materialized view must contain either the partition key column or a partition marker or `ROWID` or join dependent expression of the detail table.

- If you use a `GROUP` `BY` clause, the partition key column or the partition marker or `ROWID` or join dependent expression must be present in the `GROUP` `BY` clause.

- If you use an analytic window function or the `MODEL` clause, the partition key column or the partition marker or `ROWID` or join dependent expression must be present in their respective `PARTITION` `BY` subclauses.

- Data modifications can only occur on the partitioned table. If PCT refresh is being done for a table which has join dependent expression in the materialized view, then data modifications should not have occurred in any of the join dependent tables.

- The `COMPATIBILITY` initialization parameter must be a minimum of 9.0.0.0.0.

PCT is not supported for a materialized view that refers to views, remote tables, or outer joins.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MVIEW.md) for details regarding the `DBMS_MVIEW.PMARKER` function and partition markers

This section contains the following topics:

- About Partition Key and Partition Change Tracking

- About Join Dependent Expression and Partition Change Tracking

- About Partition Markers and Partition Change Tracking

- About Partial Rewrite in Partition Change Tracking

##### 6.1.1.1 About Partition Key and Partition Change Tracking

Partition change tracking requires sufficient information in the materialized view to be able to correlate a detail row in the source partitioned detail table to the corresponding materialized view row. This can be accomplished by including the detail table partition key columns in the `SELECT` list and, if `GROUP` `BY` is used, in the `GROUP` `BY` list.

Consider an example of a materialized view storing daily customer sales. The following example uses the `sh` sample schema and the three detail tables `sales`, `products`, and `times` to create the materialized view. `sales` table is partitioned by `time_id` column and `products` is partitioned by the `prod_id` column. `times` is not a partitioned table.

Example 6-1 Materialized View with Partition Key

    CREATE MATERIALIZED VIEW LOG ON SALES WITH ROWID
       (prod_id, time_id, quantity_sold, amount_sold) INCLUDING NEW VALUES;
    CREATE MATERIALIZED VIEW LOG ON PRODUCTS WITH ROWID
       (prod_id, prod_name, prod_desc) INCLUDING NEW VALUES;
    CREATE MATERIALIZED VIEW LOG ON TIMES WITH ROWID
       (time_id, calendar_month_name, calendar_year) INCLUDING NEW VALUES;

    CREATE MATERIALIZED VIEW cust_dly_sales_mv
    BUILD DEFERRED REFRESH FAST ON DEMAND
    ENABLE QUERY REWRITE AS
    SELECT s.time_id, p.prod_id, p.prod_name, COUNT(*),
             SUM(s.quantity_sold), SUM(s.amount_sold),
             COUNT(s.quantity_sold), COUNT(s.amount_sold)
    FROM sales s, products p, times t
    WHERE  s.time_id = t.time_id AND s.prod_id = p.prod_id
    GROUP BY s.time_id, p.prod_id, p.prod_name;

For `cust_dly_sales_mv`, PCT is enabled on the `sales` table because the partitioning key column `time_id` is in the materialized view.

##### 6.1.1.2 About Join Dependent Expression and Partition Change Tracking

An expression consisting of columns from tables directly or indirectly joined through equijoins to the partitioned detail table on the partitioning key and which is either a dimensional attribute or a dimension hierarchical parent of the joining key is called a join dependent expression. The set of tables in the path to detail table are called join dependent tables. Consider the following:

    SELECT s.time_id, t.calendar_month_name
    FROM sales s, times t WHERE s.time_id = t.time_id;

In this query, `times` table is a join dependent table because it is joined to `sales` table on the partitioning key column `time_id`. Moreover, `calendar_month_name` is a dimension hierarchical attribute of `times.time_id`, because `calendar_month_name` is an attribute of `times.mon_id` and `times.mon_id` is a dimension hierarchical parent of `times.time_id`. Hence, the expression `calendar_month_name` from `times` tables is a join dependent expression. Let's consider another example:

    SELECT s.time_id, y.calendar_year_name
    FROM sales s, times_d d, times_m m, times_y y
    WHERE s.time_id = d.time_id AND d.day_id = m.day_id AND m.mon_id = y.mon_id;

Here, `times` table is denormalized into `times_d`, `times_m` and `times_y` tables. The expression `calendar_year_name` from `times_y` table is a join dependent expression and the tables `times_d`, `times_m` and `times_y` are join dependent tables. This is because `times_y` table is joined indirectly through `times_m` and `times_d` tables to sales table on its partitioning key column `time_id`.

This lets users create materialized views containing aggregates on some level higher than the partitioning key of the detail table. Consider the following example of materialized view storing monthly customer sales.

Example 6-2 Creating a Materialized View: Join Dependent Expression

Assuming the presence of materialized view logs defined earlier, the materialized view can be created using the following DDL:

    CREATE MATERIALIZED VIEW cust_mth_sales_mv
    BUILD DEFERRED REFRESH FAST ON DEMAND
    ENABLE QUERY REWRITE AS
    SELECT t.calendar_month_name, p.prod_id, p.prod_name, COUNT(*),
        SUM(s.quantity_sold), SUM(s.amount_sold),
        COUNT(s.quantity_sold), COUNT(s.amount_sold)
    FROM sales s, products p, times t
    WHERE  s.time_id = t.time_id AND s.prod_id = p.prod_id
    GROUP BY t.calendar_month_name, p.prod_id, p.prod_name;

Here, you can correlate a detail table row to its corresponding materialized view row using the join dependent table `times` and the relationship that `times.calendar_month_name` is a dimensional attribute determined by `times.time_id`. This enables partition change tracking on `sales` table. In addition to this, PCT is enabled on products table because of presence of its partitioning key column `prod_id` in the materialized view.

##### 6.1.1.3 About Partition Markers and Partition Change Tracking

The `DBMS_MVIEW.PMARKER` function is designed to significantly reduce the cardinality (the ratio of distinct values to the number of table rows) of the materialized view (see Example 6-3 for an example). The function returns a partition identifier that uniquely identifies the partition or subpartition for a specified row within a specified partitioned table. Therefore, the `DBMS_MVIEW.PMARKER` function is used instead of the partition key column in the `SELECT` and `GROUP` `BY` clauses.

Unlike the general case of a PL/SQL function in a materialized view, use of the `DBMS_MVIEW.PMARKER` does not prevent rewrite with that materialized view even when the rewrite mode is `QUERY_REWRITE_INTEGRITY = ENFORCED`.

As an example of using the `PMARKER` function, consider calculating a typical number, such as revenue generated by a product category during a given year. If there were 1000 different products sold each month, it would result in 12,000 rows in the materialized view.

Example 6-3 Using Partition Markers in a Materialized View

Consider an example of a materialized view storing the yearly sales revenue for each product category. With approximately hundreds of different products in each product category, including the partitioning key column `prod_id` of the `products` table in the materialized view would substantially increase the cardinality. Instead, this materialized view uses the `DBMS_MVIEW.PMARKER` function, which increases the cardinality of materialized view by a factor of the number of partitions in the `products` table.

    CREATE MATERIALIZED VIEW prod_yr_sales_mv
    BUILD DEFERRED
    REFRESH FAST ON DEMAND
    ENABLE QUERY REWRITE AS
    SELECT DBMS_MVIEW.PMARKER(p.rowid), p.prod_category, t.calendar_year, COUNT(*),
           SUM(s.amount_sold), SUM(s.quantity_sold),
           COUNT(s.amount_sold), COUNT(s.quantity_sold)
    FROM   sales s, products p, times t
    WHERE  s.time_id = t.time_id AND s.prod_id = p.prod_id
    GROUP BY  DBMS_MVIEW.PMARKER (p.rowid), p.prod_category, t.calendar_year;

`prod_yr_sales_mv` includes the `DBMS_MVIEW.PMARKER` function on the `products` table in its `SELECT` list. This enables partition change tracking on `products` table with significantly less cardinality impact than grouping by the partition key column `prod_id`. In this example, the desired level of aggregation for the `prod_yr_sales_mv` is to group by `products.prod_category`. Using the `DBMS_MVIEW.PMARKER` function, the materialized view cardinality is increased only by a factor of the number of partitions in the `products` table. This would generally be significantly less than the cardinality impact of including the partition key columns.

Note that partition change tracking is enabled on `sales` table because of presence of join dependent expression `calendar_year` in the `SELECT` list.

##### 6.1.1.4 About Partial Rewrite in Partition Change Tracking

A subsequent `INSERT` statement adds a new row to the `sales_part3` partition of table `sales`. At this point, because `cust_dly_sales_mv` has PCT available on table `sales` using a partition key, Oracle can identify the stale rows in the materialized view `cust_dly_sales_mv` corresponding to `sales_part3` partition (The other rows are unchanged in their freshness state). Query rewrite cannot identify the fresh portion of materialized views `cust_mth_sales_mv` and `prod_yr_sales_mv` because PCT is available on table sales using join dependent expressions. Query rewrite can determine the fresh portion of a materialized view on changes to a detail table only if PCT is available on the detail table using a partition key or partition marker.

#### 6.1.2 Partitioning a Materialized View

Partitioning a materialized view involves defining the materialized view with the standard Oracle partitioning clauses, as illustrated in the following example. This statement creates a materialized view called `part_sales_mv`, which uses three partitions, can be fast refreshed, and is eligible for query rewrite:

    CREATE MATERIALIZED VIEW part_sales_mv
    PARALLEL PARTITION BY RANGE (time_id)
    (PARTITION month1
          VALUES LESS THAN (TO_DATE('31-12-1998', 'DD-MM-YYYY'))
          PCTFREE 0
          STORAGE (INITIAL 8M)
          TABLESPACE sf1,
     PARTITION month2
          VALUES LESS THAN (TO_DATE('31-12-1999', 'DD-MM-YYYY'))
          PCTFREE 0
          STORAGE (INITIAL 8M)
          TABLESPACE sf2,
     PARTITION month3
          VALUES LESS THAN (TO_DATE('31-12-2000', 'DD-MM-YYYY'))
          PCTFREE 0
          STORAGE (INITIAL 8M)
          TABLESPACE sf3)
    BUILD DEFERRED
    REFRESH FAST
    ENABLE QUERY REWRITE AS
    SELECT s.cust_id, s.time_id,
      SUM(s.amount_sold) AS sum_dol_sales, SUM(s.quantity_sold) AS sum_unit_sales
      FROM sales s GROUP BY s.time_id, s.cust_id;

#### 6.1.3 Partitioning a Prebuilt Table

Alternatively, a materialized view can be registered to a partitioned prebuilt table. "Benefits of Partitioning a Materialized View" describes the benefits of partitioning a prebuilt table. The following example illustrates this:

    CREATE TABLE part_sales_tab_mv(time_id, cust_id, sum_dollar_sales, sum_unit_sale)
    PARALLEL PARTITION BY RANGE (time_id)
    (PARTITION month1
          VALUES LESS THAN (TO_DATE('31-12-1998', 'DD-MM-YYYY'))
          PCTFREE 0
          STORAGE (INITIAL 8M)
          TABLESPACE sf1,
     PARTITION month2
          VALUES LESS THAN (TO_DATE('31-12-1999', 'DD-MM-YYYY'))
          PCTFREE 0
          STORAGE (INITIAL 8M)
          TABLESPACE sf2,
    PARTITION month3
          VALUES LESS THAN (TO_DATE('31-12-2000', 'DD-MM-YYYY'))
          PCTFREE 0
          STORAGE (INITIAL 8M)
          TABLESPACE sf3)  AS
    SELECT s.time_id, s.cust_id, SUM(s.amount_sold) AS sum_dollar_sales,
      SUM(s.quantity_sold) AS sum_unit_sales
    FROM sales s GROUP BY s.time_id, s.cust_id;

    CREATE MATERIALIZED VIEW part_sales_tab_mv
    ON PREBUILT TABLE
    ENABLE QUERY REWRITE AS
    SELECT s.time_id,  s.cust_id, SUM(s.amount_sold) AS sum_dollar_sales,
         SUM(s.quantity_sold) AS sum_unit_sales
    FROM sales s GROUP BY s.time_id, s.cust_id;

In this example, the table `part_sales_tab_mv` has been partitioned over three months and then the materialized view was registered to use the prebuilt table. This materialized view is eligible for query rewrite because the `ENABLE` `QUERY` `REWRITE` clause has been included.

##### 6.1.3.1 Benefits of Partitioning a Materialized View

When a materialized view is partitioned on the partitioning key column or join dependent expressions of the detail table, it is more efficient to use a `TRUNCATE` `PARTITION` statement to remove one or more partitions of the materialized view during refresh and then repopulate the partition with new data. Oracle Database uses this variant of fast refresh (called PCT refresh) with partition truncation if the following conditions are satisfied in addition to other conditions described in "About Partition Change Tracking".

- The materialized view is partitioned on the partitioning key column or join dependent expressions of the detail table.

- If PCT is enabled using either the partitioning key column or join expressions, the materialized view should be range or list partitioned.

- PCT refresh is nonatomic.

#### 6.1.4 Rolling Materialized Views

When a data warehouse or data mart contains a time dimension, it is often desirable to archive the oldest information and then reuse the storage for new information. This is called the rolling window scenario. If the fact tables or materialized views include a time dimension and are horizontally partitioned by the time attribute, then management of rolling materialized views can be reduced to a few fast partition maintenance operations provided the unit of data that is rolled out equals, or is at least aligned with, the range partitions.

If you plan to have rolling materialized views in your data warehouse, you should determine how frequently you plan to perform partition maintenance operations, and you should plan to partition fact tables and materialized views to reduce the amount of system administration overhead required when old data is aged out. An additional consideration is that you might want to use data compression on your infrequently updated partitions.

You are not restricted to using range partitions. For example, a composite partition using both a time value and a key value could result in a good partition solution for your data.

**See Also:**

[Refreshing Materialized Views](refreshing-materialized-views.md) for further details regarding `CONSIDER` `FRESH` and for details regarding compression

### 6.2 About Materialized Views in Analytic Processing Environments

This section discusses the concepts used by analytic SQL and how relational databases can handle these types of queries. It also illustrates the best approach for creating materialized views using a common scenario.

The following topics contain additional information about materialized views in different environments:

- About Materialized Views and Analytic Views

- About Materialized Views and Hierarchical Cubes

- Benefits of Partitioning Materialized Views

- About Compressing Materialized Views

- About Materialized Views with Set Operators

#### 6.2.1 About Materialized Views and Analytic Views

Creating a materialized view over queries of an analytic view or a hierarchy is not supported.

#### 6.2.2 About Materialized Views and Hierarchical Cubes

While data warehouse environments typically view data in the form of a star schema, for analytical SQL queries, data is held in the form of a hierarchical cube. A hierarchical cube includes the data aggregated along the rollup hierarchy of each of its dimensions and these aggregations are combined across dimensions. It includes the typical set of aggregations needed for business intelligence queries.

Example 6-4 Hierarchical Cube

Consider a sales data set with two dimensions, each of which has a four-level hierarchy:

- Time, which contains (all times), year, quarter, and month.

- Product, which contains (all products), division, brand, and item.

This means there are 16 aggregate groups in the hierarchical cube. This is because the four levels of time are multiplied by four levels of product to produce the cube. Table 6-1 shows the four levels of each dimension.

Table 6-1 ROLLUP By Time and Product

| ROLLUP By Time       | ROLLUP By Product     |
|:---------------------|:----------------------|
| year, quarter, month | division, brand, item |
| year, quarter        | division, brand       |
| year                 | division              |
| all times            | all products          |

Note that as you increase the number of dimensions and levels, the number of groups to calculate increases dramatically. This example involves 16 groups, but if you were to add just two more dimensions with the same number of levels, you would have 4 x 4 x 4 x 4 = 256 different groups. Also, consider that a similar increase in groups occurs if you have multiple hierarchies in your dimensions. For example, the time dimension might have an additional hierarchy of fiscal month rolling up to fiscal quarter and then fiscal year. Handling the explosion of groups has historically been the major challenge in data storage for online analytical processing systems.

Typical online analytical queries [slice and dice](glossary.md) different parts of the cube comparing aggregations from one level to aggregation from another level. For instance, a query might find sales of the grocery division for the month of January, 2002 and compare them with total sales of the grocery division for all of 2001.

#### 6.2.3 Benefits of Partitioning Materialized Views

Materialized views with multiple aggregate groups give their best performance for refresh and query rewrite when partitioned appropriately.

PCT refresh in a rolling window scenario requires partitioning at the top level on some level from the time dimension. And, partition pruning for queries rewritten against this materialized view requires partitioning on `GROUPING_ID` column. Hence, the most effective partitioning scheme for these materialized views is to use composite partitioning (range-list on (`time`, `GROUPING_ID`) columns). By partitioning the materialized views this way, you enable:

- PCT refresh, thereby improving refresh performance.

- Partition pruning: only relevant aggregate groups are accessed, thereby greatly reducing the query processing cost.

If you do not want to use PCT refresh, you can just partition by list on `GROUPING_ID` column.

#### 6.2.4 About Compressing Materialized Views

You should consider data compression when using highly redundant data, such as tables with many foreign keys. In particular, materialized views created with the `ROLLUP` clause are likely candidates.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-MATERIALIZED-VIEW.md) for data compression syntax and restrictions

- "[About Storage And Table Compression for Materialized Views](basic-materialized-views.md)" for details regarding compression

#### 6.2.5 About Materialized Views with Set Operators

Oracle Database provides support for materialized views whose defining query involves set operators. Materialized views with set operators can now be created enabled for query rewrite. You can refresh the materialized view using either `ON` `COMMIT` or `ON` `DEMAND` refresh.

Fast refresh is supported if the defining query has the `UNION` `ALL` operator at the top level and each query block in the `UNION` `ALL`, meets the requirements of a materialized view with aggregates or materialized view with joins only. Further, the materialized view must include a constant column (known as a `UNION` `ALL` marker) that has a distinct value in each query block, which, in the following example, is columns `1 marker` and `2 marker`.

**See Also:**

"[Restrictions on Fast Refresh on Materialized Views with UNION ALL](basic-materialized-views.md)" for detailed restrictions on fast refresh for materialized views with `UNION` `ALL`.

##### 6.2.5.1 Examples of Materialized Views Using UNION ALL

The following examples illustrate creation of fast refreshable materialized views involving `UNION` `ALL`.

Example 6-5 Materialized View Using UNION ALL with Two Join Views

To create a `UNION` `ALL` materialized view with two join views, the materialized view logs must have the rowid column and, in the following example, the `UNION` `ALL` marker is the columns, `1 marker` and `2 marker`.

    CREATE MATERIALIZED VIEW LOG ON sales WITH ROWID;
    CREATE MATERIALIZED VIEW LOG ON customers WITH ROWID;

    CREATE MATERIALIZED VIEW unionall_sales_cust_joins_mv
    REFRESH FAST ON COMMIT
    ENABLE QUERY REWRITE AS
    (SELECT c.rowid crid, s.rowid srid, c.cust_id, s.amount_sold, 1 marker
    FROM sales s, customers c
    WHERE s.cust_id = c.cust_id AND c.cust_last_name = 'Smith')
    UNION ALL
    (SELECT c.rowid crid, s.rowid srid, c.cust_id, s.amount_sold, 2 marker
    FROM sales s, customers c
    WHERE s.cust_id = c.cust_id AND c.cust_last_name = 'Brown');

Example 6-6 Materialized View Using UNION ALL with Joins and Aggregates

The following example shows a `UNION` `ALL` of a materialized view with joins and a materialized view with aggregates. A couple of things can be noted in this example. Nulls or constants can be used to ensure that the data types of the corresponding `SELECT` list columns match. Also, the `UNION` `ALL` marker column can be a string literal, which is `'Year' umarker`, `'Quarter' umarker`, or `'Daily' umarker` in the following example:

    CREATE MATERIALIZED VIEW LOG ON sales WITH ROWID, SEQUENCE
    (amount_sold, time_id)
    INCLUDING NEW VALUES;

    CREATE MATERIALIZED VIEW LOG ON times WITH ROWID, SEQUENCE
      (time_id, fiscal_year, fiscal_quarter_number, day_number_in_week)
    INCLUDING NEW VALUES;

    CREATE MATERIALIZED VIEW unionall_sales_mix_mv
    REFRESH FAST ON DEMAND AS
    (SELECT 'Year' umarker, NULL, NULL, t.fiscal_year,
            SUM(s.amount_sold) amt, COUNT(s.amount_sold), COUNT(*)
     FROM sales s, times t
     WHERE s.time_id = t.time_id
     GROUP BY t.fiscal_year)
    UNION ALL
    (SELECT 'Quarter' umarker, NULL, NULL, t.fiscal_quarter_number,
            SUM(s.amount_sold) amt, COUNT(s.amount_sold), COUNT(*)
    FROM sales s, times t
    WHERE s.time_id = t.time_id and t.fiscal_year = 2001
    GROUP BY t.fiscal_quarter_number)
    UNION ALL
    (SELECT 'Daily' umarker, s.rowid rid, t.rowid rid2, t.day_number_in_week,
            s.amount_sold amt, 1, 1
    FROM sales s, times t
    WHERE s.time_id = t.time_id
    AND t.time_id between '01-Jan-01' AND '01-Dec-31');

### 6.3 About Materialized Views and Models

Models, which provide array-based computations in SQL, can be used in materialized views. Because the `MODEL` clause calculations can be expensive, you may want to use two separate materialized views: one for the model calculations and one for the `SELECT` ... `GROUP` `BY` query. For example, instead of using one, long materialized view, you could create the following materialized views:

    CREATE MATERIALIZED VIEW my_groupby_mv
    REFRESH FAST
    ENABLE QUERY REWRITE AS
    SELECT country_name country, prod_name prod, calendar_year year,
      SUM(amount_sold) sale, COUNT(amount_sold) cnt, COUNT(*) cntstr
    FROM sales, times, customers, countries, products
    WHERE sales.time_id = times.time_id AND
          sales.prod_id = products.prod_id AND
          sales.cust_id = customers.cust_id AND
          customers.country_id = countries.country_id
    GROUP BY country_name, prod_name, calendar_year;

    CREATE MATERIALIZED VIEW my_model_mv
    ENABLE QUERY REWRITE AS
    SELECT country, prod, year, sale, cnt
    FROM my_groupby_mv
    MODEL PARTITION BY(country) DIMENSION BY(prod, year)
       MEASURES(sale s) IGNORE NAV
    (s['Shorts', 2000] =  0.2 * AVG(s)[CV(), year BETWEEN 1996 AND 1999],
    s['Kids Pajama', 2000] = 0.5 * AVG(s)[CV(), year BETWEEN 1995 AND 1999],
    s['Boys Pajama', 2000] = 0.6 * AVG(s)[CV(), year BETWEEN 1994 AND 1999],
    ...
    <hundreds of other update rules>);

By using two materialized views, you can incrementally maintain the materialized view `my_groupby_mv`. The materialized view `my_model_mv` is on a much smaller data set because it is built on `my_groupby_mv` and can be maintained by a complete refresh.

Materialized views with models can use complete refresh or PCT refresh only, and are available for partial text query rewrite only.

**See Also:**

[SQL for Modeling](sql-modeling-data-warehouses.md) for further details about model calculations

### 6.4 About Security Issues with Materialized Views

To create a materialized view in your own schema, you must have the `CREATE` `MATERIALIZED` `VIEW` privilege and the `SELECT` or `READ` privilege to any tables referenced that are in another schema. To create a materialized view in another schema, you must have the `CREATE` `ANY` `MATERIALIZED` `VIEW` privilege and the owner of the materialized view needs `SELECT` or `READ` privileges to the tables referenced if they are from another schema. Moreover, if you enable query rewrite on a materialized view that references tables outside your schema, you must have the `GLOBAL` `QUERY` `REWRITE` privilege or the `QUERY` `REWRITE` object privilege on each table outside your schema.

If the materialized view is on a prebuilt container, the creator, if different from the owner, must have the `READ WITH GRANT` or `SELECT` `WITH` `GRANT` privilege on the container table.

If you continue to get a privilege error while trying to create a materialized view and you believe that all the required privileges have been granted, then the problem is most likely due to a privilege not being granted explicitly and trying to inherit the privilege from a role instead. The owner of the materialized view must have explicitly been granted `SELECT` or `READ` access to the referenced tables if the tables are in a different schema.

If the materialized view is being created with `ON` `COMMIT` `REFRESH` specified, then the owner of the materialized view requires an additional privilege if any of the tables in the defining query are outside the owner's schema. In that case, the owner requires the `ON` `COMMIT` `REFRESH` system privilege or the `ON` `COMMIT` `REFRESH` object privilege on each table outside the owner's schema.

**See Also:**

Querying Materialized Views with Virtual Private Database (VPD)

#### 6.4.1 Querying Materialized Views with Virtual Private Database (VPD)

For all security concerns, a materialized view serves as a view that happens to be materialized when you are directly querying the materialized view. When creating a view or materialized view, the owner must have the necessary permissions to access the underlying base relations of the view or materialized view that they are creating. With these permissions, the owner can publish a view or materialized view that other users can access, assuming they have been granted access to the view or materialized view.

Using materialized views with Virtual Private Database is similar. When you create a materialized view, there must not be any VPD policies in effect against the base relations of the materialized view for the owner of the materialized view. If any VPD policies exist, then you must use the `USING TRUSTED CONSTRAINTS` clause when creating the materialized view. The owner of the materialized view may establish a VPD policy on the new materialized view. Users who access the materialized view are subject to the VPD policy on the materialized view. However, they are not additionally subject to the VPD policies of the underlying base relations of the materialized view, because security processing of the underlying base relations is performed against the owner of the materialized view.

This section contains the following topics:

- Using Query Rewrite with Virtual Private Database

- Restrictions with Materialized Views and Virtual Private Database

##### 6.4.1.1 Using Query Rewrite with Virtual Private Database

When you access a materialized view using query rewrite, the materialized view serves as an access structure much like an index. As such, the security implications for materialized views accessed in this way are much the same as for indexes: all security checks are performed against the relations specified in the request query. The index or materialized view is used to speed the performance of accessing the data, not provide any additional security checks. Thus, the presence of the index or materialized view presents no additional security checking.

This holds true when you are accessing a materialized view using query rewrite in the presence of VPD. The request query is subject to any VPD policies that are present against the relations specified in the query. Query rewrite may rewrite the query to use a materialize view instead of accessing the detail relations, but only if it can guarantee to deliver exactly the same rows as if the rewrite had not occurred. Specifically, query rewrite must retain and respect any VPD policies against the relations specified in the request query. However, any VPD policies against the materialized view itself do not have effect when the materialized view is accessed using query rewrite. This is because the data is already protected by the VPD policies against the relations in the request query.

##### 6.4.1.2 Restrictions with Materialized Views and Virtual Private Database

Query rewrite does not use its full and partial text match modes with request queries that include relations with active VPD policies, but it does use general rewrite methods. This is because VPD transparently transforms the request query to affect the VPD policy. If query rewrite were to perform a text match transformation against a request query with a VPD policy, the effect would be to negate the VPD policy.

In addition, when you create or refresh a materialized view, the owner of the materialized view must not have any active VPD policies in effect against the base relations of the materialized view, or an error is returned. The materialized view owner must either have no such VPD policies, or any such policy must return `NULL`. This is because VPD would transparently modify the defining query of the materialized view such that the set of rows contained by the materialized view would not match the set of rows indicated by the materialized view definition.

One way to work around this restriction yet still create a materialized view containing the desired VPD-specified subset of rows is to create the materialized view in a user account that has no active VPD policies against the detail relations of the materialized view. In addition, you can include a predicate in the `WHERE` clause of the materialized view that embodies the effect of the VPD policy. When query rewrite attempts to rewrite a request query that has that VPD policy, it matches up the VPD-generated predicate on the request query with the predicate you directly specify when you create the materialized view.

### 6.5 Invalidating Materialized Views

Dependencies related to materialized views are automatically maintained to ensure correct operation. When a materialized view is created, the materialized view depends on the detail tables referenced in its definition. Any DML operation, such as an `INSERT`, or `DELETE`, `UPDATE`, or DDL operation on any dependency in the materialized view will cause it to become invalid. To revalidate a materialized view, use the `ALTER` `MATERIALIZED` `VIEW` `COMPILE` statement.

A materialized view is automatically revalidated when it is referenced. In many cases, the materialized view will be successfully and transparently revalidated. However, if a column has been dropped in a table referenced by a materialized view or the owner of the materialized view did not have one of the query rewrite privileges and that privilege has now been granted to the owner, you should use the following statement to revalidate the materialized view:

    ALTER MATERIALIZED VIEW mview_name COMPILE;

The state of a materialized view can be checked by querying the data dictionary views `USER_MVIEWS` or `ALL_MVIEWS`. The column `STALENESS` will show one of the values `FRESH`, `STALE`, `UNUSABLE`, `UNKNOWN`, `UNDEFINED`, or `NEEDS_COMPILE` to indicate whether the materialized view can be used. The state is maintained automatically. However, if the staleness of a materialized view is marked as `NEEDS_COMPILE`, you could issue an `ALTER` `MATERIALIZED` `VIEW` ... `COMPILE` statement to validate the materialized view and get the correct staleness state. If the state of a materialized view is `UNUSABLE`, you must perform a complete refresh to bring the materialized view back to the `FRESH` state. If the materialized view is based on a prebuilt table that you never refresh, you must drop and re-create the materialized view. The staleness of remote materialized views is not tracked. Thus, if you use remote materialized views for rewrite, they are considered to be trusted.

### 6.6 Altering Materialized Views

The following modifications can be made to a materialized view:

- Change its refresh option (`FAST/FORCE/COMPLETE/NEVER`).

- Change its refresh mode (`ON` `COMMIT/ON` `DEMAND`).

- Recompile it.

- Enable or disable its use for query rewrite.

- Consider it fresh.

- Partition maintenance operations.

- Enable on-query computation

All other changes are achieved by dropping and then re-creating the materialized view. The success of a modification operation depends on whether the requirement for the change is satisfied. For example, a fast refresh succeeds if materialized view logs exist on all the base tables.

The `COMPILE` clause of the `ALTER` `MATERIALIZED` `VIEW` statement can be used when the materialized view has been invalidated. This compile process is quick, and allows the materialized view to be used by query rewrite again.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/SQL-Statements-ALTER-LIBRARY-to-ALTER-SESSION.md) for further information about the `ALTER` `MATERIALIZED` `VIEW` statement

- "Invalidating Materialized Views"

### 6.7 Using Real-time Materialized Views

Real-time materialized views provide fresh data to user queries even when the materialized view is marked as stale.

**See Also:**

- Overview of Real-time Materialized Views

- Creating Real-time Materialized Views

- Converting an Existing Materialized View into a Real-time Materialized View

- Enabling Query Rewrite to Use Real-time Materialized Views

- Using Real-time Materialized Views During Query Rewrite

- Using Real-time Materialized Views for Direct Query Access

- Listing Real-time Materialized Views

- Improving Real-time Materialized Views Performance

#### 6.7.1 Overview of Real-time Materialized Views

A real-time materialized view is a type of materialized view that provides fresh data to user queries even when the materialized view is not in sync with its base tables because of data changes.

Unless a SQL session is set to stale tolerated mode, a materialized view that is marked stale cannot be used for query rewrite. Organizations that require real-time data typically use the `ON COMMIT` refresh mode to ensure that the materialized view is updated with changes made to the base tables. However, when DML changes to the base tables are huge and very frequent, this mode may result in resource contention and reduced refresh performance. Real-time materialized views provide a lightweight solution for obtaining fresh data from stale materialized views by recomputing the data on the fly.

Real-time materialized views can use any available out-of-place refresh method including log-based or PCT based refresh. They can be used either with on demand or scheduled automatic refresh, but not with automatic refresh specified using the `ON COMMIT` clause.

##### Advantages of Real-time Materialized Views

- Provides improved availability for materialized views

- Provides fresh data for user queries that access a materialized view that may be stale

##### How Do Real-time Materialized Views Work?

Real-time materialized views use a technique called on-query computation to provide fresh data with stale materialized views. When a query accesses a real-time materialized view, Oracle Database first checks if the real-time materialized view is marked as stale. If it is not stale, then the required data is provided using the real-time materialized view as it is. If the real-time materialized view is marked as stale, then the on-query computation technique is used to generate the fresh data and return the correct query result.

Real-time materialized views use a technique that is similar log-based refresh to provide fresh data with stale materialized view. They combine the existing data with the changes that are recorded in change logs to obtain the latest data. However, unlike log-based refresh, real-time materialized views do not use the materialized view logs to update the data in the real-time materialized view. Instead, when a query accesses a stale real-time materialized view, the data that is recomputed using on-query computation is used directly to answer the query.

A real-time materialized view is created by using the `ON QUERY COMPUTATION` clause in the materialized view definition.

##### 6.7.1.1 Restrictions on Using Real-time Materialized Views

Using real-time materialized views is subject to certain restrictions.

- Real-time materialized views cannot be used when:

  - one or more materialized view logs created on the base tables are either unusable or nonexistent.

  - out-of-place, log-based or PCT refresh is not feasible for the change scenarios.

  - automatic refresh is specified using the `ON COMMIT` clause.

- If a real-time materialized view is a nested materialized view that is defined on top of one or more base materialized views, then query rewrite occurs only if all the base materialized views are fresh. If one or more base materialized views are stale, then query rewrite is not performed using this real-time materialized view.

The cursors of queries that directly access real-time materialized views are not shared.

##### 6.7.1.2 About Accessing Real-time Materialized Views

As with materialized views, multiple methods exist to access data stored in real-time materialized views.

Data stored in real-time materialized views can be accessed in one of the following ways:

- Query rewrite

  A user query that is similar to the real-time materialized view definition is rewritten to use the real-time materialized view.

- Direct access of real-time materialized views

  A user query directly references the real-time materialized view by using its name.

In both scenarios, the content of a real-time materialized view can be accessed as stale data or can trigger an on-query computation of the correct result. Whether or not on-query computation is triggered depends on the environment and the actual SQL statement.

The output of the `EXPLAIN PLAN` statement contains messages indicating if on-query computation was used for a particular user query.

**See Also:**

- Using Real-time Materialized Views for Direct Query Access

- Using Real-time Materialized Views During Query Rewrite

#### 6.7.2 Creating Real-time Materialized Views

To create a real-time materialized view, use the` ON QUERY COMPUTATION` clause in the `CREATE MATERIALIZED VIEW` statement.

You can create real-time materialized views even if they are not applicable for on-query computation for all change scenarios. The minimum requirement to create a real-time materialized view is that it supports out-of-place refresh for `INSERT` operations. If other change scenarios, such as mixed DML operations, are encountered, then on-query computation may not be feasible for all types of real-time materialized views.

Real-time materialized view must use an out-of-place log-based refresh mechanism (including PCT refresh). The `ON COMMIT` refresh mode cannot be used for real-time materialized views.

To create a real-time materialized view:

1.  Ensure that materialized view logs exist on all the base tables of the real-time materialized view.
2.  Create materialized view logs for all the tables on which the real-time materialized view is based.
3.  Create the real-time materialized view by including the `ENABLE ON QUERY COMPUTATION` clause in the `CREATE MATERIALIZED VIEW` statement.

Example 6-7 Creating a Real-time Materialized View

This example creates a real-time materialized view called `SUM_SALES_RTMV` which is based on data aggregated from the `SALES` and `PRODUCTS` tables in the `SH` schema. Before you create the real-time materialized view ensure that the required prerequisites are met.

1.  Create materialized view logs on the base tables `SALES` and `PRODUCTS`.

    The following command creates a materialized view log on the `SALES` table:

        CREATE MATERIALIZED VIEW LOG ON sales
        WITH SEQUENCE, ROWID
        (prod_id, quantity_sold, amount_sold)
        INCLUDING NEW VALUES;

    The following command creates a materialized view log on the `PRODUCTS` table.

        CREATE MATERIALIZED VIEW LOG ON products
        WITH ROWID
        (prod_id, prod_name, prod_category, prod_subcategory)
        INCLUDING NEW VALUES;

2.  Create a real-time materialized view by including the `ON QUERY COMPUTATION` clause in the `CREATE MATERIALIZED VIEW` statement. The fast refresh method is used for this real-time materialized view and the `ENABLE QUERY REWRITE` clause indicates that query rewrite must be enabled.

        CREATE MATERIALIZED VIEW sum_sales_rtmv
        REFRESH FAST ON DEMAND
        ENABLE QUERY REWRITE
        ENABLE ON QUERY COMPUTATION
        AS
        SELECT prod_name, SUM(quantity_sold) AS sum_qty, COUNT(quantity_sold) AS cnt_qty, SUM(amount_sold) AS sum_amt,
             COUNT(amount_sold) AS cnt_amt, COUNT(*) AS cnt_star
        FROM sales, products
        WHERE sales.prod_id = products.prod_id
        GROUP BY prod_name;

After the `SUM_SALES_RTMV` real-time materialized view is created, assume that the following query is run.

    SELECT prod_name, SUM(quantity_sold), SUM(amount_sold)
    FROM sales, products
    WHERE sales.prod_id = products.prod_id
    GROUP BY prod_name;

If `SUM_SALES_RTMV` is not stale, then the query result is returned using the data stored in this real-time materialized view. However, if `SUM_SALES_RTMV` is stale and the cost of rewriting the query using the materialized view with on-query computation is lower than the base table access, then the query is answered by combining the delta changes in the materialized view logs on the `SALES` and `PRODUCTS` tables with the data in the real-time materialized view `SUM_SALES_RTMV`.

#### 6.7.3 Converting an Existing Materialized View into a Real-time Materialized View

If the prerequisites for a real-time materialized view are met, then an existing materialized view can be converted into a real-time materialized view by altering its definition and enabling on-query computation.

To convert a materialized view into a real-time materialized view:

- Modify the materialized view definition and enable on-query computation by using the `ON QUERY COMPUTATION` clause in the `ALTER MATERIALIZED VIEW` statement.

You can convert a real-time materialized view into a regular materialized view by disabling on-query computation using the `DISABLE ON QUERY COMPUTATION` clause in the `ALTER MATERIALIZED VIEW` statement.

Example 6-8 Converting a Materialized View into a Real-time Materialized View

The materialized view `SALES_RTMV` is based on the `SALES`, `TIMES`, and `PRODUCTS` tables and uses fast refresh. Materialized view logs exist on all three base tables. You want to modify this materialized view and convert it into a real-time materialized view.

1.  Modify the materialized view definition and include the `ON QUERY COMPUTATION` clause to change it into a real-time materialized view.

        ALTER MATERIALIZED VIEW sales_rtmv ENABLE ON QUERY COMPUTATION;

2.  Query the `DBA_MVIEWS` view to determine if on-query computation is enabled for `SALES_RTMV`.

        SELECT mview_name, on_query_computation
        FROM dba_mviews
        WHERE mview_name = 'SALES_RTMV';

#### 6.7.4 Enabling Query Rewrite to Use Real-time Materialized Views

For the query rewrite mechanism to rewrite a user query to use real-time materialized views, query rewrite must be enabled for the real-time materialized view.

You can enable query rewrite for a real-time materialized view either at creation time or subsequently, by modifying the definition of the real-time materialized view. The `ENABLE QUERY REWRITE` clause is used to enable query rewrite.

To enable query rewrite for an existing real-time materialized view:

- Run the `ALTER MATERIALIZED VIEW` command and include the `ENABLE QUERY REWRITE` clause.

Example 6-9 Enabling Query Rewrite for Real-time Materialized Views

The real-time materialized view `my_rtmv` uses the fast refresh mechanism. You want to modify the definition of this real-time materialized view and specify that the query rewrite mechanism must consider this real-time materialized view while rewriting queries.

The following command enables query rewrite for `my_rtmv`:

`ALTER MATERIALIZED VIEW my_rtmv ENABLE QUERY REWRITE;`

#### 6.7.5 Using Real-time Materialized Views During Query Rewrite

Query rewrite can use a real-time materialized view to provide results to user queries, even if the real-time materialized view is stale, if query rewrite is enabled for the real-time materialized view. A nested real-time materialized view is eligible for query rewrite only if all its base real-time materialized views are fresh.

When a user query is run, query rewrite first checks if a fresh materialized view is available to provide the required data. If a suitable materialized view does not exist, then query rewrite looks for a real-time materialized view that can be used to rewrite the user query. A fresh materialized view is preferred over a real-time materialized view because some overhead is incurred in computing fresh data for real-time materialized view. Next, the cost based optimizer determines the cost of the SQL query with on-query computation and then decides if the real-time materialized view will be used to answer this user query.

If the `QUERY_REWRITE_INTEGRITY` mode of the current SQL session is set to `STALE_TOLERATED`, then on-query computation will not be used during query rewrite. The `STALE_TOLERATED` rewrite mode indicates that fresh results are not required to satisfy a query, so on-query computation is not necessary.

For query rewrite to use a real-time materialized view:

1.  Ensure that `QUERY_REWRITE_INTEGRITY` is set to either `ENFORCED` or `TRUSTED` mode. `QUERY_REWRITE_INTEGRITY` mode should not be set to `STALE_TOLERATED` mode.
2.  Run a user query that matches the SQL query that was used to define the real-time materialized view.
    Any query that can be rewritten to take advantage of a real-time materialized view will use the real-time materialized view with on-query computation.

    Use `EXPLAIN PLAN` to verify that the query was rewritten using the real-time materialized view.

Example 6-10 Using Real-time Materialized Views During Query Rewrite

This example creates a real-time materialized view with query rewrite enabled and then demonstrates that it was used by query rewrite to provide data for a user query.

1.  Create a materialized view log on the `SALES` table, which is the base table for the real-time materialized view being created.

2.  Create a real-time materialized view `mav_sum_sales` with query rewrite enabled.

        CREATE MATERIALIZED VIEW mav_sum_sales
        REFRESH FAST ON DEMAND
        ENABLE ON QUERY COMPUTATION
        ENABLE QUERY REWRITE
        AS
        SELECT prod_id, sum(quantity_sold) as sum_qty, count(quantity_sold) as cnt_qty,
               sum(amount_sold) sum_amt, count(amount_sold) cnt_amt, count(*) as cnt_star
        FROM sales
        GROUP BY prod_id;

3.  Run the following query:

        SELECT prod_id, sum(quantity_sold), sum(amount_sold)
        FROM  sales
        WHERE prod_id < 1000
        GROUP BY prod_id;

    Observe that the query is similar to the one used to define the real-time materialized view `mav_sum_sales`. Because no other materialized view with a definition that is similar to the query exists, query rewrite can use the `mav_sum_sales` real-time materialized view to determine the query result. You can verify that query rewrite has taken place by checking the SQL cursor cache (for example, with `DBMS_XPLAN`), using SQL Monitor, or using `EXPLAIN PLAN`.

    The internally rewritten query that uses `mav_sum_sales` is analogous to the following statement:

        SELECT prod_id, sum_qty, sum_amt
        FROM  mav_sum_sales
        WHERE prod_id < 1000;

4.  Verify that the real-time materialized view was used to provide the query result. Use the `EXPLAIN PLAN` statement to view the execution plan for the query.

    The following execution plan shows direct access to the real-time materialized view. If the materialized view is stale, then the execution plan will become more complex and include access to other objects (for example, the materialized view logs), depending on the outstanding DML operations.

        EXPLAIN PLAN for SELECT prod_id, sum(quantity_sold), sum(amount_sold) FROM sales WHERE prod_id < 1000 GROUP BY prod_id;
        SELECT plan_table_output FROM table(dbms_xplan.display('plan_table',null,'serial'));

        PLAN_TABLE_OUTPUT
        -----------------------------------------------------------------------------------------------
        Plan hash value: 13616844
        -----------------------------------------------------------------------------------------------
        | Id  | Operation             | Name          | Rows  | Bytes | Cost (%CPU) | Time      |
        -----------------------------------------------------------------------------------------------
        | 0   | SELECT STATEMENT      |               | 92    | 3588  | 3  (0)      | 00:00:01  |
        | *1  | MAT_VIEW ACCESS FULL  | MAV_SUM_SALES | 92    | 3588  | 3  (0)      | 00:00:01  |
        -----------------------------------------------------------------------------------------------
        Predicate Information (identified by operation id):
        ---------------------------------------------------
           1 - filter("PROD_ID"<1000)

        Note
        -----
           - dynamic statistics used: dynamic sampling (level=2)

        17 rows selected.

#### 6.7.6 Using Real-time Materialized Views for Direct Query Access

You can access a real-time materialized view directly by referencing the name of the real-time materialized view in a query.

If the real-time materialized view specified in a user query is fresh, then the required data is directly fetched from the real-time materialized view. If the real-time materialized view is stale, then you must use the `FRESH_MV` hint to perform on-query computation and obtain fresh data. Oracle Database does not automatically perform on-query computation for a real-time materialized view that is accessed directly in a user query.

To obtain fresh data from a stale real-time materialized view when directly accessing the real-time materialized view:

- Use the `FRESH_MV` hint in the user query to indicate that on-query computation must be performed.

Example 6-11 Creating a Real-Time Materialized View and Using it in Queries

This example creates a real-time materialized view `MY_RTMV` that is based on the `SALES_NEW` table. The `SALES_NEW` table is created as a copy of the `SH.SALES` table. A row is inserted into the base table after the real-time materialized view is created. Next the `fresh_mv` hint is used to access fresh data from the real-time materialized view by using the materialized view name in a user query.

1.  Create a materialized view log on the base table `sales_new`.

    Materialized view logs on the base table are mandatory for creating real-time materialized views.

        CREATE MATERIALIZED VIEW LOG on sales_new
        WITH sequence, ROWID (prod_id, cust_id, time_id, channel_id, promo_id, quantity_sold, amount_sold)
        INCLUDING NEW VALUES;

2.  Create a real-time materialized view called `my_rtmv` with `sales_new` as the base table.

    The `ON QUERY COMPUTATION` clause indicates that a real-time materialized view is created. The refresh mode specified is log-based fast refresh. Query rewrite is enabled for the real-time materialized view.

        CREATE MATERIALIZED VIEW my_rtmv
        REFRESH FAST
        ENABLE ON QUERY COMPUTATION
        ENABLE QUERY REWRITE
        AS
        SELECT prod_id, cust_id, channel_id, sum(quantity_sold) sum_q, count(quantity_sold) cnt_q, avg(quantity_sold) avg_q,
                sum(amount_sold) sum_a, count(amount_sold) cnt_a, avg(amount_sold) avg_a
        FROM sales_new
        GROUP BY prod_id, cust_id, channel_id;

3.  Insert a row into `sales_new`, the base table of the real-time materialized view and commit this change.

        INSERT INTO sales_new (prod_id, cust_id, time_id, channel_id, promo_id, quantity_sold, amount_sold)
            VALUES (116,100450, sysdate,9,9999,10,350);

        COMMIT;

4.  Query the real-time materialized view directly to display data for the row that was added to the real-time materialized view’s base table in the previous step.

        SELECT * from my_rtmv
        WHERE prod_id = 116 AND cust_id=100450 AND channel_id = 9;

        PROD_ID   CUST_ID   CHANNEL_ID   SUM_Q   CNT_Q    AVG_Q    SUM_A    CNT_A    AVG_A
        -------   -------   ----------   -----   -----    -----    -----    -----    ------
        116       100450    9            1       1        1        11.99    1        11.99

    Note that the query result does not display the updated value for this data. This is because the real-time materialized view has not yet been refreshed with the changes made to its base table.

5.  Include the `FRESH_MV` hint while querying the real-time materialized view to display the row updated in the base table.

        SELECT /*+ fresh_mv */ * FROM my_rtmv
        WHERE prod_id = 116 AND cust_id=100450 AND channel_id = 9;

        PROD_ID   CUST_ID   CHANNEL_ID  SUM_Q   CNT_Q   AVG_Q    SUM_A    CNT_A    AVG_A
        -------   -------   ----------  -----   -----   -----    -----    -----    ------
        116       100450    9           11      2       5.5      361.99   2        180.995

    Notice that this time the updated row is displayed. This is because the `FRESH_MV` hint triggers on-query computation for the real-time materialized view and recomputed the fresh data.

#### 6.7.7 Listing Real-time Materialized Views

The `ON_QUERY_COMPUTATION` column in the data dictionary views `ALL_MVIEWS`, `DBA_MVIEWS`, and `USER_MVIEWS` indicates if a materialized view is a real-time materialized view.

A value of Y in the `ON_QUERY_COMPUTATION` column indicates a real-time materialized view.

To list all real-time materialized views in your user schema:

- Query the `USER_MVIEWS` view and display details of the materialized view with the `ON_QUERY_COMPUTATION` column set to Y.

Example 6-12 Listing Real-time Materialized Views in the Current User’s Schema

    SELECT owner, mview_name, rewrite_enabled, staleness
    FROM user_mviews
    WHERE on_query_computation = 'Y';

    OWNER   MVIEW_NAME        REWRITE_ENABLED   STALENESS
    ------  ------------    ------------------- ------------
    SH      SALES_RTMV          N               FRESH
    SH      MAV_SUM_SALES       Y               FRESH
    SH      MY_SUM_SALES_RTMV   Y               FRESH
    SH      NEW_SALES_RTMV      Y               STALE

#### 6.7.8 Improving Real-time Materialized Views Performance

To obtain better performance for user queries that use a real-time materialized view, you can follow certain guidelines.

Use the following guidelines with real-time materialized views:

- Frequently refresh real-time materialized views to enhance the performance of queries that may use these real-time materialized views.

  Since real-time materialized views work by combining the delta changes to the base tables with the existing materialized view data, query response time is enhanced when the delta changes to be computed are small. With more outstanding DML operations, on-query computation can become more complex (and expensive), up to the point where direct base table access can become more efficient (in case of query rewrite).

- Collect statistics for the base tables, the real-time materialized view, and the materialized view logs to enable the optimizer to accurately determine the cost of a query.

  For query rewrite, the cost-based rewrite mechanism uses the optimizer to determine whether the rewritten query should be used. The optimizer uses statistics to determine the cost.
