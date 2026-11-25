Changes in Oracle Database for this book are described.

Oracle Database JSON Developer's Guide was a new book in Oracle Database 12c Release 2 (12.2.0.1). Information about using JSON data in Oracle Database 12c Release 1 (12.1.0.2) is available in [Oracle XML DB Developer’s Guide](http://www.oracle.com/pls/topic/lookup?ctx=E50529-01&id=ADXDB-GUID-A8A58B49-13A5-4F42-8EA0-508951DAE0BB).

- Changes in Oracle Database Release 19c, Version 19.1, for JSON Developer’s Guide
  The changes in JSON support and in Oracle Database JSON Developer’s Guide for Oracle Database Release 19c, Version 19.1, are described.
- Changes in Oracle Database Release 18c, Version 18.1, for JSON Developer’s Guide
  The changes in JSON support and in Oracle Database JSON Developer’s Guide for Oracle Database Release 18c, Version 18.1, are described.

### Changes in Oracle Database Release 19c, Version 19.1, for JSON Developer’s Guide

The changes in JSON support and in Oracle Database JSON Developer’s Guide for Oracle Database Release 19c, Version 19.1, are described.

- New Features
  The following features are new in this release.

**Parent topic:** Changes in This Release for Oracle Database JSON Developer's Guide

#### New Features

The following features are new in this release.

- JSON Materialized View Support
  Performance enhancement: If you create a refresh-on-statement materialized view over `json_table`  and some other conditions apply then a query that matches the query defining the view can be rewritten to a materialized-view table access. You can use this feature instead of creating multiple functional indexes.
- SQL Function JSON_MERGEPATCH: Declarative Update of JSON Documents
  You can now update a JSON document declaratively, using new SQL function `json_mergepatch`. You can apply one or more changes to multiple documents using a single statement. This feature improves the flexibility of JSON update operations.
- New SQL/JSON Function JSON_SERIALIZE and JSON Data Guide Support for GeoJSON Data
  You can use new SQL function `json_serialize` to serialize JSON data to text or to UTF-encoded `BLOB` data. SQL aggregate function `json_dataguide` can now detect GeoJSON geographic data in your documents. You can use it to create a view that projects such data as SQL data type `SDO_GEOMETRY`.
- Syntax Simplifications
  Syntax simplifications are offered for SQL/JSON path expressions and SQL/JSON generation with function `json_object`. A new SQL query clause, `NESTED`, provides a simple alternative to using `json_table` with `LEFT OUTER JOIN`.
- Mapping of JSON Data To and From SQL Object Types
  This feature enables the mapping of JSON data to and from user-defined SQL object types and collections. You can convert JSON data to an instance of a SQL object type using SQL/JSON function `json_value`. In the opposite direction, you can generate JSON data from an instance of a SQL object type using SQL/JSON function `json_object` or `json_array`.

**Parent topic:** Changes in Oracle Database Release 19c, Version 19.1, for JSON Developer’s Guide

##### JSON Materialized View Support

Performance enhancement: If you create a refresh-on-statement materialized view over `json_table`  and some other conditions apply then a query that matches the query defining the view can be rewritten to a materialized-view table access. You can use this feature instead of creating multiple functional indexes.

**Parent topic:** New Features

##### SQL Function JSON_MERGEPATCH: Declarative Update of JSON Documents

You can now update a JSON document declaratively, using new SQL function `json_mergepatch`. You can apply one or more changes to multiple documents using a single statement. This feature improves the flexibility of JSON update operations.

**Related Topics**

- [Updating a JSON Document with JSON Merge Patch](updating-json-document-json-merge-patch.md)

**Parent topic:** New Features

##### New SQL/JSON Function JSON_SERIALIZE and JSON Data Guide Support for GeoJSON Data

You can use new SQL function `json_serialize` to serialize JSON data to text or to UTF-encoded `BLOB` data. SQL aggregate function `json_dataguide` can now detect GeoJSON geographic data in your documents. You can use it to create a view that projects such data as SQL data type `SDO_GEOMETRY`.

**Related Topics**

- [Oracle SQL Function JSON_SERIALIZE](oracle-sql-function-json_serialize.md)
- [JSON Data-Guide Fields](json-dataguide.md)

