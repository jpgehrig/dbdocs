Various ideas for improving performance in a parallel execution environment are discussed under this section.

This section contains the following topics:

- Implementing a Parallel Execution Strategy

- Optimizing Performance by Creating and Populating Tables in Parallel

- Using EXPLAIN PLAN to Show Parallel Operations Plans

- Additional Considerations for Parallel DML

- Optimizing Performance by Creating Indexes in Parallel

- Parallel DML Tips

- Incremental Data Loading in Parallel

### 8.8.1 Implementing a Parallel Execution Strategy

Implementing a good parallel execution strategy is important to ensure high performance.

Recommendations for a good strategy include:

- Implement a simple setup to understand what is happening in your system.

- Use resource manager to specify the maximum degree of parallelism (DOP) for consumer groups so that each group is allotted a specific amount of processing resources without overwhelming the system. A resource management policy is needed when using parallel execution to keep the system under control, and to ensure SQL statements are able to execute in parallel.

- Base your strategy on the amount of system resources you want to make available for parallel execution. Adjust the values of the parameters `PARALLEL_MAX_SERVERS` and `PARALLEL_SERVERS_TARGET` to limit the number of parallel execution (PX) servers running in the system.

- Consider taking an ELT (Extract, Load, and Transform) strategy rather than an ETL (Extract, Transform, and Load) strategy.

- Use external tables with a parallel SQL statement, such as CTAS or IAS, for faster data loads

### 8.8.2 Optimizing Performance by Creating and Populating Tables in Parallel

To optimize parallel execution performance for queries that retrieve large result sets, create and populate tables in parallel.

Oracle Database cannot return results to a user process in parallel. If a query returns a large number of rows, execution of the query might indeed be faster. However, the user process can receive the rows only serially. To optimize parallel execution performance for queries that retrieve large result sets, use `PARALLEL` `CREATE` `TABLE` `AS` `SELECT` or direct-path `INSERT` to store the result set in the database. At a later time, users can view the result set serially.

Performing the `SELECT` in parallel does not influence the `CREATE` statement. If the `CREATE` statement is executed in parallel, however, the optimizer tries to make the `SELECT` run in parallel also.

When combined with the `NOLOGGING` option, the parallel version of `CREATE` `TABLE` `AS` `SELECT` provides a very efficient intermediate table facility, for example:

    CREATE TABLE summary PARALLEL NOLOGGING AS SELECT dim_1, dim_2 ...,
    SUM (meas_1)
    FROM facts GROUP BY dim_1, dim_2;

These tables can also be incrementally loaded with parallel `INSERT`. You can take advantage of intermediate tables using the following techniques:

- Common subqueries can be computed once and referenced many times. This can allow some queries against star schemas (in particular, queries without selective `WHERE`-clause predicates) to be better parallelized. Star queries with selective `WHERE`-clause predicates using the star-transformation technique can be effectively parallelized automatically without any modification to the SQL.

- Decompose complex queries into simpler steps to provide application-level checkpoint or restart. For example, a complex multitable join on a one terabyte database could run for dozens of hours. A failure during this query would mean starting over from the beginning. Using `CREATE` `TABLE` `AS` `SELECT` or `PARALLEL` `INSERT` `AS` `SELECT`, you can rewrite the query as a sequence of simpler queries that run for a few hours each. If a system failure occurs, the query can be restarted from the last completed step.

- Implement manual parallel delete operations efficiently by creating a new table that omits the unwanted rows from the original table, and then dropping the original table. Alternatively, you can use the convenient parallel delete feature, which directly deletes rows from the original table.

- Create summary tables for efficient multidimensional drill-down analysis. For example, a summary table might store the sum of revenue grouped by month, brand, region, and salesman.

- Reorganize tables, eliminating chained rows, compressing free space, and so on, by copying the old table to a new table. This is much faster than export/import and easier than reloading.

Be sure to use the `DBMS_STATS` package to gather optimizer statistics on newly created tables. To avoid I/O bottlenecks, specify a tablespace that is striped across at least as many physical disks as CPUs. To avoid fragmentation in allocating space, the number of files in a tablespace should be a multiple of the number of CPUs.

