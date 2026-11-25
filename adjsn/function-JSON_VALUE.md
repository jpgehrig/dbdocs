SQL/JSON function `json_value` selects JSON data and returns a SQL scalar or an instance of a user-defined SQL object type or SQL collection type (varray, nested table).

- If `json_value` targets a single scalar JSON value then it returns a scalar SQL value. You can specify the SQL data type for the returned scalar value. By default it is `VARCHAR2(4000)`.

- If `json_value` targets a JSON array, and you specify a SQL collection type (varray or nested table) as the return type, then `json_value` returns an instance of that collection type.

  The elements of a targeted JSON array provide the elements of the returned collection-type instance. A scalar JSON array element produces a scalar SQL value in the returned collection instance (see previous). A JSON array element that is an object (see next) or an array is handled recursively.

- If `json_value` targets a JSON object, and you specify a user-defined SQL object type as the return type, then `json_value` returns an instance of that object type.

  The field values of a targeted JSON object provide the attribute values of the returned object-type instance. The field names of the targeted JSON object are compared with the SQL names of the SQL object attributes. A scalar field value produces a scalar SQL value in the returned object-type instance (see above). A field value that is an array (see previous) or an object is handled recursively,

  Ultimately it is the names of JSON fields with scalar values that are compared with the names of scalar SQL object attributes. If the names do not match exactly, case-sensitively, then a mismatch error is raised at query compile time.

You can also use `json_value` to create function-based B-tree indexes for use with JSON data — see [Indexes for JSON Data](indexes-for-json-data.md).

Function `json_value` has two required arguments, and it accepts optional returning and error clauses.

The first argument to `json_value` is a SQL expression that returns an instance of either a scalar SQL data type or a user-defined SQL object type. A scalar return value can be of data type `VARCHAR2`, `BLOB`, `or CLOB`.

The first argument can be a table or view column value, a PL/SQL variable, or a bind variable with proper casting. The result of evaluating the SQL expression is used as the context item for evaluating the path expression.

The second argument to `json_value` is a SQL/JSON path expression followed by optional clauses `RETURNING`, `ON ERROR`, and `ON EMPTY`. The path expression must target a single scalar value, or else an error occurs.

The default error-handling behavior is `NULL ON ERROR`, which means that no value is returned if an error occurs — an error is not raised. In particular, if the path expression targets a non-scalar value, such as an array, no error is raised, by default. To ensure that an error is raised, use `ERROR ON ERROR`.

**Note:**

Each field name in a given JSON object is not necessarily unique; the same field name may be repeated. The streaming evaluation that Oracle Database employs always uses only one of the object members that have a given field name; any other members with the same field name are ignored. It is unspecified which of multiple such members is used.

See also [Unique Versus Duplicate Fields in JSON Objects](conditions-is-json-and-is-not-json.md).

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_VALUE.md) for information about `json_value`

- Using SQL/JSON Function JSON_VALUE With a Boolean JSON Value
  JSON has the Boolean values `true` and `false`. When SQL/JSON function `json_value` evaluates a SQL/JSON path expression and the result is JSON `true` or `false`, it can be returned to PL/SQL as a `BOOLEAN` value, or it can be returned to SQL as the `VARCHAR2` value `'true'` or `'false'`.
- SQL/JSON Function JSON_VALUE Applied to a null JSON Value
  SQL/JSON function `json_value` applied to JSON value `null` returns SQL `NULL`, not the SQL string `'null'`. This means, in particular, that you cannot use `json_value` to distinguish the JSON value `null` from the absence of a value; SQL `NULL` indicates both cases.
- Using JSON_VALUE To Instantiate a User-Defined Object Type Instance
  You can use SQL/JSON function `json_value` to instantiate an instance of a user-defined SQL object type or collection type. You do this by targeting a JSON object or array in the path expression and specifying the object or collection type, respectively, in the `RETURNING` clause.
- JSON_VALUE as JSON_TABLE
  SQL/JSON function `json_value` can be viewed as a special case of function `json_table`.

**Related Topics**

- [RETURNING Clause for SQL Query Functions](clauses-used-in-functions-and-conditions-for-json.md)
- [Error Clause for SQL Query Functions and Conditions](clauses-used-in-functions-and-conditions-for-json.md)
- [Empty-Field Clause for SQL/JSON Query Functions](clauses-used-in-functions-and-conditions-for-json.md)

**Parent topic:** [Query JSON Data](query-json-data.md)

### 18.1 Using SQL/JSON Function JSON_VALUE With a Boolean JSON Value

JSON has the Boolean values `true` and `false`. When SQL/JSON function `json_value` evaluates a SQL/JSON path expression and the result is JSON `true` or `false`, it can be returned to PL/SQL as a `BOOLEAN` value, or it can be returned to SQL as the `VARCHAR2` value `'true'` or `'false'`.

