Oracle SQL function `json_serialize` takes JSON data (of any SQL data type, `VARCHAR2`, `CLOB`, or `BLOB`) as input and returns a textual representation of it (as `VARCHAR2`, `CLOB`, or `BLOB` data). `VARCHAR2(4000)` is the default return type.

You typically use `json_serialize` to transform the result of a query. It supports an error clause and a returning clause. You can specify pretty-printing for the result, and you can truncate the result to fit the return type.

Function `json_serialize` always produces JSON data that conforms to the JSON standard (RFC 4627). The returned data uses only the standard data types of the JSON language: object, array, and the scalar types string, number, Boolean, and null.

You can use `json_serialize` to convert binary JSON data to textual form (`CLOB` or `VARCHAR2`), or to transform textual JSON data by pretty-printing it or escaping non-ASCII Unicode characters in it. An important use case is serializing JSON data that is stored in a `BLOB` column. A `BLOB` result is in the AL32UTF8 character set. But whatever the data type returned by `json_serialize`, the returned data represents textual JSON data.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_SERIALIZE.md) for information about Oracle SQL function `json_serialize`

Example 21-1 Using JSON_SERIALIZE To Convert BLOB Data To Pretty-Printed Text

This example serializes and pretty-prints the JSON purchase order that has `1600` as the value of field `PONumber` data, which is selected from column `po_document` of table `j_purchaseorder` The return-value data type is `VARCHAR2(4000)` (the default return type).

[Example 4-2](creating-a-table-with-a-json-column.md) shows the insertion of such purchase-order data into a `VARCHAR2` table. But `json_serialize` is especially useful for serializing `BLOB` data.

    SELECT json_serialize(po_document PRETTY) FROM j_purchaseorder;

**Related Topics**

- [RETURNING Clause for SQL Query Functions](clauses-used-in-functions-and-conditions-for-json.md)
- [Error Clause for SQL Query Functions and Conditions](clauses-used-in-functions-and-conditions-for-json.md)

**Parent topic:** [Query JSON Data](query-json-data.md)