**See Also:**

[Oracle Database Data Warehousing Guide](../dwhsg/data-warehouse-optimizations-techniques.md) for information about parallel execution in data warehouses

### 8.8.3 Using EXPLAIN PLAN to Show Parallel Operations Plans

Use the `EXPLAIN` `PLAN` statement to see the execution plans for parallel queries.

The `EXPLAIN` `PLAN` output shows optimizer information in the `COST`, `BYTES`, and `CARDINALITY` columns. You can also use the `utlxplp.sql` script to present the `EXPLAIN` `PLAN` output with all relevant parallel information.

There are several ways to optimize the parallel execution of join statements. You can alter system configuration, adjust parameters as discussed earlier in this chapter, or use hints, such as the `DISTRIBUTION` hint.

The key points when using `EXPLAIN` `PLAN` are to:

- Verify optimizer selectivity estimates. If the optimizer thinks that only one row is produced from a query, it tends to favor using a nested loop. This could be an indication that the tables are not analyzed or that the optimizer has made an incorrect estimate about the correlation of multiple predicates on the same table. Extended statistics or a hint may be required to provide the optimizer with the correct selectivity or to force the optimizer to use another join method.

- Use hash join on low cardinality join keys. If a join key has few distinct values, then a hash join may not be optimal. If the number of distinct values is less than the degree of parallelism (DOP), then some parallel query servers may be unable to work on the particular query.

- Consider data skew. If a join key involves excessive data skew, a hash join may require some parallel query servers to work more than others. Consider using a hint to cause a `BROADCAST` distribution method if the optimizer did not choose it. The optimizer considers the `BROADCAST` distribution method only if the `OPTIMIZER_FEATURES_ENABLE` is set to 9.0.2 or higher. See [V\$PQ_TQSTAT](monitor-parallel-performance.md) for more information.

#### 8.8.3.1 Example: Using EXPLAIN PLAN to Show Parallel Operations

You can use EXPLAIN PLAN to show parallel operations.

The following example illustrates how the optimizer intends to execute a parallel query:

    explain plan for
      SELECT /*+ PARALLEL */ cust_first_name, cust_last_name
       FROM customers c, sales s WHERE c.cust_id = s.cust_id;

    ----------------------------------------------------------
    | Id  | Operation                       |  Name          |
    ----------------------------------------------------------
    |   0 | SELECT STATEMENT                |                |
    |   1 |  PX COORDINATOR                 |                |
    |   2 |   PX SEND QC (RANDOM)           | :TQ10000       |
    |   3 |    NESTED LOOPS                 |                |
    |   4 |     PX BLOCK ITERATOR           |                |
    |   5 |      TABLE ACCESS FULL          | CUSTOMERS      |
    |   6 |     PARTITION RANGE ALL         |                |
    |   7 |      BITMAP CONVERSION TO ROWIDS|                |
    |   8 |       BITMAP INDEX SINGLE VALUE | SALES_CUST_BIX |
    ----------------------------------------------------------

    Note
    -----
       - automatic DOP: Computed Degree of Parallelism is 2

### 8.8.4 Additional Considerations for Parallel DML

Additional considerations when using parallel DML operations are introduced in this topic.

When you want to refresh your data warehouse database using parallel insert, update, or delete operations on a data warehouse, there are additional issues to consider when designing the physical database. These considerations do not affect parallel execution operations. These issues are:

- Parallel DML and Direct-Path Restrictions

- Limitation on the Degree of Parallelism

- When to Increase INITRANS

- Limitation on Available Number of Transaction Free Lists for Segments

- Multiple Archivers for Large Numbers of Redo Logs

- Database Writer Process (DBWn) Workload

- \[NO\]LOGGING Clause

#### 8.8.4.1 Parallel DML and Direct-Path Restrictions

The restrictions for parallel DML and direct-path operations are identified in this topic.

If a parallel restriction is violated, then the operation is simply performed serially. If a direct-path `INSERT` restriction is violated, then the `APPEND` hint is ignored and a conventional insert operation is performed. No error message is returned.

#### 8.8.4.2 Limitation on the Degree of Parallelism

