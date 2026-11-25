You can enhance the performance of queries that access particular JSON fields by creating, and indexing, a materialized view over such data that's defined using SQL/JSON function `json_table`.

[Example 20-10](function-JSON_TABLE.md) shows how to create a materialized view over JSON data using function `json_table`. That example creates a virtual column for each JSON field expected in the data.

You can instead create a materialized view that projects only certain fields that you query often. If you do that, and if the following conditions are all satisfied, then queries that match the column data types of any of the projected fields can be rewritten automatically to go against the materialized view.

- The materialized view is created with `REFRESH FAST ON STATEMENT`.

- The materialized view definition includes either `WITH PRIMARY KEY` or `WITH ROWID` (if there is no primary key).

- The materialized view joins the master table and only one virtual table defined by `json_table`.

- The columns projected by `json_table` use `ERROR ON ERROR`.

Automatic query rewrite is supported if those conditions are satisfied. You do not need to specify `ENABLE QUERY REWRITE` in the view definition. Rewriting applies to queries that use any of the following in a `WHERE` clause: simple dot notation, condition `json_exists`, or function `json_value`.

Columns that do not specify `ERROR ON ERROR` are also allowed, but queries are not rewritten to use those columns. If you use `ERROR ON ERROR` for the `json_table` row pattern, the effect is the same as if you specify `ERROR ON ERROR` for each column.

If some of your JSON data lacks a given projected field, using `NULL ON EMPTY` allows that field to nevertheless be picked up when it is present — no error is raised when it is missing.

Automatic query rewrite to use a materialized view can enhance performance. Performance can be further enhanced if you also create an index on the materialized view.

Example 30-1 creates such a materialized view. Example 30-2 creates an index for it.

Example 30-1 Creating a Materialized View of JSON Data To Support Query Rewrite

This example creates materialized view `mv_for_query_rewrite`, which projects several JSON fields to relational columns. Queries that access those fields in a `WHERE` clause using simple dot notation, condition `json_exists`, or function `json_value` can be automatically rewritten to instead go against the corresponding view columns.

An example of such a query is that of [Example 17-5](condition-JSON_EXISTS.md), which has comparisons for fields `User`, `UPCCode`, and `Quantity`. All of these comparisons are rewritten to use the materialized view.

In order for the materialized view to be used for a given comparison of a query, the type of that comparison must be the same as the SQL data type for the corresponding view column. See [Using a JSON_VALUE Function-Based Index with JSON_EXISTS Queries](indexes-for-json-data.md) for information about the type of a comparison.

For example, view `mv_for_query_rewrite` can be used for a query that checks whether field `UPCCode` has numeric value `85391628927`, because the view column projected from that field has SQL type `NUMBER`. But the view cannot be used for a query that checks whether that field has string value `"85391628927"`.

    CREATE MATERIALIZED VIEW mv_for_query_rewrite
      BUILD IMMEDIATE
      REFRESH FAST ON STATEMENT WITH PRIMARY KEY
      AS SELECT po.id, jt.*
           FROM j_purchaseorder po,
                json_table(po.po_document, '$' ERROR ON ERROR NULL ON EMPTY
                  COLUMNS (
                    po_number       NUMBER         PATH '$.PONumber',
                    userid          VARCHAR2(10)   PATH '$.User',
                    NESTED PATH '$.LineItems[*]'
                      COLUMNS (
                        itemno      NUMBER         PATH '$.ItemNumber',
                        description VARCHAR2(256)  PATH '$.Part.Description',
                        upc_code    NUMBER         PATH '$.Part.UPCCode',
                        quantity    NUMBER         PATH '$.Quantity',
                        unitprice   NUMBER         PATH '$.Part.UnitPrice'))) jt;

You can tell whether the materialized view is used for a particular query by examining the execution plan. If it is, then the plan refers to `mv_for_query_rewrite`. For example:

    |* 4| MAT_VIEW ACCESS FULL | MV_FOR_QUERY_REWRITE |1|51|3(0)|00:00:01|

Example 30-2 Creating an Index Over a Materialized View of JSON Data

This example creates composite relational index `mv_idx` on columns `userid`, `upc_code`, and `quantity` of the materialized view `mv_for_query_rewrite` created in Example 30-1.

    CREATE INDEX mv_idx ON mv_for_query_rewrite(userid, upc_code, quantity);

The execution plan snippet in Example 30-1 shows a full table scan (`MAT_VIEW ACCESS FULL`) of the materialized view. Defining index `mv_idx` can result in a better plan for the query. This is indicated by the presence of `INDEX RANGE SCAN` (as well as the name of the index, `MV_IDX`, and the material view, `MV_FOR_QUERY_REWRITE`).

    |  4| MAT_VIEW ACCESS BY INDEX ROWID BATCHED | MV_FOR_QUERY_REWRITE |1|51|2(0)|00:00:01|

    |* 5|                       INDEX RANGE SCAN | MV_IDX               |1|  |1(0)|00:00:01|

**Parent topic:** [Performance Tuning for JSON](performance-tuning-for-json-data.md)
