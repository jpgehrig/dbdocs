Oracle Text provides ways to improve your query and indexing performance.

This chapter contains the following topics:

- Optimizing Queries with Statistics

- Optimizing Queries for Response Time

- Optimizing Queries for Throughput

- Composite Domain Index in Oracle Text

- Performance Tuning with CDI

- Solving Index and Query Bottlenecks by Using Tracing

- Using Parallel Queries

- Tuning Queries with Blocking Operations

- Frequently Asked Questions About Query Performance

- Frequently Asked Questions About Indexing Performance

- Frequently Asked Questions About Updating the Index

### 10.1 Optimizing Queries with Statistics

Query optimization with statistics uses the collected statistics on the tables and indexes in a query to select an execution plan that can process the query in the most efficient manner. As a general rule, Oracle recommends that you collect statistics on your base table if you are interested in improving your query performance. Optimizing with statistics enables a more accurate estimation of the selectivity and costs of the `CONTAINS` predicate and thus a better execution plan.

The optimizer attempts to choose the best execution plan based on the following parameters:

- The selectivity on the `CONTAINS` predicate

- The selectivity of other predicates in the query

- The CPU and I/O costs of processing the `CONTAINS` predicates

The following topics discuss how to use statistics with the extensible query optimizer:

- Collecting Statistics

- Query Optimization with Statistics Example

- Re-Collecting Statistics

- Deleting Statistics

**Note:**

Importing and exporting statistics on domain indexes, including Oracle Text indexes, is not supported with the `DBMS_STATS` package. For more information on importing and exporting statistics, see the [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md).

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-CONTAINS-query-operators.md) for information on the `CONTAINS` query operator

#### 10.1.1 Collecting Statistics

By default, Oracle Text uses the cost-based optimizer (CBO) to determine the best execution plan for a query.

To enable the optimizer to better estimate costs, calculate the statistics on the table you queried table:

    ANALYZE TABLE <table_name> COMPUTE STATISTICS;

Alternatively, estimate the statistics on a sample of the table:

    ANALYZE TABLE <table_name> ESTIMATE STATISTICS 1000 ROWS;

or

    ANALYZE TABLE <table_name> ESTIMATE STATISTICS 50 PERCENT;

You can also collect statistics in parallel with the `DBMS_STATS.GATHER_TABLE_STATS` procedure:

    begin

    DBMS_STATS.GATHER_TABLE_STATS('owner', 'table_name',
                                           estimate_percent=>50,
                                           block_sample=>TRUE,
                                           degree=>4) ;

    end  ;

These statements collect statistics on all objects associated with `table_name,` including the table columns and any indexes (b-tree, bitmap, or Text domain) associated with the table.

To re-collect the statistics on a table, enter the `ANALYZE` statement as many times as necessary or use the `DBMS_STATS` package.

By collecting statistics on the Text domain index, the CBO in Oracle Database can perform the following tasks:

- Estimate the selectivity of the `CONTAINS` predicate

- Estimate the I/O and CPU costs of using the Oracle Text index (that is, the cost of processing the `CONTAINS` predicate by using the domain index)

- Estimate the I/O and CPU costs of each invocation of `CONTAINS`

Knowing the selectivity of a `CONTAINS` predicate is useful for queries that contain more than one predicate, such as in structured queries. This way the CBO can better decide whether to use the domain index to evaluate `CONTAINS` or to apply the `CONTAINS` predicate as a post filter.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/ANALYZE.md) for more information about the `ANALYZE` statement

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md) for information about `DBMS_STATS` package

#### 10.1.2 Query Optimization with Statistics Example

The following structured query provides an example for optimizing statistics:

    select score(1) from tab where contains(txt, 'freedom', 1)  > 0 and author = 'King' and year > 1960;

Assume the following:

- The author column is of type `VARCHAR2` and the year column is of type `NUMBER.`

- A b-tree index on the `author` column.

- The structured `author` predicate is highly selective with respect to the `CONTAINS` predicate and the `year` predicate. That is, the structured predicate (author = 'King') returns a much smaller number of rows with respect to the `year` and `CONTAINS` predicates individually, say 5 rows returned versus 1000 and 1500 rows, respectively.

In this situation, Oracle Text can execute this query more efficiently by first scanning a b-tree index range on the structured predicate (author = 'King'), then accessing a table by rowid, and then applying the other two predicates to the rows returned from the b-tree table access.

**Note:**

When statistics are not collected for a Oracle Text index, the CBO assumes low selectivity and index costs for the `CONTAINS` predicate.

#### 10.1.3 Re-Collecting Statistics

After synchronizing your index, you can re-collect statistics on a single index to update the cost estimates.

If your base table was reanalyzed before the synchronization, it is sufficient to analyze the index after the synchronization without reanalyzing the entire table.

To re-collect statistics, enter one of the following statements:

    ANALYZE INDEX <index_name> COMPUTE STATISTICS;

    ANALYZE INDEX <index_name> ESTIMATE STATISTICS SAMPLE 50 PERCENT;

#### 10.1.4 Deleting Statistics

Delete the statistics associated with a table:

    ANALYZE TABLE <table_name> DELETE STATISTICS;

Delete statistics on one index:

    ANALYZE INDEX <index_name> DELETE STATISTICS;

### 10.2 Optimizing Queries for Response Time

By default, Oracle Text optimizes queries for throughput so that queries return all rows in the shortest time possible.

However, in many cases, especially in a web application, you must optimize queries for response time, because you are only interested in obtaining the first few hits of a potentially large hitlist in the shortest time possible.

The following sections describe some ways to optimize `CONTAINS` queries for response time:

- Other Factors that Influence Query Response Time

- Improved Response Time with FIRST_ROWS(n) Hint for ORDER BY Queries

- Improved Response Time Using the DOMAIN_INDEX_SORT Hint

- Improved Response Time using Local Partitioned CONTEXT Index

- Improved Response Time with Local Partitioned Index for Order by Score

- Improved Response Time with Query Filter Cache

- Improved Response Time using BIG_IO Option of CONTEXT Index

- Improved Response Time using SEPARATE_OFFSETS Option of CONTEXT Index

- Improved Response Time Using the STAGE_ITAB, STAGE_ITAB_MAX_ROWS, and STAGE_ITAB_PARALLEL Options of CONTEXT Index

#### 10.2.1 Other Factors That Influence Query Response Time

The following factors can influence query response time:

- Collection of table statistics

- Memory allocation

- Sorting

- Presence of large object (LOB) columns in your base table

- Partitioning

- Parallelism

- The number term expansions in your query

  **See Also:**

  "Frequently Asked Questions About Query Performance"

#### 10.2.2 Improved Response Time with the FIRST_ROWS(n) Hint for ORDER BY Queries

When you need the first rows of an `ORDER BY` query, Oracle recommends that you use the cost-based `FIRST_ROWS(n)` hint.

**Note:**

As the `FIRST_ROWS(n)` hint is cost-based, Oracle recommends that you collect statistics on your tables before you use this hint.

