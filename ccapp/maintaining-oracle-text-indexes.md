You can maintain your index for an error or indexing failure.

This chapter contains the following topics:

- Viewing Index Errors

- Dropping an Index

- Resuming Failed Index

- Re-creating an Index

- Rebuilding an Index

- Dropping a Preference

- Managing DML Operations for a CONTEXT Index

### 5.1 Viewing Index Errors

Sometimes an indexing operation might fail or it might not complete successfully. When the system encounters an error during row indexing, it logs the error in an Oracle Text view.

You can view errors on your indexes with `CTX_USER_INDEX_ERRORS.` View errors on all indexes as `CTXSYS` with `CTX_INDEX_ERRORS.`

For example, to view the most recent errors on your indexes, enter the following statement:

    SELECT err_timestamp, err_text
      FROM ctx_user_index_errors
      ORDER BY err_timestamp DESC;

To clear the view of errors, enter:

    DELETE FROM ctx_user_index_errors;

This view is cleared automatically when you create a new index.

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-views.md) to learn more about index error views

### 5.2 Dropping an Index

You must drop an existing index before you can re-create it with the `CREATE` `INDEX` statement.

Drop an index by using the `DROP` `INDEX` statement in SQL.

If you try to create an index with an invalid `PARAMETERS` string, then you still need to drop it before you can re-create it.

For example, to drop an index called `newsindex,` enter the following SQL statement:

    DROP INDEX newsindex;

If Oracle Text cannot determine the state of the index (for example, because of an indexing malfunction), you cannot drop the index. Instead use:

    DROP INDEX newsindex FORCE;

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md) to learn more about the `DROP` `INDEX` statement

### 5.3 Resuming a Failed Index

You can sometimes resume a failed index by using the `ALTER` `INDEX` statement. You typically resume a failed index after you have investigated and corrected the index failure. You cannot resume all index failures.

Index optimization commits at regular intervals. Therefore, if an optimization operation fails, then all optimization work up to the commit point was already saved.

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md) to learn more about the `ALTER` `INDEX` statement syntax

The following statement resumes the indexing operation on `newsindex` with 10 megabytes of memory:

    ALTER INDEX newsindex REBUILD PARAMETERS('resume memory 10M');

### 5.4 Re-creating an Index

This section describes the procedures for re-creating an index. During the re-creation process, you can query the index normally.

- Re-creating a Global Index

- Re-creating a Local Partitioned Index

#### 5.4.1 Re-creating a Global Index

Oracle Text provides `RECREATE_INDEX_ONLINE` to re-create a `CONTEXT` index with new preferences, while preserving inserts, updates, and deletes on the base table. You can use `RECREATE_INDEX_ONLINE` in a single-step procedure to re-create a `CONTEXT` index online for global indexes. Because the new index is created alongside the existing index, this operation requires storage that is roughly equal to the size of the existing index. Also, because the `RECREATE_INDEX_ONLINE` operation is performed online, you can perform inserts, updates, and deletes on the base table during the operation. All insert, update, and delete operations that occur during the re-creation process are logged into an online pending queue.

- After the re-creation operation is complete, new information may not be immediately reflected. As with creating an index online, you should synchronize the index after the re-creation operation is complete to bring it fully up-to-date.

- Synchronizations issued against the index during the re-creation operation are processed against the existing data. Synchronizations are blocked when queries return errors.

- Optimize commands issued against the index during the re-creation operation return immediately without error and without processing.

- During `RECREATE_INDEX_ONLINE,` you can query the index normally most of the time. Queries return results based on the existing index and policy until after the final swap. Also, if you issue insert, update, and delete operations and synchronize them, then you will be able to see the new rows when you query the existing index.

**Note:**

Transactional queries are not supported with `RECREATE_INDEX_ONLINE.`

##### Re-creating a Global Index with Time Limit for Synch

You can control index re-creation to set a time limit for `SYNC_INDEX` during nonbusiness hours and incrementally re-create the index. Use the [`CREATE_SHADOW_INDEX`](../ccref/CTX_DDL-package.md) procedure with `POPULATE_PENDING` and maxtime.

