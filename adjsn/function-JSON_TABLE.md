SQL/JSON function `json_table` projects specific JSON data to columns of various SQL data types. You use it to map parts of a JSON document into the rows and columns of a new, virtual table, which you can also think of as an inline view.

You can then insert this virtual table into a pre-existing database table, or you can query it using SQL — in a join expression, for example.

A common use of `json_table` is to create a view of JSON data. You can use such a view just as you would use any table or view. This lets applications, tools, and programmers operate on JSON data without consideration of the syntax of JSON or JSON path expressions.

Defining a view over JSON data in effect maps a kind of schema onto that data. This mapping is after the fact: the underlying JSON data can be defined and created without any regard to a schema or any particular pattern of use. Data first, schema later.

Such a schema (mapping) imposes no restriction on the kind of JSON documents that can be stored in the database (other than being well-formed JSON data). The view exposes only data that conforms to the mapping (schema) that defines the view. To change the schema, just redefine the view — no need to reorganize the underlying JSON data.

You use `json_table` in a SQL `FROM` clause. It is a **row source**: it generates a row of virtual-table data for each JSON value selected by a row path expression (row pattern). The columns of each generated row are defined by the column path expressions of the `COLUMNS` clause.

Typically a `json_table` invocation is laterally joined, implicitly, with a source table in the `FROM` list, whose rows each contain a JSON document that is used as input to the function. `json_table` generates zero or more new rows, as determined by evaluating the row path expression against the input document.

The first argument to `json_table` is a SQL expression. It can be a table or view column value, a PL/SQL variable, or a bind variable with proper casting. The result of evaluating the expression is used as the context item for evaluating the row path expression.

The second argument to `json_table` is the SQL/JSON row path expression followed by an optional error clause for handling the row and the (required) `COLUMNS` clause, which defines the columns of the virtual table to be created. There is no `RETURNING` clause.

There are two levels of error handling for `json_table`, corresponding to the two levels of path expressions: row and column. When present, a column error handler overrides row-level error handling. The default error handler for both levels is `NULL ON ERROR`.

As an alternative to passing the context-item argument and the row path expression, you can use simple dot-notation syntax. (You can still use an error clause, and the `COLUMNS` clause is still required.) Dot notation specifies a table or view column together with a simple path to the targeted JSON data. For example, these two queries are equivalent:

    json_table(t.j, '$.ShippingInstructions.Phone[*]' ...)

    json_table(t.j.ShippingInstructions.Phone[*] ...)

And in cases where the row path expression is only `'$'`, which targets the entire document, you can omit the path part. These queries are equivalent:

    json_table(t.j, '$' ...)

    json_table(t.j ...)

Example 20-1 illustrates the difference between using the simple dot notation and using the fuller, more explicit notation.

Example 20-1 Equivalent JSON_TABLE Queries: Simple and Full Syntax

This example uses `json_table` for two equivalent queries. The first query uses the simple, dot-notation syntax for the expressions that target the row and column data. The second uses the full syntax.

Except for column `Special Instructions`, whose SQL identifier is quoted, the SQL column names are, in effect, uppercase. (Identifier `Special Instructions` contains a space character.)

In the first query the column names are written exactly the same as the names of the targeted object fields, including with respect to letter case. Regardless of whether they are quoted, they are interpreted case-sensitively for purposes of establishing the default path (the path used when there is no explicit `PATH` clause).

The second query has:

- Separate arguments of a JSON column-expression and a SQL/JSON row path-expression

- Explicit column data types of `VARCHAR2(4000)`

- Explicit `PATH` clauses with SQL/JSON column path expressions, to target the object fields that are projected

