Clauses `RETURNING`, wrapper, error, and empty-field are described. Each is used in one or more of the SQL functions and conditions `json_value`, `json_query`, `json_table`, `json_serialize`, `json_mergepatch`, `is json`, `is not json`, `json_exists`, and `json_equal`.

- RETURNING Clause for SQL Query Functions
  SQL functions `json_value`, `json_query`, `json_serialize`, and `json_mergepatch` accept an optional `RETURNING` clause, which specifies the data type of the value returned by the function. This clause and the default behavior (no `RETURNING` clause) are described here.
- Wrapper Clause for SQL/JSON Query Functions JSON_QUERY and JSON_TABLE
  SQL/JSON query functions `json_query` and `json_table` accept an optional wrapper clause, which specifies the form of the value returned by `json_query` or used for the data in a `json_table` column. This clause and the default behavior (no wrapper clause) are described here. Examples are provided.
- Error Clause for SQL Query Functions and Conditions
  Some SQL query functions and conditions accept an optional error clause, which specifies handling for a runtime error that is raised by the function or condition. This clause and the default behavior (no error clause) are summarized here.
- Empty-Field Clause for SQL/JSON Query Functions
  SQL/JSON query functions `json_value`, `json_query`, and` json_table` accept an optional `ON EMPTY` clause, which specifies the handling to use when a targeted JSON field is absent from the data queried. This clause and the default behavior (no `ON EMPTY` clause) are described here.
- ON MISMATCH Clause for JSON_VALUE
  When the `RETURNING` clause specifies a user-defined object-type or collection-type instance, function `json_value` accepts an optional `ON MISMATCH` clause, which specifies handling to use when a targeted JSON value does not match the specified SQL return value. This clause and its default behavior (no `ON MISMATCH` clause) are described here.

**Parent topic:** [Query JSON Data](query-json-data.md)

### 16.1 RETURNING Clause for SQL Query Functions

SQL functions `json_value`, `json_query`, `json_serialize`, and `json_mergepatch` accept an optional `RETURNING` clause, which specifies the data type of the value returned by the function. This clause and the default behavior (no `RETURNING` clause) are described here.

For `json_value`, you can use any of these predefined SQL data types in a `RETURNING` clause: `VARCHAR2`, `NUMBER`, `DATE`, `TIMESTAMP`, `TIMESTAMP WITH TIME ZONE`, `SDO_GEOMETRY`, and `CLOB`. You can also use a user-defined object type or a collection type.

**Note:**

An instance of Oracle SQL data type `DATE` includes a time component. And in your JSON data you can use a string that represents an ISO 8601 date-with-time value, that is, it can have a time component.

By default, `json_value` with `RETURNING DATE` returns a SQL `DATE` value that has a zero time component (zero hours, minutes, and seconds). By default, a time component in the queried JSON scalar value is truncated in the returned SQL `DATE` instance. But before any time truncation is done, if the value represented by an ISO 8601 date-with-time string has a time-zone component then the value is first converted to UTC, to take any time-zone information into account.

You can use `RETURNING DATE ``PRESERVE TIME` to override this default truncating behavior and preserve the time component, when present, of the queried JSON scalar value. (Using `RETURNING DATE TRUNCATE TIME` has the same effect as just `RETURNING DATE`, the default behavior.)

(The same considerations apply to item methods `date()`, which corresponds to `TRUNCATE TIME`, and `dateWithTime()`, which corresponds to `PRESERVE TIME`.)

For` json_query`, `json_serialize`, and `json_mergepatch` you can use `VARCHAR2`, `CLOB`, or `BLOB`. A `BLOB` result is in the AL32UTF8 character set. Whatever the data type returned by `json_serialize`, the returned data represents textual JSON data.

You can optionally specify a length for `VARCHAR2` (default: `4000`) and a precision and scale for `NUMBER`.

The default behavior (no `RETURNING` clause) is to use `VARCHAR2(4000)`.

Data type `SDO_GEOMETRY` is for Oracle Spatial and Graph data. In particular, this means that you can use `json_value` with GeoJSON data, which is a format for encoding geographic data in JSON.

The `RETURNING` clause also accepts two optional keywords, `PRETTY` and `ASCII`. If both are present then `PRETTY` must come before `ASCII`. Keyword `PRETTY` is not allowed for `json_value`.

The effect of keyword `PRETTY` is to pretty-print the returned data, by inserting newline characters and indenting. The default behavior is not to pretty-print.

The effect of keyword `ASCII` is to automatically escape all non-ASCII Unicode characters in the returned data, using standard ASCII Unicode escape sequences. The default behavior is not to escape non-ASCII Unicode characters.

**Tip:**

You can pretty-print the entire context item by using only `$` as the path expression.