##### Re-creating a Global Index with Scheduled Swap

With `CTX_DDL.EXCHANGE_SHADOW_INDEX,` you can perform index re-creation during nonbusiness hours when query failures and DML blocking can be tolerated.

**See Also:**

- [Oracle Text Reference](../ccref/CTX_DDL-package.md) to learn more about the `RECREATE_INDEX_ONLINE` procedure

- [Oracle Text Reference](../ccref/CTX_DDL-package.md) for information and examples for `CREATE_SHADOW_INDEX`

- [Oracle Text Reference](../ccref/CTX_DDL-package.md) for information and examples for `CTX_DDL.EXCHANGE_SHADOW_INDEX`

#### 5.4.2 Re-creating a Local Partitioned Index

If the index is locally partitioned, you cannot re-create the index in one step. You must first create a shadow policy, and then run the `RECREATE_INDEX_ONLINE` procedure for every partition. You can specify `SWAP` or `NOSWAP,` which indicates whether re-creating the index for the partition swaps the index partition data and index partition metadata.

You can also use this procedure to update the metadata (for example, the storage preference) of each partition when you specify `NOPOPULATE` in the parameter string. This keyword is useful for incremental building of a shadow index through time-limited synchronization. If you specify `NOPOPULATE,` then `NOSWAP` is silently enforced.

- When all partitions use `NOSWAP,` the storage requirement is approximately equal to the size of the existing index. During re-creation of the index partition, because no swapping is performed, queries on the partition are processed normally. Queries spanning multiple partitions return consistent results across partitions until the swapping stage is reached.

- When the partitions are rebuilt with `SWAP,` the storage requirement for the operation is equal to the size of the existing index partition. Because index partition data and metadata are swapped after re-creation, queries spanning multiple partitions do not return consistent results from partition to partition, but they will always be correct with respect to each index partition.

- If you specify `SWAP,` then insert, update, and delete operations and synchronization on the partition are blocked during the swap process.

##### Re-creating a Local Index with All-at-Once Swap

You can re-create a local partitioned index online to create or change preferences. The swapping of the index and partition metadata occurs at the end of the process. Queries spanning multiple partitions return consistent results across partitions when the re-creation is in process, except at the end when [`EXCHANGE_SHADOW_INDEX`](../ccref/CTX_DDL-package.md) is running.

##### Scheduling Local Index Re-creation with All-at-Once Swap

With `RECREATE_INDEX_ONLINE` of the `CTX.DDL` package, you can incrementally re-create a local partitioned index, where partitions are all swapped at the end.

##### Re-creating a Local Index with Per-Partition Swap

Instead of swapping all partitions at once, you can re-create the index online with new preferences, and each partition is swapped as it is completed. Queries across all partitions may return inconsistent results during this process. This procedure uses `CREATE_SHADOW_INDEX` with `RECREATE_INDEX_ONLINE.`

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md) for complete information about `RECREATE_INDEX_ONLINE`

### 5.5 Rebuilding an Index

You can rebuild a valid index by using `ALTER` `INDEX.` Rebuilding an index does not allow most index settings to be changed. You might rebuild an index when you want to index with a new preference. Generally, there is no advantage in rebuilding an index over dropping it and re-creating it with the `CREATE` `INDEX` statement.

**See Also:**

"Re-creating an Index" for information about changing index settings

The following statement rebuilds the index and replaces the lexer preference with `my_lexer:`

    ALTER INDEX newsindex REBUILD PARAMETERS('replace lexer my_lexer');

### 5.6 Dropping a Preference

You might drop a custom index preference when you no longer need it for indexing.

You drop index preferences with the `CTX_DDL.DROP_PREFERENCE` procedure.

Dropping a preference does not affect the index that is created from the preference.

**See Also:**

[Oracle Text Reference](../ccref/CTX_DDL-package.md) to learn more about the syntax for the `CTX_DDL.DROP_PREFERENCE` procedure

