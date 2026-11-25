Oracle SQL function `json_transform` modifies JSON documents. You specify modification operations to perform and SQL/JSON path expressions that target the places to modify. The operations are applied to the input data in the order specified: each operation acts on the result of applying all of the preceding operations.

Function `json_transform` is atomic: if attempting any of the operations raises an error then none of the operations take effect. `json_transform` either succeeds completely, so that the data is modified as required, or the data remains unchanged. `json_transform` returns the original data, modified as expressed by the arguments.

You can use `json_transform` in a SQL `UPDATE` statement, to update the documents in a JSON column. Example 11-1 illustrates this.

You can use it in a `SELECT` list, to modify the selected documents. The modified documents can be returned or processed further. Example 11-2 illustrates this.

Function `json_transform` can accept as input, and return as output, any SQL data type that supports JSON data.

The default return (output) data type is the same as the input data type.<sup>Foot 1</sup> (If the input is `VARCHAR2` of any size then the default is `VARCHAR2(``4000``))`.

Unlike Oracle SQL function `json_mergepatch`, which has limited applicability (it is suitable for updating JSON documents that primarily use objects for their structure, and that do not make use of explicit `null` values), `json_transform` is a general modification function.

When you specify more than one operation to be performed by a single invocation of `json_transform`, the operations are performed in sequence, in the order specified. Each operation thus acts on the result of applying all of the preceding operations.

Following the sequence of modification operations that you specify, you can include optional `RETURNING` and `PASSING` clauses. The `RETURNING` clause is the same as for SQL/JSON function `json_query`. The `PASSING` clause is the same as for SQL/JSON condition `json_exists`. They specify the return data type and SQL bind variables, respectively.

The possible modification operations are as follows:

- `REMOVE` — Remove the input data that is targeted by the specified path expression. An error is raised if you try to remove all of the data; that is, you cannot use `REMOVE '$'`. By default, no error is raised if the targeted data does not exist (`IGNORE ON MISSING`).

- `KEEP` — Remove all parts of the input data that are not targeted by at least one of the specified path expressions. A topmost object or array is not removed; it is emptied, becoming an empty object (`{}`) or array (`[]`).

- `RENAME` — Rename the field targeted by the specified path expression to the value of the SQL expression that follows the equal sign (`=`). By default, no error is raised if the targeted field does not exist (`IGNORE ON MISSING`).

- `SET` — Set the data targeted by the specified path expression to the value of the specified SQL expression. The default behavior is like that of SQL `UPSERT`: replace existing targeted data with the new value, or insert the new value at the targeted location if the path expression matches nothing.

  (See operator `INSERT` about inserting an array element past the end of the array.)

- `REPLACE` — Replace the data targeted by the specified path expression with the value of the specified SQL expression. By default, no error is raised if the targeted data does not exist (`IGNORE ON MISSING`).

  (`REPLACE` has the effect of `SET` with clause `IGNORE ON MISSING`.)

- `INSERT` — Insert the value of the specified SQL expression at the location targeted by the specified path expression, which must be either the field of an object or an array position (otherwise, an error is raised). By default, an error is raised if a targeted object field already exists.

  (`INSERT` for an object field has the effect of `SET` with clause `CREATE ON MISSING` (default for `SET`), except that the default behavior for `ON EXISTING` is `ERROR`, not `REPLACE`.)

  You can specify an array position past the current end of an array. In that case, the array is lengthened to accommodate insertion of the value at the indicated position, and the intervening positions are filled with JSON `null` values.

  For example, if the input JSON data is `{"a":["b"]}` then `INSERT '$.a[3]'=42` returns `{"a":["b", ``null``, ``null`` 42]}` as the modified data. The elements at array positions 1 and 2 are `null`.

- `APPEND` — Append the value of the specified SQL expression to the targeted array. By default, an error is raised if the path expression does not target an array.

  (`APPEND` has the effect of `INSERT` for an array position of `last+1`.)

Immediately following the keyword for each kind of operation is the path expression for the data targeted by that operation. Operation `KEEP` is an exception in that the keyword is followed by one or more path expressions, which target the data to keep — all data not targeted by at least one of these path expressions is removed.

For all operations except `KEEP`, and `REMOVE`, the path expression is followed by an equal sign (`=`) and then a SQL result expression. This is evaluated and the resulting value is used to modify the targeted data. <sup>Foot 1</sup>

For operation `RENAME` the result expression must evaluate to a SQL string. Otherwise, an error is raised.

For all operations except `RENAME`, the result expression must evaluate to a SQL value that can be rendered as a JSON value. Otherwise, an error is raised because of the inappropriate SQL data type. (This is the same requirement as for the value part of a name–value pair provided to SQL/JSON generation function `json_object`.)

You can convert the evaluation of the result expression to JSON data by following the expression immediately with keywords `FORMAT JSON`. This is particularly useful to convert the SQL string `'true'` or `'false'` to the corresponding JSON-language value `true` or `false`. Example 11-7 illustrates this.

The last part of an operation specification is an optional set of handlers. Different operations allow different handlers and provide different handler defaults. (An error is raised if you provide a handler for an operation that disallows it.)

There are three kinds of handler:

- `ON EXISTING` — Specifies what happens if a path expression matches the data; that is, it targets at least one value.

  - `ERROR`` ON EXISTING` — Raise an error.

  - `IGNORE`` ON EXISTING` — Leave the data unchanged (no modification).

  - `REPLACE`` ON EXISTING` — Replace data at the targeted location with the value of the SQL result expression.

  - `REMOVE`` ON EXISTING` — Remove the targeted data.

- `ON MISSING` — Specifies what happens if a path expression does not match the data; that is, it does not target at least one value.

  - `ERROR`` ON MISSING` — Raise an error.

  - `IGNORE`` ON MISSING` — Leave the data unchanged (no modification).

  - `CREATE`` ON MISSING` — Add data at the targeted location.

  Note that for a path-expression array step, an `ON MISSING` handler does not mean that the targeted array itself is missing from the data — that is instead covered by handler `ON EMPTY`. An `ON MISSING` handler covers the case where one or more of the positions specified by the array step does not match the data. For example, array step `[2]` does not match data array `["a", "b"]` because that array has no element at position 2.

- `ON NULL` — Specifies what happens if the value of the SQL result expression is `NULL`.

  - `NULL`` ON NULL` — Use a JSON `null` value for the targeted location.

  - `ERROR`` ON NULL` — Raise an error.

  - `IGNORE`` ON NULL` — Leave the data unchanged (no modification).

  - `REMOVE`` ON NULL` — Remove the targeted data.

  The default behavior for all handlers that allow `ON NULL` is `NULL ON NULL`.

The handlers allowed for the various operations are as follows:

- `REMOVE`: `IGNORE ON MISSING` (default), `ERROR ON MISSING`

- `KEEP`: no handlers

- `RENAME`: `IGNORE ON MISSING` (default), `ERROR ON MISSING`

- `SET`:

  - `REPLACE ON EXISTING` (default), `ERROR ON EXISTING`, `IGNORE ON EXISTING`,

  - `CREATE ON MISSING` (default), `ERROR ON MISSING`, `IGNORE ON MISSING`

  - `NULL ON NULL` (default), `ERROR ON NULL`, `IGNORE ON NULL`, `REMOVE ON NULL`

- `REPLACE`:

  - `IGNORE ON MISSING` (default), `ERROR ON MISSING`, `CREATE ON MISSING`

  - `NULL ON NULL` (default), `ERROR ON NULL`, `IGNORE ON NULL`, `REMOVE ON NULL`

- `INSERT`:

  - `ERROR ON EXISTING` (default), `IGNORE ON EXISTING`, `REPLACE ON EXISTING`

  - `NULL ON NULL` (default), `ERROR ON NULL`, `IGNORE ON NULL`, `REMOVE ON NULL`

- `APPEND`:

  - `ERROR ON MISSING` (default), `IGNORE ON MISSING`, `CREATE ON MISSING`. Create means insert a singleton array at the targeted location. The single array element is the value of the SQL result expression.

  - `NULL ON NULL` (default), `ERROR ON NULL`, `IGNORE ON NULL`

Example 11-1 Updating a JSON Column Using JSON_TRANSFORM

This example updates all documents in `j_purchaseorder.po_document`, setting the value of field `lastUpdated` to the current timestamp.

If the field already exists then its value is replaced; otherwise, the field and its value are added. (That is, the default handlers are used: `REPLACE ON EXISTING` and `CREATE ON MISSING`.)

    UPDATE j_purchaseorder SET po_document =
      json_transform(po_document, SET '$.lastUpdated' = SYSTIMESTAMP);

Example 11-2 Modifying JSON Data On the Fly With JSON_TRANSFORM

This example selects all documents in `j_purchaseorder.po_document`, returning pretty-printed, updated copies of them, where field `"Special Instructions"` has been removed.

It does nothing (no error is raised) if the field does not exist: `IGNORE ON MISSING` is the default behavior.

The return data type is `CLOB`.

    SELECT json_transform(po_document, REMOVE '$."Special Instructions"'
                          RETURNING CLOB PRETTY)
      FROM j_purchaseorder;

Example 11-3 Adding a Field Using JSON_TRANSFORM

These two uses of `json_tranform` are equivalent. They each add field `Comments` with value `"Helpful"`. An error is raised if the field already exists. The input for the field value is literal SQL string `'Helpful'`. The default behavior for `SET` is `CREATE ON MISSING`.

    json_transform(po_document, INSERT '$.Comments' = 'Helpful')

    json_transform(po_document, SET '$.Comments' = 'Helpful'
                                    ERROR ON EXISTING)

Example 11-4 Removing a Field Using JSON_TRANSFORM

This example removes field `Special Instructions`. It does nothing (no error is raised) if the field does not exist: `IGNORE ON MISSING` is the default behavior.

    json_transform(po_document, REMOVE '$.Special Instructions')

Example 11-5 Creating or Replacing a Field Value Using JSON_TRANSFORM

This sets the value of field `Address` to the JSON object `{"street":"8 Timbly Lane", "city":"Penobsky", "state":"Utah"}`. It creates the field if it does not exist, and it replaces any existing value for the field. The input for the field value is a literal SQL string. The updated field value is a JSON object, because `FORMAT JSON` is specified for the input value.

    json_transform(po_document,
                   SET '$.Address' =
                       '{"street":"8 Timbly Rd.",
                         "city":"Penobsky",
                         "state":"UT"}'
                       FORMAT JSON)