There are certain limitations on the degree of parallelism based on the software level of Oracle Database in use.

For tables that do not have the parallel DML `itl` invariant property (tables created before Oracle9i Release 2 (9.2) or tables that were created with the `COMPATIBLE` initialization parameter set to less than `9.2`), the degree of parallelism (DOP) equals the number of partitions or subpartitions. That means that, if the table is not partitioned, the query runs serially. To determine which tables do not have this property, issue the following statement:

    SELECT u.name, o.name FROM obj$ o, tab$ t, user$ u
     WHERE o.obj# = t.obj# AND o.owner# = u.user#
     AND bitand(t.property,536870912) != 536870912;

**See Also:**

[Oracle Database Concepts](../cncpt/data-concurrency-and-consistency.md) for information about the interested transaction list (ITL), also called the transaction table

#### 8.8.4.3 When to Increase INITRANS

You should increase the value of `INITRANS` under certain situations.

If you have global indexes, a global index segment and global index blocks are shared by server processes of the same parallel DML statement. Even if the operations are not performed against the same row, the server processes can share the same index blocks. Each server transaction needs one transaction entry in the index block header before it can make changes to a block.

In this situation, when using the `CREATE` `INDEX` or `ALTER` `INDEX` statements, you should set `INITRANS`, the initial number of transactions allocated within each data block, to a large value, such as the maximum DOP against this index.

#### 8.8.4.4 Limitation on Available Number of Transaction Free Lists for Segments

There is a limitation on the available number of transaction free lists for segments in dictionary-managed tablespaces.

After a segment has been created, the number of process and transaction free lists is fixed and cannot be altered. If you specify a large number of process free lists in the segment header, you might find that this limits the number of transaction free lists that are available. You can abate this limitation the next time you re-create the segment header by decreasing the number of process free lists; this leaves more room for transaction free lists in the segment header.

For `UPDATE` and `DELETE` operations, each server process can require its own transaction free list. The parallel DML DOP is thus effectively limited by the smallest number of transaction free lists available on the table and on any of the global indexes the DML statement must maintain. For example, if the table has 25 transaction free lists and the table has two global indexes, one with 50 transaction free lists and one with 30 transaction free lists, the DOP is limited to 25. If the table had 40 transaction free lists, the DOP would have been limited to 30.

The `FREELISTS` parameter of the `STORAGE` clause is used to set the number of process free lists. By default, no process free lists are created.

The default number of transaction free lists depends on the block size. For example, if the number of process free lists is not set explicitly, a 4 KB block has about 80 transaction free lists by default. The minimum number of transaction free lists is 25.

#### 8.8.4.5 Multiple Archivers for Large Numbers of Redo Logs

Multiple archiver processes are needed for archiving large numbers of redo logs.

Parallel DDL and parallel DML operations can generate a large number of redo logs. A single `ARCH` process to archive these redo logs might not be able to keep up. To avoid this problem, you can spawn multiple archiver processes manually or by using a job queue.

#### 8.8.4.6 Database Writer Process (DBWn) Workload

There are situations when you should increase the number of database writer processes.

Parallel DML operations use a large number of data, index, and undo blocks in the buffer cache during a short interval. For example, suppose you see a high number of `free_buffer_waits` after querying the `V$SYSTEM_EVENT` view, as in the following syntax:

    SELECT TOTAL_WAITS FROM V$SYSTEM_EVENT WHERE EVENT = 'FREE BUFFER WAITS';

In this case, you should consider increasing the DBWn processes. If there are no waits for free buffers, the query does not return any rows.

#### 8.8.4.7 \[NO\]LOGGING Clause

Understand the considerations when setting the `[NO]LOGGING` clause.

The `[NO]LOGGING` clause applies to tables, partitions, tablespaces, and indexes. Virtually no log is generated for certain operations (such as direct-path `INSERT`) if the `NOLOGGING` clause is used. The `NOLOGGING` attribute is not specified at the `INSERT` statement level but is instead specified when using the `ALTER` or `CREATE` statement for a table, partition, index, or tablespace.

