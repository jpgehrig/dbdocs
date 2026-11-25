You can index JSON data as you would any data of the type you use to store it. In addition, you can define a JSON search index, which is useful for both ad hoc structural queries and full-text queries.

- Overview of Indexing JSON Data
  There is no dedicated SQL data type for JSON data, so you can index it in the usual ways. In addition, you can index it in a general way, with a JSON search index, for ad hoc structural queries and full-text queries.
- How To Tell Whether a Function-Based Index for JSON Data Is Picked Up
  To determine whether a given query picks up a given function-based index, look for the index name in the execution plan for the query.
- Creating Bitmap Indexes for SQL/JSON Condition JSON_EXISTS
  You can create a bitmap index for the value returned by `json_exists`. This is the right kind of index to use for `json_exists`, because there are only two possible return values for a condition (true and false).
- Creating JSON_VALUE Function-Based Indexes
  You can create a function-based index for SQL/JSON function `json_value`. You can use the standard syntax for this, explicitly specifying function `json_value`, or you can use the simple dot-notation syntax. Indexes created in either of these ways can be used with both dot-notation queries and `json_value` queries.
- Using a JSON_VALUE Function-Based Index with JSON_TABLE Queries
  An index created using `json_value` with `ERROR ON ERROR` can be used for a query involving `json_table`, if the `WHERE` clause refers to a column projected by `json_table`, and the effective SQL/JSON path that targets that column matches the indexed path expression.
- Using a JSON_VALUE Function-Based Index with JSON_EXISTS Queries
  An index created using SQL/JSON function `json_value` with `ERROR ON ERROR` can be used for a query involving SQL/JSON condition `json_exists`, provided the query path expression has a filter expression that contains only a path-expression comparison or multiple such comparisons separated by `&&`.
- Data Type Considerations for JSON_VALUE Indexing and Querying
  By default, SQL/JSON function `json_value` returns a `VARCHAR2` value. When you create a function-based index using `json_value`, unless you use a `RETURNING` clause to specify a different return data type, the index is not picked up for a query that expects a non-`VARCHAR2` value.
- Indexing Multiple JSON Fields Using a Composite B-Tree Index
  To index multiple fields of a JSON object, you first create virtual columns for them. Then you create a composite B-tree index on the virtual columns.
- JSON Search Index: Ad Hoc Queries and Full-Text Search
  A JSON search index is a general index. It can improve the performance of both (1) ad hoc structural queries, that is, queries that you might not anticipate or use regularly, and (2) full-text search. It is an Oracle Text index that is designed specifically for use with JSON data.

**Parent topic:** [Performance Tuning for JSON](performance-tuning-for-json-data.md)

### 28.1 Overview of Indexing JSON Data

There is no dedicated SQL data type for JSON data, so you can index it in the usual ways. In addition, you can index it in a general way, with a JSON search index, for ad hoc structural queries and full-text queries.

You can index JSON data as you would any data of the type that you use to store it. In particular, you can use a B-tree index or a bitmap index for SQL/JSON function `json_value`, and you can use a bitmap index for SQL/JSON conditions `is json`, `is not json`, and `json_exists`.

(More generally, a bitmap index can be appropriate wherever the number of possible values for the function is small. For example, you can use a bitmap index for function `json_value` if the value is expected to be Boolean or otherwise one of a small number of string values.)

As always, such function-based indexing is appropriate for queries that target particular functions, which in the context of SQL/JSON functions means particular SQL/JSON path expressions. It is not very helpful for queries that are ad hoc, that is, arbitrary. Define a function-based index if you know that you will often query a particular path expression.

If you query in an ad hoc manner then define a **JSON search index**. This is a general index, not targeted to any specific path expression. It is appropriate for structural queries, such as looking for a JSON field with a particular value, and for full-text queries using SQL/JSON condition `json_textcontains`, such as looking for a particular word among various string values.

You can of course define both function-based indexes and a JSON search index for the same JSON column.

