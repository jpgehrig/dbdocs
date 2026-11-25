A column of JSON data can be stored in the In-Memory Column Store (IM column store) to improve query performance.

**See Also:**

[Oracle Database In-Memory Guide](../inmem/in-memory-column-store-architecture.md)

- Overview of In-Memory JSON Data
  You can move a table with a column of JSON data to the In-Memory Column Store (IM column store), to improve the performance of queries that share costly expressions by caching the expression results. This is especially useful for analytical queries that scan a large number of small JSON documents.
- Populating JSON Data Into the In-Memory Column Store
  You use `ALTER TABLE INMEMORY` to populate a table with a column of JSON data into the In-Memory Column Store (IM column store), to improve the performance of queries that share costly expressions by caching the results of evaluating those expressions.
- Upgrading Tables With JSON Data For Use With the In-Memory Column Store
  A table with JSON columns created using a database that did not have a compatibility setting of at least 12.2 or did not have `max_string_size = extended` must first be upgraded, before it can be populated into the In-Memory Column Store (IM column store). To do this, run script `rdbms/admin/utlimcjson.sql`.

**Parent topic:** [Performance Tuning for JSON](performance-tuning-for-json-data.md)

### 29.1 Overview of In-Memory JSON Data

You can move a table with a column of JSON data to the In-Memory Column Store (IM column store), to improve the performance of queries that share costly expressions by caching the expression results. This is especially useful for analytical queries that scan a large number of small JSON documents.

The IM column store is supported only for JSON documents smaller than 32,767 bytes. If you have a mixture of document sizes, those documents that are larger than 32,767 bytes are processed without the In-Memory optimization. For better performance, consider breaking up documents larger than 32,767 bytes into smaller documents.

The IM column store is an optional SGA pool that stores copies of tables and partitions in a special columnar format optimized for rapid scans. The IM column store supplements the row-based storage in the database buffer cache. You do not need to load the same object into both the IM column store and the buffer cache. The two caches are kept transactionally consistent. The database transparently sends online transaction processing (OLTP) queries (such as primary-key lookups) to the buffer cache and analytic and reporting queries to the IM column store.

You can think of the use of JSON data in memory as improving the performance of SQL/JSON path access. SQL/JSON functions `json_table`, `json_query`, and `json_value`, and SQL condition `json_exists` all accept a SQL/JSON path argument, and they can all benefit from loading JSON data into the IM column store. (Full-text search using SQL/JSON function `json_textcontains` does not benefit from the IM column store.) Once JSON documents have been loaded into memory, any subsequent path-based operations on them use the In-Memory representation, which avoids the overhead associated with reading and parsing the on-disk format.

If queried JSON data is populated into the IM column store, and if there are function-based indexes that can apply to that data, the optimizer chooses whether to use an index or to scan the data in memory. In general, if index probing results in few documents then a functional index can be preferred by the optimizer. In practice this means that the optimizer can prefer a functional index for very selective queries or DML statements.

On the other hand, if index probing results in many documents then the optimizer might choose to scan the data in memory, by scanning the function-based index expression as a virtual-column expression.

Ad hoc queries, that is, queries that are not used frequently to target a given SQL/JSON path expression, benefit in a general way from populating JSON data into the IM column store, by quickly scanning the data. But if you have some frequently used queries then you can often further improve their performance in these ways:

- Creating virtual columns that project scalar values (not under an array) from a column of JSON data and loading those virtual columns into the IM column store.

- Creating a materialized view on a frequently queried `json_table` expression and loading the view into the IM column store.

However, if you have a function-based index that projects a scalar value using function `json_value` then you need not explicitly create a virtual column to project it. As mentioned above, in this case the function-based index expression is automatically loaded into the IM column store as a virtual column. The optimizer can choose, based on estimated cost, whether to scan the function-based index in the usual manner or to scan the index expression as a virtual-column expression.

**Note:**

- The advantages of a virtual column over a materialized view are that you can build an index on it and you can obtain statistics on it for the optimizer.

- Virtual columns, like columns in general, are subject to the 1000-column limit for a given table.

#### Prerequisites For Using JSON Data In Memory

To be able to take advantage of the IM column store for JSON data, the following must all be true:

- Database compatibility is 12.2.0.0 or higher.

- The values set for `max_string_size` in the Oracle instance startup configuration file must be `'extended'`.

- Sufficient SGA memory must be configured for the IM column store.

- A DBA has specified that the tablespace, table, or materialized view that contains the JSON columns is eligible for population into the IM column store, using keyword `INMEMORY` in a `CREATE` or `ALTER` statement.