When a table or index has `NOLOGGING` set, neither parallel nor serial direct-path `INSERT` operations generate redo logs. Processes running with the `NOLOGGING` option set run faster because no redo is generated. However, after a `NOLOGGING` operation against a table, partition, or index, if a media failure occurs before a backup is performed, then all tables, partitions, and indexes that have been modified might be corrupted.

Direct-path `INSERT` operations (except for dictionary updates) never generate redo logs if the `NOLOGGING` clause is used. The `NOLOGGING` attribute does not affect undo, only redo. To be precise, `NOLOGGING` allows the direct-path `INSERT` operation to generate a negligible amount of redo (range-invalidation redo, as opposed to full image redo).

For backward compatibility, `[UN]RECOVERABLE` is still supported as an alternate keyword with the `CREATE` `TABLE` statement. This alternate keyword might not be supported, however, in future releases.

At the tablespace level, the logging clause specifies the default logging attribute for all tables, indexes, and partitions created in the tablespace. When an existing tablespace logging attribute is changed by the `ALTER` `TABLESPACE` statement, then all tables, indexes, and partitions created after the `ALTER` statement have the new logging attribute; existing ones do not change their logging attributes. The tablespace-level logging attribute can be overridden by the specifications at the table, index, or partition level.

The default logging attribute is `LOGGING`. However, if you have put the database in `NOARCHIVELOG` mode, by issuing `ALTER` `DATABASE` `NOARCHIVELOG`, then all operations that can be done without logging do not generate logs, regardless of the specified logging attribute.

### 8.8.5 Optimizing Performance by Creating Indexes in Parallel

You can optimize performance by creating indexes in parallel.

Multiple processes can work simultaneously to create an index. By dividing the work necessary to create an index among multiple server processes, Oracle Database can create the index more quickly than if a single server process created the index serially.

Parallel index creation works in much the same way as a table scan with an `ORDER` `BY` clause. The table is randomly sampled and a set of index keys is found that equally divides the index into the same number of pieces as the DOP. A first set of query processes scans the table, extracts key-rowid pairs, and sends each pair to a process in a second set of query processes based on a key. Each process in the second set sorts the keys and builds an index in the usual fashion. After all index pieces are built, the parallel execution coordinator simply concatenates the pieces (which are ordered) to form the final index.

Parallel local index creation uses a single server set. Each server process in the set is assigned a table partition to scan and for which to build an index partition. Because half as many server processes are used for a given DOP, parallel local index creation can be run with a higher DOP. However, the DOP is restricted to be less than or equal to the number of index partitions you want to create. To avoid this limitation, you can use the `DBMS_PCLXUTIL` package.

You can optionally specify that no redo and undo logging should occur during index creation. This can significantly improve performance but temporarily renders the index unrecoverable. Recoverability is restored after the new index is backed up. If your application can tolerate a window where recovery of the index requires it to be re-created, then you should consider using the `NOLOGGING` clause.

The `PARALLEL` clause in the `CREATE` `INDEX` statement is the only way in which you can specify the DOP for creating the index. If the DOP is not specified in the parallel clause of the `CREATE` `INDEX` statement, then the number of CPUs is used as the DOP. If there is no `PARALLEL` clause, index creation is done serially.

When creating an index in parallel, the `STORAGE` clause refers to the storage of each of the subindexes created by the query server processes. Therefore, an index created with an `INITIAL` value of 5 MB and a DOP of 12 consumes at least 60 MB of storage during index creation because each process starts with an extent of 5 MB. When the query coordinator process combines the sorted subindexes, some extents might be trimmed, and the resulting index might be smaller than the requested 60 MB.

When you add or enable a `UNIQUE` or `PRIMARY` `KEY` constraint on a table, you cannot automatically create the required index in parallel. Instead, manually create an index on the desired columns, using the `CREATE` `INDEX` statement and an appropriate `PARALLEL` clause, and then add or enable the constraint. Oracle Database then uses the existing index when enabling or adding the constraint.