<!-- -->

    SELECT jt.*
      FROM j_purchaseorder po,
           json_table(po.po_document
             COLUMNS ("Special Instructions",
                      NESTED LineItems[*]
                        COLUMNS (ItemNumber NUMBER,
                                 Description PATH Part.Description))) AS "JT";

    SELECT jt.*
      FROM j_purchaseorder po,
           json_table(po.po_document,
             '$'
             COLUMNS (
               "Special Instructions" VARCHAR2(4000) PATH '$."Special Instructions"',
               NESTED PATH '$.LineItems[*]'
                 COLUMNS (
                   ItemNumber  NUMBER        PATH '$.ItemNumber',
                   Description VARCHAR(4000) PATH '$.Part.Description'))) AS "JT";

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_TABLE.md) for information about `json_table`

- SQL NESTED Clause Instead of JSON_TABLE
  In a `SELECT` clause you can often use a `NESTED` clause instead of SQL/JSON function `json_table`. This can mean a simpler query expression. It also has the advantage of including rows with non-`NULL` relational columns when the JSON column is `NULL`.
- COLUMNS Clause of SQL/JSON Function JSON_TABLE
  The mandatory `COLUMNS` clause for SQL/JSON function `json_table` defines the columns of the virtual table that the function creates.
- JSON_TABLE Generalizes SQL/JSON Query Functions and Conditions
  SQL/JSON function `json_table` generalizes SQL/JSON condition `json_exists` and SQL/JSON functions `json_value` and `json_query`. Everything that you can do using these functions you can do using `json_table`. For the jobs they accomplish, the syntax of these functions is simpler to use than is the syntax of `json_table`.
- Using JSON_TABLE with JSON Arrays
  A JSON value can be an array or can include one or more arrays, nested to any number of levels inside other JSON arrays or objects. You can use a `json_table` `NESTED` path clause to project specific elements of an array.
- Creating a View Over JSON Data Using JSON_TABLE
  To improve query performance you can create a view over JSON data that you project to columns using SQL/JSON function `json_table`. To further improve query performance you can create a materialized view and place the JSON data in memory.

**Related Topics**

- [Error Clause for SQL Query Functions and Conditions](clauses-used-in-functions-and-conditions-for-json.md)
- [SQL/JSON Function JSON_QUERY](function-JSON_QUERY.md)

**Parent topic:** [Query JSON Data](query-json-data.md)

### 20.1 SQL NESTED Clause Instead of JSON_TABLE

In a `SELECT` clause you can often use a `NESTED` clause instead of SQL/JSON function `json_table`. This can mean a simpler query expression. It also has the advantage of including rows with non-`NULL` relational columns when the JSON column is `NULL`.