You use the `FIRST_ROWS(n)` hint in cases where you want the first n number of rows in the shortest possible time. For example, consider the following PL/SQL block that uses a cursor to retrieve the first 10 hits of a query and the `FIRST_ROWS(n)` hint to optimize the response time:

    declare
    cursor c is

    select /*+ FIRST_ROWS(10) */ article_id from articles_tab
       where contains(article, 'Omophagia')>0 order by pub_date desc;

    begin

    for i in c
    loop
    insert into t_s values(i.pk, i.col);
    exit when c%rowcount > 11;
    end loop;

    end;
    /

The `c` cursor is a `SELECT` statement that returns the rowids that contain the word omophagia in sorted order. The code loops through the cursor to extract the first 10 rows. These rows are stored in the temporary `t_s` table.

With the `FIRST_ROWS(n)` hint, the optimizer instructs the Oracle Text index to return rowids in score-sorted order when the cost of returning the top-N hits is lower.

Without the hint, Oracle Database sorts the rowids after the Oracle Text index returns all rows in unsorted order that satisfy the `CONTAINS` predicate. Retrieving the entire result set takes time.

Because only the first 10 hits are needed in this query, using the hint results in better performance.

**Note:**

Use the `FIRST_ROWS(n)` hint when you need only the first few hits of a query. When you need the entire result set, do not use this hint as it might result in poor performance.

#### 10.2.3 Improved Response Time Using the DOMAIN_INDEX_SORT Hint

You can also optimize for response time by using the related `DOMAIN_INDEX_SORT` hint. Like `FIRST_ROWS(n),` when queries are optimized for response time, Oracle Text returns the first rows in the shortest time possible.

For example, you can use this hint:

    select /*+ DOMAIN_INDEX_SORT */ pk, score(1), col from ctx_tab
                where contains(txt_col, 'test', 1) > 0 order by score(1) desc;

However, this hint is only rule-based. This means that Oracle Text always chooses the index which satisfies the `ORDER BY` clause. This hint might result in suboptimal performance for queries where the `CONTAINS` clause is very selective. In these cases, Oracle recommends that you use the `FIRST_ROWS(n)` hint, which is fully cost-based.

#### 10.2.4 Improved Response Time Using the Local Partitioned CONTEXT Index

Partitioning your data and creating local partitioned indexes can improve your query performance. On a partitioned table, each partition has its own set of index tables. Effectively, there are multiple indexes, but the results are combined as necessary to produce the final result set.

Create the `CONTEXT` index with the `LOCAL` keyword:

    CREATE INDEX index_name ON table_name (column_name)
    INDEXTYPE IS ctxsys.context
    PARAMETERS ('...')
    LOCAL

With partitioned tables and indexes, you can improve performance of the following types of queries:

- Range Search on Partition Key Column: This query restricts the search to a particular range of values on a column that is also the partition key. For example, consider a query on a date range:

      SELECT storyid FROM storytab WHERE CONTAINS(story, 'oliver')>0 and pub_date BETWEEN '1-OCT-93' AND '1-NOV-93';

  If the date range is quite restrictive, it is very likely that the query can be satisfied by only looking in a single partition.

- ORDER BY Partition Key Column: This query requires only the first `n` hits, and the `ORDER BY` clause names the partition key. Consider an `ORDER BY` query on a `price` column to fetch the first 20 hits:

      SELECT * FROM (

      SELECT itemid FROM item_tab WHERE CONTAINS(item_desc, 'cd player')
        >0 ORDER BY price)
        WHERE ROWNUM < 20;

  In this example, with the table partitioned by price, the query might only need to get hits from the first partition to satisfy the query.

#### 10.2.5 Improved Response Time with the Local Partitioned Index for Order by Score

The `DOMAIN_INDEX_SORT` hint on a local partitioned index might result in poor performance, especially when you order by score. All hits to the query across all partitions must be obtained before the results can be sorted.

Instead, use an inline view when you use the `DOMAIN_INDEX_SORT` hint. Specifically, use the `DOMAIN_INDEX_SORT` hint to improve query performance on a local partitioned index under the following conditions:

- The Oracle Text query itself, including the order by `SCORE`() clause, is expressed as an in-line view.

- The Oracle Text query inside the in-line view contains the `DOMAIN_INDEX_SORT` hint.

- The query on the in-line view has a `ROWNUM` predicate that limits the number of rows to fetch from the view.

For example, the following Oracle Text query and local Oracle Text index are created on a partitioned `doc_tab` table:

         select doc_id, score(1) from doc_tab
            where contains(doc, 'oracle', 1)>0
            order by score(1) desc;

If you are interested in fetching only the top 20 rows, you can rewrite the query as follows:

         select * from
              (select /*+ DOMAIN_INDEX_SORT */ doc_id, score(1) from doc_tab
                  where contains(doc, 'oracle', 1)>0 order by score(1) desc)
          where rownum < 21;

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/EXPLAIN-PLAN.md) for more information about the `EXPLAIN PLAN` statement

#### 10.2.6 Improved Response Time with the Query Filter Cache

Oracle Text provides a cache layer called the query filter cache that you can use to cache the query results. The query filter cache is sharable across queries. Multiple queries can reuse cached query results to improve the query response time.

Use the `ctxfiltercache` operator to specify which query results to cache. The following example uses the operator to store the results of the `common_predicate` query in the cache:

    select * from docs where contains(txt, 'ctxfiltercache((common_predicate), FALSE)')>0;

In this example, the cached results of the `common_predicate` query are reused by the `new_query` query, to improve the query response time.

    select * from docs where contains(txt, 'new_query & ctxfiltercache((common_predicate), FALSE)')>0;

**Note:**

- You can specify the size of the query filter cache by using the basic `query_filter_cache_size` storage attribute.

- The `ctx_filter_cache_statistics` view provides various statistics about the query filter cache.

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-indexing-elements.md) for more information about:

- `ctxfiltercache` operator

- `query_filter_cache_size` basic storage attribute

- `ctx_filter_cache_statistics` view

#### 10.2.7 Improved Response Time Using the BIG_IO Option of CONTEXT Index

Oracle Text provides the `BIG_IO` option for improving the query performance for the `CONTEXT` indexes that extensively use IO operations. The query performance improvement is mainly for data stored on rotating disks, not for data stored on solid state disks.

When you enable the `BIG_IO` option, a `CONTEXT` index creates token type pairs with one large object (LOB) data type for each unique token text. Tokens with the same text but different token types correspond to different rows in the `$I` table.

The indexes with the `BIG_IO` option enabled should have the token LOBs created as SecureFile LOBs, so that the data is stored sequentially in multiple blocks. This method improves the response time of the queries, because the queries can now perform longer sequential reads instead of many short reads.

**Note:**

If you use SecureFiles, you must set the `COMPATIBLE` setting to 11.0 or higher. In addition, you must create the LOB on an automatic segment space management (ASSM) tablespace. When you migrate the existing Oracle Text indexes to SecureFiles, use an ASSM tablespace. To help migrate the existing indexes to SecureFiles, you can extend `ALTER INDEX REBUILD` to provide storage preferences that only affect the \$I table.