Multiple constraints on the same table can be enabled concurrently and in parallel if all the constraints are in the `ENABLE` `NOVALIDATE` state. In the following example, the `ALTER` `TABLE` `ENABLE` `CONSTRAINT` statement performs the table scan that checks the constraint in parallel:

    CREATE TABLE a (a1 NUMBER CONSTRAINT ach CHECK (a1 > 0) ENABLE NOVALIDATE)
    PARALLEL;
    INSERT INTO a values (1);
    COMMIT;
    ALTER TABLE a ENABLE CONSTRAINT ach;

### 8.8.6 Parallel DML Tips

The tips for parallel DML functionality are introduced in this topic.

The topics covered include:

- Parallel DML Tip 1: INSERT

- Parallel DML Tip 2: Direct-Path INSERT

- Parallel DML Tip 3: Parallelizing INSERT, MERGE, UPDATE, and DELETE

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-tables.md) for information about improving load performance with direct-path insert

- [Oracle Database SQL Language Reference](../sqlrf/INSERT.md) for information about the `INSERT` statement

#### 8.8.6.1 Parallel DML Tip 1: INSERT

Parallel DML when using the SQL `INSERT` statement is discussed in this topic.

The functionality available using an `INSERT` statement can be summarized as shown in Table 8-5:

Table 8-5 Summary of INSERT Features

| Insert Type                           | Parallel                                                                                                                                                                                                                                                                                                                                                                                        | Serial                              | NOLOGGING                                                              |
|:--------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------|:-----------------------------------------------------------------------|
| Conventional                          | No<br>See text in this section for information about using the `NOAPPEND` hint with parallel DML enabled to perform a parallel conventional insert.                                                                                                                                                                                                                                             | Yes                                 | No                                                                     |
| Direct-path<br>`INSERT`<br>(`APPEND`) | Yes, but requires<br>`ALTER` `SESSION` `ENABLE` `PARALLEL` `DML` or the `ENABLE_PARALLEL_DML` SQL hint to enable `PARALLEL` `DML` mode<br>and one of the following:<br>• Table `PARALLEL` attribute or `PARALLEL` hint to explicitly set parallelism<br>• `APPEND` hint to explicitly set mode<br>Or the following<br>`ALTER` `SESSION` `FORCE` `PARALLEL` `DML` to force `PARALLEL` `DML` mode | Yes, but requires:<br>`APPEND` hint | Yes, but requires:<br>`NOLOGGING` attribute set for partition or table |

If parallel DML is enabled and there is a `PARALLEL` hint or `PARALLEL` attribute set for the table in the data dictionary, then insert operations are parallel and appended, unless a restriction applies. If either the `PARALLEL` hint or `PARALLEL` attribute is missing, the insert operation is performed serially. Automatic DOP only parallelizes the DML part of a SQL statement if and only if parallel DML is enabled or forced.

If parallel DML is enabled, then you can use the `NOAPPEND` hint to perform a parallel conventional insert operation. For example, you can use `/*+` `noappend` `parallel` `*/` with the SQL `INSERT` statement to perform a parallel conventional insert.

    SQL> INSERT /*+ NOAPPEND PARALLEL */ INTO sales_hist SELECT * FROM sales;

The advantage of the parallel conventional insert operation is the ability to perform online operations with none of the restrictions of direct-path `INSERT`. The disadvantage of the parallel conventional insert operation is that this process may be slower than direct-path `INSERT`.

#### 8.8.6.2 Parallel DML Tip 2: Direct-Path INSERT

Parallel DML when using Direct-Path `INSERT` operations is discussed in this topic.

The append mode is the default during a parallel insert operation. Data is always inserted into a new block, which is allocated to the table. Using the `APPEND` hint is optional. You should use append mode to increase the speed of `INSERT` operations, but not when space utilization must be optimized. You can use `NOAPPEND` to override append mode.

The `APPEND` hint applies to both serial and parallel insert operation. Serial insertions are also faster if you use this hint. The `APPEND` hint, however, does require more space and locking overhead.

You can use `NOLOGGING` with `APPEND` to make the process even faster. `NOLOGGING` means that no redo log is generated for the operation. `NOLOGGING` is never the default; use it when you want to optimize performance. It should not typically be used when recovery is needed for the table or partition. If recovery is needed, be sure to perform a backup immediately after the operation. Use the `ALTER` `TABLE` `[NO]LOGGING` statement to set the appropriate value.