**Parent topic:** New Features

##### Syntax Simplifications

Syntax simplifications are offered for SQL/JSON path expressions and SQL/JSON generation with function `json_object`. A new SQL query clause, `NESTED`, provides a simple alternative to using `json_table` with `LEFT OUTER JOIN`.

**Related Topics**

- [Basic SQL/JSON Path Expression Syntax](json-path-expressions.md)
- [Overview of SQL/JSON Generation Functions](generation.md)
- [SQL/JSON Function JSON_OBJECT](generation.md)
- [SQL NESTED Clause Instead of JSON_TABLE](function-JSON_TABLE.md)
- [Diagrams for Basic SQL/JSON Path Expression Syntax](diagrams-basic-sql-json-path-expression-syntax.md)

**Parent topic:** New Features

##### Mapping of JSON Data To and From SQL Object Types

This feature enables the mapping of JSON data to and from user-defined SQL object types and collections. You can convert JSON data to an instance of a SQL object type using SQL/JSON function `json_value`. In the opposite direction, you can generate JSON data from an instance of a SQL object type using SQL/JSON function `json_object` or `json_array`.

**Related Topics**

- [SQL/JSON Function JSON_VALUE](function-JSON_VALUE.md)
- [Using JSON_VALUE To Instantiate a User-Defined Object Type Instance](function-JSON_VALUE.md)
- [ON MISMATCH Clause for JSON_VALUE](clauses-used-in-functions-and-conditions-for-json.md)
- [SQL/JSON Function JSON_OBJECT](generation.md)
- [SQL/JSON Function JSON_ARRAY](generation.md)

**Parent topic:** New Features

### Changes in Oracle Database Release 18c, Version 18.1, for JSON Developer’s Guide

The changes in JSON support and in Oracle Database JSON Developer’s Guide for Oracle Database Release 18c, Version 18.1, are described.

- New Features
  The following features are new in this release.
- Deprecated Features
  The following features are deprecated in this release, and may be desupported in a future release.

**Parent topic:** Changes in This Release for Oracle Database JSON Developer's Guide

#### New Features

The following features are new in this release.

- SQL Enhancements
  Multiple SQL enhancements are provided for storing and querying JSON data in the database.
- Sharding Support
  Sharding support for JSON data has been enhanced.
- Performance Improvements for LOB Storage
  Performance has been improved for JSON data that uses LOB storage. This particularly affects the common use case of reading and writing an entire JSON document stored as a LOB.
- JSON Search Index Support for Longer Field Names
  The maximum JSON field name length supported for a JSON search index is now 255 bytes (formerly it was 64 bytes).

**Parent topic:** Changes in Oracle Database Release 18c, Version 18.1, for JSON Developer’s Guide

##### SQL Enhancements

Multiple SQL enhancements are provided for storing and querying JSON data in the database.

##### You Can Specify That a SQL Expression Returns JSON Data

You can apply SQL function `treat`, with keywords `AS JSON`, to a SQL expression to specify that the expression returns JSON data. This is useful in situations where Oracle cannot determine that the result is JSON data. It is also useful in situations where you want to force some text to be interpreted as JSON data. For example, you can use it to tell Oracle to interpret a `VARCHAR2` value of `{}` not as a string but as an empty JSON object.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/TREAT.md)

##### LOB Results for JSON_VALUE, JSON_QUERY, and JSON_TABLE

SQL/JSON function `json_value` can now return a `CLOB` instance.

SQL/JSON function `json_query` can now return a `CLOB` or `BLOB` instance. A `BLOB` result is in the AL32UTF8 character set.

As before, the data type of a `json_table` column depends on whether the column is specified as `FORMAT JSON`. If it is, the `json_query` return types are supported; if it is not, the `json_value` return types are supported.

Previously:

- `json_value` supported only `VARCHAR2`, `NUMBER`, `DATE`, `TIMESTAMP`, `TIMESTAMP WITH TIME ZONE`, and `SDO_GEOMETRY`

  as return types.

- `json_query` supported only `VARCHAR2` as return type.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Single-Row-Functions.md)

##### SQL/JSON Generation Function Enhancements