To create a `CONTEXT` index with the `BIG_IO` index option, first create a basic storage preference by setting the value of its `BIG_IO` storage attribute to `YES,` and then specify this storage preference while creating the `CONTEXT` index.

The following example creates a basic `mystore` storage preference and sets the value of its `BIG_IO` storage attribute to `YES:`

    exec ctx_ddl.create_preference('mystore', 'BASIC_STORAGE');
    exec ctx_ddl.set_attribute('mystore', 'BIG_IO', 'YES');

To disable the `BIG_IO` option, update the existing storage preference (`mystore`) by setting the value of its `BIG_IO` storage attribute to `NO,` and then rebuild the index.

    exec ctx_ddl.set_attribute('mystore', 'BIG_IO', 'NO');
    alter index idx rebuild('replace storage mystore');

**WARNING:**

Do not use the replace metadata operation to disable the `BIG_IO` index option. It can leave the index in an inconsistent state.

To enable the `BIG_IO` option for a partitioned index without rebuilding the index, modify the basic storage preference by setting the value of its `BIG_IO` storage attribute to `YES,` replace the global index metadata using `ctx_ddl.replace_index_metadata,` and then call `optimize_index` in `REBUILD` mode for each partition of the partitioned index table.

The following example enables the `BIG_IO` option for the `idx` partitioned index:

    exec ctx_ddl.set_attribute('mystore', 'BIG_IO', 'YES');
    exec ctx_ddl.replace_index_metadata('idx', 'replace metadata storage mystore');
    exec ctx_ddl.optimize_index('idx', 'rebuild', part_name=>'part1');

**Note:**

If a procedure modifies the existing index tables with only the `BIG_IO` option enabled, then it will not result in reindexing of the data.

**Note:**

Because the `BIG_IO` index option performs longer sequential reads, the queries that use the `BIG_IO` index option require a large program global area (PGA) memory.

#### 10.2.8 Improved Response Time Using the SEPARATE_OFFSETS Option of the CONTEXT Index

Oracle Text provides the `SEPARATE_OFFSETS` option to improve the query performance for the `CONTEXT` indexes that use IO operations, and whose queries are mainly single-word or Boolean queries.

The `SEPARATE_OFFSETS` option creates a different postings list structure for the tokens of type `TEXT.` Instead of interspersing docids, frequencies, info-length (length of the offsets information), and the offsets in the postings list, the `SEPARATE_OFFSETS` option stores all docids and frequencies at the beginning of the postings list, and all info-lengths and offsets at the end of the postings list. The header at the beginning of the posting contains the information about the boundary points between docids and offsets. Because separation of docids and offsets reduces the time for the queries to read the data, it improves the query response time.

Performance of the `SEPARATE_OFFSETS` option is best realized when you use it in conjunction with the `BIG_IO` option and for tokens with a very long posting.

To create a `CONTEXT` index with the `SEPARATE_OFFSETS` option, first create a basic storage preference by setting the value of its `SEPARATE_OFFSETS` storage attribute to `T.` Next, specify this storage preference when you create the `CONTEXT` index.

The following example creates a basic `mystore` storage preference and sets the value of its `SEPARATE_OFFSETS` storage attribute to `T:`

    exec ctx_ddl.create_preference('mystore', 'BASIC_STORAGE');
    exec ctx_ddl.set_attribute('mystore', 'SEPARATE_OFFSETS', 'T');

To disable the `SEPARATE_OFFSETS` option, update the existing storage preference (`mystore`) by setting the value of its `SEPARATE_OFFSETS` storage attribute to `F,` and then rebuild the index.

    exec ctx_ddl.set_attribute('mystore', 'SEPARATE_OFFSETS', 'F');
    alter index idx rebuild('replace storage mystore');

**WARNING:**

Do not use replace metadata operation to disable the `SEPARATE_OFFSETS` index option, as it can leave the index in an inconsistent state.

To enable the `SEPARATE_OFFSETS` option for a partitioned index without rebuilding the index, modify the basic storage preference by setting the value of its `SEPARATE_OFFSETS` storage attribute to `T,` replace the global index metadata by using `ctx_ddl.replace_index_metadata,` and then call `optimize_index` in REBUILD mode for each partition in the partitioned index table.

The following example enables the `SEPARATE_OFFSETS` option for the partitioned `idx` index:

    exec ctx_ddl.set_attribute('mystore', 'SEPARATE_OFFSETS', 'T');
    exec ctx_ddl.replace_index_metadata('idx', 'replace storage mystore');
    exec ctx_ddl.optimize_index('idx', 'rebuild', part_name=>'part1');

**Note:**

If a procedure modifies the existing index tables with only the `SEPARATE_OFFSETS` option enabled, then the data is not reindexed.

#### 10.2.9 Improved Response Time Using the STAGE_ITAB, STAGE_ITAB_MAX_ROWS, and STAGE_ITAB_PARALLEL Options of CONTEXT Index

Oracle Text provides the `STAGE_ITAB` option for improving the query performance for the `CONTEXT` indexes that extensively use insert, update, and delete operations for near real-time indexing.

If you do not use the `STAGE_ITAB` index option, then when you add a new document to the `CONTEXT` index, `SYNC_INDEX` is called to make the documents searchable. This call creates new rows in the `$I` table, and increases the fragmentation in the `$I` table. The result is deterioration of the query performance.

When you enable the `STAGE_ITAB` index option, the following happens:

- Information about the new documents is stored in the `$G` staging table, not in the `$I` table. This storage ensures that the `$I` table is not fragmented and does not deteriorate the query performance.

- The `$H` b-tree index is created on the `$G` table. The `$G` table and `$H` b-tree index are equivalent to the `$I` table and `$X` b-tree index.

Use the `MERGE` optimization mode to optimize the rows in the `$G` table and move them to the `$I` table.

**Note:**

The `$G` table is stored in the `KEEP` pool. To improve query performance, you should allocate sufficient `KEEP` pool memory and maintain a large enough `$G` table size by using the new `stage_itab_max_rows` option.

To create a `CONTEXT` index with the `STAGE_ITAB` index option, first create a basic storage preference by setting the value of its `STAGE_ITAB` storage attribute to `YES.` Next, specify this storage preference when you create the `CONTEXT` index.

The following example creates a basic `mystore` storage preference and sets the value of its `STAGE_ITAB` storage attribute to `YES:`

    exec ctx_ddl.create_preference('mystore', 'BASIC_STORAGE');
    exec ctx_ddl.set_attribute('mystore', 'STAGE_ITAB', 'YES');

You can also enable the `STAGE_ITAB` index option for an existing nonpartitioned `CONTEXT` index by using the rebuild option of the `ALTER INDEX` statement.

    alter index IDX rebuild parameters('replace storage mystore');

To disable the `STAGE_ITAB` option for a nonpartitioned `CONTEXT` index, update the existing storage preference (`mystore`) by setting the value of its `STAGE_ITAB` storage attribute to `NO,` and then rebuild the index.

    exec ctx_ddl.set_attribute('mystore', 'STAGE_ITAB', 'NO');
    alter index idx rebuild parameters('replace storage mystore');