- Initialization parameters are set as follows:

  - `IMMEMORY_EXPRESSIONS_USAGE` is `STATIC_ONLY` or `ENABLE`.

    `ENABLE` allows In-Memory materialization of dynamic expressions, if used in conjunction with PL/SQL procedure `DBMS_INMEMORY.ime_capture_expressions`.

  - `IMMEMORY_VIRTUAL_COLUMNS` is `ENABLE`, meaning that the IM column store populates all virtual columns. (The default value is `MANUAL`.)

- The columns storing the JSON data must each have `is json` check constraints. (That is, the data must be known to be JSON data.)

You can check the value of each initialization parameter using command `SHOW PARAMETER`. (You must be logged in as database user `SYS` or equivalent for this.) For example:

    SHOW PARAMETER INMEMORY_VIRTUAL_COLUMNS

**Related Topics**

- Populating JSON Data Into the In-Memory Column Store

**Parent topic:** In-Memory JSON Data

### 29.2 Populating JSON Data Into the In-Memory Column Store

You use `ALTER TABLE INMEMORY` to populate a table with a column of JSON data into the In-Memory Column Store (IM column store), to improve the performance of queries that share costly expressions by caching the results of evaluating those expressions.

The IM column store is an optional SGA pool that stores copies of tables and partitions in a special columnar format optimized for rapid scans. The IM column store supplements the row-based storage in the database buffer cache. (It does not replace the buffer cache, but you do not need to load the same object into both the IM column store and the buffer cache. The two caches are kept transactionally consistent.)

You specify that a table with a given JSON column (that is, a column that has an `is json` check constraint) is to be populated into the IM column store by marking the table as `INMEMORY`. Example 29-1 illustrates this.

The IM column store is used for queries of documents that are smaller than 32,767 bytes. Queries of documents that are larger than that do not benefit from the IM column store.

**Note:**

If a JSON column in a table that is to be populated into the IM column store was created using a database that did not have a compatibility setting of at least 12.2 or did not have `max_string_size` set to `extended` (this is the case prior to Oracle Database 12c Release 2 (12.2.0.1), for instance) then you must first run script `rdbms/admin/utlimcjson.sql`. It prepares all existing tables that have JSON columns to take advantage of the In-Memory JSON processing that was added in Release 12.2.0.1. See Upgrading Tables With JSON Data For Use With the In-Memory Column Store.

After you have marked a table that has JSON columns as `INMEMORY`, an In-Memory virtual column is added to it for each JSON column. The corresponding virtual column is used for queries of a given JSON column. The virtual column contains the same JSON data as the corresponding JSON column, but in an Oracle binary format, **OSON**.

Example 29-1 Populating JSON Data Into the IM Column Store

    SELECT COUNT(1) FROM j_purchaseorder
      WHERE json_exists(po_document,
                        '$.ShippingInstructions?(@.Address.zipCode == 99236)');

    -- The execution plan shows: TABLE ACCESS FULL

    -- Specify table as INMEMORY, with default PRIORITY setting of NONE,
    -- so it is populated only when a full scan is triggered.

    ALTER TABLE j_purchaseorder INMEMORY;

    -- Query the table again, to populate it into the IM column store.
    SELECT COUNT(1) FROM j_purchaseorder
      WHERE json_exists(po_document,
                        '$.ShippingInstructions?(@.Address.zipCode == 99236)');

    -- The execution plan for the query now shows: TABLE ACCESS INMEMORY FULL

**See Also:**

[Oracle Database In-Memory Guide](../inmem/populating-objects-in-memory.md)

**Parent topic:** In-Memory JSON Data

### 29.3 Upgrading Tables With JSON Data For Use With the In-Memory Column Store

A table with JSON columns created using a database that did not have a compatibility setting of at least 12.2 or did not have `max_string_size = extended` must first be upgraded, before it can be populated into the In-Memory Column Store (IM column store). To do this, run script `rdbms/admin/utlimcjson.sql`.

Script `rdbms/admin/utlimcjson.sql` upgrades all existing tables that have JSON columns so they can be populated into the IM column store. To use it, all of the following must be true:

- Database parameter `compatible` must be set to `12.2.0.0` or higher.

- Database parameter `max_string_size` must be set to `extended`.

- The JSON columns being upgraded must have an `is json` check constraint defined on them.

**Related Topics**

- Overview of In-Memory JSON Data

**Parent topic:** In-Memory JSON Data