If `VARCHAR2` is specified in a `RETURNING` clause then scalars in the value are represented as follows:

- Boolean values are represented by the lowercase strings `"true"` and `"false"`.

- The `null` value is represented by SQL `NULL`.

- A JSON number is represented in a canonical form. It can thus appear differently in the output string from its representation in textual input data. When represented in canonical form:
  - It can be subject to the precision and range limitations for a SQL `NUMBER`.

  - When it is not subject to the SQL `NUMBER` limitations:
    - The precision is limited to forty (40) digits.

    - The optional exponent is limited to nine (9) digits plus a sign (`+` or `-`).

    - The entire text, including possible signs (`-`, `+`), decimal point (`.`), and exponential indicator (`E`), is limited to 48 characters.

  The **canonical form** of a JSON number:

  - Is a JSON number. (It can be parsed in JSON data as a number.)

  - Does not have a leading plus (`+`) sign.

  - Has a decimal point (`.`) only when necessary.

  - Has a single zero (`0`) before the decimal point if the number is a fraction (between zero and one).

  - Uses exponential notation (`E`) only when necessary. In particular, this can be the case if the number of output characters is too limited (by a small `N` for `VARCHAR2(``N``)`).

Oracle extends the SQL/JSON standard in the case when the returning data type is `VARCHAR2(``N``)`, by allowing optional keyword `TRUNCATE` immediately after the data type. When `TRUNCATE` is present and the value to return is wider than `N`, the value is truncated — only the first `N` characters are returned. If `TRUNCATE` is absent then this case is treated as an error, handled as usual by an error clause or the default error-handling behavior.

**Related Topics**

- Error Clause for SQL Query Functions and Conditions
- [Using JSON_VALUE To Instantiate a User-Defined Object Type Instance](function-JSON_VALUE.md)

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for information about SQL data types `DATE` and `TIMESTAMP`

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for information about SQL data type `NUMBER`

- [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-concepts.md) for information about using Oracle Spatial and Graph data

- [GeoJSON.org](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=geojson_org)

**Parent topic:** Clauses Used in SQL Query Functions and Conditions

### 16.2 Wrapper Clause for SQL/JSON Query Functions JSON_QUERY and JSON_TABLE

SQL/JSON query functions `json_query` and `json_table` accept an optional wrapper clause, which specifies the form of the value returned by `json_query` or used for the data in a `json_table` column. This clause and the default behavior (no wrapper clause) are described here. Examples are provided.

The wrapper clause takes one of these forms:

- `WITH WRAPPER` – Use a string value that represents a JSON array containing all of the JSON values that match the path expression. The order of the array elements is unspecified.

- `WITHOUT WRAPPER` – Use a string value that represents the single JSON object or array that matches the path expression. Raise an error if the path expression matches either a scalar value (not an object or array) or more than one value.

- `WITH CONDITIONAL WRAPPER` – Use a string value that represents all of the JSON values that match the path expression. For zero values, a single scalar value, or multiple values, `WITH CONDITIONAL WRAPPER` is the same as `WITH WRAPPER`. For a single JSON object or array value, it is the same as `WITHOUT WRAPPER`.

The default behavior is `WITHOUT WRAPPER`.

You can add the optional keyword `UNCONDITIONAL` immediately after keyword `WITH`, if you find it clearer: `WITH WRAPPER` and `WITH UNCONDITIONAL WRAPPER` mean the same thing.

You can add the optional keyword `ARRAY` immediately before keyword `WRAPPER`, if you find it clearer: `WRAPPER` and `ARRAY WRAPPER` mean the same thing.

Table 16-1 illustrates the wrapper clause possibilities. The array wrapper is shown in `bold`.

Table 16-1 JSON_QUERY Wrapper Clause Examples

| JSON Values Matching Path Expression | WITH WRAPPER            | WITHOUT WRAPPER         | WITH CONDITIONAL WRAPPER |
|:-------------------------------------|:------------------------|:------------------------|:-------------------------|
| `{"id": 38327}` (single object)      | `[``{"id": 38327}``]`   | `{"id": 38327}`         | `{"id": 38327}`          |
| `[42, "a", true]` (single array)     | `[``[42, "a", true]``]` | `[42, "a", true]`       | `[42, "a", true]`        |
| `42`                                 | `[``42``]`              | Error (scalar)          | `[``42``]`               |
| `42`, `"a"`, `true`                  | `[``42, "a", true``]`   | Error (multiple values) | `[``42, "a", true``]`    |
| none                                 | `[]`                    | Error (no values)       | `[]`                     |

Consider, for example, a `json_query` query to retrieve a JSON object. What happens if the path expression matches a JSON scalar value instead of an object, or it matches multiple JSON values (of any kind)? You might want to retrieve the matched values instead of raising an error. For example, you might want to pick one of the values that is an object, for further processing. Using an array wrapper lets you do this.