This operation runs the optimization process by using the `MERGE` optimization mode and then drops the `$G` table.

The rebuild option of the `ALTER INDEX` statement does not work with the partitioned `CONTEXT` index for enabling and disabling the `STAGE_ITAB` option.

The following example enables the `STAGE_ITAB` option for the partitioned `CONTEXT` `idx` index:

    alter index idx parameters('add stage_itab');

The following example disables the `STAGE_ITAB` option for the partitioned `CONTEXT` `idx` index:

    alter index idx parameters('remove stage_itab');

Starting with Oracle Database 12c Release 2 (12.2), the contents of `$G` are automatically moved to `$I` during index synchronization when `$G` has more than 1 million rows. This value is controlled by the `STAGE_ITAB_MAX_ROWS` attribute of the `STORAGE` preference.

**Note:**

If an occasional index synchronization takes a long time, you can either reduce the value of the `STAGE_ITAB_MAX_ROWS` parameter or increase the degree of parallelism by using the `STAGE_ITAB_PARALLEL` attribute of the `STORAGE` preference. If you set the value of `STAGE_ITAB_MAX_ROWS` to a very small value, then the contents of `$G` are moved to `$I` frequently. So, do not be set it to a very low value.

**Note:**

To use the `STAGE_ITAB` index option for a `CONTEXT` index, you must specify the `g_index_clause` and `g_table_clause` `BASIC_STORAGE` preferences.

The query performance is deteriorated when `$G` table is too fragmented. To avoid deterioration, starting with Oracle Database Release 18c, Oracle Text provides automatic background optimize merge for every index or partition. To enable automatic background optimize merge, you must set the `STAGE_ITAB` and `STAGE_ITAB_AUTO_OPT` storage preference attributes to `TRUE,` and you must create the index with a storage preference.

By default, if you had enabled `STAGE_ITAB` in indexes before you upgraded to Oracle Database Release 18c, then `STAGE_ITAB_AUTO_OPT` is not enabled. If `STAGE_ITAB` and `AUTO_OPTIMIZE` are enabled in existing indexes, then you must disable `AUTO_OPTIMIZE` before you enable `STAGE_ITAB_AUTO_OPT`.

The following example creates a basic `mystore` storage preference and sets the value of its `STAGE_ITAB_AUTO_OPT` storage attribute to `TRUE`:

    exec ctx_ddl.create_preference('mystore', 'basic_storage');
    exec ctx_ddl.set_attribute('mystore', 'stage_itab', 'TRUE');
    exec ctx_ddl.set_attribute('mystore', 'stage_itab_auto_opt', 'TRUE');
    exec ctx_ddl.set_attribute(‘mystore’, 'stage_itab_parallel', 16);

**Related Topics**

- [Oracle Text Reference](../ccref/CTX_OUTPUT-package.md)

### 10.3 Optimizing Queries for Throughput

When you optimize a query for throughput, the default behavior returns all hits in the shortest time possible.

Here is how you can explicitly optimize queries for throughput:

- CHOOSE and ALL ROWS Modes: By default, you optimize queries with the `CHOOSE` and `ALL_ROWS` modes. Oracle Text returns all rows in the shortest time possible.

- FIRST_ROWS(n) Mode: In `FIRST_ROWS(n)` mode, the optimizer in Oracle Database optimizes for fast response time by having the Text domain index return score-sorted rows, if possible. This is the default behavior when you use the `FIRST_ROWS(n)` hint.

  If you want to optimize throughput with `FIRST_ROWS(n),` then use the `DOMAIN_INDEX_NO_SORT` hint. Better throughput means that you are interested in getting all query rows in the shortest time possible.

  The following example achieves better throughput by not using the Text domain index to return score-sorted rows. Instead, Oracle Text sorts the rows after all rows that satisfy the `CONTAINS` predicate are retrieved from the index:

      select /*+ FIRST_ROWS(10) DOMAIN_INDEX_NO_SORT */ pk, score(1), col from ctx_tab
                  where contains(txt_col, 'test', 1) > 0 order by score(1) desc;

**See Also:**

[Oracle Database SQL Tuning Guide](../tgsql/query-optimizer-concepts.md) for more information about the query optimizer and using hints such as `FIRST_ROWS(n)` and `CHOOSE`

### 10.4 Composite Domain Index in Oracle Text

The Composite Domain Index (CDI) feature of the Extensibility Framework in Oracle Database enables structured columns to be indexed by Oracle Text. Therefore, both text and one or more structured criteria can be satisfied by one single Oracle Text index row source. Performance for the following types of queries is improved:

- Oracle Text query with structured criteria in the SQL `WHERE` clause

- Oracle Text query with structured `ORDER` `BY` criteria

- A combination of the previous two query types

As with concatenated b-tree indexes or bitmap indexes, applications experience a slowdown in data manipulation language (DML) performance as the number of `FILTER` `BY` and `ORDER` `BY` columns increases. Where `SCORE`-sort pushdown is optimized for response time, the structured sort or combination of `SCORE` and structured sort pushdown is also optimized for response time, but not for throughput. However, using `DOMAIN_INDEX_SORT` or `FIRST_ROWS``(n)` hints to force the sort to be pushed into the CDI while fetching the entire hitlist may result in poor query response time.

### 10.5 Performance Tuning with CDI

Because you can map a `FILTER BY` column to `MDATA,` you can optimize query performances for equality searches by restricting the supported functionality of `RANGE` and `LIKE.` However, Oracle does not recommend mapping a `FILTER` `BY` column to `MDATA` if the `FILTER` `BY` column contains sequential values or has very high cardinality. Doing so can result in a very long and narrow `$I` table and reduced `$X` performance. One example of such a sequential column might be one that uses the `DATE` stamp. For such sequential columns, mapping to `SDATA` is recommended.

Use the following hints to push or not push the `SORT` and `FILTER` `BY` predicates into the CDI:

- `DOMAIN_INDEX_SORT:` The query optimizer tries to push the applicable sorting criteria into the specified CDI.

- `DOMAIN_INDEX_NO_SORT:` The query optimizer tries not to push sorting criteria into the specified CDI.

- `DOMAIN_INDEX_FILTER`(table name index name): The query optimizer tries to push the applicable `FILTER` `BY` predicates into the specified CDI.

- `DOMAIN_INDEX_NO_FILTER`(table name index name): The query optimizer does not try to push the applicable `FILTER` `BY` predicate(s) into the specified CDI.

**Note:**

The `domain_index_filter` hint does not force the query optimizer to use CDI. Instead, if the CBO chooses to use the CDI, then it should also push the filter predicate into the index. To force the query optimizer to choose the CDI index, you additionally need to use the `INDEX` hint.

Example 10-1 Performance Tuning an Oracle Text Query with CDI Hints