A JSON search index is an Oracle Text (full-text) index designed specifically for use with JSON data.

**Note:**

Oracle recommends that you use AL32UTF8 as the database character set. Automatic character-set conversion can take place when creating or applying an index. Such conversion can be lossy, which can mean that some data that you might expect to be returned by a query is not returned. See [Character Sets and Character Encoding for JSON Data](json-character-sets-and-encoding.md).

**Related Topics**

- [Using GeoJSON Geographic Data](using-GeoJSON-geographic-data.md)
- JSON Search Index: Ad Hoc Queries and Full-Text Search

**Parent topic:** Indexes for JSON Data

### 28.2 How To Tell Whether a Function-Based Index for JSON Data Is Picked Up

To determine whether a given query picks up a given function-based index, look for the index name in the execution plan for the query.

For example, given the index defined in Example 28-4, an execution plan for the `json_value` query of [Example 14-1](simple-dot-notation-access-to-json-data.md) references an index scan with index `po_num_id1`.

**Parent topic:** Indexes for JSON Data

### 28.3 Creating Bitmap Indexes for SQL/JSON Condition JSON_EXISTS

You can create a bitmap index for the value returned by `json_exists`. This is the right kind of index to use for `json_exists`, because there are only two possible return values for a condition (true and false).

This is illustrated by Example 28-1.

Example 28-2 creates a bitmap index for a value returned by `json_value`. This is an appropriate index to use if there are only few possible values for field `CostCenter` in your data.

Example 28-1 Creating a Bitmap Index for JSON_EXISTS

    CREATE BITMAP INDEX has_zipcode_idx
      ON j_purchaseorder (json_exists(po_document,
                                      '$.ShippingInstructions.Address.zipCode'));

Example 28-2 Creating a Bitmap Index for JSON_VALUE

    CREATE BITMAP INDEX cost_ctr_idx
      ON j_purchaseorder (json_value(po_document, '$.CostCenter'));

**Parent topic:** Indexes for JSON Data

### 28.4 Creating JSON_VALUE Function-Based Indexes

You can create a function-based index for SQL/JSON function `json_value`. You can use the standard syntax for this, explicitly specifying function `json_value`, or you can use the simple dot-notation syntax. Indexes created in either of these ways can be used with both dot-notation queries and `json_value` queries.

Example 28-4 creates a function-based index for `json_value` on field `PONumber` of the object that is in column `po_document` of table `j_purchaseorder`. The object is passed as the path-expression context item.

The use of `ERROR ON ERROR` here means that if the data contains a record that has no `PONumber` field, has more than one `PONumber` field, or has a `PONumber` field with a non-number value then index creation fails. And if the index exists then trying to insert such a record fails.

An alternative is to create an index using the simplified syntax described in [Simple Dot-Notation Access to JSON Data](simple-dot-notation-access-to-json-data.md). Example 28-3 illustrates this; it indexes both scalar and non-scalar results, corresponding to what a dot-notation query can return.

The indexes created in both Example 28-4 and Example 28-3 can be picked up for either a query that uses dot-notation syntax or a query that uses `json_value`.

If the index of Example 28-3 is picked up for a `json_value` query then filtering is applied after index pickup, to test for the correct field value. Non-scalar values can be stored in this index, since dot-notation queries can return such values, but a `json_value` query cannot, so such values are filtered out after index pickup.

If you want to allow indexing of data that might be missing the field targeted by a `json_value` expression, then use a `NULL ON EMPTY` clause, together with an `ERROR ON ERROR` clause. Example 28-5 illustrates this.

Oracle recommends that you create a function-based index for `json_value` using one of these forms:

- Dot-notation syntax

  The indexed values correspond to the flexible behavior of dot-notation queries, which return JSON values whenever possible. They can include non-scalar JSON values (JSON objects and arrays). They can match dot-notation queries in addition to `json_value` queries. The index is used to come up with an initial set of matches, which are then filtered according to the specifics of the query. For example, any indexed values that are not JSON scalars are filtered out.