Without using `FORMAT JSON`, the `Address` field value would be a JSON string that corresponds to the SQL input string. Each of the double-quote (`"`) characters in the input would be escaped in the JSON string:

    "{\"street\":\"8 Timbly Rd.\","city\":\"Penobsky\",\"state\":\"UT\"}"

Example 11-6 Replacing an Existing Field Value Using JSON_TRANSFORM

This sets the value of field `Address` to the JSON object `{"street":"8 Timbly Lane", "city":"Penobsky", "state":"Utah"}`. It replaces an existing value for the field, and it does nothing if the field does not exist. The only difference between this example and Example 11-5 is the presence of handler `IGNORE ON MISSING`.

    json_transform(po_document,
                   SET '$.Address' =
                       '{"street":"8 Timbly Rd.",
                         "city":"Penobsky",
                         "state":"UT"}'
                       FORMAT JSON
                       IGNORE ON MISSING)

Example 11-7 Using FORMAT JSON To Set a JSON Boolean Value

This example sets the value of field `AllowPartialShipment` to the JSON-language Boolean value `true`. Without keywords `FORMAT JSON` it would instead set the field to the JSON-language string `"true"`.

    json_transform(po_document,
                   SET '$.AllowPartialShipment' = 'true' FORMAT JSON)

Example 11-8 Setting an Array Element Using JSON_TRANSFORM