The `NESTED` clause is a shortcut for using `json_table` with an ANSI left outer join. That is, these two queries are equivalent:

    SELECT ...
      FROM mytable NESTED jcol COLUMNS (...);

    SELECT ...
      FROM mytable t1 LEFT OUTER JOIN
           json_table(t1.jcol COLUMNS (...)
           ON 1=1;

Using a left outer join with `json_table`, or using the `NESTED` clause, allows the selection result to include rows with relational columns where there is no corresponding JSON-column data, that is, where the JSON column is `NULL`. The only semantic difference between the two is that if you use a `NESTED` clause then the JSON column itself is not included in the result.

The `NESTED` clause provides the same `COLUMNS` clause as `json_table`, including the possibility of nested columns. Advantages of using `NESTED` are that you need not provide an `is json` check constraint (needed for `json_table` with the simple dot notation) or a table alias, and you need not specify `LEFT OUTER JOIN`. The `NESTED` clause syntax is simpler, it allows all of the flexibility of the `COLUMNS` clause, and it performs an implicit left outer join.

Example 20-2 Equivalent: SQL NESTED and JSON_TABLE with LEFT OUTER JOIN

These two queries are equivalent. One uses SQL/JSON function `json_table` with an explicit `LEFT OUTER JOIN`. The other uses a SQL `NESTED` clause.

    SELECT id, requestor, type, "number"
      FROM j_purchaseorder LEFT OUTER JOIN
           json_table(po_document
             COLUMNS (Requestor,
                      NESTED ShippingInstructions.Phone[*]
                        COLUMNS (type, "number")))
           ON 1=1);

    SELECT id, requestor, type, "number"
      FROM j_purchaseorder NESTED
           po_document
             COLUMNS (Requestor,
                      NESTED ShippingInstructions.Phone[*]
                        COLUMNS (type, "number");

The output is the same in both cases:

    7C3A54B183056369E0536DE05A0A15E4 Alexis Bull Office 909-555-7307
    7C3A54B183056369E0536DE05A0A15E4 Alexis Bull Mobile 415-555-1234
    7C3A54B183066369E0536DE05A0A15E4 Sarah Bell

If table `j_purchaseorder` had a row with non-`NULL` values for columns `id` and `requestor`, but a `NULL` value for column `po_document` then that row would appear in both cases. But it would not appear in the `json_table` case if `LEFT OUTER JOIN` were absent.

**Parent topic:** SQL/JSON Function JSON_TABLE

### 20.2 COLUMNS Clause of SQL/JSON Function JSON_TABLE

The mandatory `COLUMNS` clause for SQL/JSON function `json_table` defines the columns of the virtual table that the function creates.

It consists of the keyword `COLUMNS` followed by the following entries, enclosed in parentheses. Other than the optional `FOR ORDINALITY` entry, each entry in the `COLUMNS` clause is either a regular column specification or a nested columns specification.

- At most one entry in the `COLUMNS` clause can be a column name followed by the keywords `FOR ORDINALITY`, which specifies a column of generated row numbers (SQL data type `NUMBER`). These numbers start with one. For example:

      COLUMNS (linenum FOR ORDINALITY, ProductID)

- A **regular column** specification consists of a column name followed by an optional scalar data type for the column, which can be SQL data type `VARCHAR2`, `NUMBER`, `DATE`, `TIMESTAMP`, `TIMESTAMP WITH TIME ZONE`, or `SDO_GEOMETRY` (the same as for the `RETURNING` clause of `json_value`), followed by an optional value clause and an optional `PATH` clause. The default data type is `VARCHAR2(4000)`.

  Data type `SDO_GEOMETRY` is used for Oracle Spatial and Graph data. In particular, this means that you can use `json_table` with GeoJSON data, which is a format for encoding geographic data in JSON.

  Oracle extends the SQL/JSON standard in the case when the returning data type for a column is `VARCHAR2(``N``)`, by allowing optional keyword `TRUNCATE` immediately after the data type. When `TRUNCATE` is present and the value to return is wider than `N`, the value is truncated — only the first `N` characters are returned. If `TRUNCATE` is absent then this case is treated as an error, handled as usual by an error clause or the default error-handling behavior.

- A **nested columns** specification consists of the keyword `NESTED` followed by an optional `PATH` keyword, a SQL/JSON row path expression, and then a `COLUMNS` clause. This `COLUMNS` clause specifies columns that represent nested data. The row path expression used here provides a refined context for the specified nested columns: each nested column path expression is relative to the row path expression. You can nest columns clauses to project values that are present in arrays at different levels to columns of the same row.

  A `COLUMNS` clause at any level (nested or not) has the same characteristics. In other words, the `COLUMNS` clause is defined recursively. For each level of nesting (that is, for each use of keyword `NESTED`), the nested `COLUMNS` clause is said to be the **child** of the `COLUMNS` clause within which it is nested, which is its **parent**. Two or more `COLUMNS` clauses that have the same parent clause are **siblings**.

  The virtual tables defined by parent and child `COLUMNS` clauses are joined using an outer join, with the parent being the outer table. The virtual columns defined by sibling `COLUMNS` clauses are joined using a `union` join.

  Example 20-1 and Example 20-8 illustrate the use of a nested columns clause.

The only thing required in a regular column specification is the column name. Defining the column projection in more detail, by specifying a scalar data type, value handling, or a target path, is optional.

- The optional **value** clause specifies how to handle the data projected to the column: whether to handle it as would `json_value`, `json_exists`, or `json_query`. This value handling includes the return data type, return format (pretty or ASCII), wrapper, and error treatment.

  By default, the projected data is handled as if by `json_value`. If you use keyword `EXISTS` then it is handled as if by `json_exists`. If you use keywords `FORMAT JSON` then it is handled as if by `json_query`.

  For `FORMAT JSON` you can override the default wrapping behavior by adding an explicit wrapper clause.

  You can override the default error handling for the given handler (`json_value`, `json_exists`, or `json_query`) by adding an explicit error clause appropriate for it.

- The optional `PATH` clause specifies the portion of the row that is to be used as the column content. The column path expression following keyword `PATH` is matched against the context item provided by the virtual row. The column path expression must represent a relative path; it is relative to the path specified by the row path expression.

  If the `PATH` clause is not present then the behavior is the same as if it were present with a path of `'$.``<column-name>``'`, where `<column-name>` is the column name. That is, the name of the object field that is targeted is taken implicitly as the column name. For purposes of specifying the targeted field only, the SQL identifier used for `<column-name>` is interpreted case-sensitively, even if it is not quoted. The SQL name of the column follows the usual rule: if it is enclosed in double quotation marks (`"`) then the letter case used is significant; otherwise, it is not (it is treated as if uppercase).

  For example, these two `COLUMNS` clauses are equivalent. For SQL, case is significant only for column `Comments`.

      COLUMNS(ProductId, quantity NUMBER, "Comments")

      COLUMNS(ProductId   VARCHAR2(4000) PATH '$.ProductId',
              quantity    NUMBER         PATH '$.quantity',
              "Comments"  VARCHAR2(4000) PATH '$.Comments')

  Example 20-1 presents equivalent queries that illustrate this.

If you use `FORMAT JSON` in a given `json_table` column specification then `json_query` semantics are used when projecting the JSON data to the column. The data type specified for the column can be any of the SQL data types that `json_query` can return: `VARCHAR2`, `CLOB`, or `BLOB`.

`json_query` semantics imply the following:

- The projected JSON data is always well-formed. This includes ensuring that non-ASCII characters in string values are escaped as needed. For example, a TAB character (CHARACTER TABULATION, U+0009) is escaped as `\t`.

- `json_query` error handling applies.

- You can use a wrapper clause, to project multiple JSON values as elements in an array.

If you do not use `FORMAT JSON` in a given `json_table` column specification then `json_value` semantics are used when projecting the JSON data. The data type specified for the column can be any of the SQL data types that `json_value` can return: `VARCHAR2`, `NUMBER`, `DATE`, `TIMESTAMP`, `TIMESTAMP WITH TIME ZONE`, `SDO_GEOMETRY`, or `CLOB`. `json_value` error handling applies (and you cannot use a wrapper clause).

For example, here the value of column `FirstName` is projected directly using `json_value` semantics, and the value of column `Address` is projected as a JSON string using `json_query` semantics:

    COLUMNS (FirstName, Address FORMAT JSON)

You typically use `FORMAT JSON` when the projected data is a JSON object or array. You typically do not use `FORMAT JSON` when the projected data is a JSON scalar.

**Related Topics**

- [RETURNING Clause for SQL Query Functions](clauses-used-in-functions-and-conditions-for-json.md)
- [Wrapper Clause for SQL/JSON Query Functions JSON_QUERY and JSON_TABLE](clauses-used-in-functions-and-conditions-for-json.md)
- [Error Clause for SQL Query Functions and Conditions](clauses-used-in-functions-and-conditions-for-json.md)
- [Empty-Field Clause for SQL/JSON Query Functions](clauses-used-in-functions-and-conditions-for-json.md)
- [SQL/JSON Function JSON_QUERY](function-JSON_QUERY.md)

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/JSON_TABLE.md)