The following example performs an optimized query on the `books` table.

    SELECT bookid, pub_date, source FROM
      (SELECT /*+ domain_index_sort domain_index_filter(books books_ctxcdi) */ bookid, pub_date, source
          FROM books
          WHERE CONTAINS(text, 'aaa',1)>0 AND bookid >= 80
          ORDER BY PUB_DATE desc nulls last, SOURCE asc  nulls last, score(1) desc)
     WHERE rownum < 20;

### 10.6 Solving Index and Query Bottlenecks by Using Tracing

Tracing enables you to identify bottlenecks in indexing and querying. Oracle Text provides a set of predefined traces.

Each trace is identified by a unique number. `CTX_OUTPUT` includes a symbol for this number. Each trace measures a specific numeric quantity, such as the number of `$I` rows selected during text queries.

Traces are cumulative counters, so usage is as follows:

1.  The user enables a trace.

2.  The user performs one or more operations. Oracle Text measures activities and accumulates the results in the trace.

3.  The user retrieves the trace value, which is the total value across all operations done in step 2.

4.  The user resets the trace to 0.

5.  The user starts over at Step 2.

So, for instance, if in step 2 the user runs two queries, and query 1 selects 15 rows from `$I,` and query 2 selects 17 rows from `$I,` then in step 3 the value of the trace is 32 (15 + 17).

Traces are associated with a session—they can measure operations that take place within a single session, and, conversely, cannot make measurements across sessions.

During parallel synchronization or optimization, the trace profile is copied to the secondary sessions if and only if tracing is currently enabled. Each secondary session accumulates its own traces and implicitly writes all trace values to its logfile before termination.

**Related Topics**

- [Oracle Text Reference](../ccref/CTX_OUTPUT-package.md)

### 10.7 Using Parallel Queries

In general, parallel queries are optimal for Decision Support System (DSS) and Online Analysis Processing (OLAP). They are also optimal for analytical systems that have large data collections, multiple CPUs with a low number of concurrent users, or Oracle Real Application Clusters (Oracle RAC) nodes.

Oracle Text supports the following parallel queries:

- Parallel Queries on a Local Context Index

- Parallelizing Queries Across Oracle RAC Nodes

#### 10.7.1 Parallel Queries on a Local Context Index

Parallel query refers to the parallelized processing of a local `CONTEXT` index.

Based on the parallel degree of the index and various system attributes, Oracle determines the number of parallel query workers to be spawned to process the index. Each parallel query worker processes one or more index partitions. This default query behavior applies to local indexes that are created in parallel.

However, for heavily loaded systems with a high number of concurrent users, query throughput is usually not effective with parallel query; if the query is run serially, the top-N hits can usually be satisfied by the first few partitions. For example, take the typical top-N text queries with an `ORDER` `BY` partition key column:

    select * from (
            select story_id from stories_tab where contains(...)>0 order by
    publication_date desc)
        where rownum <= 10;

These text queries generally do not perform well with a parallel query.

You can disable parallel querying after a parallel index operation with an `ALTER INDEX` statement:

    Alter index <text index name> NOPARALLEL;
    Alter index <text index name> PARALLEL 1;

You can also enable or increase the parallel degree:

    Alter index <text index name> parallel < parallel degree >;

#### 10.7.2 Parallelizing Queries Across Oracle RAC Nodes

Oracle Real Application Clusters (Oracle RAC) enables you to improve query throughput and scalability as the query load increases.

You can achieve further improvements in Oracle Text performance by physically partitioning the text data and Oracle Text indexes (using local partitioned indexes) and ensuring that partitions are handled by separate Oracle RAC nodes. This way, you avoid duplication of the cache contents across multiple nodes and, therefore, maximize the benefit of Oracle RAC cache fusion.

Oracle supports database object-level affinity, which makes it much easier to allocate index objects (`$I` and `$R` tables) to particular nodes.

Although Oracle RAC offers solutions for improving query throughput and performance, it does not necessarily enable you to continue to get the same performance improvements as you scale up the data volumes. You are more likely to see improvements by increasing the amount of memory available to the system global area (SGA) cache or by partitioning your data so that queries do not have to hit all table partitions in order to provide the required set of query results.

### 10.8 Tuning Queries with Blocking Operations

If you issue a query with more than one predicate, you can cause a blocking operation in the execution plan. For example, consider the following mixed query:

    select docid from mytab where contains(text, 'oracle', 1) > 0
      AND colA > 5
      AND colB > 1
      AND colC > 3;

Assume that all predicates are unselective and colA, colB, and colC have bitmap indexes. The CBO in Oracle Database chooses the following execution plan:

    TABLE ACCESS BY ROWIDS
      BITMAP CONVERSION TO ROWIDS
        BITMAP AND
          BITMAP INDEX COLA_BMX
          BITMAP INDEX COLB_BMX
          BITMAP INDEX COLC_BMX
          BITMAP CONVERSION FROM ROWIDS
            SORT ORDER BY
              DOMAIN INDEX MYINDEX

Because `BITMAP` `AND` is a blocking operation, Oracle Text must temporarily save the rowid and score pairs returned from the Oracle Text domain index before it runs the `BITMAP` `AND` operation.

Oracle Text attempts to save these rowid and score pairs in memory. However, when the size of the result set exceeds the `SORT_AREA_SIZE` initialization parameter, Oracle Text spills these results to temporary segments on disk.

Because saving results to disk causes extra overhead, you can improve performance by increasing the `SORT_AREA_SIZE` parameter.

    alter session set SORT_AREA_SIZE = <new memory size in bytes>;

For example, set the buffer to approximately 8 megabytes.

    alter session set SORT_AREA_SIZE = 8300000;

**See Also:**

[Oracle Database Performance Tuning Guide](../tgdba/managing-operating-system-resources.md) and [Oracle Database Reference](../refrn/SORT_AREA_SIZE.md) for more information on `SORT_AREA_SIZE`

### 10.9 Frequently Asked Questions About Query Performance

This section answers some of the frequently asked questions about query performance.

- What is Query Performance?

- What is the fastest type of text query?

- Should I collect statistics on my tables?

- How does the size of my data affect queries?

- How does the format of my data affect queries?

- What is a functional versus an indexed lookup?

- What tables are involved in queries?

- How is \$R contention reduced?

- Does sorting the results slow a text-only query?

- How do I make an ORDER BY score query faster?

- Which memory settings affect querying?

- Does out-of-line LOB storage of wide base table columns improve performance?

- How can I make a CONTAINS query on more than one column faster?

- Is it OK to have many expansions in a query?

- How can local partition indexes help?

- Should I query in parallel?

- Should I index themes?

- When should I use a CTXCAT index?

- When is a CTXCAT index NOT suitable?

- What optimizer hints are available and what do they do?

#### 10.9.1 What is query performance?

Answer: There are two measures of query performance:

- Response time: The time to get an answer to an individual query

- Throughput: The number of queries that can be run in any given time period; for example, queries each second

These two measures are related, but they are not the same. In a heavily loaded system, you want maximum throughput, whereas in a relatively lightly loaded system, you probably want minimum response time. Also, some applications require a query to deliver all hits to the user, whereas others only require the first 20 hits from an ordered set. It is important to distinguish between these two scenarios.

