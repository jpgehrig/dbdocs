You can query JSON data using a simple dot notation or, for more functionality, using SQL/JSON functions and conditions. You can create and query a data guide that summarizes the structure and type information of a set of JSON documents.

Because JSON data is stored in the database using standard data types (`VARCHAR2`, `BLOB`, and `CLOB`), SQL queries work with JSON data the same as with any other database data.

To query particular JSON fields, or to map particular JSON fields to SQL columns, you can use the SQL/JSON path language. In its simplest form a path expression consists of one or more field names separated by periods (`.`). More complex path expressions can contain filters and array indexes.

Oracle provides two ways of querying JSON content:

- A dot-notation syntax, which is essentially a table alias, followed by a JSON column name, followed by one or more field names — all separated by periods (`.`). An array step can follow each of the field names. This syntax is designed to be simple to use and to return JSON values whenever possible.

- SQL/JSON functions and conditions, which completely support the path language and provide more power and flexibility than is available using the dot-notation syntax. You can use them to create, query, and operate on JSON data stored in Oracle Database.

  - Condition `json_exists` tests for the existence of a particular value within some JSON data.

  - Conditions `is json` and `is not json` test whether some data is well-formed JSON data. The former is used especially as a check constraint.

  - Function `json_value` selects a scalar value from some JSON data, as a SQL value.

  - Function `json_query` selects one or more values from some JSON data, as a SQL string representing the JSON values. It is used especially to retrieve fragments of a JSON document, typically a JSON object or array.

  - Function `json_table` projects some JSON data as a virtual table, which you can also think of as an inline view.

Because the path language is part of the query language, no fixed schema is imposed on the data. This design supports schemaless development. A “schema”, in effect, gets defined on the fly at query time, by your specifying a given path. This is in contrast to the more usual approach with SQL of defining a schema (a set of table rows and columns) for the data at storage time.

Oracle SQL condition `json_equal` does not accept a path-expression argument. It just compares two JSON values and returns true if they are equal, false otherwise. For this comparison, insignificant whitespace and insignificant object member order are ignored. For example, JSON objects are equal if they have the same members, regardless of their order. However, if either of two compared objects has one or more duplicate fields then the value returned by `json_equal` is unspecified.

You can generate and query a JSON data guide, to help you develop expressions for navigating your JSON content. A data guide can give you a deep understanding of the structure and type information of your JSON documents. Data guide information can be updated automatically, to keep track of new documents that you add.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Single-Row-Functions.md) for complete information about the syntax and semantics of the SQL/JSON functions and conditions

- [Simple Dot-Notation Access to JSON Data](simple-dot-notation-access-to-json-data.md)
  Dot notation is designed for easy, general use and common use cases. Queries of JSON data that use dot-notation syntax return JSON values whenever possible.
- [SQL/JSON Path Expressions](json-path-expressions.md)
  Oracle Database provides SQL access to JSON data using SQL/JSON path expressions.
- [Clauses Used in SQL Query Functions and Conditions](clauses-used-in-functions-and-conditions-for-json.md)
  Clauses `RETURNING`, wrapper, error, and empty-field are described. Each is used in one or more of the SQL functions and conditions `json_value`, `json_query`, `json_table`, `json_serialize`, `json_mergepatch`, `is json`, `is not json`, `json_exists`, and `json_equal`.
- [SQL/JSON Condition JSON_EXISTS](condition-JSON_EXISTS.md)
  SQL/JSON condition `json_exists` lets you use a SQL/JSON path expression as a row filter, to select rows based on the content of JSON documents. You can use condition `json_exists` in a `CASE` expression or the `WHERE` clause of a `SELECT` statement.
- [SQL/JSON Function JSON_VALUE](function-JSON_VALUE.md)
  SQL/JSON function `json_value` selects JSON data and returns a SQL scalar or an instance of a user-defined SQL object type or SQL collection type (varray, nested table).
- [SQL/JSON Function JSON_QUERY](function-JSON_QUERY.md)
  SQL/JSON function `json_query` selects one or more values from JSON data and returns a string (`VARCHAR2`, `CLOB`, or `BLOB` instance) that represents the JSON values. You can thus use `json_query` to retrieve fragments of a JSON document.
- [SQL/JSON Function JSON_TABLE](function-JSON_TABLE.md)
  SQL/JSON function `json_table` projects specific JSON data to columns of various SQL data types. You use it to map parts of a JSON document into the rows and columns of a new, virtual table, which you can also think of as an inline view.
- [Oracle SQL Function JSON_SERIALIZE](oracle-sql-function-json_serialize.md)
  Oracle SQL function `json_serialize` takes JSON data (of any SQL data type, `VARCHAR2`, `CLOB`, or `BLOB`) as input and returns a textual representation of it (as `VARCHAR2`, `CLOB`, or `BLOB` data). `VARCHAR2(4000)` is the default return type.
- [JSON Data Guide](json-dataguide.md)
  A JSON data guide lets you discover information about the structure and content of JSON documents stored in Oracle Database.
