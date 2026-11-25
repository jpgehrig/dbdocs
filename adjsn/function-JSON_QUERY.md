SQL/JSON function `json_query` selects one or more values from JSON data and returns a string (`VARCHAR2`, `CLOB`, or `BLOB` instance) that represents the JSON values. You can thus use `json_query` to retrieve fragments of a JSON document.

The first argument to `json_query` is a SQL expression that returns an instance of a scalar SQL data type (that is, not an object or collection data type). It can be of data type `VARCHAR2`, `CLOB`, or `BLOB`. It can be a table or view column value, a PL/SQL variable, or a bind variable with proper casting. The result of evaluating the SQL expression is used as the context item for evaluating the path expression.

The second argument to `json_query` is a SQL/JSON path expression followed by optional clauses `RETURNING`, `WRAPPER`, `ON ERROR`, and `ON EMPTY`. The path expression can target any number of JSON values.

In the `RETURNING` clause you can specify data type `VARCHAR2`, `CLOB`, or `BLOB`. A `BLOB` result is in the AL32UTF8 character set. (`VARCHAR2` is the default.) The value returned always contains well-formed JSON data. This includes ensuring that non-ASCII characters in string values are escaped as needed. For example, an ASCII TAB character (Unicode character CHARACTER TABULATION, U+0009) is escaped as `\t`. Keywords `FORMAT JSON` are not needed (or available) for `json_query` — JSON formatting is implicit for the return value.

The wrapper clause determines the form of the returned string value.

The error clause for `json_query` can specify `EMPTY ON ERROR`, which means that an empty array (`[]`) is returned in case of error (no error is raised).

Example 19-1 shows an example of the use of SQL/JSON function `json_query` with an array wrapper. For each document it returns a `VARCHAR2` value whose contents represent a JSON array with elements the phone types, in an unspecified order. For the document in [Example 4-2](creating-a-table-with-a-json-column.md) the phone types are `"Office"` and `"Mobile"`, and the array returned is either `["Mobile", "Office"]` or `["Office", "Mobile"]`.

Note that if path expression `$.ShippingInstructions.Phone.type` were used in Example 19-1 it would give the same result. Because of SQL/JSON path-expression syntax relaxation, `[*].type` is equivalent to `.type`.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_QUERY.md) for information about `json_query`

Example 19-1 Selecting JSON Values Using JSON_QUERY

    SELECT json_query(po_document, '$.ShippingInstructions.Phone[*].type'
                                   WITH WRAPPER)
      FROM j_purchaseorder;

- JSON_QUERY as JSON_TABLE
  SQL/JSON function `json_query` can be viewed as a special case of function `json_table`.

**Related Topics**

- [SQL/JSON Path Expression Syntax Relaxation](json-path-expressions.md)
- [RETURNING Clause for SQL Query Functions](clauses-used-in-functions-and-conditions-for-json.md)
- [Wrapper Clause for SQL/JSON Query Functions JSON_QUERY and JSON_TABLE](clauses-used-in-functions-and-conditions-for-json.md)
- [Error Clause for SQL Query Functions and Conditions](clauses-used-in-functions-and-conditions-for-json.md)
- [Empty-Field Clause for SQL/JSON Query Functions](clauses-used-in-functions-and-conditions-for-json.md)

**Parent topic:** [Query JSON Data](query-json-data.md)

### 19.1 JSON_QUERY as JSON_TABLE

SQL/JSON function `json_query` can be viewed as a special case of function `json_table`.

Example 19-2 illustrates the equivalence: the two `SELECT` statements have the same effect.

In addition to perhaps helping you understand `json_query` better, this equivalence is important practically, because it means that you can use either function to get the same effect.

In particular, if you use `json_query` more than once, or you use it in combination with `json_exists` or `json_value` (which can also be expressed using `json_table`), to access the same data, then a single invocation of `json_table` presents the advantage that the data is parsed only once.

Because of this, the optimizer often automatically rewrites multiple invocations of `json_exists`, `json_value` and `json_query` (any combination) to fewer invocations of `json_table`.

Example 19-2 JSON_QUERY Expressed Using JSON_TABLE

    SELECT json_query(column, json_path
                      RETURNING data_type array_wrapper error_hander ON ERROR)
      FROM table;

    SELECT jt.column_alias
      FROM table,
           json_table(column, '$' error_handler ON ERROR
             COLUMNS ("COLUMN_ALIAS" data_type FORMAT JSON array_wrapper
                      PATH json_path)) AS "JT";

**Related Topics**

- [JSON_TABLE Generalizes SQL/JSON Query Functions and Conditions](function-JSON_TABLE.md)

**Parent topic:** SQL/JSON Function JSON_QUERY