- Optional keyword `STRICT` has been added. When present, any inputs that are declared or otherwise expected to be JSON data are checked to ensure that they are, in fact, well-formed JSON data. If any of them is not then an error is raised.

  (You can declare input to be JSON by using keywords `FORMAT JSON` or by using SQL function `treat` with keywords `AS JSON`. Input is expected to be JSON data if it is from a table column that has an `is json` constraint or it is the output of another JSON generation function.)

- The SQL/JSON generation functions (`json_object`, `json_array`, `json_objectagg`, and `json_arrayagg`) can now return a `CLOB` or `BLOB` instance. A `BLOB` result is in the AL32UTF8 character set.

- The input expression to a generation function can now be of any of these SQL data types (in addition to `NUMBER`, `VARCHAR2`, `DATE` and `TIMESTAMP`):

  - `BINARY_DOUBLE`

  - `BINARY_FLOAT`

  - `CLOB`

  - `BLOB`

  - `NVARCHAR2`

  - `RAW`

  - `TIMESTAMP WITH TIME ZONE`

  - `TIMESTAMP WITH LOCAL TIME ZONE`

  - `INTERVAL YEAR TO MONTH`

  - `INTERVAL DAY TO SECOND`

  How the result of generation is rendered in JSON depends on the data type of the input.

  **See Also:**

  - [Handling of Input Values For SQL/JSON Generation Functions](generation.md)

  - [Oracle Database SQL Language Reference](../sqlrf/Single-Row-Functions.md)

##### Item Methods for SQL/JSON Path Expressions

- New item methods have been added: `numberOnly()`, `stringOnly()`, `boolean()`, `booleanOnly()`, `size()`, and `type()`.

  The data-type conversion methods with “only” in their name are the same as the corresponding methods with names without “only”, except that the former convert only JSON values that are of the given type (e.g., `number`) to the related SQL data type (e.g. `NUMBER`). The methods without “only” in the name allow conversion, when possible, of any JSON value to the given SQL data type.

- All item methods can now be used in path expressions for SQL/JSON functions `json_value`, `json_query`, and `json_table` (columns). In Oracle Database 12c Release 2 (12.2.0.1), item methods could only be used in path expressions for SQL/JSON condition `json_exists`.

- Item method `string()` can now return `CLOB` or `BLOB` (in addition to `VARCHAR2`). The default is `VARCHAR2(4000)`.

**See Also:**

[SQL/JSON Path Expression Item Methods](json-path-expressions.md)

##### JSON Data Guide Enhancements

- Oracle SQL aggregate function `json_dataguide` now accepts optional formatting arguments:

  - You can return a hierarchical dataguide, by specifying keyword `FORMAT` with argument `DBMS_JSON.FORMAT_``HIERARCHICAL`.

  - You can specify pretty-printing (indentation to improve readability) of the returned dataguide, by specifying keyword `PRETTY` with argument `DBMS_JSON.``PRETTY` .

- New data-dictionary views are available, to show you the dataguide information recorded for individual JSON object fields in a dataguide-enabled search index: `USER_JSON_DATAGUIDE_FIELDS`, `ALL_JSON_DATAGUIDE_FIELDS`, `DBA_JSON_DATAGUIDE_FIELDS`. (These are in addition to views `USER_JSON_DATAGUIDES`, `ALL_JSON_DATAGUIDES`, and `DBA_JSON_DATAGUIDES`, which list the tables that have JSON columns with a dataguide-enabled search index.)

- For JSON documents that contain an array of scalar values, a dataguide now records the scalar types as well as the type `ARRAY`. The recorded path for the scalar values is indicated in a flat data guide by appending `[*]` to the path recorded for the array itself.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_DATAGUIDE.md)

##### Data-Dictionary Views That Record the Presence of JSON Columns

Data-dictionary views `USER_JSON_COLUMNS`, `ALL_JSON_COLUMNS`, and `DBA_JSON_COLUMNS` now list the views, as well as the tables, that have columns with JSON data.

**See Also:**

[Oracle Database Reference](../refrn/ALL_JSON_COLUMNS.md) for information about `ALL_JSON_COLUMNS` and the related data-dictionary views

##### SQL/JSON Function JSON_TABLE Syntax

The syntax of `json_table` has been enhanced by making it simpler for some common use cases:

- You can now use simple dot-notation syntax in place of a path expression.

- If a column is the projection of a JSON object field, and if you want the column to have the same name as the field, then you need not provide a path expression to that object — the path is inferred from the column name.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_TABLE.md)

##### ON STATEMENT Support For JSON_TABLE Materialized Views

You can now use keywords `ON STATEMENT` when creating a materialized view using a `json_table` query. Using `ON STATEMENT` instead of `ON COMMIT` means that the view is automatically synchronized for each DML statement against the base table.

##### New SQL Function TO_UTC_TIMESTAMP_TZ

SQL function `to_UTC_timestamp_tz` takes as input an ISO 8601 date format string and returns an instance of SQL data type `TIMESTAMP WITH TIMEZONE`. It normalizes the input to UTC time (Coordinated Universal Time, formerly Greenwich Mean Time). Unlike SQL function `to_timestamp_tz`, the new function assumes that the input string uses the ISO 8601 date format, defaulting the time zone to UTC 0.

A typical use of this function would be to provide its output to SQL function `sys_extract_UTC`, obtaining a UTC time that is then passed as a SQL bind variable to SQL/JSON condition `json_exists`, to perform a time-stamp range comparison.

**See Also:**

[ISO 8601](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=wikipedia_iso8601) for information about the ISO date formats

##### New Oracle SQL Condition JSON_EQUAL

Oracle SQL condition `json_equal` compares two JSON values and returns true if they are equal, false otherwise. For this comparison, insignificant whitespace and insignificant object member order are ignored. For example, JSON objects are equal if they have the same members, regardless of their order. However, if either of two compared objects has one or more duplicate fields then the value returned by `json_equal` is unspecified.

**Related Topics**

- [Determining Whether a Column Necessarily Contains JSON Data](creating-a-table-with-a-json-column.md)
- [Basic SQL/JSON Path Expression Syntax](json-path-expressions.md)
- [Data-Dictionary Views For Persistent Data-Guide Information](json-dataguide.md)

**Parent topic:** New Features

##### Sharding Support

Sharding support for JSON data has been enhanced.

The following are now supported:

- JSON search index on sharded tables, whether user-managed or system-managed.

- Cross-shard (and in-shard) queries for JSON data returned as `CLOB` or `BLOB` from SQL and PL/SQL. This includes projection of JSON data to `CLOB` and `BLOB` columns using SQL/JSON function `json_table`.

- Evaluation on individual shards of cross-shard queries that use SQL/JSON functions and conditions. This includes the use of the following:

  - Function `json_value` and aggregate function `json_dataguide` in a `SELECT` clause

  - Function `json_table` in a `FROM` clause

  - Function `json_value`, and conditions `json_exists` and `json_textcontains`, in a `WHERE` clause.

- Automatic relocation of base-table and index storage-table partitions during chunk migration.

**See Also:**

[Using Oracle Sharding](../shard/changes-in-this-release.md)

**Parent topic:** New Features

##### Performance Improvements for LOB Storage

Performance has been improved for JSON data that uses LOB storage. This particularly affects the common use case of reading and writing an entire JSON document stored as a LOB.

**Parent topic:** New Features

##### JSON Search Index Support for Longer Field Names

The maximum JSON field name length supported for a JSON search index is now 255 bytes (formerly it was 64 bytes).

**Note:**

You must rebuild any JSON search indexes and Oracle Text indexes created prior to Oracle Database 18c if they index JSON data that contains object fields with names longer than 64 bytes. See [Oracle Database Upgrade Guide](../upgrd/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information.

**Related Topics**

- [Oracle Database JSON Restrictions](oracle-json-restrictions.md)

**Parent topic:** New Features

#### Deprecated Features

The following features are deprecated in this release, and may be desupported in a future release.

- SQL/JSON functions returning a Boolean JSON value as a number (zero or one). Return the value as `VARCHAR2` or (in PL/SQL only) as `BOOLEAN`; do not return it as `NUMBER`. If you really need a SQL numeric value then you can use SQL `DECODE` or `CASE WHEN` to obtain zero or one from a `VARCHAR2` value.

**Parent topic:** Changes in Oracle Database Release 18c, Version 18.1, for JSON Developer’s Guide