In PL/SQL code, `BOOLEAN` is a valid PL/SQL return type for built-in PL/SQL function `json_value`. Example 18-1 illustrates this.

Oracle SQL has no Boolean data type, so a string (`VARCHAR2`) value is used to return a JSON Boolean value. Example 18-2 illustrates this — the query returns the string `'true'`.

SQL/JSON function `json_table` generalizes other SQL/JSON query functions such as `json_value`. When you use it to project a JSON Boolean value, `json_value` is used implicitly, and the resulting SQL value is returned as a `VARCHAR2` value. The data type of the projection column must therefore be `VARCHAR2`.

Example 18-1 JSON_VALUE: Returning a JSON Boolean Value to PL/SQL as BOOLEAN

PL/SQL also has exception handling. This example uses clause `ERROR ON ERROR`, to raise an error (which can be handled by user code) in case of error.

    DECLARE
      b BOOLEAN;
      jsonData CLOB;
    BEGIN
      SELECT po_document INTO jsonData FROM j_purchaseorder WHERE rownum = 1;
         b := json_value(jsonData, '$.AllowPartialShipment'
                        RETURNING BOOLEAN
                        ERROR ON ERROR);
    END;
    / 

Example 18-2 JSON_VALUE: Returning a JSON Boolean Value to SQL as VARCHAR2

    SELECT json_value(po_document, '$.AllowPartialShipment')
      FROM j_purchaseorder;

**Related Topics**

- JSON_VALUE as JSON_TABLE
- [JSON_TABLE Generalizes SQL/JSON Query Functions and Conditions](function-JSON_TABLE.md)

**Parent topic:** SQL/JSON Function JSON_VALUE

### 18.2 SQL/JSON Function JSON_VALUE Applied to a null JSON Value

SQL/JSON function `json_value` applied to JSON value `null` returns SQL `NULL`, not the SQL string `'null'`. This means, in particular, that you cannot use `json_value` to distinguish the JSON value `null` from the absence of a value; SQL `NULL` indicates both cases.

**Parent topic:** SQL/JSON Function JSON_VALUE

### 18.3 Using JSON_VALUE To Instantiate a User-Defined Object Type Instance

You can use SQL/JSON function `json_value` to instantiate an instance of a user-defined SQL object type or collection type. You do this by targeting a JSON object or array in the path expression and specifying the object or collection type, respectively, in the `RETURNING` clause.

The elements of a targeted JSON array provide the elements of a returned collection-type instance. The JSON array elements must correspond, one-to-one, with the collection-type elements. If they do not then a mismatch error occurs. A JSON array element that is an object (see next) or an array is handled recursively.

The fields of a targeted JSON object provide the attribute values of a returned object-type instance. The JSON fields must correspond, one-to-one, with the object-type attributes. If they do not then a mismatch error occurs.

The field names of the targeted JSON object are compared with the SQL names of the object attributes. A field value that is an array or an object is handled recursively, so that ultimately it is the names of JSON fields with scalar values that are compared with the names of scalar SQL object attributes. If the names do not match (case insensitively, by default), then a mismatch error occurs.

If all names match then the corresponding data types are checked for compatibility. If there is any type incompatibility then a mismatch error occurs. Table 18-1 specifies the compatible scalar data types — any other type combinations are incompatible entails a mismatch error.

Table 18-1 Compatible Scalar Data Types: Converting JSON to SQL

| JSON Type (Source) | SQL Type (Destination) | Notes                                                       |
|:-------------------|:-----------------------|:------------------------------------------------------------|
| `string`           | `VARCHAR2`             | None                                                        |
| `string`           | `CLOB`                 | None                                                        |
| `string`           | `NUMBER`               | The JSON string must be numeric.                            |
| `string`           | `DATE`                 | The JSON string must have a supported ISO 8601 format.      |
| `string`           | `TIMESTAMP`            | The JSON string must have a supported ISO 8601 format.      |
| `number`           | `NUMBER`               | None                                                        |
| `number`           | `VARCHAR2`             | None                                                        |
| `number`           | `CLOB`                 | None                                                        |
| `boolean`          | `VARCHAR2`             | The instance value is the SQL string `"true"` or `"false"`. |
| `boolean`          | `CLOB`                 | The instance value is the SQL string `"true"` or `"false"`. |
| `null`             | Any SQL data type.     | The instance value is SQL `NULL`.                           |

A mismatch error occurs at query compile time if any of the following are true. By default, mismatch errors are ignored, but you can change this error handling by including one or more `ON MISMATCH` clauses in your invocation of `json_value`.

- The fields of a targeted JSON object, or the elements of a targeted JSON array, do not correspond in number and kind to the attributes of the specified object-type instance, or to the elements of the specified collection-type instance, respectively.