- [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-concepts.md) for information about using Oracle Spatial and Graph data

- [GeoJSON.org](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=geojson_org)

**Parent topic:** SQL/JSON Function JSON_TABLE

### 20.3 JSON_TABLE Generalizes SQL/JSON Query Functions and Conditions

SQL/JSON function `json_table` generalizes SQL/JSON condition `json_exists` and SQL/JSON functions `json_value` and `json_query`. Everything that you can do using these functions you can do using `json_table`. For the jobs they accomplish, the syntax of these functions is simpler to use than is the syntax of `json_table`.

If you use any of `json_exists`, `json_value`, or `json_query` more than once, or in combination, to access the same data then a single invocation of `json_table` presents the advantage that the data is parsed only once.

Because of this, the optimizer often automatically rewrites multiple invocations of `json_exists`, `json_value` and `json_query` (any combination) to fewer invocations of `json_table` instead, so the data is parsed only once.

Example 20-3 and Example 20-4 illustrate this. They each select the requestor and the set of phones used by each object in column `j_purchaseorder.po_document`. But Example 20-4 parses that column only once, not four times.

Note the following in connection with Example 20-4:

- A JSON value of `null` is a value as far as SQL is concerned; it is not `NULL`, which in SQL represents the absence of a value (missing, unknown, or inapplicable data). In Example 20-4, if the JSON value of object attribute `zipCode` is `null` then the SQL string `'true'` is returned.