A conditional wrapper can be convenient if the only reason you are using a wrapper is to avoid raising an error and you do not need to distinguish those error cases from non-error cases. If your application is looking for a single object or array and the data matched by a path expression is just that, then there is no need to wrap that expected value in a singleton array.

On the other hand, with an unconditional wrapper you know that the resulting array is always a wrapper — your application can count on that. If you use a conditional wrapper then your application might need extra processing to interpret a returned array. In Table 16-1, for instance, note that the same array (`[42, "a", true]`) is returned for the very different cases of a path expression matching that array and a path expression matching each of its elements.

**Parent topic:** Clauses Used in SQL Query Functions and Conditions

### 16.3 Error Clause for SQL Query Functions and Conditions

Some SQL query functions and conditions accept an optional error clause, which specifies handling for a runtime error that is raised by the function or condition. This clause and the default behavior (no error clause) are summarized here.

By default, SQL functions and conditions for JSON avoid raising runtime errors. For example, when JSON data is syntactically invalid, `json_exists` and `json_equal` return false and `json_value` returns `NULL`.

But in some cases you can also specify an error clause, which overrides the default behavior. The error handling you can specify varies, but each SQL function and condition for JSON that lets you specify error handling supports at least the `ERROR ON ERROR` behavior of raising an error.

The optional error clause can take these forms:

- `ERROR ON ERROR` – Raise the error (no special handling).

- `NULL ON ERROR` – Return `NULL` instead of raising the error.

  Not available for `json_exists`.

- `FALSE ON ERROR` – Return false instead of raising the error.

  Available only for `json_exists` and `json_equal`, for which it is the default.

- `TRUE ON ERROR` – Return true instead of raising the error.

  Available only for `json_exists` and `json_equal`.

- `EMPTY OBJECT ON ERROR` – Return an empty object (`{}`) instead of raising the error.

  Available only for `json_query`.

- `EMPTY ARRAY ON ERROR` – Return an empty array (`[]`) instead of raising the error.

  Available only for `json_query`.

- `EMPTY ON ERROR` – Same as `EMPTY ARRAY ON ERROR`.

- `DEFAULT '``literal_return_value``' ON ERROR` – Return the specified value instead of raising the error. The value must be a constant at query compile time.

  Not available:

  - For `json_exists`, `json_equal`, `json_serialize`, `json_mergepatch`, or a `json_table` column value clause that has `json_exists` behavior

  - For `json_query` or a `json_table` column value clause that has `json_query` behavior

  - For row-level error-handing for `json_table`

  - When `SDO_GEOMETRY` is specified either as the `RETURNING` clause data type for `json_value` or as a `json_table` column data type

The default behavior is `NULL ON ERROR`, except for conditions `json_exists` and `json_equal`.

**Note:**

There are two levels of error handling for `json_table`, corresponding to its two levels of path expressions: row and column. When present, a column error handler overrides row-level error handling. The default error handler for both levels is `NULL ON ERROR`.

**Note:**

An `ON EMPTY` clause overrides the behavior specified by `ON ERROR` for the error of trying to match a missing field.

**Note:**

The `ON ERROR` clause takes effect only for runtime errors that arise when a syntactically correct SQL/JSON path expression is matched against JSON data. A path expression that is syntactically incorrect results in a compile-time syntax error; it is not handled by the `ON ERROR` clause.

**Related Topics**

- Empty-Field Clause for SQL/JSON Query Functions
- [SQL/JSON Function JSON_TABLE](function-JSON_TABLE.md)
- [SQL/JSON Function JSON_QUERY](function-JSON_QUERY.md)
- [SQL/JSON Function JSON_VALUE](function-JSON_VALUE.md)
- [Oracle SQL Function JSON_SERIALIZE](oracle-sql-function-json_serialize.md)
- [SQL/JSON Condition JSON_EXISTS](condition-JSON_EXISTS.md)
- ON MISMATCH Clause for JSON_VALUE

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/Single-Row-Functions.md) for detailed information about the error clause for SQL functions for JSON

- [Oracle Database SQL Language Reference](../sqlrf/SQL-JSON-Conditions.md) for detailed information about the error clause for SQL conditions for JSON

**Parent topic:** Clauses Used in SQL Query Functions and Conditions

### 16.4 Empty-Field Clause for SQL/JSON Query Functions

SQL/JSON query functions `json_value`, `json_query`, and` json_table` accept an optional `ON EMPTY` clause, which specifies the handling to use when a targeted JSON field is absent from the data queried. This clause and the default behavior (no `ON EMPTY` clause) are described here.