- A `json_value` expression that specifies a `RETURNING` data type, uses `ERROR ON ERROR` (and optionally uses `NULL ON EMPTY`).

  The indexed values are only (non-`null`) scalar values of the specified data type. The index can nevertheless be used in dot-notation queries that lead to such a scalar result.

Indexes created in either of these ways can thus be used with both dot-notation queries and `json_value` queries.

Example 28-3 Creating a Function-Based Index for a JSON Field: Dot Notation

    CREATE UNIQUE INDEX po_num_idx2 ON j_purchaseorder po (po.po_document.PONumber);

Example 28-4 Creating a Function-Based Index for a JSON Field: JSON_VALUE

    CREATE UNIQUE INDEX po_num_idx1
      ON j_purchaseorder (json_value(po_document, '$.PONumber'
                                     RETURNING NUMBER ERROR ON ERROR));

Example 28-5 Specifying NULL ON EMPTY for a JSON_VALUE Function-Based Index

Because of clause `NULL ON EMPTY`, index `po_ref_idx1` can index JSON documents that have no `Reference` field.

    CREATE UNIQUE INDEX po_ref_idx1
      ON j_purchaseorder (json_value(po_document, '$.Reference'
                                     RETURNING VARCHAR2(200) ERROR ON ERROR
                                     NULL ON EMPTY));

**Related Topics**

- [Empty-Field Clause for SQL/JSON Query Functions](clauses-used-in-functions-and-conditions-for-json.md)
- [Using GeoJSON Geographic Data](using-GeoJSON-geographic-data.md)

**Parent topic:** Indexes for JSON Data

### 28.5 Using a JSON_VALUE Function-Based Index with JSON_TABLE Queries

An index created using `json_value` with `ERROR ON ERROR` can be used for a query involving `json_table`, if the `WHERE` clause refers to a column projected by `json_table`, and the effective SQL/JSON path that targets that column matches the indexed path expression.

The index acts as a constraint on the indexed path, to ensure that only one (non-`null`) scalar JSON value is projected for each item in the JSON collection.

The query in Example 28-6 thus makes use of the index created in Example 28-4.

**Note:**

A function-based index created using a `json_value` expression or dot notation can be picked up for a corresponding occurrence in a query `WHERE` clause only if the occurrence is used in a SQL comparison condition, such as `>=`. In particular, it is not picked up for an occurrence used in condition `IS NULL` or `IS NOT NULL`.

See [Oracle Database SQL Language Reference](../sqlrf/Comparison-Conditions.md) for information about SQL comparison conditions.

Example 28-6 Use of a JSON_VALUE Function-Based Index with a JSON_TABLE Query

    SELECT jt.*
      FROM j_purchaseorder po,
           json_table(po.po_document, '$'
             COLUMNS po_number  NUMBER(5) PATH '$.PONumber',
                     reference  VARCHAR2(30 CHAR) PATH '$.Reference',
                     requestor  VARCHAR2(32 CHAR) PATH '$.Requestor',
                     userid     VARCHAR2(10 CHAR) PATH '$.User',
                     costcenter VARCHAR2(16 CHAR) PATH '$.CostCenter') jt
      WHERE po_number = 1600;

**Parent topic:** Indexes for JSON Data

### 28.6 Using a JSON_VALUE Function-Based Index with JSON_EXISTS Queries

An index created using SQL/JSON function `json_value` with `ERROR ON ERROR` can be used for a query involving SQL/JSON condition `json_exists`, provided the query path expression has a filter expression that contains only a path-expression comparison or multiple such comparisons separated by `&&`.

In order for a `json_value` function-based index to be picked up for one of the comparisons of the query, the type of that comparison must be the same as the returning SQL data type for the index. The SQL data types used are those mentioned for item methods `double()`, `number()`, `timestamp()`, `date()`, and `string()` — see [SQL/JSON Path Expression Item Methods](json-path-expressions.md).