- `json_exists` is a SQL condition; you can use it in a SQL `WHERE` clause, a `CASE` statement, or a check constraint. In Example 20-3 it is used in a `WHERE` clause. Function `json_table` employs the semantics of `json_exists` implicitly when you specify keyword `EXISTS`. It must return a SQL value in the virtual column. Since Oracle SQL has no Boolean data type, a SQL string `'true'` or `'false'` is used to represent the Boolean value. This is the case in Example 20-4: the `VARCHAR2` value is stored in column `jt.has_zip`, and it is then tested explicitly for equality against the literal SQL string `'true'`.

- JSON field `AllowPartialShipment` has a JSON Boolean value. When `json_value` is applied to that value it is returned as a string. In Example 20-4, data type `VARCHAR2` is used as the column data type. Function `json_table` implicitly uses `json_value` for this column, returning the value as a `VARCHAR2` value, which is then tested for equality against the literal SQL string `'true'`.

Example 20-3 Accessing JSON Data Multiple Times to Extract Data

    SELECT json_value(po_document, '$.Requestor' RETURNING VARCHAR2(32)),
           json_query(po_document, '$.ShippingInstructions.Phone'
                                   RETURNING VARCHAR2(100))
      FROM j_purchaseorder
      WHERE json_exists(po_document, '$.ShippingInstructions.Address.zipCode')
        AND json_value(po_document,  '$.AllowPartialShipment' RETURNING VARCHAR2(5 CHAR))
            = 'true';

Example 20-4 Using JSON_TABLE to Extract Data Without Multiple Parses

    SELECT jt.requestor, jt.phones
      FROM j_purchaseorder,
           json_table(po_document, '$'
             COLUMNS (requestor VARCHAR2(32 CHAR) PATH '$.Requestor',
                      phones    VARCHAR2(100 CHAR) FORMAT JSON
                                PATH '$.ShippingInstructions.Phone',
                      partial   VARCHAR2(5 CHAR) PATH '$.AllowPartialShipment',
                      has_zip   VARCHAR2(5 CHAR) EXISTS
                                PATH '$.ShippingInstructions.Address.zipCode')) jt
      WHERE jt.partial = 'true' AND jt.has_zip = 'true';

**Related Topics**

- [Using SQL/JSON Function JSON_VALUE With a Boolean JSON Value](function-JSON_VALUE.md)

**Parent topic:** SQL/JSON Function JSON_TABLE

### 20.4 Using JSON_TABLE with JSON Arrays

A JSON value can be an array or can include one or more arrays, nested to any number of levels inside other JSON arrays or objects. You can use a `json_table` `NESTED` path clause to project specific elements of an array.

Example 20-5 projects the requestor and associated phone numbers from the JSON data in column `po_document`. The entire JSON array `Phone` is projected as a column of JSON data, `ph_arr`. To format this JSON data as a `VARCHAR2` column, the keywords `FORMAT JSON` are needed.