This sets the first element of array `Phone` to the JSON string `"909-555-1212"`.

    json_transform(po_document,
                   SET '$.ShippingInstructions.Phone[0]' = '909-555-1212')

If the value of array `Phone` before the operation is this:

    [{"type":"Office","number":"909-555-7307"},
     {"type":"Mobile","number":415-555-1234"}]

Then this is the value after the modification:

    ["909-555-1212",
     {"type":"Mobile","number":415-555-1234"}]

Example 11-9 Prepending an Array Element Using JSON_TRANSFORM

This prepends element `"909-555-1212"` to array `Phone`. Insertion at position 0 shifts all existing elements to the right: element N becomes element N+1.

    json_transform(po_document,
                   INSERT '$.ShippingInstructions.Phone[0]' =
                          '909-555-1212')

Example 11-10 Appending an Array Element Using JSON_TRANSFORM

These two uses of `json_tranform` are equivalent. They each append element `"909-555-1212"` to array `Phone`.

    json_transform(po_document,
                   APPEND '$.ShippingInstructions.Phone' =
                          '909-555-1212')

    json_transform(po_document,
                   INSERT '$.ShippingInstructions.Phone[last+1]' =
                          '909-555-1212')

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/json_transform.md) for information about Oracle SQL function `json_transform`

**Parent topic:** [Insert, Update, and Load JSON Data](insert-load-and-update-json-data.md)

------------------------------------------------------------------------



Footnote Legend

Footnote 1: Do not confuse the SQL return type for function `json_transform` with the type of the SQL result expression that follows an equal sign (`=`) in a modification operation other than `KEEP` and `REMOVE`.