- The fields of a targeted JSON object do not have the same names as the attributes of a specified object-type instance. By default this matching is case-insensitive.

- The JSON and SQL scalar data types of a JSON value and its corresponding object attribute value or collection element value are not compatible, according to Table 18-1.

Example 18-3 Instantiate a User-Defined Object Instance From JSON Data with JSON_VALUE

This example defines SQL object types `shipping_t` and `addr_t`. Object type `shipping_t` has attributes `name` and `address`, which have types `VARCHAR2(30)` and `addr_t`, respectively.

Object type `addr_t` has attributes `street` and `city`.

The example uses `json_value` to select the JSON object that is the value of field `ShippingInstructions` and return an instance of SQL object type `shipping_t`. Names of the object-type attributes are matched against JSON object field names case-insensitively, so that, for example, attribute `address` (which is the same as `ADDRESS`) of SQL object-type `shipping_t` matches JSON field `address`.

(The query output is shown pretty-printed here, for clarity.)

    CREATE TYPE shipping_t AS OBJECT
      (name    VARCHAR2(30),
       address addr_t);

    CREATE TYPE addr_t AS OBJECT
      (street VARCHAR2(100),
       city   VARCHAR2(30));

    -- Query data to return shipping_t instances:
    SELECT json_value(po_document, '$.ShippingInstructions'
                      RETURNING shipping_t)
      FROM j_purchaseorder;

    JSON_VALUE(PO_DOCUMENT,'$.SHIPPINGINSTRUCTIONS'RETURNING
    --------------------------------------------------------
    SHIPPING_T('Alexis Bull',
               ADDR_T('200 Sporting Green',
                      'South San Francisco'))
    SHIPPING_T('Sarah Bell',
               ADDR_T('200 Sporting Green',
                      'South San Francisco'))

Example 18-4 Instantiate a Collection Type Instance From JSON Data with JSON_VALUE

This example defines SQL collection type `items_t` and SQL object types `part_t` and `item_t`. An instance of collection type `items_t` is a varray of `item_t` instances. Attribute `part` of object-type `item_t` is itself of SQL object-type `part_t`.

It then uses `json_value` to select the JSON

(The query output is shown pretty-printed here, for clarity.)

    CREATE TYPE part_t AS OBJECT
      (description VARCHAR2(30),
       unitprice   NUMBER);

    CREATE TYPE item_t AS OBJECT
      (itemnumber NUMBER,
       part       part_t);

    CREATE TYPE items_t AS VARRAY(10) OF item_t;

    -- Query data to return items_t collections of item_t objects
    SELECT json_value(po_document, '$.LineItems' RETURNING items_t)
      FROM j_purchaseorder;

    JSON_VALUE(PO_DOCUMENT,'$.LINEITEMS'RETURNINGITEMS_TUSIN
    --------------------------------------------------------
    ITEMS_T(ITEM_T(1, PART_T('One Magic Christmas', 19.95)),
            ITEM_T(2, PART_T('Lethal Weapon', 19.95)))
    ITEMS_T(ITEM_T(1, PART_T('Making the Grade', 20)),
            ITEM_T(2, PART_T('Nixon', 19.95)),
            ITEM_T(3, PART_T(NULL, 19.95)))

**Related Topics**

- [ON MISMATCH Clause for JSON_VALUE](clauses-used-in-functions-and-conditions-for-json.md)

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_VALUE.md) for information about `json_value`

**Parent topic:** SQL/JSON Function JSON_VALUE

### 18.4 JSON_VALUE as JSON_TABLE

SQL/JSON function `json_value` can be viewed as a special case of function `json_table`.

Example 18-5 illustrates the equivalence: the two `SELECT` statements have the same effect.

In addition to perhaps helping you understand `json_value` better, this equivalence is important practically, because it means that you can use either function to get the same effect.

In particular, if you use `json_value` more than once, or you use it in combination with `json_exists` or `json_query` (which can also be expressed using `json_table`), to access the same data, then a single invocation of `json_table` presents the advantage that the data is parsed only once.

Because of this, the optimizer often automatically rewrites multiple invocations of `json_exists`, `json_value` and `json_query` (any combination) to fewer invocations of `json_table`.

Example 18-5 JSON_VALUE Expressed Using JSON_TABLE

    SELECT json_value(column, json_path RETURNING data_type error_hander ON ERROR)
      FROM table;

    SELECT jt.column_alias
      FROM table,
           json_table(column, '$' error_handler ON ERROR
             COLUMNS ("COLUMN_ALIAS" data_type PATH json_path)) AS "JT";

**Related Topics**

- [JSON_TABLE Generalizes SQL/JSON Query Functions and Conditions](function-JSON_TABLE.md)

**Parent topic:** SQL/JSON Function JSON_VALUE