What if you wanted to project the individual elements of JSON array `Phone` and not the array as a whole? Example 20-6 shows one way to do this, which you can use if the array elements are the only data you need to project.

If you want to project both the requestor and the corresponding phone data then the row path expression of Example 20-6 (`$.Phone[*]`) is not appropriate: it targets only the (phone object) elements of array `Phone`.

Example 20-7 shows one way to target both: use a row path expression that targets both the name and the entire phones array, and use column path expressions that target fields `type` and `number` of individual phone objects.

In Example 20-7 as in Example 20-5, keywords `FORMAT JSON` are needed because the resulting `VARCHAR2` columns contain JSON data, namely arrays of phone types or phone numbers, with one array element for each phone. In addition, unlike the case for Example 20-5, a wrapper clause is needed for column `phone_type` and column `phone_num`, because array `Phone` contains multiple objects with fields `type` and `number`.

Sometimes you might not want the effect of Example 20-7. For example, you might want a column that contains a single phone number (one row per number), rather than one that contains a JSON array of phone numbers (one row for all numbers for a given purchase order).

To obtain that result, you need to tell `json_table` to project the array elements, by using a `json_table` `NESTED` path clause for the array. A `NESTED` path clause acts, in effect, as an additional row source (row pattern). Example 20-8 illustrates this.

You can use any number of `NESTED` keywords in a given `json_table` invocation.

In Example 20-8 the outer `COLUMNS` clause is the parent of the nested (inner) `COLUMNS` clause. The virtual tables defined are joined using an outer join, with the table defined by the parent clause being the outer table in the join.

(If there were a second columns clause nested directly under the same parent, the two nested clauses would be sibling `COLUMNS` clauses.)

Example 20-5 Projecting an Entire JSON Array as JSON Data

    SELECT jt.*
      FROM j_purchaseorder,
           json_table(po_document, '$'
             COLUMNS (requestor VARCHAR2(32 CHAR) PATH '$.Requestor',
                      ph_arr    VARCHAR2(100 CHAR) FORMAT JSON
                                PATH '$.ShippingInstructions.Phone')) AS "JT";

Example 20-6 Projecting Elements of a JSON Array

    SELECT jt.*
      FROM j_purchaseorder,
           json_table(po_document, '$.ShippingInstructions.Phone[*]'
             COLUMNS (phone_type VARCHAR2(10) PATH '$.type',
                      phone_num  VARCHAR2(20) PATH '$.number')) AS "JT";

    PHONE_TYPE     PHONE_NUM
    ----------     ---------
    Office         909-555-7307
    Mobile         415-555-1234

Example 20-7 Projecting Elements of a JSON Array Plus Other Data

    SELECT jt.*
      FROM j_purchaseorder,
           json_table(po_document, '$'
             COLUMNS (
               requestor  VARCHAR2(32 CHAR) PATH '$.Requestor',
               phone_type VARCHAR2(50 CHAR) FORMAT JSON WITH WRAPPER
                          PATH '$.ShippingInstructions.Phone[*].type',
               phone_num  VARCHAR2(50 CHAR) FORMAT JSON WITH WRAPPER
                          PATH '$.ShippingInstructions.Phone[*].number')) AS "JT";

    REQUESTOR    PHONE_TYPE            PHONE_NUM
    ---------    ----------            ---------
    Alexis Bull  ["Office", "Mobile"]  ["909-555-7307", "415-555-1234"]

Example 20-8 JSON_TABLE: Projecting Array Elements Using NESTED

This example shows two equivalent queries that project array elements. The first query uses the simple, dot-notation syntax for the expressions that target the row and column data. The second uses the full syntax.

Except for column `number`, whose SQL identifier is quoted (`"number"`), the SQL column names are, in effect, uppercase. (Column `number` is lowercase.)

In the first query the column names are written exactly the same as the field names that are targeted, including with respect to letter case. Regardless of whether they are quoted, they are interpreted case-sensitively for purposes of establishing the proper path.