#### 10.9.2 What is the fastest type of Oracle Text query?

Answer: The fastest type of query meets the following conditions:

- Single `CONTAINS` clause

- No other conditions in the `WHERE` clause

- No `ORDER` `BY` clause

- Returns only the first page of results (for example, the first 10 or 20 hits)

#### 10.9.3 Should I collect statistics on my tables?

Answer: Yes. Collecting statistics on your tables enables Oracle Text to do cost-based analysis. This helps Oracle Text choose the most efficient execution plan for your queries.

If your queries are always pure text queries (no structured predicate and no joins), you should delete statistics on your Oracle Text index.

#### 10.9.4 How does the size of my data affect queries?

Answer: The speed at which the Oracle Text index can deliver rowids is not affected by the actual size of the data. Oracle Text query speed is related to the number of rows that must be fetched from the index table, the number of hits requested, the number of hits produced by the query, and the presence or absence of sorting.

#### 10.9.5 How does the format of my data affect queries?

Answer: The format of the documents (plain ASCII text, HTML, or Microsoft Word) should make no difference to query speed. The documents are filtered to plain text at indexing time, not query time.

The cleanliness of the data makes a difference. Spell-checked and subedited text for publication tends to have a much smaller total vocabulary (and therefore size of the index table) than informal text such as email, which contains spelling errors and abbreviations. For a given index memory setting, the extra text takes up memory, creates more fragmented rows, and adversely affects query response time.

#### 10.9.6 What is the difference between an indexed lookup and a functional lookup

Answer: The kernel can query the Oracle Text index with an indexed lookup and a functional lookup. In the indexed lookup, the first and most common case, the kernel asks the Oracle Text index for all rowids that satisfy a particular text search. These rowids are returned in batches.

In the functional lookup, the kernel passes individual rowids to the Oracle Text index and asks whether that particular rowid satisfies a certain text criterion. The functional lookup is most commonly used with a very selective structured clause, so that only a few rowids must be checked against the Oracle Text index. Here is an example of a search where a functional lookup is useful:

    SELECT ID, SCORE(1), TEXT FROM MYTABLE

    WHERE START_DATE = '21 Oct 1992'         <- highly selective
    AND CONTAINS (TEXT, 'commonword') > 0    <- unselective

Functional invocation is also used for an Oracle Text query that is ordered by a structured column (for example date, price) and if the Oracle Text query contains unselective words.

#### 10.9.7 What tables are involved in queries?

Answer: All queries look at the index token table. The table’s name has the form of `DR$indexname$I` and contains the list of tokens (`TOKEN_TEXT` column) and the information about the row and word positions where the token occurs (`TOKEN_INFO` column).

The row information is stored as internal docid values that must be translated into external rowid values. The table that you use depends on the type of lookup:

- For functional lookups, use the `$K` table, `DR$indexname$K.` This simple Index Organized Table (IOT) contains a row for each docid/rowid pair.

- For indexed lookups, use the `$R` table, `DR$indexname$R.` This table holds the complete list of rowids in a BLOB column.

Starting with Oracle Database 12c Release 2 (12.2), a new storage attribute, `SMALL_R_ROW,` was introduced to reduce the size of the `$R` row. It populates `$R` rows on demand instead of creating 22 static rows, thereby reducing the Data Manipulation Language contention. The contention happens when parallel insert, update, and delete operations try to lock the same `$R` row.

You can easily find out whether a functional or indexed lookup is being used by examining a SQL trace and looking for the `$K` or `$R` tables.

**Note:**

These internal index tables are subject to change from release to release. Oracle recommends that you do not directly access these tables in your application.

#### 10.9.8 How is the \$R table contention reduced?

The `$R` contention during base table delete and update operations has become a recurring theme over the past few years. Currently, each `$R` index table has 22 static rows, and each row can contain up to 200 million rowids. The contention happens when the parallel insert, update, and delete operations try to lock the same `$R` row for insert or delete operations. The following enhancements made during this release reduce the contention:

- The maximum number of rowids that each `$R` row can contain is 70,000, which translates to 1 MB of data stored on each row. To use this feature, you must set the `SMALL_R_ROW` storage attribute.

- The `$R` rows are created on demand instead of just populating a pre-determined number of rows.

#### 10.9.9 Does sorting the results slow a text-only query?

Answer: Yes, it certainly does.

If Oracle Text does not sort, then it can return results as it finds them. This approach is quicker when the application needs to display only a page of results at a time.

#### 10.9.10 How do I make an ORDER BY score query faster?

Answer: Sorting by relevance (`SCORE(n)`) can be fast if you use the `FIRST_ROWS(n)` hint. In this case, Oracle Text performs a high-speed internal sort when fetching from the Oracle Text index tables.

Here is an example of this query:

                  SELECT /*+ FIRST_ROWS(10) */ ID, SCORE(1), TEXT FROM mytable
                    WHERE CONTAINS (TEXT, 'searchterm', 1) > 0
                    ORDER BY SCORE(1) DESC;

It is important to note that, there must be no other criteria in the `WHERE` clause, other than a single `CONTAINS.`

#### 10.9.11 Which memory settings affect querying?

Answer: For querying, you want to strive for a large system global area (SGA). You can set these SGA parameters in your Oracle Database initialization file. You can also set these parameters dynamically.

The `SORT_AREA_SIZE` parameter controls the memory that is available for sorting `ORDER BY` queries. You should increase the size of this parameter if you frequently order by structured columns.

**See Also:**