The following code drops the `my_lexer` preference:

    begin
    ctx_ddl.drop_preference('my_lexer');
    end;

### 5.7 Managing DML Operations for a CONTEXT Index

DML operations refer to when documents are inserted, updated, or deleted from the base table. This section describes how you can view, synchronize, and optimize the Oracle Text `CONTEXT` index for DML operations. This section contains the following topics:

- Viewing Pending DML Operations

- Synchronizing the Index

- Optimizing the Index

**Note:**

`CTXCAT` indexes are transactional and are updated immediately when the base table changes. The manual synchronization as described in this section is not necessary for a `CTXCAT` index.

#### 5.7.1 Viewing Pending DML Operations

When you insert or update documents in the base table, their rowids are held in a DML queue until you synchronize the index. You can view this queue in the `CTX_USER_PENDING` view.

For example, to view pending DML operations on your indexes, enter the following statement:

    SELECT pnd_index_name, pnd_rowid, to_char(
            pnd_timestamp, 'dd-mon-yyyy hh24:mi:ss'
            ) timestamp FROM ctx_user_pending;

This statement gives output in the following form:

    PND_INDEX_NAME                 PND_ROWID          TIMESTAMP
    ------------------------------ ------------------ --------------------
    MYINDEX                        AAADXnAABAAAS3SAAC 06-oct-1999 15:56:50

**See Also:**

[Oracle Text Reference](../ccref/oracle-text-views.md) to learn more about the `CTX_USER_PENDING` view

#### 5.7.2 Synchronizing the Index

When you synchronize the index, you process all pending updates and inserts to the base table. You can do this in PL/SQL with the `CTX_DDL.SYNC_INDEX` procedure. You can also control the duration and locking behavior for index synchronization with the `CTX_DDL.SYNC_INDEX` procedure.

##### Synchronizing the Index with SYNC_INDEX

The following example synchronizes the index with 2 megabytes of memory:

    begin

    ctx_ddl.sync_index('myindex', '2M');

    end;

Starting with Oracle Database 12c Release 2 (12.2.0.1), you automatically merge rows from `STAGE_ITAB` back to the `$I` table by using `SYNC_INDEX.` This merging of rows happens when the number of rows in `STAGE_ITAB ($G)` exceeds the `STAGE_ITAB_MAX_ROWS` parameter (1 million by default). Therefore, you do not have to run merge optimization explicitly or schedule an auto optimize job.

##### Maxtime Parameter for SYNC_INDEX

The `SYNC_INDEX` procedure includes a `maxtime` parameter that, like `OPTIMIZE_INDEX,` indicates a suggested time limit in minutes for the operation. The `SYNC_INDEX` procedure processes as many documents in the queue as possible within the given time limit.

- `NULL maxtime` is equivalent to `CTX_DDL.MAXTIME_UNLIMITED.`

- The time limit is approximate. The actual time may be less than, or greater than, what you specify.

- The `ALTER` `INDEX`... `sync` command has no changes because it is deprecated.

- The `maxtime` parameter is ignored when `SYNC_INDEX` is invoked without an index name.

- The `maxtime` parameter cannot be communicated for automatic synchronizations (for example, `sync` `on` `commit` or `sync` `every`).

##### Locking Parameter for SYNC_INDEX

The locking parameter of `SYNC_INDEX` enables you to configure how the synchronization works when another synchronization is already running on the index.

- The locking parameter is ignored when `SYNC_INDEX` is invoked without an index name.

- The locking parameter cannot be communicated for automatic synchronizations (that is, `sync` `on` `commit` or `sync` `every`).

- When the locking mode is `LOCK_WAIT,` the mode waits forever and ignores the maxtime setting if it cannot get a lock.

The options are as follows:

| Option                      | Description                                                                                                                                             |
|:----------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CTX_DDL.LOCK_WAIT`         | If another `SYNC_INDEX` is running, wait until the running synchronization is complete, and then begin the new synchronization.                         |
| `CTX_DDL.LOCK_NOWAIT`       | If another `SYNC_INDEX` is running, immediately return without error.                                                                                   |
| `CTX_DDL.LOCK_NOWAIT_ERROR` | If another `SYNC_INDEX` is running, immediately generate an error (DRG-51313: timeout while waiting for inserts, updates, or deletes or optimize lock). |

**See Also:**

[Oracle Text Reference](../ccref/CTX_DDL-package.md) to learn more about the `CTX_DDL.SYNC_INDEX` statement syntax

#### 5.7.3 Optimizing the Index

The `CONTEXT` index is an inverted index where each word contains the list of documents that contain that word. For example, after a single initial indexing operation, the word DOG might have the following entry:

    DOG DOC1 DOC3 DOC5

Frequent index synchronization ultimately causes fragmentation of your `CONTEXT` index. Index fragmentation can adversely affect query response time. Therefore, to reduce fragmentation and index size and to ensure optimal query performance, allow time to optimize your `CONTEXT` index.

To schedule an auto optimize job, you must explicitly set `STAGE_ITAB_MAX_ROWS` to `0` to disable the automatic merging that now happens with `SYNC_INDEX.`

To optimize an index, Oracle recommends that you use `CTX_DDL.OPTIMIZE_INDEX.` To understand index optimization, you must understand the structure of the index and what happens when it is synchronized. This section contains the following topics:

- Index Fragmentation

- Document Invalidation and Garbage Collection

- Single Token Optimization

- Viewing Index Fragmentation and Garbage Data

**See Also:**

[Oracle Text Reference](../ccref/CTX_DDL-package.md) for the `CTX_DDL.OPTIMIZE_INDEX` statement syntax and examples

##### 5.7.3.1 Index Fragmentation

When you add new documents to the base table, the index is synchronized by adding new rows. For example, if you add the DOC 7 document with the word dog and synchronize the index, you now have:

    DOG DOC1 DOC3 DOC5
    DOG DOC7

Subsequent inserts, updates, or deletes also create new rows, as follows:

    DOG DOC1 DOC3 DOC5
    DOG DOC7
    DOG DOC9
    DOG DOC11

Index fragmentation occurs when you add new documents and synchronize the index. In particular, background inserts, updates, or deletes, which synchronize the index frequently, generally produce more fragmentation than batch mode synchronization.

When you perform batch processing less frequently, you reduce fragmentation because you produce longer document lists with a reduced number of rows in the index.

You can reduce index fragmentation by optimizing the index in either `FULL` or `FAST` mode with `CTX_DDL.OPTIMIZE_INDEX.`

##### 5.7.3.2 Document Invalidation and Garbage Collection

When you remove documents from the base table, Oracle Text marks the document as removed but does not immediately alter the index.

Because the old information takes up space and can cause extra overhead at query time, you must remove the old information from the index by optimizing it in `FULL` mode. This process is called garbage collection. Optimizing in `FULL` mode for garbage collection is necessary when you perform frequent updates or deletes to the base table.

##### 5.7.3.3 Single Token Optimization

In addition to optimizing the entire index, you can optimize single tokens. You can use token mode to optimize index tokens that are frequently searched, without spending time on optimizing tokens that are rarely referenced.

For example, you can specify that only the token DOG be optimized in the index, if you know that this token is updated and queried frequently.

An optimized token can improve query response time for the token.

To optimize an index in token mode, use `CTX_DDL.OPTIMIZE_INDEX.`

##### 5.7.3.4 Viewing Index Fragmentation and Garbage Data

With the `CTX_REPORT.INDEX_STATS` procedure, you can create a statistical report on your index. The report includes information on optimal row fragmentation, a list of most fragmented tokens, and the amount of garbage data in your index. Although this report might take a long time to run for large indexes, it can help you decide whether to optimize your index.

**See Also:**

[Oracle Text Reference](../ccref/CTX_REPORT-package.md) to learn more about using the `CTX_REPORT.INDEX_STATS` procedure