The second query has:

- Separate arguments of a JSON column-expression and a SQL/JSON row path-expression

- Explicit column data types of `VARCHAR2(4000)`

- Explicit `PATH` clauses with SQL/JSON column path expressions, to target the object fields that are projected

<!-- -->

    SELECT jt.*
      FROM j_purchaseorder po,
           json_table(po.po_document
             COLUMNS (Requestor,
                      NESTED ShippingInstructions.Phone[*]
                        COLUMNS (type, "number"))) AS "JT";

    SELECT jt.*
      FROM j_purchaseorder po,
           json_table(po.po_document, '$'
             COLUMNS (Requestor VARCHAR2(4000) PATH '$.Requestor',
                      NESTED                   PATH '$.ShippingInstructions.Phone[*]'
                        COLUMNS (type     VARCHAR2(4000) PATH '$.type',
                                 "number" VARCHAR2(4000) PATH '$.number'))) AS "JT";

**Related Topics**

- Creating a View Over JSON Data Using JSON_TABLE
- SQL/JSON Function JSON_TABLE

**Parent topic:** SQL/JSON Function JSON_TABLE

### 20.5 Creating a View Over JSON Data Using JSON_TABLE

To improve query performance you can create a view over JSON data that you project to columns using SQL/JSON function `json_table`. To further improve query performance you can create a materialized view and place the JSON data in memory.

Example 20-9 defines a view over JSON data. It uses a `NESTED` path clause to project the elements of array `LineItems`.

Example 20-10 defines a materialized view that has the same data and structure as Example 20-9.

In general, you cannot update a view directly (whether materialized or not). But if a materialized view is created using keywords `REFRESH` and `ON STATEMENT`, as in Example 20-10, then the view is updated automatically whenever you update the base table.

You can use `json_table` to project any fields as view columns, and the view creation (materialized or not) can involve joining any tables and any number of invocations of` json_table`.

The only differences between Example 20-9 and Example 20-10 are these:

- The use of keyword `MATERIALIZED`.

- The use of `BUILD IMMEDIATE`.

- The use of `REFRESH FAST ON STATEMENT WITH PRIMARY KEY`.

The use of `REFRESH FAST` means that the materialized view will be refreshed incrementally. For this to occur, you must use either `WITH PRIMARY KEY` or `WITH ROWID` (if there is no primary key). Oracle recommends that you specify a primary key for a table that has a JSON column and that you use `WITH PRIMARY KEY` when creating a materialized view based on it.

You could use `ON COMMIT` in place of `ON STATEMENT` for the view creation. The former synchronizes the view with the base table only when your table-updating transaction is committed. Until then the table changes are not reflected in the view. If you use `ON STATEMENT` then the view is immediately synchronized after each DML statement. This also means that a view created using `ON STATEMENT` reflects any rollbacks that you might perform. (A subsequent `COMMIT` statement ends the transaction, preventing a rollback.)

**See Also:**

[Refreshing Materialized Views](../dwhsg/refreshing-materialized-views.md) in Oracle Database Data Warehousing Guide