- [Oracle Database Administrator's Guide](../admin/managing-memory.md) for more information on setting SGA related parameters

- [Oracle Database Performance Tuning Guide](../tgdba/database-memory-allocation.md) for more information on memory allocation

- [Oracle Database Reference](../refrn/SORT_AREA_SIZE.md) for more information on setting the `SORT_AREA_SIZE` parameter

#### 10.9.12 Does out-of-line LOB storage of wide base table columns improve performance?

Answer: Yes. Typically, a `SELECT` statement selects more than one column from your base table. Because Oracle Text fetches columns to memory, it is more efficient to store wide base table columns such as large objects (LOBs) out of line, especially when these columns are rarely updated but frequently selected.

When LOBs are stored out of line, only the LOB locators need to be fetched to memory during querying. Out-of-line storage reduces the effective size of the base table. It makes it easier for Oracle Text to cache the entire table to memory, and so reduces the cost of selecting columns from the base table, and speeds up text queries.

In addition, smaller base tables cached in memory enables more index table data to be cached during querying, which improves performance.

#### 10.9.13 How can I speed up a CONTAINS query on more than one column?

Answer: The fastest type of query is one where there is only a single `CONTAINS` clause and no other conditions in the `WHERE` clause.

Consider the following multiple `CONTAINS` query:

                  SELECT title, isbn FROM booklist
                    WHERE CONTAINS (title, 'horse') > 0
                      AND CONTAINS (abstract, 'racing') > 0

You can get the same result with section searching and the `WITHIN` operator:

                  SELECT title, isbn FROM booklist
                    WHERE CONTAINS (alltext,
                      'horse WITHIN title AND racing WITHIN abstract')>0

This query is completed more quickly than the single `CONTAINS` clause. To use a query like this, you must copy all data into a single text column for indexing, with section tags around each column's data. You can do that with PL/SQL procedures before indexing, or you can use the `USER_DATASTORE` datastore during indexing to synthesize structured columns with the text column into one document.

#### 10.9.14 Can I have many expansions in a query?

Answer: Each distinct word used in a query requires at least one row to be fetched from the index table. It is therefore best to keep the number of expansions down as much as possible.

You should not use expansions such as wild cards, thesaurus, stemming, and fuzzy matching unless they are necessary to the task. In general, a few expansions (for example, 10 to 20) does not cause difficulty, but avoid a large number of expansions (80 or 100) in a query. Use the query feedback mechanism to determine the number of expansions for any particular query expression.

For wildcard and stem queries, you can avoid term expansion from query time to index time by creating prefix, substring, or stem indexes. Query performance increases at the cost of longer indexing time and added disk space.

Prefix and substring indexes can improve wildcard performance. You enable prefix and substring indexing with the `BASIC_WORDLIST` preference. The following example sets the wordlist preference for prefix and substring indexing. For prefix indexing, it specifies that Oracle Text creates token prefixes between 3 and 4 characters long:

    begin

    ctx_ddl.create_preference('mywordlist', 'BASIC_WORDLIST');
    ctx_ddl.set_attribute('mywordlist','PREFIX_INDEX','TRUE');
    ctx_ddl.set_attribute('mywordlist','PREFIX_MIN_LENGTH', '3');
    ctx_ddl.set_attribute('mywordlist','PREFIX_MAX_LENGTH', '4');
    ctx_ddl.set_attribute('mywordlist','SUBSTRING_INDEX', 'YES');

    end

Enable stem indexing with the `BASIC_LEXER` preference:

    begin

    ctx_ddl.create_preference('mylex', 'BASIC_LEXER');
    ctx_ddl.set_attribute ( 'mylex', 'index_stems', 'ENGLISH');

    end;

#### 10.9.15 How can local partition indexes help?

Answer: You can create local partitioned `CONTEXT` indexes on partitioned tables. This means that, on a partitioned table, each partition has its own set of index tables. Effectively, the results from the multiple indexes are combined as necessary to produce the final result set.

Use the `LOCAL` keyword to create the index:

    CREATE INDEX index_name ON table_name (column_name)
    INDEXTYPE IS ctxsys.context
    PARAMETERS ('...')
    LOCAL

With partitioned tables and local indexes, you can improve performance of the following types of `CONTAINS` queries:

- Range Search on Partition Key Column: This query restricts the search to a particular range of values on a column that is also the partition key.

- ORDER BY Partition Key Column: This query requires only the first `n` hits, and the `ORDER BY` clause names the partition key.

  **See Also:**

  "Improved Response Time using Local Partitioned CONTEXT Index"

#### 10.9.16 Should I query in parallel?

Answer: It depends on system load and server capacity. Even though parallel querying is the default behavior for indexes created in parallel, it usually degrades the overall query throughput on heavily loaded systems.

Parallel queries are optimal for Decision Support System (DSS) and Online Analysis Processing (OLAP). They are also optimal for analytical systems that have large data collections, multiple CPUs with a low number of concurrent users, or Oracle Real Application Clusters (Oracle RAC) nodes.

**See Also:**

"Using Parallel Queries"

#### 10.9.17 Should I index themes?

Answer: Indexing theme information with a `CONTEXT` index takes longer and also increases the size of your index. However, theme indexes enable `ABOUT` queries to be more precise by using the knowledge base. If your application uses many `ABOUT` queries, it might be worthwhile to create a theme component to the index, despite the extra indexing time and extra storage space required.

**See Also:**

"[ABOUT Queries and Themes](querying-with-oracle-text.md)"

#### 10.9.18 When should I use a CTXCAT index?

Answer: `CTXCAT` indexes work best when the text is in small chunks (just a few lines), and you want searches to restrict or sort the result set according to certain structured criteria, such as numbers or dates.

For example, consider an online auction site. Each item for sale has a short description, a current bid price, and start and end dates for the auction. You want to see all records with antique cabinet in the description, with a current bid price less than \$500. Because you are particularly interested in newly posted items, you want the results sorted by auction start time.

This search is not always efficient with a `CONTAINS` structured query on a `CONTEXT` index. The response time can vary significantly depending on the structured and `CONTAINS` clauses, because the intersection of structured and `CONTAINS` clauses or the Oracle Text query ordering is computed during query time.

By including structured information within the `CTXCAT` index, you ensure that the query response time is always in an optimal range regardless of search criteria. Because the interaction between text and structured query is precomputed during indexing, query response time is optimum.

#### 10.9.19 When is a CTXCAT index NOT suitable?

Answer: There are differences in the time and space needed to create the index. `CTXCAT` indexes take a bit longer to create, and they use considerably more disk space than `CONTEXT` indexes. If you are tight on disk space, consider carefully whether `CTXCAT` indexes are appropriate for you.

With query operators, you can use the richer `CONTEXT` grammar in `CATSEARCH` queries with query templates. The older restriction of a single `CATSEARCH` query grammar no longer holds.

#### 10.9.20 What optimizer hints are available and what do they do?

Answer: To drive the query with a text or b-tree index, you can use the `INDEX(table column)` optimizer hint in the usual way.

You can also use the `NO_INDEX(table column)` hint to disable a specific index.

The `FIRST_ROWS(n)` hint has a special meaning for text queries. Use it when you need the first `n` hits to a query. When you use the `DOMAIN_INDEX_SORT` hint in conjunction with `ORDER BY SCORE(n) DESC,` you tell the Oracle optimizer to accept a sorted set from the Oracle Text index and to sort no farther.

**See Also:**

"Optimizing Queries for Response Time"

### 10.10 Frequently Asked Questions About Indexing Performance

This section answers some of the frequently asked questions about indexing performance.

- How long should indexing take?

- Which index memory settings should I use?

- How much disk overhead will indexing require?

- How does the format of my data affect indexing?

- Can parallel indexing improve performance?

- How can I improve index performance for creating local partitioned index?

- How can I tell how much indexing has completed?

#### 10.10.1 How long should indexing take?

Answer: Indexing text is a resource-intensive process. The speed of indexing depends on the power of your hardware. Indexing speed depends on CPU and I/O capacity. With sufficient I/O capacity to read in the original data and write out index entries, the CPU is the limiting factor.

Tests with Intel x86 (Core 2 architecture, 2.5GHz) CPUs have shown that Oracle Text can index around 100 GB of text per CPU core, per day. This speed would be expected to increase as CPU clock speeds increase and CPU architectures become more efficient.

Other factors, such as your document format, location of your data, and the calls to user-defined datastores, filters, and lexers, can affect your indexing speed.

#### 10.10.2 Which index memory settings should I use?

Answer: You can set your index memory with the `DEFAULT_INDEX_MEMORY` and `MAX_INDEX_MEMORY` system parameters. You can also set your index memory at runtime with the `CREATE INDEX` `memory` parameter in the parameter string.

You should aim to set the `DEFAULT_INDEX_MEMORY` value as high as possible, without causing paging.

You can also improve indexing performance by increasing the `SORT_AREA_SIZE` system parameter.

Oracle recommends that you use a large index memory setting. Large settings, even up to hundreds of megabytes, can improve the speed of indexing and reduce fragmentation of the final indexes. However, if you set the index memory setting too high, then memory paging reduces indexing speed.

With parallel indexing, each stream requires its own index memory. When dealing with very large tables, you can tune your database system global area (SGA) differently for indexing and retrieval. For querying, you want to get as much information cached in the SGA block buffer cache as possible. So you should allocate a large amount of memory to the block buffer cache. Because this approach does not make any difference to indexing, you would be better off reducing the size of the SGA to make more room for large index memory settings during indexing.

You set the size of SGA in your Oracle Database initialization file.

**See Also:**

- [Oracle Text Reference](../ccref/oracle-text-indexing-elements.md) to learn more about Oracle Text system parameters

- [Oracle Database Administrator's Guide](../admin/managing-memory.md) for more information on setting SGA related parameters

- [Oracle Database Performance Tuning Guide](../tgdba/database-memory-allocation.md) for more information on memory allocation

- [Oracle Database Reference](../refrn/SORT_AREA_SIZE.md) for more information on setting the `SORT_AREA_SIZE` parameter

#### 10.10.3 How much disk overhead will indexing require?

Answer: The overhead, the amount of space needed for the index tables, varies between about 50 and 200 percent of the original text volume. Generally, larger amounts of text result in smaller overhead, but many small records use more overhead than fewer large records. Also, clean data (such as published text) requires less overhead than dirty data such as emails or discussion notes, because the dirty data is likely to include many misspelled and abbreviated words.

A text-only index is smaller than a combined text and theme index. A prefix and substring index makes the index significantly larger.

#### 10.10.4 How does the format of my data affect indexing?

Answer: You can expect much lower storage overhead for formatted documents such as Microsoft Word files because the documents tend to be very large compared to the actual text held in them. So 1 GB of Word documents might only require 50 MB of index space, whereas 1 GB of plain text might require 500 MB, because there is ten times as much plain text in the latter set.

Indexing time is less clear-cut. Although the reduction in the amount of text to be indexed has an obvious effect, you must balance this against the cost of filtering the documents with the `AUTO_FILTER` filter or other user-defined filters.

#### 10.10.5 Can parallel indexing improve performance?

Answer: Parallel indexing can improve index performance when you have a large amount of data and multiple CPUs.

Use the `PARALLEL` keyword to create an index with up to three separate indexing processes, depending on your resources.

    CREATE INDEX index_name ON table_name (column_name)
    INDEXTYPE IS ctxsys.context PARAMETERS ('...') PARALLEL 3;

You can also use parallel indexing to create local partitioned indexes on partitioned tables. However, indexing performance improves only with multiple CPUs.

**Note:**

Using `PARALLEL` to create a local partitioned index enables parallel queries. (Creating a nonpartitioned index in parallel does not turn on parallel query processing.)

Parallel querying degrades query throughput especially on heavily loaded systems. Because of this, Oracle recommends that you disable parallel querying after parallel indexing. To do so, use `ALTER INDEX NOPARALLEL.`

#### 10.10.6 How can I improve index performance when I create a local partitioned index?

Answer: When you have multiple CPUs, you can improve indexing performance by creating a local index in parallel.

You can create a local partitioned index in parallel in the following ways:

- Use the `PARALLEL` clause with the `LOCAL` clause in the `CREATE INDEX` statement. In this case, the maximum parallel degree is limited to the number of partitions.

- Create an unusable index, and then run the `DBMS_PCLXUTIL.BUILD_PART_INDEX` utility. This method can result in a higher degree of parallelism, especially if you have more CPUs than partitions.

The following is an example of the second method. The base table has three partitions. You create a local partitioned unusable index first, and then run the `DBMS_PCLUTIL.BUILD_PART_INDEX`, to build the three partitions in parallel (inter-partition parallelism). Inside each partition, index creation occurs in parallel (intra-partition parallelism) with a parallel degree of 2.

    create index tdrbip02bx on tdrbip02b(text)
    indextype is ctxsys.context local (partition tdrbip02bx1,
                                       partition tdrbip02bx2,
                                       partition tdrbip02bx3)
    unusable;

    exec dbms_pclxutil.build_part_index(3,2,'TDRBIP02B','TDRBIP02BX',TRUE);

#### 10.10.7 How can I tell how much indexing has completed?

Answer: You can use the `CTX_OUTPUT.START_LOG` procedure to log output from the indexing process. The filename is normally written to `$ORACLE_HOME/ctx/log,` but you can change the directory by using the `LOG_DIRECTORY` parameter in `CTX_ADM.SET_PARAMETER.`

**See Also:**

[Oracle Text Reference](../ccref/CTX_OUTPUT-package.md) to learn more about the `CTX_OUTPUT` package

### 10.11 Frequently Asked Questions About Updating the Index

This section answers some of the frequently asked questions about updating your index and related performance issues.

- How often should I index new or updated records?

- How can I tell when my indexes are getting fragmented?

- Does memory allocation affect index synchronization?

#### 10.11.1 How often should I index new or updated records?

Answer: If you run reindexing with `CTX_DDL.SYNC_INDEX` less often, your indexes will be less fragmented, and you will not have to optimize them as often.

However, your data becomes progressively more out-of-date, and that may be unacceptable to your users.

Overnight indexing is acceptable for many systems. In this case, data that is less than a day old is not searchable. Other systems use hourly, 10-minute, or 5-minute updates.

**See Also:**

- [Oracle Text Reference](../ccref/CTX_DDL-package.md) to learn more about using `CTX_DDL.SYNC_INDEX`

- "[Managing DML Operations for a CONTEXT Index](maintaining-oracle-text-indexes.md)"

#### 10.11.2 How can I tell when my indexes are fragmented?

Answer: The best way is to time some queries, run index optimization, and then time the same queries (restarting the database to clear the SGA each time, of course). If the queries speed up significantly, then optimization was worthwhile. If they do not, then you can wait longer next time.

You can also use `CTX_REPORT.INDEX_STATS` to analyze index fragmentation.

**See Also:**

- [Oracle Text Reference](../ccref/CTX_REPORT-package.md) to learn more about using the `CTX_REPORT` package

- "[Optimizing the Index](maintaining-oracle-text-indexes.md)"

#### 10.11.3 Does memory allocation affect index synchronization?

Answer: Yes, the same way as for normal indexing. There are often far fewer records to be indexed during a synchronize operation, so it is not usually necessary to provide hundreds of megabytes of indexing memory.