#### 8.8.6.3 Parallel DML Tip 3: Parallelizing INSERT, MERGE, UPDATE, and DELETE

Parallel DML when using insert, merge, update, and delete operations is discussed in this topic.

When the table or partition has the `PARALLEL` attribute in the data dictionary, that attribute setting is used to determine parallelism of `INSERT`, `UPDATE`, and `DELETE` statements and queries. An explicit `PARALLEL` hint for a table in a statement overrides the effect of the `PARALLEL` attribute in the data dictionary.

You can use the `NO_PARALLEL` hint to override a `PARALLEL` attribute for the table in the data dictionary. In general, hints take precedence over attributes.

DML operations are considered for parallelization if the session has been enabled in the `PARALLEL` `DML` mode with the `ALTER` `SESSION` `ENABLE` `PARALLEL` `DML` statement or a specific SQL statement has been enabled in the `PARALLEL` `DML` mode with the `ENABLE_PARALLEL_DML` hint. The mode does not affect parallelization of queries or of the query portions of a DML statement.

##### 8.8.6.3.1 Parallelizing INSERT SELECT

In the `INSERT `... `SELECT` statement, you can specify a `PARALLEL` hint after the `INSERT` keyword, in addition to the hint after the `SELECT` keyword.

The `PARALLEL` hint after the `INSERT` keyword applies to the `INSERT` operation only, and the `PARALLEL` hint after the `SELECT` keyword applies to the `SELECT` operation only. Thus, parallelism of the `INSERT` and `SELECT` operations are independent of each other. If one operation cannot be performed in parallel, it has no effect on whether the other operation can be performed in parallel.

The ability to parallelize insert operations causes a change in existing behavior if the user has explicitly enabled the session for parallel DML and if the table in question has a `PARALLEL` attribute set in the data dictionary entry. In that case, existing `INSERT` `SELECT` statements that have the select operation parallelized can also have their insert operation parallelized.

If you query multiple tables, you can specify multiple `SELECT` `PARALLEL` hints and multiple `PARALLEL` attributes.

Example 8-5 shows the addition of the new employees who were hired after the acquisition of `ACME`.

Example 8-5 Parallelizing INSERT SELECT

    INSERT /*+ PARALLEL(employees) */ INTO employees
    SELECT /*+ PARALLEL(ACME_EMP) */ *  FROM ACME_EMP;

The `APPEND` keyword is not required in this example because it is implied by the `PARALLEL` hint.

##### 8.8.6.3.2 Parallelizing UPDATE and DELETE

The `PARALLEL` hint (placed immediately after the `UPDATE` or `DELETE` keyword) applies not only to the underlying scan operation, but also to the `UPDATE` or `DELETE` operation.

Alternatively, you can specify `UPDATE` or `DELETE` parallelism in the `PARALLEL` clause specified in the definition of the table to be modified.

If you have explicitly enabled parallel DML for the session or transaction, `UPDATE` or `DELETE` statements that have their query operation parallelized can also have their `UPDATE` or `DELETE` operation parallelized. Any subqueries or updatable views in the statement can have their own separate `PARALLEL` hints or clauses, but these parallel directives do not affect the decision to parallelize the update or delete. If these operations cannot be performed in parallel, it has no effect on whether the `UPDATE` or `DELETE` portion can be performed in parallel.

Example 8-6 shows the update operation to give a 10 percent salary raise to all clerks in Dallas.

Example 8-6 Parallelizing UPDATE and DELETE

    UPDATE /*+ PARALLEL(employees) */ employees
     SET salary=salary * 1.1 WHERE job_id='CLERK' AND department_id IN
      (SELECT department_id FROM DEPARTMENTS WHERE location_id = 'DALLAS');

The `PARALLEL` hint is applied to the `UPDATE` operation and to the scan.

Example 8-7 shows the removal of all products of category `39` because that business line was recently spun off into a separate company.

Example 8-7 Parallelizing UPDATE and DELETE

    DELETE /*+ PARALLEL(PRODUCTS) */ FROM PRODUCTS
      WHERE category_id = 39;

Again, the parallelism is applied to the scan and `UPDATE` operations on the table `employees`.