For example, if the index returns a number then the comparison type must also be number. If the query filter expression contains more than one comparison that matches a `json_value` index, the optimizer chooses one of the indexes.

The type of a comparison is determined as follows:

1.  If the SQL data types of the two comparison terms (sides of the comparison) are different then the type of the comparison is unknown, and the index is not picked up. Otherwise, the types are the same, and this type is the type of the comparison.

2.  If a comparison term is of SQL data type string (a text literal) then the type of the comparison is the type of the other comparison term.

3.  If a comparison term is a path expression with a function step whose item method imposes a SQL match type then that is also the type of that comparison term. The item methods that impose a SQL match type are `double()`, `number()`, `timestamp()`, `date()`, and `string()`.

4.  If a comparison term is a path expression with no such function step then its type is SQL string (text literal).

Example 28-4 creates a function-based index for `json_value` on field `PONumber`. The index return type is `NUMBER`.

Each of the queries Example 28-7, Example 28-8, and Example 28-9 can make use of this index when evaluating its `json_exists` condition. Each of these queries uses a comparison that involves a simple path expression that is relative to the absolute path expression `$.PONumber`. The relative simple path expression in each case targets the current filter item, `@`, but in the case of Example 28-9 it transforms (casts) the matching data to SQL data type `NUMBER`.

Example 28-7 JSON_EXISTS Query Targeting Field Compared to Literal Number

This query makes use of the index because:

1.  One comparison term is a path expression with no function step, so its type is SQL string (text literal).

2.  Because one comparison term is of type string, the comparison has the type of the other term, which is number (the other term is a numeral).

3.  The type of the (lone) comparison is the same as the type returned by the index: number.

<!-- -->

    SELECT count(*) FROM j_purchaseorder
      WHERE json_exists(po_document, '$.PONumber?(@ > 1500)');

Example 28-8 JSON_EXISTS Query Targeting Field Compared to Variable Value

This query can make use of the index because:

1.  One comparison term is a path expression with no function step, so its type is SQL string (text literal).

2.  Because one comparison term is of type string, the comparison has the type of the other term, which is number (the other term is a variable that is bound to a number).

3.  The type of the (lone) comparison is the same as the type returned by the index: number.

<!-- -->

    SELECT count(*) FROM j_purchaseorder
      WHERE json_exists(po_document, '$.PONumber?(@ > $D)'
                        PASSING 1500 AS "D");

Example 28-9 JSON_EXISTS Query Targeting Field Cast to Number Compared to Variable Value

This query can make use of the index because:

1.  One comparison term is a path expression with a function step whose item method (`number()`) transforms the matching data to a number, so the type of that comparison term is SQL number.

2.  The other comparison term is a numeral, which has SQL type number. The types of the comparison terms match, so the comparison has this same type, number.

3.  The type of the (lone) comparison is the same as the type returned by the index: number.

<!-- -->

    SELECT count(*) FROM j_purchaseorder
      WHERE json_exists(po_document, '$.PONumber?(@.number() > $D)'
                        PASSING 1500 AS "D");

Example 28-10 JSON_EXISTS Query Targeting a Conjunction of Field Comparisons

Just as for Example 28-7, this query can make use of the index on field `PONumber`. If a `json_value` index is also defined for field `Reference` then the optimizer chooses which index to use for this query.

    SELECT count(*) FROM j_purchaseorder
      WHERE json_exists(po_document, '$?(@.PONumber > 1500
                                         && @.Reference == "ABULL-20140421")');

**Related Topics**

- Creating JSON_VALUE Function-Based Indexes
- [SQL/JSON Path Expressions](json-path-expressions.md)

**Parent topic:** Indexes for JSON Data

### 28.7 Data Type Considerations for JSON_VALUE Indexing and Querying

By default, SQL/JSON function `json_value` returns a `VARCHAR2` value. When you create a function-based index using `json_value`, unless you use a `RETURNING` clause to specify a different return data type, the index is not picked up for a query that expects a non-`VARCHAR2` value.

