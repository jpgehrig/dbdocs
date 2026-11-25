SQL/JSON condition `json_exists` lets you use a SQL/JSON path expression as a row filter, to select rows based on the content of JSON documents. You can use condition `json_exists` in a `CASE` expression or the `WHERE` clause of a `SELECT` statement.

Condition `json_exists` checks for the existence of a particular value within JSON data: it returns true if the value is present and false if it is absent. More precisely, `json_exists` returns true if the data it targets matches one or more JSON values. If no JSON values are matched then it returns false.

You can also use `json_exists` to create bitmap indexes for use with JSON data — see [Example 28-1](indexes-for-json-data.md).

Error handlers `ERROR ON ERROR`, `FALSE ON ERROR`, and `TRUE ON ERROR` apply. The default is `FALSE ON ERROR`. The handler takes effect when any error occurs, but typically an error occurs when the given JSON data is not well-formed (using lax syntax). Unlike the case for conditions `is json` and `is not json`, condition `json_exists` expects the data it examines to be well-formed JSON data.

The second argument to `json_exists` is a SQL/JSON path expression followed by an optional `PASSING` clause and an optional error clause.

The optional filter expression of a SQL/JSON path expression used with `json_exists` can refer to SQL/JSON variables, whose values are passed from SQL by binding them with the `PASSING` clause. The following SQL data types are supported for such variables: `VARCHAR2`, `NUMBER`, `BINARY_DOUBLE`, `DATE`, `TIMESTAMP`, and `TIMESTAMP WITH TIMEZONE`.

**Tip:**

For queries that you use often, use a `PASSING` clause to define SQL bind variables, which you use as SQL/JSON variables in path expressions. This can improve performance by avoiding query recompilation when the (variable) values change.

For example, this query passes the value of bind variable `V1` as SQL/JSON variable `$V1`:

    SELECT po.po_document FROM j_purchaseorder po
      WHERE json_exists(po.po_document,
                        '$.LineItems.Part?(@.UPCCode == $V1)'
                        PASSING '85391628927' AS "V1");

**Note:**

SQL/JSON condition `json_exists` applied to JSON value `null` returns the SQL string `'true'`.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/SQL-JSON-Conditions.md) for information about `json_exists`

- Using Filters with JSON_EXISTS
  You can use SQL/JSON condition `json_exists` with a path expression that has one or more filter expressions, to select documents that contain matching data. Filters let you test for the existence of documents that have particular fields that satisfy various conditions.
- JSON_EXISTS as JSON_TABLE
  SQL/JSON condition `json_exists` can be viewed as a special case of SQL/JSON function `json_table`.

**Related Topics**

- [RETURNING Clause for SQL Query Functions](clauses-used-in-functions-and-conditions-for-json.md)
- [Error Clause for SQL Query Functions and Conditions](clauses-used-in-functions-and-conditions-for-json.md)

**Parent topic:** [Query JSON Data](query-json-data.md)

### 17.1 Using Filters with JSON_EXISTS

You can use SQL/JSON condition `json_exists` with a path expression that has one or more filter expressions, to select documents that contain matching data. Filters let you test for the existence of documents that have particular fields that satisfy various conditions.

SQL/JSON condition `json_exists` returns true for documents containing data that matches a SQL/JSON path expression. If the path expression contains a filter, then the data that matches the path to which that filter is applied must also satisfy the filter, in order for `json_exists` to return true for the document containing the data.

A filter applies to the path that immediately precedes it, and the test is whether both (a) the given document has some data that matches that path, and (b) that matching data satisfies the filter. If both of these conditions hold then `json_exists` returns true for the document.

The path expression immediately preceding a filter defines the scope of the patterns used in it. An at-sign (`@`) within a filter refers to the data targeted by that path, which is termed the current item for the filter. For example, in the path expression `$.LineItems?(@.Part.UPCCode == 85391628927)`, `@` refers to an occurrence of array `LineItems`.

Example 17-1 JSON_EXISTS: Path Expression Without Filter

This example selects purchase-order documents that have a line item whose part description contains a UPC code entry.

    SELECT po.po_document FROM j_purchaseorder po
      WHERE json_exists(po.po_document, '$.LineItems.Part.UPCCode');

Example 17-2 JSON_EXISTS: Current Item and Scope in Path Expression Filters

