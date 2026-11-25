Dot notation is designed for easy, general use and common use cases. Queries of JSON data that use dot-notation syntax return JSON values whenever possible.

The return value for a dot-notation query is always a string (data type `VARCHAR2(4000)`) representing JSON data. The content of the string depends on the targeted JSON data, as follows:

- If a single JSON value is targeted, then that value is the string content, whether it is a JSON scalar, object, or array.

- If multiple JSON values are targeted, then the string content is a JSON array whose elements are those values.

This behavior contrasts with that of SQL/JSON functions `json_value` and `json_query`, which you can use for more complex queries. They can return `NULL` or raise an error if the path expression you provide them does not match the queried JSON data. They accept optional clauses to specify the data type of the return value (`RETURNING` clause), whether or not to wrap multiple values as an array (wrapper clause), how to handle errors generally (`ON ERROR` clause), and how to handle missing JSON fields (`ON EMPTY` clause).

In the first case above, the dot-notation behavior is similar to that of function `json_value` for a scalar value, and it is similar to that of `json_query` for an object or array value. In the second case, the behavior is similar to that of `json_query` with an array wrapper.

The dot-notation syntax is a table alias (mandatory) followed by a dot, that is, a period (`.`), the name of a JSON column, and one or more pairs of the form `.` `json_field` or `.` `json_field` followed by `array_step`, where `json_field` is a JSON field name and `array_step` is an array step expression as described in [Basic SQL/JSON Path Expression Syntax](json-path-expressions.md).

Each `json_field` must be a valid SQL identifier,<sup>Foot 1</sup> and the column must have an `is json` check constraint, which ensures that it contains well-formed JSON data. If either of these rules is not respected then an error is raised at query compile time. (The check constraint must be present to avoid raising an error; however, it need not be active. If you deactivate the constraint then this error is not raised.)

For the dot notation for JSON queries, unlike the case generally for SQL, unquoted identifiers (after the column name) are treated case sensitively, that is, just as if they were quoted. This is a convenience: you can use JSON field names as identifiers without quoting them. For example, you can write `jcolumn.friends` instead of `jcolumn."friends"`. This also means that if a JSON object is named using uppercase, such as `FRIENDS`, then you must write `jcolumn.FRIENDS`, not `jcolumn.friends`.

Here are some examples of dot notation syntax. All of them refer to JSON column `po_document` of a table that has alias `po`.

- `po.po_document.PONumber` – The value of field `PONumber`.

- `po.po_document.LineItems[1]` – The second element of array `LineItems` (array positions are zero-based).

- `po.po_document.LineItems[*]` – All of the elements of array `LineItems` (`*` is a wildcard).

- `po.po_document.ShippingInstructions.name` – The value of field `name`, a child of object `ShippingInstructions`.

**Note:**

- Each component of the dot-notation syntax is limited to a maximum of 128 bytes.

  See [Oracle Database SQL Language Reference](../sqlrf/Database-Object-Names-and-Qualifiers.md) for more information about SQL dot-notation syntax and SQL identifiers.

- A simple dot-notation JSON query cannot return a value longer than 4K bytes. If the value surpasses this limit then SQL `NULL` is returned instead. To obtain the actual value, use SQL/JSON function `json_query` or `json_value` instead of dot notation, specifying an appropriate return type with a `RETURNING` clause.

  See [Oracle Database SQL Language Reference](../sqlrf/JSON-Object-Access-Expressions.md) for more information about JSON dot-notation syntax.

Matching of a JSON dot-notation expression against JSON data is the same as matching of a SQL/JSON path expression, including the relaxation to allow implied array iteration (see [SQL/JSON Path Expression Syntax Relaxation](json-path-expressions.md)). The JSON column of a dot-notation expression corresponds to the context item of a path expression, and each identifier used in the dot notation corresponds to an identifier used in a path expression.

For example, if JSON column `jcolumn` corresponds to the path-expression context item, then the expression `jcolumn.friends` corresponds to path expression `$.friends`, and `jcolumn.friends.name` corresponds to path expression `$.friends.name`.

For the latter example, the context item could be an object or an array of objects. If it is an array of objects then each of the objects in the array is matched for a field `friends`. The value of field `friends` can itself be an object or an array of objects. In the latter case, the first object in the array is used.

**Note:**

Other than (1) the implied use of a wildcard for array elements (see [SQL/JSON Path Expression Syntax Relaxation](json-path-expressions.md)) and (2) the explicit use of a wildcard between array brackets (`[*]`), you cannot use wildcards in a path expression when you use the dot-notation syntax. This is because an asterisk (`*`) is not a valid SQL identifier.

For example, this raises a syntax error: `mytable.mycolumn.object1.``*``.object2`.

Dot-notation syntax is a handy alternative to using simple path expressions; it is not a replacement for using path expressions in general.

Example 14-1 shows equivalent dot-notation and `json_value` queries. Given the data from [Example 4-2](creating-a-table-with-a-json-column.md), each of the queries returns the string `"1600"`, a `VARCHAR2` value representing the JSON number `1600`.

Example 14-2 shows equivalent dot-notation and `json_query` queries. Each query in the first pair returns (a `VARCHAR2` value representing) a JSON array of phone objects. Each query in the second pair returns (a `VARCHAR2` value representing) an array of phone types, just as in [Example 19-1](function-JSON_QUERY.md).

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON-Object-Access-Expressions.md) for information about dot notation used for SQL object and object attribute access (object access expressions)

Example 14-1 JSON Dot-Notation Query Compared With JSON_VALUE

    SELECT po.po_document.PONumber FROM j_purchaseorder po;

    SELECT json_value(po_document, '$.PONumber') FROM j_purchaseorder;

Example 14-2 JSON Dot-Notation Query Compared With JSON_QUERY

    SELECT po.po_document.ShippingInstructions.Phone FROM j_purchaseorder po;

    SELECT json_query(po_document, '$.ShippingInstructions.Phone')
      FROM j_purchaseorder;

    SELECT po.po_document.ShippingInstructions.Phone.type FROM j_purchaseorder po;

    SELECT json_query(po_document, '$.ShippingInstructions.Phone.type' WITH WRAPPER)
      FROM j_purchaseorder;

**Related Topics**

- [Overview of SQL/JSON Path Expressions](json-path-expressions.md)
- [Creating a Table With a JSON Column](creating-a-table-with-a-json-column.md)
- [SQL/JSON Function JSON_TABLE](function-JSON_TABLE.md)

**Parent topic:** [Query JSON Data](query-json-data.md)

------------------------------------------------------------------------



Footnote Legend

Footnote 1: In particular, this means that you cannot use an empty field name (`""`) with dot-notation syntax.