### 8.8.7 Incremental Data Loading in Parallel

Parallel DML combined with the updatable join views facility provides an efficient solution for refreshing the tables of a data warehouse system.

To refresh tables is to update them with the differential data generated from the OLTP production system.

In the following example, assume a refresh of a table named `customers` that has columns `c_key`, `c_name`, and `c_addr`. The differential data contains either new rows or rows that have been updated since the last refresh of the data warehouse. In this example, the updated data is shipped from the production system to the data warehouse system by means of ASCII files. These files must be loaded into a temporary table, named `diff_customer`, before starting the refresh process. You can use SQL\*Loader with both the parallel and direct options to efficiently perform this task. You can use the `APPEND` hint when loading in parallel as well.

After `diff_customer` is loaded, the refresh process can be started. It can be performed in two phases or by merging in parallel, as demonstrated in the following:

- Optimizing Performance for Updating the Table in Parallel

- Efficiently Inserting the New Rows into the Table in Parallel

- Optimizing Performance by Merging in Parallel

#### 8.8.7.1 Optimizing Performance for Updating the Table in Parallel

How to optimize performance for updating a table in parallel is discussed in this topic.

The following statement is a straightforward SQL implementation of the update using subqueries:

    UPDATE customers SET(c_name, c_addr) = (SELECT c_name, c_addr
      FROM diff_customer WHERE diff_customer.c_key = customer.c_key)
      WHERE c_key IN(SELECT c_key FROM diff_customer);

Unfortunately, the two subqueries in this statement affect performance.

An alternative is to rewrite this query using updatable join views. To rewrite the query, you must first add a primary key constraint to the `diff_customer` table to ensure that the modified columns map to a key-preserved table:

    CREATE UNIQUE INDEX diff_pkey_ind ON diff_customer(c_key) PARALLEL NOLOGGING;

    ALTER TABLE diff_customer ADD PRIMARY KEY (c_key);

You can then update the `customers` table with the following SQL statement:

    UPDATE /*+ PARALLEL(cust_joinview) */
      (SELECT /*+ PARALLEL(customers) PARALLEL(diff_customer) */
      CUSTOMER.c_name AS c_name CUSTOMER.c_addr AS c_addr,
       diff_customer.c_name AS c_newname, diff_customer.c_addr AS c_newaddr
       FROM diff_customer
       WHERE customers.c_key = diff_customer.c_key) cust_joinview
       SET c_name = c_newname, c_addr = c_newaddr;

The underlying scans feeding the join view `cust_joinview` are done in parallel. You can then parallelize the update to further improve performance, but only if the `customers` table is partitioned.

#### 8.8.7.2 Efficiently Inserting the New Rows into the Table in Parallel

How to efficiently insert new rows into a table in parallel is discussed in this topic.

The last phase of the refresh process consists of inserting the new rows from the `diff_customer` temporary table to the `customers` table. Unlike the update case, you cannot avoid having a subquery in the `INSERT` statement:

    INSERT /*+PARALLEL(customers)*/ INTO customers SELECT * FROM diff_customer s);

However, you can guarantee that the subquery is transformed into an anti-hash join by using the `HASH_AJ` hint. Doing so enables you to use parallel `INSERT` to execute the preceding statement efficiently. Parallel `INSERT` is applicable even if the table is not partitioned.

#### 8.8.7.3 Optimizing Performance by Merging in Parallel

How to optimize performance by merging in parallel is discussed in this topic.

You can combine update and insert operations into one statement, commonly known as a merge, as shown in the following example.

    MERGE INTO customers USING diff_customer
    ON (diff_customer.c_key = customer.c_key) WHEN MATCHED THEN
      UPDATE SET (c_name, c_addr) = (SELECT c_name, c_addr
      FROM diff_customer WHERE diff_customer.c_key = customers.c_key)
    WHEN NOT MATCHED THEN
     INSERT VALUES (diff_customer.c_key,diff_customer.c_data);

The SQL statement in the previous example achieves the same result as all of the statements in Optimizing Performance for Updating the Table in Parallel and Efficiently Inserting the New Rows into the Table in Parallel.