Example 20-9 Creating a View Over JSON Data

    CREATE VIEW j_purchaseorder_detail_view
      AS SELECT jt.*
           FROM j_purchaseorder po,
                json_table(po.po_document, '$'
                  COLUMNS (
                    po_number        NUMBER(10)         PATH '$.PONumber',
                    reference        VARCHAR2(30 CHAR)  PATH '$.Reference',
                    requestor        VARCHAR2(128 CHAR) PATH '$.Requestor',
                    userid           VARCHAR2(10 CHAR)  PATH '$.User',
                    costcenter       VARCHAR2(16)       PATH '$.CostCenter',
                    ship_to_name     VARCHAR2(20 CHAR)
                                     PATH '$.ShippingInstructions.name',
                    ship_to_street   VARCHAR2(32 CHAR)
                                     PATH '$.ShippingInstructions.Address.street',
                    ship_to_city     VARCHAR2(32 CHAR)
                                     PATH '$.ShippingInstructions.Address.city',
                    ship_to_county   VARCHAR2(32 CHAR)
                                     PATH '$.ShippingInstructions.Address.county',
                    ship_to_postcode VARCHAR2(10 CHAR)
                                     PATH '$.ShippingInstructions.Address.postcode',
                    ship_to_state    VARCHAR2(2 CHAR)
                                     PATH '$.ShippingInstructions.Address.state',
                    ship_to_zip      VARCHAR2(8 CHAR)
                                     PATH '$.ShippingInstructions.Address.zipCode',
                    ship_to_country  VARCHAR2(32 CHAR)
                                     PATH '$.ShippingInstructions.Address.country',
                    ship_to_phone    VARCHAR2(24 CHAR)
                                     PATH '$.ShippingInstructions.Phone[0].number',
                    NESTED PATH '$.LineItems[*]'
                      COLUMNS (
                        itemno      NUMBER(38)         PATH '$.ItemNumber',
                        description VARCHAR2(256 CHAR) PATH '$.Part.Description',
                        upc_code    NUMBER             PATH '$.Part.UPCCode',
                        quantity    NUMBER(12,4)       PATH '$.Quantity',
                        unitprice   NUMBER(14,2)       PATH '$.Part.UnitPrice'))) jt;

Example 20-10 Creating a Materialized View Over JSON Data

    CREATE MATERIALIZED VIEW j_purchaseorder_materialized_view
      BUILD IMMEDIATE
      REFRESH FAST ON STATEMENT WITH PRIMARY KEY
      AS SELECT jt.*
           FROM j_purchaseorder po,
                json_table(po.po_document, '$'
                  COLUMNS (
                    po_number        NUMBER(10)         PATH '$.PONumber',
                    reference        VARCHAR2(30 CHAR)  PATH '$.Reference',
                    requestor        VARCHAR2(128 CHAR) PATH '$.Requestor',
                    userid           VARCHAR2(10 CHAR)  PATH '$.User',
                    costcenter       VARCHAR2(16)       PATH '$.CostCenter',
                    ship_to_name     VARCHAR2(20 CHAR)
                                     PATH '$.ShippingInstructions.name',
                    ship_to_street   VARCHAR2(32 CHAR)
                                     PATH '$.ShippingInstructions.Address.street',
                    ship_to_city     VARCHAR2(32 CHAR)
                                     PATH '$.ShippingInstructions.Address.city',
                    ship_to_county   VARCHAR2(32 CHAR)
                                     PATH '$.ShippingInstructions.Address.county',
                    ship_to_postcode VARCHAR2(10 CHAR)
                                     PATH '$.ShippingInstructions.Address.postcode',
                    ship_to_state    VARCHAR2(2 CHAR)
                                     PATH '$.ShippingInstructions.Address.state',
                    ship_to_zip      VARCHAR2(8 CHAR)
                                     PATH '$.ShippingInstructions.Address.zipCode',
                    ship_to_country  VARCHAR2(32 CHAR)
                                     PATH '$.ShippingInstructions.Address.country',
                    ship_to_phone    VARCHAR2(24 CHAR)
                                     PATH '$.ShippingInstructions.Phone[0].number',
                    NESTED PATH '$.LineItems[*]'
                      COLUMNS (
                        itemno      NUMBER(38)         PATH '$.ItemNumber',
                        description VARCHAR2(256 CHAR) PATH '$.Part.Description',
                        upc_code    NUMBER             PATH '$.Part.UPCCode',
                        quantity    NUMBER(12,4)       PATH '$.Quantity',
                        unitprice   NUMBER(14,2)       PATH '$.Part.UnitPrice'))) jt;

**Related Topics**

- Using JSON_TABLE with JSON Arrays
- [Using GeoJSON Geographic Data](using-GeoJSON-geographic-data.md)

**Parent topic:** SQL/JSON Function JSON_TABLE