You generally handle errors for SQL/JSON functions and conditions using an error clause (`ON ERROR`). However, there is a special case where you might want different handling from this general error handling: when querying to match given JSON fields that are missing from the data. Sometimes you do not want to raise an error just because a field to be matched is absent. (A missing field is normally treated as an error.)

You typically use a `NULL ON EMPTY` clause in conjunction with an accompanying `ON ERROR` clause. This combination specifies that other errors are handled according to the `ON ERROR` clause, but the error of trying to match a missing field is handled by just returning `NULL`. If no `ON EMPTY` clause is present then an `ON ERROR` clause handles also the missing-field case.

In addition to `NULL ON EMPTY` there are `ERROR ON EMPTY` and `DEFAULT` ... `ON EMPTY`, which are analogous to the similarly named `ON ERROR` clauses.

If only an `ON EMPTY` clause is present (no `ON ERROR` clause) then missing-field behavior is specified by the `ON EMPTY` clause, and other errors are handled the same as if `NULL ON ERROR` were present (it is the `ON ERROR` default). If both clauses are absent then only `NULL ON ERROR` is used.

#### Use NULL ON EMPTY for an Index Created on JSON_VALUE

`NULL ON EMPTY` is especially useful for the case of a functional index created on a `json_value` expression. The clause has no effect on whether or when the index is picked up, but it is effective in allowing some data to be indexed that would otherwise not be because it is missing a field targeted by the `json_value` expression.

You generally want to use `ERROR ON ERROR` for the queries that populate the index, so that a query path expression that results in multiple values or complex values raises an error. But you sometimes do not want to raise an error just because the field targeted by a path expression is missing — you want that data to be indexed. [Example 28-5](indexes-for-json-data.md) illustrates this use of `NULL ON EMPTY` when creating an index on a `json_value` expression.

**Related Topics**

- [Creating JSON_VALUE Function-Based Indexes](indexes-for-json-data.md)
- Error Clause for SQL Query Functions and Conditions

**Parent topic:** Clauses Used in SQL Query Functions and Conditions

### 16.5 ON MISMATCH Clause for JSON_VALUE

When the `RETURNING` clause specifies a user-defined object-type or collection-type instance, function `json_value` accepts an optional `ON MISMATCH` clause, which specifies handling to use when a targeted JSON value does not match the specified SQL return value. This clause and its default behavior (no `ON MISMATCH` clause) are described here.

**Note:**

Clauses `ON ERROR` and `ON EMPTY` apply only when no JSON data matches the path expression. Clause `ON MISMATCH` applies when the JSON data that matches the path expression does not match the specified object or collection return type. Clause `ON MISMATCH` is allowed only when the return type is an instance of a user-defined object type or collection type. If you use it with another return type then a query compile-time error is raised.

When you return an instance of a SQL object or collection type that reflects the JSON data targeted by function ` json_value`, the definitions of that targeted data and the object or collection to be returned must match, or else a query compile-time error applies.

The default handling of such an error is just to ignore it. But you can instead handle such an error in various ways, by providing one or more `ON MISMATCH` clauses, as follows:

- `IGNORE ON MISMATCH` — Explicitly specify the default behavior: ignore the mismatch. The object or collection instance returned can contain one or more SQL `NULL` values because of mismatches against the targeted JSON data.

- `NULL ON MISMATCH` — Return SQL `NULL` as the object-type or collection-type value.

- `ERROR ON MISMATCH` — Raise a query compile-time error for the mismatch.

Each of these `ON MISMATCH` clause types can also be followed, in parentheses (`(`…`)`), by one or more clauses that each indicates a kind of mismatch to handle, separated by commas (`,`). These are the possible mismatch kinds:

- `MISSING DATA` — Some JSON data was needed to match the object-type or collection-type data, but it was missing.

- `EXTRA DATA` — One or more JSON fields have no corresponding object-type or collection-type data. For example, for JSON field `address` there is no object-type attribute with the same name (matching case-insensitively, by default).

- `TYPE ERROR` — A JSON scalar value has a data type that is incompatible with the corresponding return SQL scalar data type. This can be because of type incompatibility, as put forth in [Table 18-1](function-JSON_VALUE.md), or because the SQL data type is too constraining (e.g., `VARCHAR(2)` is two short for JSON string `"hello"`).

If no such kind-of-mismatch clause (e.g. `EXTRA DATA`) is present for a given handler (e.g. `NULL ON MISMATCH`) then that handler applies to all kinds of mismatch.

You can have any number of `ON MISMATCH` clauses of different kinds, but if two or more such contradict each other then a query compile-time error is raised.

**Related Topics**

- [Using JSON_VALUE To Instantiate a User-Defined Object Type Instance](function-JSON_VALUE.md)

**Parent topic:** Clauses Used in SQL Query Functions and Conditions