This example shows three equivalent ways to select documents that have a line item whose part contains a UPC code with a value of `85391628927`.

    SELECT po.po_document FROM j_purchaseorder po
      WHERE json_exists(po.po_document,
                        '$?(@.LineItems.Part.UPCCode == 85391628927)');

    SELECT po.po_document FROM j_purchaseorder po
      WHERE json_exists(po.po_document,
                        '$.LineItems?(@.Part.UPCCode == 85391628927)');

    SELECT po.po_document FROM j_purchaseorder po
      WHERE json_exists(po.po_document,
                        '$.LineItems.Part?(@.UPCCode == 85391628927)');

- In the first query, the scope of the filter is the context item, that is, an entire purchase order. `@` refers to the context item.

- In the second query, the filter scope is a `LineItems` array (and each of its elements, implicitly). `@` refers to an element of that array.

- In the third query, the filter scope is a `Part` field of an element in a `LineItems` array. `@` refers to a `Part` field.

Example 17-3 JSON_EXISTS: Filter Conditions Depend On the Current Item

This example selects purchase-order documents that have both a line item with a part that has UPC code `85391628927` and a line item with an order quantity greater than 3. The scope of each filter, that is, the current item, is in this case the context item. Each filter condition applies independently (to the same document); the two conditions do not necessarily apply to the same line item.

    SELECT po.po_document FROM j_purchaseorder po
      WHERE json_exists(po.po_document,
                        '$?(@.LineItems.Part.UPCCode == 85391628927
                            && @.LineItems.Quantity > 3)');

Example 17-4 JSON_EXISTS: Filter Downscoping

This example looks similar to Example 17-3, but it acts quite differently. It selects purchase-order documents that have a line item with a part that has UPC code and with an order quantity greater than 3. The scope of the current item in the filter is at a lower level; it is not the context item but a `LineItems` array element. That is, the same line item must satisfy both conditions, for `json_exists` to return true.

    SELECT po.po_document FROM j_purchaseorder po
      WHERE json_exists(po.po_document,
                        '$.LineItems[*]?(@.Part.UPCCode == 85391628927
                                      && @.Quantity > 3)');

Example 17-5 JSON_EXISTS: Path Expression Using Path-Expression exists Condition

This example shows how to downscope one part of a filter while leaving another part scoped at the document (context-item) level. It selects purchase-order documents that have a `User` field whose value is `"ABULL"` and documents that have a line item with a part that has UPC code and with an order quantity greater than 3. That is, it selects the same documents selected by Example 17-4, as well as all documents that have `"ABULL"` as the user. The argument to path-expression predicate `exists` is a path expression that specifies particular line items; the predicate returns true if a match is found, that is, if any such line items exist.

(If you use this example or similar with SQL\*Plus then you must use `SET DEFINE OFF` first, so that SQL\*Plus does not interpret `&& exists` as a substitution variable and prompt you to define it.)

    SELECT po.po_document FROM j_purchaseorder po
      WHERE json_exists(po.po_document,
                        '$?(@.User == "ABULL"
                            && exists(@.LineItems[*]?(
                                        @.Part.UPCCode == 85391628927
                                        && @.Quantity > 3)))');

**Related Topics**

- [Basic SQL/JSON Path Expression Syntax](json-path-expressions.md)

**Parent topic:** SQL/JSON Condition JSON_EXISTS

### 17.2 JSON_EXISTS as JSON_TABLE

SQL/JSON condition `json_exists` can be viewed as a special case of SQL/JSON function `json_table`.

Example 17-6 illustrates the equivalence: the two `SELECT` statements have the same effect.

In addition to perhaps helping you understand `json_exists` better, this equivalence is important practically, because it means that you can use either to get the same effect.

In particular, if you use `json_exists` more than once, or you use it in combination with `json_value` or `json_query` (which can also be expressed using `json_table`), to access the same data, then a single invocation of `json_table` presents the advantage that the data is parsed only once.

Because of this, the optimizer often automatically rewrites multiple invocations of `json_exists`, `json_value` and `json_query` (any combination) to fewer invocations of `json_table`.

Example 17-6 JSON_EXISTS Expressed Using JSON_TABLE

    SELECT select_list
      FROM table WHERE json_exists(column, json_path error_handler ON ERROR);

    SELECT select_list
      FROM table,
           json_table(column, '$' error_handler ON ERROR
             COLUMNS ("COLUMN_ALIAS" NUMBER EXISTS PATH json_path)) AS "JT"
      WHERE jt.column_alias = 1;

**Related Topics**

- [JSON_TABLE Generalizes SQL/JSON Query Functions and Conditions](function-JSON_TABLE.md)

**Parent topic:** SQL/JSON Condition JSON_EXISTS