For example, in the query of Example 28-11, `json_value` uses `RETURNING NUMBER`. The index created in Example 28-4 can be picked up for this query, because the indexed `json_value` expression specifies a return type of `NUMBER`.

But the index created in Example 28-3 does not use `RETURNING NUMBER` (the return type is `VARCHAR2(4000)`, by default), so it cannot be picked up for a such a query.

Now consider the queries in Example 28-12 and Example 28-13, which use `json_value` without a `RETURNING` clause, so that the value returned is of type `VARCHAR2`.

In Example 28-12, SQL function `to_number` explicitly converts the `VARCHAR2` value returned by `json_value` to a number. Similarly, in Example 28-13, comparison condition \> (greater-than) implicitly converts the value to a number.

Neither of the indexes of Example 28-4 and Example 28-3 is picked up for either of these queries. The queries might return the right results in each case, because of type-casting, but the indexes cannot be used to evaluate the queries.

Consider also what happens if some of the data cannot be converted to a particular data type. For example, given the queries in Example 28-11, Example 28-12, and Example 28-13, what happens to a `PONumber` value such as `"alpha"`?

For Example 28-12 and Example 28-13, the query stops in error because of the attempt to cast the value to a number. For Example 28-11, however, because the default error handling behavior is `NULL ON ERROR`, the non-number value `"alpha"` is simply filtered out. The value is indexed, but it is ignored for the query.

Similarly, if the query used, say, `DEFAULT '1000' ON ERROR`, that is, if it specified a numeric default value, then no error would be raised for the value `"alpha"`: the default value of `1000` would be used.

Example 28-11 JSON_VALUE Query with Explicit RETURNING NUMBER

    SELECT count(*) FROM j_purchaseorder po
      WHERE json_value(po_document, '$.PONumber' RETURNING NUMBER) > 1500;

Example 28-12 JSON_VALUE Query with Explicit Numerical Conversion

    SELECT count(*) FROM j_purchaseorder po
      WHERE to_number(json_value(po_document, '$.PONumber')) > 1500;

Example 28-13 JSON_VALUE Query with Implicit Numerical Conversion

    SELECT count(*) FROM j_purchaseorder po
      WHERE json_value(po_document, '$.PONumber') > 1500;

**Parent topic:** Indexes for JSON Data

### 28.8 Indexing Multiple JSON Fields Using a Composite B-Tree Index

To index multiple fields of a JSON object, you first create virtual columns for them. Then you create a composite B-tree index on the virtual columns.

Example 28-14 and Example 28-15 illustrate this. Example 28-14 creates virtual columns `userid` and `costcenter` for JSON object fields `User` and `CostCenter`, respectively.

Example 28-15 creates a composite B-tree index on the virtual columns of Example 28-14.

A SQL query that references either the virtual columns or the corresponding JSON data (object fields) picks up the composite index. This is the case for both of the queries in Example 28-16.

These two queries have the same effect, including the same performance. However, the first query form does not target the JSON data itself; it targets the virtual columns that are used to index that data.

The data does not depend logically on any indexes implemented to improve query performance. If you want this independence from implementation to be reflected in your code, then use the second query form. Doing that ensures that the query behaves the same functionally with or without the index — the index serves only to improve performance.

Example 28-14 Creating Virtual Columns For JSON Object Fields

    ALTER TABLE j_purchaseorder ADD (userid VARCHAR2(20)
      GENERATED ALWAYS AS (json_value(po_document, '$.User' RETURNING VARCHAR2(20))));

    ALTER TABLE j_purchaseorder ADD (costcenter VARCHAR2(6)
      GENERATED ALWAYS AS (json_value(po_document, '$.CostCenter'
                           RETURNING VARCHAR2(6))));

Example 28-15 Creating a Composite B-tree Index For JSON Object Fields

    CREATE INDEX user_cost_ctr_idx on j_purchaseorder(userid, costcenter);

Example 28-16 Two Ways to Query JSON Data Indexed With a Composite Index

    SELECT po_document FROM j_purchaseorder WHERE userid      = 'ABULL'
                                              AND costcenter  = 'A50';

    SELECT po_document
      FROM j_purchaseorder WHERE json_value(po_document, '$.User')       = 'ABULL'
                             AND json_value(po_document, '$.CostCenter') = 'A50';

**Parent topic:** Indexes for JSON Data

### 28.9 JSON Search Index: Ad Hoc Queries and Full-Text Search

A JSON search index is a general index. It can improve the performance of both (1) ad hoc structural queries, that is, queries that you might not anticipate or use regularly, and (2) full-text search. It is an Oracle Text index that is designed specifically for use with JSON data.

**Note:**

If you created a JSON search index using Oracle Database 12c Release 1 (12.1.0.2) then Oracle recommends that you drop that index and create a new search index for use with later releases, using `CREATE SEARCH INDEX` as shown here.

**Note:**

You must rebuild any JSON search indexes and Oracle Text indexes created prior to Oracle Database 18c if they index JSON data that contains object fields with names longer than 64 bytes. See [Oracle Database Upgrade Guide](../upgrd/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information.

#### Introduction to JSON Search Indexes

You create a JSON search index using `CREATE SEARCH INDEX` with the keywords `FOR JSON`. Example 28-17 illustrates this.

The column on which you create a JSON search index can be of data type `VARCHAR2`, `CLOB`, or `BLOB`. It must be known to contain only well-formed JSON data, which means that it has an `is json` check constraint. `CREATE SEARCH INDEX` raises an error if the column is not known to contain JSON data.

If the name of your JSON search index is present in the execution plan for your query, then you know that the index was in fact picked up for that query. You will see a line similar to that shown in Example 28-19.

You can specify a `PARAMETERS` clause to override the default settings of certain configurable options. By default (no `PARAMETERS` clause), the index is synchronized on commit and both text and numeric ranges are indexed.

If your queries that make use of a JSON search index involve only full-text search or string-equality search, and never involve string-range search or numeric or temporal search (equality or range), then you can save some index maintenance time and some disk space by specifying `TEXT` for parameter `SEARCH_ON`. The default value of `SEARCH_ON` is `TEXT_VALUE`, which means index numeric ranges as well as text.

Also by default, the search index created records and maintains persistent data-guide information, which requires some maintenance overhead. You can inhibit this support for persistent data-guide information by specifying `DATAGUIDE OFF` in the `PARAMETERS` clause.

A JSON search index is maintained asynchronously. Until it is synchronized, the index is not used for data that has been modified or newly inserted. An index can improve query performance, but the act of synchronizing it with the data affects performance negatively while it occurs. In particular, it can negatively affect DML operations.

There are essentially three ways to synchronize a JSON search index. Each is typically appropriate for a different use case.

- Synchronize on commit.

  This is appropriate when commits are infrequent and it is important that the committed changes be immediately visible to other operations (such as queries). (A stale index can result in uncommitted changes not being visible.) Example 28-17 creates a search index that is synchronized on commit.

- Synchronize periodically at some interval of time.

  For online transaction-processing (OLTP) applications, which require fast and reliable transaction handling with high throughput, and which typically commit each operation, periodic index synchronization is often appropriate. In this case, the synchronization interval is generally greater than the time between commits, and it is not essential that the result of each commit be immediately visible to other operations.Example 28-18 creates a search index that is synchronized each second.

- Synchronize on demand, for example at a time when database load is reduced.

  You generally do this infrequently — the index is synchronized less often than with on-commit or interval synchronizing. This method is typically appropriate when DML performance is particularly important.

If you need to invoke procedures in package `CTX_DDL`, such as `CTX_DDL.sync_index` to manually sync the index, then you need privilege `CTXAPP`.

**Note:**

To alter a JSON search index `j_s_idx`, you use `ALTER INDEX j_s_idx REBUILD ...` (not `ALTER SEARCH INDEX j_s_idx ...`).

Example 28-17 Creating a JSON Search Index That Is Synchronized On Commit

    CREATE SEARCH INDEX po_search_idx ON j_purchaseorder (po_document) FOR JSON;

Example 28-18 Creating a JSON Search Index That Is Synchronized Each Second

    CREATE SEARCH INDEX po_search_1_sec_idx ON j_purchaseorder (po_document)
      FOR JSON
      PARAMETERS('SYNC (EVERY "FREQ=SECONDLY; INTERVAL=1")')

Example 28-19 Execution Plan Indication that a JSON Search Index Is Used

    |* 2|   DOMAIN INDEX     | PO_SEARCH_IDX |     |     |     4 (0)

#### Full-Text Search of JSON Data

You can use SQL/JSON condition `json_textcontains` in a `CASE` expression or the `WHERE` clause of a `SELECT` statement to perform a full-text search of JSON data that is stored in a `VARCHAR2`, `BLOB`, or `CLOB` column.

Oracle Text technology underlies SQL condition `json_textcontains`. This means, for instance, that you can query for text that is near some other text, or query use fuzzy pattern-matching.

To be able to use condition `json_textcontains`, you first must create a JSON search index. If you do not, then an error is raised when `json_textcontains` is used.

Example 28-20 shows a full-text query that finds purchase-order documents that contain the keyword `Magic` in any of the line-item part descriptions.

**Note:**

For powerful full-text search, use Oracle SQL function `json_textcontains`, which requires that you create a JSON search index. As a less-powerful alternative, if you do not create a JSON search index, and you just want simple string pattern-matching in a filter condition, you can use any of the pattern-matching comparisons: `has substring`, `starts with`, `like`, `like_regex`, or `eq_regex`.

Example 28-20 Full-Text Query of JSON Data

    SELECT po_document FROM j_purchaseorder
      WHERE json_textcontains(po_document, '$.LineItems.Part.Description', 'Magic');

#### Ad Hoc Queries of JSON Data

Example 28-21 shows some non full-text queries of JSON data that also make use of the JSON search index created in Example 28-17.

Example 28-21 Some Ad Hoc JSON Queries

This query selects documents that contain a shipping instructions address that includes a country.

    SELECT po_document FROM j_purchaseorder
      WHERE json_exists(po_document, '$.ShippingInstructions.Address.country');

This query selects documents that contain user `AKHOO` where there are more than 8 items ordered. It takes advantage of numeric-range indexing.

    SELECT po_document FROM j_purchaseorder
      WHERE json_exists(po_document, '$?(@.User == "AKHOO"
                                         && @.LineItems.Quantity > 8)');

This query selects documents where the user is `AKHOO`. It uses `json_value` instead of `json_exists` in the `WHERE` clause.

    SELECT po_document FROM j_purchaseorder
      WHERE json_value(po_document, '$.User') = 'ABULL';

**Related Topics**

- Indexes for JSON Data
- [JSON Data Guide](json-dataguide.md)

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/SQL-JSON-Conditions.md) for information about condition `json_textcontains`

- [Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md) for information about the `PARAMETERS` clause for `CREATE SEARCH INDEX`

- [Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md) for information about the `PARAMETERS` clause for `ALTER INDEX` ... `REBUILD`

- [Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md) for information about synchronizing a JSON search index

- [Oracle Text Application Developer's Guide](../ccapp/maintaining-oracle-text-indexes.md) for guidance about optimizing and tuning the performance of a JSON search index

- [Oracle Text Reference](../ccref/special-characters-in-oracle-text-queries.md) for information about the words and characters that are reserved with respect to Oracle Text search, and [Oracle Text Reference](../ccref/special-characters-in-oracle-text-queries.md) for information about how to escape them.

**Parent topic:** Indexes for JSON Data
