A JSON data guide lets you discover information about the structure and content of JSON documents stored in Oracle Database.

Some ways that you can use this information include:

- Generating a JSON Schema document that describes the set of JSON documents.

- Creating views that you can use to perform SQL operations on the data in the documents.

- Automatically adding or updating virtual columns that correspond to added or changed fields in the documents.

**See Also:**

- [JSON Schema: core definitions and terminology json-schema-core](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=json_schema_core)

- [JSON Schema: interactive and non interactive validation](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=json_schema_validation)

<!-- -->

- Overview of JSON Data Guide
  A data guide is a summary of the structural and type information contained in a set of JSON documents. It records metadata about the fields used in those documents.
- Persistent Data-Guide Information: Part of a JSON Search Index
  JSON data-guide information can be saved persistently as part of the JSON search index infrastructure, and this information is updated automatically as new JSON content is added. This is the case by default, when you create a JSON search index: data-guide information is part of the index infrastructure.
- Data-Guide Formats and Ways of Creating a Data Guide
  There are two formats for a data guide: flat and hierarchical. Both are made available to SQL and PL/SQL as `CLOB` data. You can construct a data guide from the data-guide information stored in a JSON search index or by scanning JSON documents.
- JSON Data-Guide Fields
  The predefined fields of a JSON data guide are described. They include JSON Schema fields (keywords) and Oracle-specific fields.
- Data-Dictionary Views For Persistent Data-Guide Information
  You can query static data-dictionary views to see which tables have JSON columns with data guide-enabled JSON search indexes and to extract JSON object field information that is recorded in dataguide-enabled JSON search indexes.
- Specifying a Preferred Name for a Field Column
  You can project JSON fields from your data as columns in a database view or as virtual columns added to the same table that contains the JSON column. You can specify a preferred name for such a column.
- Creating a View Over JSON Data Based on Data-Guide Information
  Based on data-guide information, you can create a database view whose columns project particular scalar fields present in a set of JSON documents. You can choose the fields to project by editing a hierarchical data guide or by specifying a SQL/JSON path expression and a minimum frequency of field occurrence.
- Adding and Dropping Virtual Columns For JSON Fields Based on Data-Guide Information
  Based on data-guide information for a JSON column, you can project scalar fields from that JSON data as virtual columns in the same table. The scalar fields projected are those that are not under an array.
- Change Triggers For Data Guide-Enabled Search Index
  When JSON data changes, some information in a data guide-enabled JSON search index is automatically updated. You can specify a procedure whose invocation is triggered whenever this happens. You can define your own PL/SQL procedure for this, or you can use the predefined change-trigger procedure `add_vc`.
- Multiple Data Guides Per Document Set
  A data guide reflects the shape of a given set of JSON documents. If a JSON column contains different types of documents, with different structure or type information, you can create and use different data guides for the different kinds of documents.
- Querying a Data Guide
  A data guide is information about a set of JSON documents. You can query it from a flat data guide that you obtain using either Oracle SQL function `json_dataguide` or PL/SQL function `DBMS_JSON.get_index_dataguide`. In the latter case, a data guide-enabled JSON search index must be defined on the JSON data.
- A Flat Data Guide For Purchase-Order Documents
  The fields of a sample flat data guide are described. It corresponds to a set of purchase-order documents.
- A Hierarchical Data Guide For Purchase-Order Documents
  The fields of a sample hierarchical data guide are described. It corresponds to a set of purchase-order documents.

**Parent topic:** [Query JSON Data](query-json-data.md)

### 22.1 Overview of JSON Data Guide

A data guide is a summary of the structural and type information contained in a set of JSON documents. It records metadata about the fields used in those documents.

For example, for the JSON object presented in [Example 2-1](json-data.md), a data guide specifies that the document has, among other things, an object `ShippingInstructions` with fields `name`, `Address`, and `Phone`, of types string, object, and array, respectively. The structure of object `Address` is recorded similarly, as are the types of the elements in array `Phone`.

JSON data-guide information can be saved persistently as part of the JSON search index infrastructure, and this information is updated automatically as new JSON content is added. This is the case by default, when you create a JSON search index: data-guide information is part of the index infrastructure.

You can use a data guide:

- As a basis for developing applications that involve data mining, business intelligence, or other analysis of JSON documents.

- As a basis for providing user assistance about requested JSON information, including search.

- To check or manipulate new JSON documents before adding them to a document set (for example: validate, type-check, or exclude certain fields).

For such purposes you can:

- Query a data guide directly for information about the document set, such as field lengths or which fields occur with at least a certain frequency.

- Create views, or add virtual columns, that project particular JSON fields of interest, based on their significance according to a data guide.

**Note:**

- The advantages of virtual columns over a view are that you can build an index on a virtual column and you can obtain statistics on it for the optimizer.

- Virtual columns, like columns in general, are subject to the 1000-column limit for a given table.

**Related Topics**

- JSON Data-Guide Fields
- [JSON Search Index: Ad Hoc Queries and Full-Text Search](indexes-for-json-data.md)
- Querying a Data Guide
- Creating a View Over JSON Data Based on a Hierarchical Data Guide
- Adding and Dropping Virtual Columns For JSON Fields Based on Data-Guide Information

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.get_index_dataguide`

- [Oracle Database SQL Language Reference](../sqlrf/JSON_DATAGUIDE.md) for information about SQL function `json_dataguide`

**Parent topic:** JSON Data Guide

### 22.2 Persistent Data-Guide Information: Part of a JSON Search Index

JSON data-guide information can be saved persistently as part of the JSON search index infrastructure, and this information is updated automatically as new JSON content is added. This is the case by default, when you create a JSON search index: data-guide information is part of the index infrastructure.

You can use `CREATE SEARCH INDEX` with keywords `FOR JSON` to create a search index, a data guide, or both at the same time. The default behavior is to create both.

To create persistent data-guide information as part of a JSON search index without enabling support for search in the index, you specify `SEARCH_ON NONE` in the `PARAMETERS` clause for `CREATE SEARCH INDEX`, but you leave the value for `DATAGUIDE` as `ON` (the default value). Example 22-1 illustrates this.

You can use `ALTER INDEX` ... `REBUILD` to enable or disable data-guide support for an existing JSON search index. Example 22-2 illustrates this — it disables the data-guide support that is added by default in [Example 28-17](indexes-for-json-data.md).

**Note:**

To create a data guide-enabled JSON search index, or to data guide-enable an existing JSON search index, you need database privilege `CTXAPP` and Oracle Database Release 12c (12.2.0.1) or later.

**Note:**

A data guide-enabled JSON search index can be built only on a column that has an `is json` check constraint. Furthermore, for the data-guide information in the index to be updated the check constraint must be enabled.

If the check constraint becomes disabled for some reason then you must rebuild the data-guide information in the index and re-enable the check constraint, to resume automatic data-guide support updating, as follows:

    ALTER INDEX index_name REBUILD ('dataguide off');
    ALTER INDEX index_name REBUILD ('dataguide on');
    ALTER TABLE table_name ENABLE CONSTRAINT is_json_check_constraint_name;

In particular, using SQL\*Loader (`sqlldr`) disables `is json` check constraints.

Because persistent data-guide information is part of the search index infrastructure, it is always live: its content is automatically updated whenever the index is synchronized. Changes in the indexed data are reflected in the search index, including in its data-guide information, only after the index is synchronized.

In addition, update of data-guide information in a search index is always additive: none of it is ever deleted. This is another reason that the index often does not accurately reflect the data in its document set: deletions within the documents it applies to are not reflected in its data-guide information. If you need to ensure that such information accurately reflects the current data then you must drop the JSON search index and create it anew.

The persistent data-guide information in a search index can also include statistics, such as how frequently each JSON field is used in the document set. Statistics are present only if you explicitly gather them on the document set (gather them on the JSON search index, for example). They are not updated automatically — gather statistics anew if you want to be sure they are up to date. Example 22-3 gathers statistics on the JSON data indexed by JSON search index `po_search_idx`, which is created in [Example 28-17](indexes-for-json-data.md).

**Note:**

When a local data guide-enabled JSON search index is created in a sharding environment, each individual shard contains the data-guide information for the JSON documents stored in that shard. For this reason, if you invoke data guide-related operations on the shard catalog database then they will have no effect.

#### Considerations for a Data Guide-Enabled Search Index on a Partitioned Table

The data-guide information in a data guide-enabled JSON search index that is local to a partitioned table is not partitioned. It is shared among all partitions.

Because the data-guide information in the index is only additive, dropping, merging, splitting, or truncating partitions has no impact on the index.

Exchanging a partitioned table with a table that is not partitioned updates the data-guide information in an index on the partitioned table, but any data guide-enabled index on the non-partitioned table must be rebuilt.

#### Avoid Persistent Data-Guide Information If Serializing Hash-Table Data

If you serialize Java hash tables or associative arrays (such as are found in JavaScript) as JSON objects, then avoid the use of persistent data-guide information.

The default hash-table serialization provided by popular libraries such as GSON and Jackson produces textual JSON documents with object field names that are taken from the hash-table key entries and with field values taken from the corresponding Java hash-table values. Serializing a single Java hash-table entry produces a new (unique) JSON field and value.

Persisted data-guide information reflects the shape of your data, and it is updated automatically as new JSON documents are inserted. Each hash-table key–value pair results in a separate entry in the JSON search index. Such serialization can thus greatly increase the size of the information maintained in the index. In addition to the large size, the many index updates affect performance negatively, making DML slow.

If you serialize a hash table or an associative array instead as a JSON array of objects, each of which includes a field derived from a hash-table key entry, then there are no such problems.

The default serialization of a hash table or associative array as a JSON object is indistinguishable from an object that has field names assigned by a developer. A JSON data guide cannot tell which (metadata-like) field names have been assigned by a developer and which (data-like) names might have been derived from a hash table or associative array. It treats all field names as essentially metadata, as if specified by a developer.

For example:

- If you construct an application object using a hash table that has `animalName` as the hash key and sets of animal properties as values then the resulting default serialization is a single JSON object that has a separate field (`"cat"`, `"mouse"`,...) for each hash-table entry, with the field value being an object with the corresponding animal properties. This can be problematic in terms of data-guide size and performance because of the typically large number of fields (`"cat"`, `"mouse"`,...) derived from the hash key.

- If you instead construct an application array of `animal` structures, each of which has a field `animalName` (with value `"cat"` or `"mouse"`...) then the resulting serialization is a JSON array of objects, each of which has the same field, `animalName`. The corresponding data guide has no size or performance problem.

Example 22-1 Enabling Persistent Support for a JSON Data Guide But Not For Search

    CREATE SEARCH INDEX po_dg_only_idx ON j_purchaseorder (po_document) FOR JSON
      PARAMETERS ('SEARCH_ON NONE');

Example 22-2 Disabling JSON Data-Guide Support For an Existing JSON Search Index

    ALTER INDEX po_search_idx REBUILD PARAMETERS ('DATAGUIDE OFF');

Example 22-3 Gathering Statistics on JSON Data Using a JSON Search Index

    EXEC DBMS_STATS.gather_index_stats(docuser, po_search_idx, NULL, 99);

**Related Topics**

- [JSON Search Index: Ad Hoc Queries and Full-Text Search](indexes-for-json-data.md)

**See Also:**

- [Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md) for information about the `PARAMETERS` clause for `CREATE SEARCH INDEX`

- [Oracle Text Reference](../ccref/oracle-text-SQL-statements-and-operators.md) for information about the `PARAMETERS` clause for `ALTER INDEX` ... `REBUILD`

- [Faster XML / Jackson](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=fasterxml_jacksonhome) for information about the Jackson JSON processor

- [google / gson](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=gson_java_library) for information about the GSON Java library

**Parent topic:** JSON Data Guide

### 22.3 Data-Guide Formats and Ways of Creating a Data Guide

There are two formats for a data guide: flat and hierarchical. Both are made available to SQL and PL/SQL as `CLOB` data. You can construct a data guide from the data-guide information stored in a JSON search index or by scanning JSON documents.

- You can use a flat data guide to query data-guide information such as field frequencies and types.

  A flat data guide is represented in JSON as an array of objects, each of which represents the JSON data of a specific path in the document set. A Flat Data Guide For Purchase-Order Documents describes a flat data guide for the purchase-order data of [Example 2-1](json-data.md).

- You can use a hierarchical data guide to create a view, or to add virtual columns, using particular fields that you choose on the basis of data-guide information.

  A hierarchical data guide is represented in JSON as an object with nested JSON data, in the same format as that defined by JSON Schema (version 4, json-schema-core). A Hierarchical Data Guide For Purchase-Order Documents describes a hierarchical data guide for the purchase-order data of [Example 2-1](json-data.md).

You use PL/SQL function `DBMS_JSON.``get_index_dataguide` to obtain a data guide from the data-guide information stored in a JSON search index.

You can also use SQL aggregate function `json_dataguide` to scan your document set and construct a data guide for it, whether or not it has a data guide-enabled search index. The data guide accurately reflects the document set at the moment of function invocation.

Table 22-1 SQL and PL/SQL Functions to Obtain a Data Guide

| Uses Data Guide-Enabled Search Index? | Flat Data Guide                                                                                               | Hierarchical Data Guide                                                                    |
|:--------------------------------------|:--------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------|
| Yes                                   | PL/SQL function `get_index_dataguide` with format `DBMS_JSON.``FORMAT_FLAT`                                   | PL/SQL function `get_index_dataguide` with format `DBMS_JSON.``FORMAT_HIERARCHICAL`        |
| No                                    | SQL function `json_dataguide`, with no format argument or with `DBMS_JSON.FORMAT_FLAT` as the format argument | SQL function `json_dataguide`, with `DBMS_JSON.FORMAT_HIERARCHICAL` as the format argument |

Advantages of obtaining a data guide based on a data guide-enabled JSON search index include:

- Additive updates to the document set are automatically reflected in the persisted data-guide information whenever the index is synced.

- Because this data-guide information is persisted, obtaining a data guide based on it (using PL/SQL function `get_index_dataguide`) is faster than obtaining a data guide by analyzing the document set (using SQL function `json_dataguide`).

- If you have gathered statistics on the document set then these are included in the stored information and in a data guide obtained from it.

- Column-name conflicts encountered when creating a view or virtual columns are automatically resolved.

Advantages of obtaining a data guide without using a data guide-enabled JSON search index include assurance that the data guide is accurate and the lack of index maintenance overhead. In addition, a data guide that is not derived from an index is appropriate in some particular use cases:

- The JSON data is in an external table. You cannot create an index on it.

- The JSON column could be indexed, but the index would not be very useful. This can be the case, for example, if the column contains different kinds of documents. In this case, it can sometimes be helpful to add a column to the table that identifies the kind of document stored in the JSON column. You can then use the data guide with SQL aggregate functions and `GROUP BY`. See Multiple Data Guides Per Document Set.

**Related Topics**

- A Flat Data Guide For Purchase-Order Documents
- A Hierarchical Data Guide For Purchase-Order Documents
- Persistent Data-Guide Information: Part of a JSON Search Index

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.get_index_dataguide`

- [Oracle Database SQL Language Reference](../sqlrf/JSON_DATAGUIDE.md) for information about SQL function `json_dataguide`

- [Oracle Database SQL Language Reference](../arpls/DBMS_JSON.md) for information about PL/SQL constants `DBMS_JSON.FORMAT_FLAT` and `DBMS_JSON.FORMAT_HIERARCHICAL`

**Parent topic:** JSON Data Guide

### 22.4 JSON Data-Guide Fields

The predefined fields of a JSON data guide are described. They include JSON Schema fields (keywords) and Oracle-specific fields.

A given occurrence of a field in a data guide corresponds to a field that is present in one or more JSON documents of the document set.

#### JSON Schema Fields (Keywords)

A JSON Schema is a JSON document that contains a JSON object, which can itself contain child objects (subschemas). Fields that are defined by JSON Schema are called JSON Schema **keywords**. Table 22-2 describes the keywords that can be used in an Oracle JSON data guide. Keywords `properties`, `items`, and `oneOf` are used only in a hierarchical JSON data guide (which is a JSON schema). Keyword `type` is used in both flat and hierarchical data guides.

Table 22-2 JSON Schema Fields (Keywords)

| Field (Keyword) | Value Description                                                                                                                                                                                                   |
|:----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `properties`    | An object whose members represent the properties of a JSON object used in JSON data that is represented by the hierarchical data guide (JSON schema).                                                               |
| `items`         | An object whose members represent the elements (items) of an array used in JSON data represented by the hierarchical data guide (JSON schema).                                                                      |
| `oneOf`         | An array, each of whose items represents one or more occurrences of a JSON field in the JSON data represented by the hierarchical data guide (JSON schema).                                                         |
| `type`          | A string naming the type of some JSON data represented by the (flat or hierarchical) data guide.<br>The possible values are: `"number"`, `"string"`, `"boolean"`, `"null"`, `"object"`, `"array"`, and `"GeoJSON"`. |

#### Oracle-Specific JSON Data-Guide Fields

In addition to JSON Schema keywords, a JSON data guide can contain Oracle data guide-specific fields. The field names all have the prefix `o:`. They are described in Table 22-3.

Table 22-3 Oracle-Specific Data-Guide Fields

| Field                     | Value Description                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:--------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `o:path`                  | Path through the JSON documents to the JSON field. Used only in a flat data guide. The value is a simple SQL/JSON path expression (no filter expression), possibly with relaxation (implicit array wrapping and unwrapping), and possibly with a wildcard array step. It has no array steps with array indexes or range specifications, and it has no function step. See [SQL/JSON Path Expression Syntax](json-path-expressions.md). |
| `o:length`                | Maximum length of the JSON field value, in bytes. The value is always a power of two. For example, if the maximum length of all actual field values is 5 then the value of `o:length` is 8, the smallest power of two greater than or equal to 5.                                                                                                                                                                                     |
| `o:preferred_column_name` | An identifier, case-sensitive and unique to a given data guide, that you prefer as the name to use for a view column or a virtual column that is created using the data guide.<br>This field is absent if the data guide was obtained using SQL function `json_dataguide` with format parameter `DBMS_JSON.FORMAT_FLAT` or without any format parameter (`DBMS_JSON.FORMAT_FLAT` is the default).                                     |
| `o:frequency`             | Percentage of JSON documents that contain the given field. Duplicate occurrences of a field under the same array are ignored. (Available only if statistics were gathered on the document set.)<br>This field is absent if the data guide was obtained using SQL function `json_dataguide`.                                                                                                                                           |
| `o:num_nulls`             | Number of documents whose value for the targeted scalar field is JSON `null`. (Available only if statistics were gathered on the document set.)<br>This field is absent if the data guide was obtained using SQL function `json_dataguide`.                                                                                                                                                                                           |
| `o:high_value`            | Highest value for the targeted scalar field, among all documents. (Available only if statistics were gathered on the document set.)<br>This field is absent if the data guide was obtained using SQL function `json_dataguide`.                                                                                                                                                                                                       |
| `o:low_value`             | Lowest value for the targeted scalar field, among all documents. (Available only if statistics were gathered on the document set.)<br>This field is absent if the data guide was obtained using SQL function `json_dataguide`.                                                                                                                                                                                                        |
| `o:last_analyzed`         | Date and time when statistics were last gathered on the document set. (Available only if statistics were gathered on the document set.)<br>This field is absent if the data guide was obtained using SQL function `json_dataguide`.                                                                                                                                                                                                   |

The data-guide information for documents that contain a JSON array with only scalar elements records the path and type for both (1) the array and (2) all of the array elements taken together. For the elements:

- The `o:path` value is the `o:path` value for the array, followed by an array with a wildcard (`[*]`), which indicates all array elements.

- The `type` value is the type `string`, if the scalar types are not the same for all elements in all documents. If all of the scalar elements the array have the same type, across all documents, then that type is recorded.

For example, if, in all documents, all of the elements in the array value for object field `serial_numbers` are JSON numbers, then `type` for the array elements is `number`. Otherwise it is `string`.

When present, the default value of field `o:preferred_column_name` depends on whether the data guide was obtained using SQL function `json_dataguide` (with format `DBMS_JSON.FORMAT_HIERARCHICAL`) or using PL/SQL function `DBMS_JSON.get_index_dataguide`:

- `json_dataguide` (hierarchical format) — Same as the corresponding JSON field name.

- `get_index_dataguide` — Same as the corresponding JSON field name, prefixed with the JSON column name followed by `$`, and with any non-ASCII characters removed. If the resulting field name already exists in the same data guide then it is suffixed with a new sequence number, to make it unique.

  The column name is uppercase unless the column was defined using escaped lowercase letters (for example, `'PO_Column'` instead of `po_column`).

  For example, the default value for field `User` for data in JSON column `po_document` is `PO_DOCUMENT$``User`.

You can use PL/SQL procedure `DBMS_JSON.rename_column` to set the value of `o:preferred_column_name` for a given field and type.

Field `o:preferred_column_name` is used to name a new, virtual column in the table that contains the JSON column, or it is used to name a column in a new view that also contains the other columns of the table. In either case, the name specified by `o:preferred_column_name` must be unique with respect to the other column names of the table. In addition, the name must be unique across all JSON fields of any type in the document set. When you use `DBMS_JSON.get_index_dataguide`, the default name is guaranteed to be unique in these ways.

If the name you specify with `DBMS_JSON.rename_column` causes a name conflict then the specified name is ignored and a system-generated name is used instead.

**Related Topics**

- Specifying a Preferred Name for a Field Column
- A Flat Data Guide For Purchase-Order Documents
- A Hierarchical Data Guide For Purchase-Order Documents
- [Using GeoJSON Geographic Data](using-GeoJSON-geographic-data.md)

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.get_index_dataguide`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.rename_column`

- [Oracle Database SQL Language Reference](../sqlrf/JSON_DATAGUIDE.md) for information about SQL function `json_dataguide`

- [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-concepts.md) for information about using GeoJSON data with Oracle Spatial and Graph

- [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-concepts.md) for information about Oracle Spatial and Graph and `SDO_GEOMETRY` object type

- [GeoJSON.org](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=geojson_org) for information about GeoJSON

**Parent topic:** JSON Data Guide

### 22.5 Data-Dictionary Views For Persistent Data-Guide Information

You can query static data-dictionary views to see which tables have JSON columns with data guide-enabled JSON search indexes and to extract JSON object field information that is recorded in dataguide-enabled JSON search indexes.

Tables that do not have JSON columns with data guide-enabled indexes are not present in the views.

You can use the following views to find columns that have data guide-enabled JSON search indexes. The views have columns `TABLE_NAME` (the table name), `COLUMN_NAME` (the JSON column name), and `DATAGUIDE` (a data guide).

- `USER_JSON_``DATAGUIDES` — tables owned by the current user

- `ALL_JSON_``DATAGUIDES` — tables accessible by the current user

- `DBA_JSON_``DATAGUIDES` — all tables

If the JSON column has a data guide-enabled JSON search index then the value of column `DATAGUIDE` is the data guide for the JSON column, in flat format as a `CLOB` instance. If it does not have a data guide-enabled index then there is no row for that column in the view.

You can use the following views to extract JSON field path and type information that is recorded in dataguide-enabled JSON search indexes. The views have columns `TABLE_NAME`, `COLUMN_NAME`, `PATH`, `TYPE`, and `LENGTH`. Columns `PATH`, `TYPE`, and `LENGTH` correspond to the values of data-guide fields `o:path`, `o:type`, and `o:length`, respectively.

- `USER_JSON_DATAGUIDE_``FIELDS` — tables owned by the current user

- `ALL_JSON_DATAGUIDE_``FIELDS` — tables accessible by the current user

- `DBA_JSON_DATAGUIDE_``FIELDS` — all tables

In the case of both types of view, a view whose name has the prefix `ALL_` or `DBA_` also has column `OWNER`, whose value is the table owner.

**See Also:**

- [Oracle Database Reference](../refrn/ALL_JSON_DATAGUIDES.md) for information about `ALL_JSON_DATAGUIDES` and the related data-dictionary views

- [Oracle Database Reference](../refrn/ALL_JSON_DATAGUIDE_FIELDS.md) for information about `ALL_JSON_DATAGUIDE_FIELDS` and the related data-dictionary views

**Parent topic:** JSON Data Guide

### 22.6 Specifying a Preferred Name for a Field Column

You can project JSON fields from your data as columns in a database view or as virtual columns added to the same table that contains the JSON column. You can specify a preferred name for such a column.

A data guide obtained from the same document set is used to define this projection. The name of each projected column is taken from data-guide field `o:preferred_column_name` for the JSON data field to be projected. Specifying your preferred name changes the value of this data-guide field.

If your JSON data has a data guide-enabled search index then you can use procedure `DBMS_JSON.rename_column` to specify your preferred name for the column projected from a given field. Example 22-4 illustrates this. It specifies preferred names for the columns to be projected from various fields, as described in Table 22-4. (The fields are projected as columns when you use procedure `DBMS_JSON.create_view`, `DBMS_JSON.create_view_on_path`, or `DBMS_JSON.add_virtual_columns`.)

Table 22-4 Preferred Names for Some JSON Field Columns

| Field                                                   | JSON Type | Preferred Column Name |
|:--------------------------------------------------------|:----------|:----------------------|
| `PONumber`                                              | `number`  | `PONumber`            |
| `Phone` (phone as string, not object – just the number) | `string`  | `Phone`               |
| `type` (phone type)                                     | `string`  | `PhoneType`           |
| `number` (phone number)                                 | `string`  | `PhoneNumber`         |
| `ItemNumber` (line-item number)                         | `number`  | `ItemNumber`          |
| `Description` (part description)                        | `string`  | `PartDescription`     |

**See Also:**

- JSON Data-Guide Fields for information about the default value of field `o:preferred_column_name` and the possibility of name conflicts when you use `DBMS_JSON.rename_column`

- [Creating a Table With a JSON Column](creating-a-table-with-a-json-column.md) for information about the JSON data referenced here

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.create_view`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.create_view_on_path`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.rename_column`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md)for information about `DBMS_JSON.add_virtual_columns`

Example 22-4 Specifying Preferred Column Names For Some JSON Fields

    BEGIN
      DBMS_JSON.rename_column(
        'J_PURCHASEORDER', 'PO_DOCUMENT', '$.PONumber',
        DBMS_JSON.TYPE_NUMBER, 'PONumber');
      DBMS_JSON.rename_column(
        'J_PURCHASEORDER', 'PO_DOCUMENT', '$.ShippingInstructions.Phone',
        DBMS_JSON.TYPE_STRING, 'Phone');
      DBMS_JSON.rename_column(
        'J_PURCHASEORDER', 'PO_DOCUMENT', '$.ShippingInstructions.Phone.type',
        DBMS_JSON.TYPE_STRING, 'PhoneType');
      DBMS_JSON.rename_column(
        'J_PURCHASEORDER', 'PO_DOCUMENT', '$.ShippingInstructions.Phone.number',
        DBMS_JSON.TYPE_STRING, 'PhoneNumber');
      DBMS_JSON.rename_column(
        'J_PURCHASEORDER', 'PO_DOCUMENT', '$.LineItems.ItemNumber',
        DBMS_JSON.TYPE_NUMBER, 'ItemNumber');
      DBMS_JSON.rename_column(
        'J_PURCHASEORDER', 'PO_DOCUMENT', '$.LineItems.Part.Description',
        DBMS_JSON.TYPE_STRING, 'PartDescription');
    END;
    /

**Parent topic:** JSON Data Guide

### 22.7 Creating a View Over JSON Data Based on Data-Guide Information

Based on data-guide information, you can create a database view whose columns project particular scalar fields present in a set of JSON documents. You can choose the fields to project by editing a hierarchical data guide or by specifying a SQL/JSON path expression and a minimum frequency of field occurrence.

(You can create multiple views based on the same JSON document set, projecting different fields. See Multiple Data Guides Per Document Set.)

You can create a view by projecting JSON fields using SQL/JSON function `json_table` — see [Creating a View Over JSON Data Using JSON_TABLE](function-JSON_TABLE.md). An alternative is to use PL/SQL procedure `DBMS_JSON.create_view` or `DBMS_JSON.create_view_on_path` to create a view by projecting fields that you choose based on available data-guide information.

This information can come from either a hierarchical data guide that includes only the fields to project or from a data guide-enabled JSON search index together with a SQL/JSON path expression and a minimum field frequency.

In the former case, use procedure `create_view`. You can edit a (hierarchical) data guide to specify the fields you want. In this case you do not need a data guide-enabled search index.

In the latter case, use procedure `create_view_on_path`. In this case you need a data guide-enabled search index, but you do not need a data guide. You provide a SQL/JSON path expression and possibly a minimum frequency of occurrence. The fields in the document set that are projected include both:

- All scalar fields that are not under an array.

- All scalar fields present, at any level, in the data that is targeted by a given SQL/JSON path expression.

Regardless of which way you create the view, in addition to the JSON fields that are projected as columns, the non-JSON columns of the table are also columns of the view.

If you use procedure `create_view_on_path` then the `PATH` argument you provide must be a simple SQL/JSON path expression (no filter expression), possibly with relaxation (implicit array wrapping and unwrapping), but with no array steps and no function step. See [SQL/JSON Path Expression Syntax](json-path-expressions.md).

However it is created, the data guide that serves as the basis for a given view definition is static and does not necessarily faithfully reflect the current data in the document set. The fields that are projected for the view are determined when the view is created.

In particular, if you use `create_view_on_path` (which requires a data guide-enabled search index) then what counts are the fields specified by the given path expression and that have at least the given frequency, based on the index data at the time of the view creation.

- Creating a View Over JSON Data Based on a Hierarchical Data Guide
  You can use a hierarchical data guide to create a database view whose columns project specified JSON fields from your documents. The fields projected are those in the data guide. You can edit the data guide to include only the fields that you want to project.
- Creating a View Over JSON Data Based on a Path Expression
  You can use the information in a data guide-enabled JSON search index to create a database view whose columns project JSON fields from your documents. The fields projected are the scalar fields not under an array plus the scalar fields in the data targeted by a specified SQL/JSON path expression.

**Related Topics**

- [Creating a View Over JSON Data Using JSON_TABLE](function-JSON_TABLE.md)

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.create_view`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.create_view_on_path`

**Parent topic:** JSON Data Guide

#### 22.7.1 Creating a View Over JSON Data Based on a Hierarchical Data Guide

You can use a hierarchical data guide to create a database view whose columns project specified JSON fields from your documents. The fields projected are those in the data guide. You can edit the data guide to include only the fields that you want to project.

You can obtain a hierarchical data guide using either PL/SQL function `DBMS_JSON.get_index_dataguide` or SQL function `json_dataguide` with argument `DBMS_JSON.FORMAT_HIERARCHICAL`. In the former case a data guide-enabled JSON search index must be defined on the column of JSON data.

You can edit the data guide obtained to include only specific fields, change the length of given types, or rename fields. The resulting data guide specifies which fields of the JSON data to project as columns of the view.

You use PL/SQL procedure `DBMS_JSON.create_view` to create the view.

Example 22-5 illustrates this using a data guide obtained with `DBMS_JSON.get_index_dataguide`. Example 22-6 illustrates it using a data guide obtained with `json_dataguide` with argument `DBMS_JSON.FORMAT_HIERARCHICAL`.

If you create a view using the data guide obtained with `json_dataguide` then GeoJSON data in your documents is supported. In this case the view column corresponding to the GeoJSON data has SQL data type `SDO_GEOMETRY`. For that you pass constant `DBMS_JSON.GEOJSON` or `DBMS_JSON.GEOJSON+DBMS_JSON.PRETTY` as the third argument to `json_dataguide`.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.create_view`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.get_index_dataguide`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.rename_column`

- [Oracle Database SQL Language Reference](../sqlrf/JSON_DATAGUIDE.md) for information about SQL function `json_dataguide`

- [Oracle Database SQL Language Reference](../arpls/DBMS_JSON.md) for information about PL/SQL constant `DBMS_JSON.FORMAT_HIERARCHICAL`

Example 22-5 Creating a View Using a Hierarchical Data Guide Obtained With GET_INDEX_DATAGUIDE

This example creates a view that projects all of the fields present in the hierarchical data guide that is obtained from the data guide-enabled JSON search index on JSON column `po_document` of table `j_purchaseorder`. (Columns whose names are `italic` in the `describe` command output are those that have been renamed using PL/SQL procedure `DBMS_JSON.rename_column`.)

    EXEC DBMS_JSON.create_view(
           'VIEW1',
           'J_PURCHASEORDER',
           'PO_DOCUMENT',
           DBMS_JSON.get_index_dataguide('J_PURCHASEORDER',
                                         'PO_DOCUMENT',
                                         DBMS_JSON.FORMAT_HIERARCHICAL));

    DESCRIBE view1
     Name                             Null?    Type
     -------------------------------- -------- ---------------------------
     DATE_LOADED                               TIMESTAMP(6) WITH TIME ZONE
     ID                               NOT NULL RAW(16)
     PO_DOCUMENT$User                          VARCHAR2(8)
     PONumber                                  NUMBER
     PO_DOCUMENT$Reference                     VARCHAR2(16)
     PO_DOCUMENT$Requestor                     VARCHAR2(16)
     PO_DOCUMENT$CostCenter                    VARCHAR2(4)
     PO_DOCUMENT$AllowPartialShipment          VARCHAR2(4)
     PO_DOCUMENT$name                          VARCHAR2(16)
     Phone                                     VARCHAR2(16)
     PO_DOCUMENT$city                          VARCHAR2(32)
     PO_DOCUMENT$state                         VARCHAR2(2)
     PO_DOCUMENT$street                        VARCHAR2(32)
     PO_DOCUMENT$country                       VARCHAR2(32)
     PO_DOCUMENT$zipCode                       NUMBER
     PO_DOCUMENT$SpecialInstructions           VARCHAR2(8)
     PO_DOCUMENT$UPCCode                       NUMBER
     PO_DOCUMENT$UnitPrice                     NUMBER
     PartDescription                           VARCHAR2(32)
     PO_DOCUMENT$Quantity                      NUMBER
     ItemNumber                                NUMBER
     PhoneType                                 VARCHAR2(8)
     PhoneNumber                               VARCHAR2(16)

Example 22-6 Creating a View Using a Hierarchical Data Guide Obtained With JSON_DATAGUIDE

This example creates a view that projects all of the fields present in the hierarchical data guide that is obtained by invoking SQL function `json_dataguide` on `po_document` of table `j_purchaseorder`. The second and third arguments passed to `json_dataguide` are used, respectively, to specify that the data guide is to be hierarchical and pretty-printed.

Note that none of the view column names here have the prefix `PO_DOCUMENT$`. That prefix is used only when you use a data guide that is obtained from the information in a data guide-enabled JSON search index.

The data guide returned by `json_dataguide` has only `o:path`, `type`, `o:length`, and `o:preferred_column_name` as its predefined fields. The values of field `o:preferred_column_name` are the same as the field names. (There can of course be no fields holding statistical information, as that can only be stored in an index.)

The view column names come from the values of field `o:preferred_column_name` of the data guide that you pass to `DBMS_JSON.create_view`. By default, the view columns are thus named the same as the projected fields.

Because the columns must be uniquely named in the view, you must ensure that the field names themselves are unique, or else you must edit the data guide returned by `json_dataguide` to add appropriate `o:preferred_column_name` entries that ensure uniqueness. An error is raised by `DBMS_JSON.create_view` if the names for the columns are not unique.

    DECLARE
      dg CLOB;
      BEGIN
        SELECT json_dataguide(po_document,
                              FORMAT DBMS_JSON.FORMAT_HIERARCHICAL,
                              DBMS_JSON.PRETTY)
          INTO dg
          FROM j_purchaseorder
          WHERE extract(YEAR FROM date_loaded) = 2014;
        DBMS_JSON.create_view('MYVIEW', 'J_PURCHASEORDER', 'PO_DOCUMENT', dg);
      END;
    /

    DESCRIBE myview
     Name                 Null?    Type
     -------------------- -------- ---------------------------
     DATE_LOADED                   TIMESTAMP(6) WITH TIME ZONE
     ID                   NOT NULL RAW(16)
     User                          VARCHAR2(8)
     PONumber                      NUMBER
     UPCCode                       NUMBER
     UnitPrice                     NUMBER
     Description                   VARCHAR2(32)
     Quantity                      NUMBER
     ItemNumber                    NUMBER
     Reference                     VARCHAR2(16)
     Requestor                     VARCHAR2(16)
     CostCenter                    VARCHAR2(4)
     AllowPartialShipment          VARCHAR2(4)
     name                          VARCHAR2(16)
     Phone                         VARCHAR2(16)
     type                          VARCHAR2(8)
     number                        VARCHAR2(16)
     city                          VARCHAR2(32)
     state                         VARCHAR2(2)
     street                        VARCHAR2(32)
     country                       VARCHAR2(32)
     zipCode                       NUMBER
     Special Instructions          VARCHAR2(8)

**Parent topic:** Creating a View Over JSON Data Based on Data-Guide Information

#### 22.7.2 Creating a View Over JSON Data Based on a Path Expression

You can use the information in a data guide-enabled JSON search index to create a database view whose columns project JSON fields from your documents. The fields projected are the scalar fields not under an array plus the scalar fields in the data targeted by a specified SQL/JSON path expression.

For example, if the path expression is `$` then all scalar fields are projected, because the root (top) of the document is targeted. Example 22-7 illustrates this. If the path is `$.LineItems.Part` then only the scalar fields that are present (at any level) in the data targeted by `$.LineItems.Part` are projected (in addition to scalar fields elsewhere that are not under an array). Example 22-8 illustrates this.

If you gather statistics on your JSON document set then the data-guide information in a data guide-enabled JSON search index records the frequency of occurrence, across the document set, of each path to a field that is present in a document. When you create the view, you can specify that only the (scalar) fields with a given minimum frequency of occurrence (as a percentage) are to be projected as view columns. You do this by specifying a non-zero value for parameter `FREQUENCY` of procedure `DBMS_JSON.create_view_on_path`.

For example, if you specify the path as `$` and the minimum frequency as `50` then all scalar fields (on any path, since `$` targets the whole document) that occur in at least half (50%) of the documents are projected. Example 22-9 illustrates this.

The value of argument `PATH` is a simple SQL/JSON path expression (no filter expression), possibly with relaxation (implicit array wrapping and unwrapping), but with no array steps and no function step. See [SQL/JSON Path Expression Syntax](json-path-expressions.md).

No frequency filtering is done in either of the following cases — targeted fields are projected regardless of their frequency of occurrence in the documents:

- You never gather statistics information on your set of JSON documents. (No frequency information is included in the data guide-enabled JSON search index.)

- The `FREQUENCY` argument of `DBMS_JSON.create_view_on_path` is zero (0).

**Note:**

When the `FREQUENCY` argument is non-zero, even if you have gathered statistics information on your document set, the index contains no statistical information for any documents added after the most recent gathering of statistics. This means that any fields added after that statistics gathering are ignored (not projected).

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.create_view_on_path`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.rename_column`

Example 22-7 Creating a View That Projects All Scalar Fields

All scalar fields are represented in the view, because the specified path is `$`.

(Columns whose names are `italic` in the `describe` command output are those that have been renamed using PL/SQL procedure `DBMS_JSON.rename_column`. Underlined rows are missing from Example 22-9.)

    EXEC DBMS_JSON.create_view_on_path('VIEW2',
                                       'J_PURCHASEORDER',
                                       'PO_DOCUMENT',
                                       '$');

    DESCRIBE view2;
     Name                              Null?    Type
     --------------------------------  -------- ------------------
     ID                                NOT NULL RAW(16)
     DATE_LOADED                       TIMESTAMP(6) WITH TIME ZONE
     PO_DOCUMENT$User                  VARCHAR2(8)
     PONumber                          NUMBER
     PO_DOCUMENT$Reference             VARCHAR2(16)
     PO_DOCUMENT$Requestor             VARCHAR2(16)
     PO_DOCUMENT$CostCenter            VARCHAR2(4)
     PO_DOCUMENT$AllowPartialShipment  VARCHAR2(4)
     PO_DOCUMENT$name                  VARCHAR2(16)
     Phone                             VARCHAR2(16)
     PO_DOCUMENT$city                  VARCHAR2(32)
     PO_DOCUMENT$state                 VARCHAR2(2)
     PO_DOCUMENT$street                VARCHAR2(32)
     PO_DOCUMENT$country               VARCHAR2(32)
     PO_DOCUMENT$zipCode               NUMBER
     PO_DOCUMENT$SpecialInstructions   VARCHAR2(8)
     PO_DOCUMENT$UPCCode               NUMBER
     PO_DOCUMENT$UnitPrice             NUMBER
     PartDescription                   VARCHAR2(32)
     PO_DOCUMENT$Quantity              NUMBER
     ItemNumber                        NUMBER
     PhoneType                         VARCHAR2(8)
     PhoneNumber                       VARCHAR2(16)

Example 22-8 Creating a View That Projects Scalar Fields Targeted By a Path Expression

Fields `Itemnumber`, `PhoneType`, and `PhoneNumber` are not represented in the view. The only fields that are projected are those scalar fields that are not under an array plus those that are present (at any level) in the data that is targeted by `$.LineItems.Part` (that is, the scalar fields whose paths start with `$.LineItems.Part`). (Columns whose names are `italic` in the `describe` command output are those that have been renamed using PL/SQL procedure `DBMS_JSON.rename_column`.)

    SQL> EXEC DBMS_JSON.create_view_on_path('VIEW4',
                                            'J_PURCHASEORDER',
                                            'PO_DOCUMENT',
                                            '$.LineItems.Part');

    SQL> DESCRIBE view4;
     Name                             Null?    Type
     -------------------------------- -------- ------------------
     ID                               NOT NULL RAW(16)
     DATE_LOADED                      TIMESTAMP(6) WITH TIME ZONE
     PO_DOCUMENT$User                 VARCHAR2(8)
     PONumber                         NUMBER
     PO_DOCUMENT$Reference            VARCHAR2(16)
     PO_DOCUMENT$Requestor            VARCHAR2(16)
     PO_DOCUMENT$CostCenter           VARCHAR2(4)
     PO_DOCUMENT$AllowPartialShipment VARCHAR2(4)
     PO_DOCUMENT$name                 VARCHAR2(16)
     Phone                            VARCHAR2(16)
     PO_DOCUMENT$city                 VARCHAR2(32)
     PO_DOCUMENT$state                VARCHAR2(2)
     PO_DOCUMENT$street               VARCHAR2(32)
     PO_DOCUMENT$country              VARCHAR2(32)
     PO_DOCUMENT$zipCode              NUMBER
     PO_DOCUMENT$SpecialInstructions  VARCHAR2(8)
     PO_DOCUMENT$UPCCode              NUMBER
     PO_DOCUMENT$UnitPrice            NUMBER
     PartDescription                  VARCHAR2(32)

Example 22-9 Creating a View That Projects Scalar Fields Having a Given Frequency

All scalar fields that occur in all (100%) of the documents are represented in the view. Field `AllowPartialShipment` does not occur in all of the documents, so there is no column `PO_DOCUMENT$AllowPartialShipment` in the view. Similarly for fields `Phone`, `PhoneType`, and `PhoneNumber`.

(Columns whose names are `italic` in the `describe` command output are those that have been renamed using PL/SQL procedure `DBMS_JSON.rename_column`.)

    SQL> EXEC DBMS_JSON.create_view_on_path('VIEW3',
                                            'J_PURCHASEORDER',
                                            'PO_DOCUMENT',
                                            '$',
                                            100);

    SQL> DESCRIBE view3;
     Name                             Null?    Type
     -------------------------------- -------- ------------------
     ID                               NOT NULL RAW(16)
     DATE_LOADED                      TIMESTAMP(6) WITH TIME ZONE
     PO_DOCUMENT$User                 VARCHAR2(8)
     PONumber                         NUMBER
     PO_DOCUMENT$Reference            VARCHAR2(16)
     PO_DOCUMENT$Requestor            VARCHAR2(16)
     PO_DOCUMENT$CostCenter           VARCHAR2(4)
     PO_DOCUMENT$name                 VARCHAR2(16)
     PO_DOCUMENT$city                 VARCHAR2(32)
     PO_DOCUMENT$state                VARCHAR2(2)
     PO_DOCUMENT$street               VARCHAR2(32)
     PO_DOCUMENT$country              VARCHAR2(32)
     PO_DOCUMENT$zipCode              NUMBER
     PO_DOCUMENT$SpecialInstructions  VARCHAR2(8)
     PO_DOCUMENT$UPCCode              NUMBER
     PO_DOCUMENT$UnitPrice            NUMBER
     PartDescription                  VARCHAR2(32)
     PO_DOCUMENT$Quantity             NUMBER
     ItemNumber                       NUMBER

**Related Topics**

- Specifying a Preferred Name for a Field Column
- [SQL/JSON Path Expressions](json-path-expressions.md)

**Parent topic:** Creating a View Over JSON Data Based on Data-Guide Information

### 22.8 Adding and Dropping Virtual Columns For JSON Fields Based on Data-Guide Information

Based on data-guide information for a JSON column, you can project scalar fields from that JSON data as virtual columns in the same table. The scalar fields projected are those that are not under an array.

You can do all of the following with a virtual column, with the aim of improving performance:

- Build an index on it.

- Gather statistics on it for the optimizer.

- Load it into the In-Memory Column Store (IM column store).

**Note:**

Virtual columns, like columns in general, are subject to the 1000-column limit for a given table.

You use PL/SQL procedure `DBMS_JSON.add_virtual_columns` to add virtual columns based on data-guide information for a JSON column. Before it adds virtual columns, procedure `add_virtual_columns` first drops any existing virtual columns that were projected from fields in the same JSON column by a previous invocation of `add_virtual_columns` or by data-guide change-trigger procedure `add_vc` (in effect, it does what procedure `DBMS_JSON.drop_virtual_columns` does).

There are two alternative sources of the data-guide information that you provide to procedure `add_virtual_columns`:

- It can come from a hierarchical data guide that you pass as an argument. All scalar fields in the data guide that are not under an array are projected as virtual columns. All other fields in the data guide are ignored (not projected).

  In this case, you can edit the data guide before passing it, so that it specifies the scalar fields (not under an array) that you want projected. You do not need a data guide-enabled search index in this case.

- It can come from a data guide-enabled JSON search index.

  In this case, you can specify, as the value of argument `FREQUENCY` to procedure `add_virtual_columns`, a minimum frequency of occurrence for the scalar fields to be projected. You need a data guide-enabled search index in this case, but you do not need a data guide.

You can also specify that added virtual columns be hidden. The SQL `describe` command does not list hidden columns.

- If you pass a (hierarchical) data guide to `add_virtual_columns` then you can specify projection of particular scalar fields (not under an array) as hidden virtual columns by adding `"o:hidden": ``true` to their descriptions in the data guide.

- If you use a data guide-enabled JSON search index with `add_virtual_columns` then you can specify a PL/SQL `TRUE` value for argument `HIDDEN`, to make all of the added virtual columns be hidden. (The default value of `HIDDEN` is `FALSE`, meaning that the added virtual columns are not hidden.)

<!-- -->

- Adding Virtual Columns For JSON Fields Based on a Hierarchical Data Guide
  You can use a hierarchical data guide to project scalar fields from JSON data as virtual columns in the same table. All scalar fields in the data guide that are not under an array are projected as virtual columns. All other fields in the data guide are ignored (not projected).
- Adding Virtual Columns For JSON Fields Based on a Data Guide-Enabled Search Index
  You can use a data guide-enabled search index for a JSON column to project scalar fields from that JSON data as virtual columns in the same table. Only scalar fields not under an array are projected. You can specify a minimum frequency of occurrence for the fields to be projected.
- Dropping Virtual Columns for JSON Fields Based on Data-Guide Information
  You can use procedure `DBMS_JSON.drop_virtual_columns` to drop all virtual columns that were added for JSON fields in a column of JSON data.

**Related Topics**

- [In-Memory JSON Data](in-memory-json-data.md)

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.add_virtual_columns`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.create_view_on_path`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.drop_virtual_columns`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.rename_column`

**Parent topic:** JSON Data Guide

#### 22.8.1 Adding Virtual Columns For JSON Fields Based on a Hierarchical Data Guide

You can use a hierarchical data guide to project scalar fields from JSON data as virtual columns in the same table. All scalar fields in the data guide that are not under an array are projected as virtual columns. All other fields in the data guide are ignored (not projected).

You can obtain a hierarchical data guide using PL/SQL function `DBMS_JSON.get_index_dataguide`. A data guide-enabled JSON search index must be defined on the column of JSON data.

You can edit the data guide obtained, to include only specific scalar fields (that are not under an array), rename those fields, or change the lengths of their types. The resulting data guide specifies which such fields to project as new virtual columns. Any fields in the data guide that are not scalar fields not under an array are ignored (not projected).

You use PL/SQL procedure `DBMS_JSON.add_virtual_columns` to add the virtual columns to the table that contains the JSON column containing the projected fields. That procedure first drops any existing virtual columns that were projected from fields in the same JSON column by a previous invocation of `add_virtual_columns` or by data-guide change-trigger procedure `add_vc` (in effect, it does what procedure `DBMS_JSON.drop_virtual_columns` does).

Example 22-10 illustrates this. It projects scalar fields that are not under an array, from the data in JSON column `po_document` of table `j_purchaseorder`. The fields projected are those that are indicated in the hierarchical data guide.

Example 22-11 illustrates passing a data-guide argument that specifies the projection of two fields as virtual columns. Data-guide field `o:hidden` is used to hide one of these columns.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.add_virtual_columns`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.drop_virtual_columns`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.get_index_dataguide`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.rename_column`

- [Oracle Database SQL Language Reference](../arpls/DBMS_JSON.md) for information about PL/SQL constant `DBMS_JSON.FORMAT_HIERARCHICAL`

Example 22-10 Adding Virtual Columns That Project JSON Fields Using a Data Guide Obtained With GET_INDEX_DATAGUIDE

In this example the hierarchical data guide is obtained from a data guide-enabled JSON search index on JSON column `po_document`.

The added virtual columns are all of the columns in table `j_purchaseorder` except for `ID`, `DATE_LOADED`, and `PODOCUMENT`.

(Columns whose names are `italic` in the `describe` command output are those that have been renamed using PL/SQL procedure `DBMS_JSON.rename_column`.)

    EXEC DBMS_JSON.add_virtual_columns(
           'J_PURCHASEORDER',
           'PO_DOCUMENT',
           DBMS_JSON.get_index_dataguide('J_PURCHASEORDER',
                                         'PO_DOCUMENT',
                                         DBMS_JSON.FORMAT_HIERARCHICAL));

    DESCRIBE j_purchaseorder;
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     ID                                        NOT NULL RAW(16)
     DATE_LOADED                                        TIMESTAMP(6) WITH TIME ZONE
     PO_DOCUMENT                                        CLOB
     PO_DOCUMENT$User                                   VARCHAR2(8)
     PONumber                                           NUMBER
     PO_DOCUMENT$Reference                              VARCHAR2(16)
     PO_DOCUMENT$Requestor                              VARCHAR2(16)
     PO_DOCUMENT$CostCenter                             VARCHAR2(4)
     PO_DOCUMENT$AllowPartialShipment                   VARCHAR2(4)
     PO_DOCUMENT$name                                   VARCHAR2(16)
     Phone                                              VARCHAR2(16)
     PO_DOCUMENT$city                                   VARCHAR2(32)
     PO_DOCUMENT$state                                  VARCHAR2(2)
     PO_DOCUMENT$street                                 VARCHAR2(32)
     PO_DOCUMENT$country                                VARCHAR2(32)
     PO_DOCUMENT$zipCode                                NUMBER
     PO_DOCUMENT$SpecialInstructions                    VARCHAR2(8)

Example 22-11 Adding Virtual Columns, Hidden and Visible

In this example only two fields are projected as virtual columns: `PO_Number` and `PO_Reference`. The data guide is defined locally as a literal string. Data-guide field `o:hidden` is used here to hide the virtual column for `PO_Reference`. (For `PO_Number` the `o:hidden: false` entry is not needed, as `false` is the default value.)

    DECLARE
      dg CLOB;
    BEGIN
      dg := '{"type" : "object",
              "properties" :
                {"PO_Number"    : {"type" : "number",
                                   "o:length" : 4,
                                   "o:preferred_column_name" : "PO_Number",
                                   "o:hidden" : false},
                 "PO_Reference" : {"type" : "string",
                                   "o:length" : 16,
                                   "o:preferred_column_name" : "PO_Reference",
                                   "o:hidden" : true}}}';
      DBMS_JSON.add_virtual_columns('J_PURCHASEORDER', 'PO_DOCUMENT', dg);
    END;
    /

    DESCRIBE j_purchaseorder;
     Name        Null?    Type
     ----------- -------- ---------------------------
     ID          NOT NULL RAW(16)
     DATE_LOADED          TIMESTAMP(6) WITH TIME ZONE
     PO_DOCUMENT          CLOB
     PO_Number            NUMBER

    SELECT column_name FROM user_tab_columns
      WHERE table_name = 'J_PURCHASEORDER' ORDER BY 1;
    COLUMN_NAME
    -----------
    DATE_LOADED
    ID
    PO_DOCUMENT
    PO_Number
    PO_Reference

    5 rows selected.

**Parent topic:** Adding and Dropping Virtual Columns For JSON Fields Based on Data-Guide Information

#### 22.8.2 Adding Virtual Columns For JSON Fields Based on a Data Guide-Enabled Search Index

You can use a data guide-enabled search index for a JSON column to project scalar fields from that JSON data as virtual columns in the same table. Only scalar fields not under an array are projected. You can specify a minimum frequency of occurrence for the fields to be projected.

You use procedure `DBMS_JSON.add_virtual_columns` to add the virtual columns.

Example 22-12 illustrates this. It projects all scalar fields that are not under an array to table `j_purchaseorder` as virtual columns.

If you gather statistics on the documents in the JSON column where you want to project fields then the data-guide information in the data guide-enabled JSON search index records the frequency of occurrence, across that document set, of each field in a document.

When you add virtual columns you can specify that only those fields with a given minimum frequency of occurrence are to be projected.

You do this by specifying a non-zero value for parameter `FREQUENCY` of procedure `add_virtual_columns`. Zero is the default value, so if you do not include argument `FREQUENCY` then all scalar fields (not under an array) are projected. The frequency of a given field is the number of documents containing that field divided by the total number of documents in the JSON column, expressed as a percentage.

Example 22-13 projects all scalars (not under an array) that occur in all (100%) of the documents as virtual columns.

If you want to hide all of the added virtual columns then specify a `TRUE` value for argument `HIDDEN`. (The default value of parameter `HIDDEN` is `FALSE`, meaning that the added virtual columns are not hidden.)

Example 22-14 projects, as hidden virtual columns, the scalar fields (not under an array) that occur in all (100%) of the documents.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.add_virtual_columns`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.rename_column`

Example 22-12 Projecting All Scalar Fields Not Under an Array as Virtual Columns

The added virtual columns are all of the columns in table `j_purchaseorder` except for `ID`, `DATE_LOADED`, and `PODOCUMENT`. This is because no `FREQUENCY` argument is passed to `add_virtual_columns`, so all scalar fields (that are not under an array) are projected.

(Columns whose names are `italic` in the `describe` command output are those that have been renamed using PL/SQL procedure `DBMS_JSON.rename_column`.)

    EXEC DBMS_JSON.add_virtual_columns('J_PURCHASEORDER', 'PO_DOCUMENT');

    DESCRIBE j_purchaseorder;
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     ID                                        NOT NULL RAW(16)
     DATE_LOADED                                        TIMESTAMP(6) WITH TIME ZONE
     PO_DOCUMENT                                        CLOB
     PO_DOCUMENT$User                                   VARCHAR2(8)
     PONumber                                           NUMBER
     PO_DOCUMENT$Reference                              VARCHAR2(16)
     PO_DOCUMENT$Requestor                              VARCHAR2(16)
     PO_DOCUMENT$CostCenter                             VARCHAR2(4)
     PO_DOCUMENT$AllowPartialShipment                   VARCHAR2(4)
     PO_DOCUMENT$name                                   VARCHAR2(16)
     Phone                                              VARCHAR2(16)
     PO_DOCUMENT$city                                   VARCHAR2(32)
     PO_DOCUMENT$state                                  VARCHAR2(2)
     PO_DOCUMENT$street                                 VARCHAR2(32)
     PO_DOCUMENT$country                                VARCHAR2(32)
     PO_DOCUMENT$zipCode                                NUMBER
     PO_DOCUMENT$SpecialInstructions                    VARCHAR2(8)

Example 22-13 Projecting Scalar Fields With a Minimum Frequency as Virtual Columns

All scalar fields that occur in all (100%) of the documents are projected as virtual columns. The result is the same as that for Example 22-12, except that fields `AllowPartialShipment` and `Phone` are not projected, because they do not occur in 100% of the documents.

(Columns whose names are `italic` in the `describe` command output are those that have been renamed using PL/SQL procedure `DBMS_JSON.rename_column`.)

    EXEC DBMS_JSON.add_virtual_columns('J_PURCHASEORDER', 'PO_DOCUMENT', 100);

    DESCRIBE j_purchaseorder;
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     ID                                        NOT NULL RAW(16)
     DATE_LOADED                                        TIMESTAMP(6) WITH TIME ZONE
     PO_DOCUMENT                                        CLOB
     PO_DOCUMENT$User                                   VARCHAR2(8)
     PONumber                                           NUMBER
     PO_DOCUMENT$Reference                              VARCHAR2(16)
     PO_DOCUMENT$Requestor                              VARCHAR2(16)
     PO_DOCUMENT$CostCenter                             VARCHAR2(4)
     PO_DOCUMENT$name                                   VARCHAR2(16)
     PO_DOCUMENT$city                                   VARCHAR2(32)
     PO_DOCUMENT$state                                  VARCHAR2(2)
     PO_DOCUMENT$street                                 VARCHAR2(32)
     PO_DOCUMENT$country                                VARCHAR2(32)
     PO_DOCUMENT$zipCode                                NUMBER
     PO_DOCUMENT$SpecialInstructions                    VARCHAR2(8)

Example 22-14 Projecting Scalar Fields With a Minimum Frequency as Hidden Virtual Columns

The result is the same as that for Example 22-13, except that all of the added virtual columns are hidden. (The query of view `USER_TAB_COLUMNS` shows that the virtual columns were in fact added.)

    EXEC DBMS_JSON.add_virtual_columns('J_PURCHASEORDER', 'PO_DOCUMENT', 100, TRUE);

    DESCRIBE j_purchaseorder;
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     ID                                        NOT NULL RAW(16)
     DATE_LOADED                                        TIMESTAMP(6) WITH TIME ZONE
     PO_DOCUMENT                                        CLOB

    SELECT column_name FROM user_tab_columns
      WHERE table_name = 'J_PURCHASEORDER'
      ORDER BY 1;

    COLUMN_NAME
    -----------
    DATE_LOADED
    ID
    PONumber
    PO_DOCUMENT
    PO_DOCUMENT$CostCenter
    PO_DOCUMENT$Reference
    PO_DOCUMENT$Requestor
    PO_DOCUMENT$SpecialInstructions
    PO_DOCUMENT$User
    PO_DOCUMENT$city
    PO_DOCUMENT$country
    PO_DOCUMENT$name
    PO_DOCUMENT$state
    PO_DOCUMENT$street
    PO_DOCUMENT$zipCode

**Parent topic:** Adding and Dropping Virtual Columns For JSON Fields Based on Data-Guide Information

#### 22.8.3 Dropping Virtual Columns for JSON Fields Based on Data-Guide Information

You can use procedure `DBMS_JSON.drop_virtual_columns` to drop all virtual columns that were added for JSON fields in a column of JSON data.

Procedure `DBMS_JSON.drop_virtual_columns` drops all virtual columns that were projected from fields in a given JSON column by an invocation of `add_virtual_columns` or by data-guide change-trigger procedure `add_vc`. Example 22-15 illustrates this for fields projected from column `po_document` of table `j_purchaseorder`.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.add_virtual_columns`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.drop_virtual_columns`

Example 22-15 Dropping Virtual Columns Projected From JSON Fields

    EXEC DBMS_JSON.drop_virtual_columns('J_PURCHASEORDER', 'PO_DOCUMENT');

**Parent topic:** Adding and Dropping Virtual Columns For JSON Fields Based on Data-Guide Information

### 22.9 Change Triggers For Data Guide-Enabled Search Index

When JSON data changes, some information in a data guide-enabled JSON search index is automatically updated. You can specify a procedure whose invocation is triggered whenever this happens. You can define your own PL/SQL procedure for this, or you can use the predefined change-trigger procedure `add_vc`.

The data-guide information in a data guide-enabled JSON search index records structure, type, and possibly statistical information about a set of JSON documents. Except for the statistical information, which is updated only when you gather statistics, relevant changes in the document set are automatically reflected in the data-guide information stored in the index.

You can define a PL/SQL procedure whose invocation is automatically triggered by such an index update. The invocation occurs when the index is updated. Any errors that occur during the execution of the procedure are ignored.

You can use the predefined change-trigger procedure `add_vc` to automatically add virtual columns that project JSON fields from the document set or to modify existing such columns, as needed. The virtual columns added by `add_vc` follow the same naming rules as those you add by invoking procedure `DBMS_JSON.add_virtual_columns` for a JSON column that has a data guide-enabled search index.

In either case, any error that occurs during the execution of the procedure is ignored.

Unlike `DBMS_JSON.add_virtual_columns`, `add_vc` does not first drop any existing virtual columns that were projected from fields in the same JSON column. To drop virtual columns projected from fields in the same JSON column by `add_vc` or by `add_virtual_columns`, use procedure `DBMS_JSON.drop_virtual_columns`.

You specify the use of a trigger for data-guide changes by using the keywords `DATAGUIDE ON CHANGE` in the `PARAMETERS` clause when you create or alter a JSON search index. Only one change trigger is allowed per index: altering an index to specify a trigger automatically replaces any previous trigger for it.

Example 22-16 alters existing JSON search index `po_search_idx` to use procedure `add_vc`.

Example 22-16 Adding Virtual Columns Automatically With Change Trigger ADD_VC

This example adds predefined change trigger `add_vc` to JSON search index `po_search_idx`.

It first drops any existing virtual columns that were projected from fields in JSON column `po_document` either by procedure `DBMS_JSON.add_virtual_columns` or by a pre-existing `add_vc` change trigger for the same JSON search index.

Then it alters the search index to add change trigger `add_vc` (if it was already present then this is has no effect).

Finally, it inserts a new document that provokes a change in the data guide. Two virtual columns are added to the table, for the two scalar fields not under an array.

    EXEC DBMS_JSON.drop_virtual_columns('J_PURCHASEORDER', 'PO_DOCUMENT');

    ALTER INDEX po_search_idx REBUILD PARAMETERS ('DATAGUIDE ON CHANGE add_vc');

    INSERT INTO j_purchaseorder
      VALUES (
        SYS_GUID(),
        to_date('30-JUN-2015'),
        '{"PO_Number"     : 4230,
          "PO_Reference"  : "JDEER-20140421",
          "PO_LineItems"  : [{"Part_Number"  : 230912362345,
                              "Quantity"     : 3.0}]}');

    DESCRIBE j_purchaseorder;
     Name                      Null?    Type
     ------------------------- -------- ----------------------------
     ID                        NOT NULL RAW(16)
     DATE_LOADED                        TIMESTAMP(6) WITH TIME ZONE
     PO_DOCUMENT                        CLOB
     PO_DOCUMENT$PO_Number              NUMBER
     PO_DOCUMENT$PO_Reference           VARCHAR2(16)

- User-Defined Data-Guide Change Triggers
  You can define a procedure whose invocation is triggered automatically whenever a given data guide-enabled JSON search index is updated. Any errors that occur during the execution of the procedure are ignored.

**Related Topics**

- Adding and Dropping Virtual Columns For JSON Fields Based on Data-Guide Information

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.add_virtual_columns`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.drop_virtual_columns`

**Parent topic:** JSON Data Guide

#### 22.9.1 User-Defined Data-Guide Change Triggers

You can define a procedure whose invocation is triggered automatically whenever a given data guide-enabled JSON search index is updated. Any errors that occur during the execution of the procedure are ignored.

Example 22-17 illustrates this.

A user-defined procedure specified with keywords `DATAGUIDE ON CHANGE` in a JSON search index `PARAMETERS` clause must accept the parameters specified in Table 22-5.

Table 22-5 Parameters of a User-Defined Data-Guide Change Trigger Procedure

| Name              | Type       | Description                                                                                                                                                                                                                                                                                     |
|:------------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `table_name`      | `VARCHAR2` | Name of the table containing column `column_name`.                                                                                                                                                                                                                                              |
| `column_name`     | `VARCHAR2` | Name of a JSON column that has a data guide-enabled JSON search index.                                                                                                                                                                                                                          |
| `path`            | `VARCHAR2` | A SQL/JSON path expression that targets a particular field in the data in column `column_name`. This path is affected by the index change that triggered the procedure invocation. For example, the index change involved adding this path or changing its type value or its type-length value. |
| `new_type`        | `NUMBER`   | A new type for the given path.                                                                                                                                                                                                                                                                  |
| `new_type_length` | `NUMBER`   | A new type length for the given path.                                                                                                                                                                                                                                                           |

Example 22-17 Tracing Data-Guide Updates With a User-Defined Change Trigger

This example first drops any existing virtual columns projected from fields in JSON column `po_document`.

It then defines PL/SQL procedure `my_dataguide_trace`, which prints the names of the table and JSON column, together with the path, type and length fields of the added virtual column. It then alters JSON search index `po_search_idx` to specify that this procedure be invoked as a change trigger for updates to the data-guide information in the index.

It then inserts a new document that provokes a change in the data guide, which triggers the output of trace information.

Note that the `TYPE` argument to the procedure must be a number that is one of the `DBMS_JSON` constants for a JSON type. The procedure tests the argument and outputs a user-friendly string in place of the number.

    EXEC DBMS_JSON.drop_virtual_columns('J_PURCHASEORDER', 'PO_DOCUMENT');

    CREATE OR REPLACE PROCEDURE my_dataguide_trace(tableName VARCHAR2,
                                                   jcolName  VARCHAR2,
                                                   path      VARCHAR2,
                                                   type      NUMBER,
                                                   tlength   NUMBER)
      IS
        typename VARCHAR2(10);
      BEGIN
        IF    (type = DBMS_JSON.TYPE_NULL)    THEN typename := 'null';
        ELSIF (type = DBMS_JSON.TYPE_BOOLEAN) THEN typename := 'boolean';
        ELSIF (type = DBMS_JSON.TYPE_NUMBER)  THEN typename := 'number';
        ELSIF (type = DBMS_JSON.TYPE_STRING)  THEN typename := 'string';
        ELSIF (type = DBMS_JSON.TYPE_OBJECT)  THEN typename := 'object';
        ELSIF (type = DBMS_JSON.TYPE_ARRAY)   THEN typename := 'array';
        ELSE                                       typename := 'unknown';
        END IF;
        DBMS_OUTPUT.put_line('Updating ' || tableName || '(' || jcolName
                             || '): Path = ' || path || ', Type = ' || type
                             || ', Type Name = ' || typename
                             || ', Type Length = ' || tlength);
      END;
    /

    ALTER INDEX po_search_idx REBUILD
      PARAMETERS ('DATAGUIDE ON CHANGE my_dataguide_trace');

    INSERT INTO j_purchaseorder
      VALUES (
        SYS_GUID(),
        to_date('30-MAR-2016'),
        '{"PO_ID"     : 4230,
          "PO_Ref"  : "JDEER-20140421",
          "PO_Items"  : [{"Part_No"       : 98981327234,
                          "Item_Quantity" : 13}]}');

    COMMIT;
    Updating J_PURCHASEORDER(PO_DOCUMENT):
      Path = $.PO_ID, Type = 3, Type Name = number, Type Length = 4
    Updating J_PURCHASEORDER(PO_DOCUMENT):
      Path = $.PO_Ref, Type = 4, Type Name = string, Type Length = 16
    Updating J_PURCHASEORDER(PO_DOCUMENT):
      Path = $.PO_Items, Type = 6, Type Name = array, Type Length = 64
    Updating J_PURCHASEORDER(PO_DOCUMENT):
      Path = $.PO_Items.Part_No, Type = 3, Type Name = number, Type Length = 16
    Updating J_PURCHASEORDER(PO_DOCUMENT):
      Path = $.PO_Items.Item_Quantity, Type = 3, Type Name = number, Type Length = 2

    Commit complete.

**See Also:**

- [Oracle Database SQL Language Reference](../arpls/DBMS_JSON.md) for information about PL/SQL constants `TYPE_NULL`, `TYPE_BOOLEAN`, `TYPE_NUMBER`, `TYPE_STRING`, `TYPE_OBJECT`, and `TYPE_ARRAY`.

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.drop_virtual_columns`

**Parent topic:** Change Triggers For Data Guide-Enabled Search Index

### 22.10 Multiple Data Guides Per Document Set

A data guide reflects the shape of a given set of JSON documents. If a JSON column contains different types of documents, with different structure or type information, you can create and use different data guides for the different kinds of documents.

#### Data Guides For Different Kinds of JSON Documents

JSON documents need not, and typically do not, follow a prescribed schema. This is true even for documents that are used similarly in a given application; they may differ in structural ways (shape), and field types may differ.

A JSON data guide summarizes the structural and type information of a given set of documents. In general, the more similar the structure and type information of the documents in a given set, the more useful the resulting data guide.

A data guide is created for a given column of JSON data. If the column contains very different kinds of documents (for example, purchase orders and health records) then a single data guide for the column is likely to be of limited use.

One way to address this concern is to put different kinds of JSON documents in different JSON columns. But sometimes other considerations decide in favor of mixing document types in the same column.

In addition, documents of the same general type, which you decide to store in the same column, can nevertheless differ in relatively systematic ways. This includes the case of evolving document shape and type information. For example, the structure of tax-information documents could change from year to year.

When you create a data guide you can decide which information to summarize. And you can thus create different data guides for the same JSON column, to represent different subsets of the document set.

An additional aid in this regard is to have a separate, non-JSON, column in the same table, which is used to label, or categorize, the documents in a JSON column.

In the case of the purchase-order documents used in our examples, let’s suppose that their structure can evolve significantly from year to year, so that column `date_loaded` of table `j_purchaseorder` can be used to group them into subsets of reasonably similar shape. Example 22-18 adds a purchase-order document for 2015, and Example 22-19 adds a purchase-order document for 2016. (Compare with the documents for 2014, which are added in [Example 4-2](creating-a-table-with-a-json-column.md).)

#### Using a SQL Aggregate Function to Create Multiple Data Guides

Oracle SQL function `json_dataguide` is in fact an aggregate function. An aggregate function returns a single result row based on groups of rows, rather than on a single row. It is typically used in a `SELECT` list for a query that has a `GROUP BY` clause, which divides the rows of a queried table or view into groups. The aggregate function applies to each group of rows, returning a single result row for each group. For example, aggregate function `avg` returns the average of a group of values.

Function `json_dataguide` aggregates JSON data to produce a summary, or specification, of it, which is returned in the form of a JSON document. In other words, for each group of JSON documents to which they are applied, they return a data guide.

If you omit `GROUP BY` then this function returns a single data guide that summarizes all of the JSON data in the subject JSON column.

Example 22-20 queries the documents of JSON column `po_document`, grouping them to produce three data guides, one for each year of column `date_loaded`.

Example 22-18 Adding a 2015 Purchase-Order Document

The 2015 purchase-order format uses only part number, reference, and line-items as its top-level fields, and these fields use prefix `PO_`. Each line item contains only a part number and a quantity.

    INSERT INTO j_purchaseorder
      VALUES (
        SYS_GUID(),
        to_date('30-JUN-2015'),
        '{"PO_Number"     : 4230,
          "PO_Reference"  : "JDEER-20140421",
          "PO_LineItems"  : [{"Part_Number"  : 230912362345,
                              "Quantity"     : 3.0}]}');

Example 22-19 Adding a 2016 Purchase-Order Document

The 2016 format uses `PO_ID` instead of `PO_Number`, `PO_Ref` instead of `PO_Reference`, `PO_Items` instead of `PO_LineItems`, `Part_No` instead of `Part_Number`, and `Item_Quantity` instead of `Quantity`.

    INSERT INTO j_purchaseorder
      VALUES (
        SYS_GUID(),
        to_date('30-MAR-2016'),
        '{"PO_ID"     : 4230,
          "PO_Ref"  : "JDEER-20140421",
          "PO_Items"  : [{"Part_No"       : 98981327234,
                          "Item_Quantity" : 13}]}');

Example 22-20 Creating Multiple Data Guides With Aggregate Function JSON_DATAGUIDE

This example uses aggregate SQL function `json_dataguide` to obtain three flat<sup>Foot 1</sup> data guides, one for each year-specific format. The data guide for 2014 is shown only partially — it is the same as the data guide from A Flat Data Guide For Purchase-Order Documents, except that no statistics fields are present. (Data guides returned by functions `json_dataguide` do not contain any statistics fields.

    SELECT extract(YEAR FROM date_loaded), json_dataguide(po_document)
      FROM j_purchaseorder
      GROUP BY extract(YEAR FROM date_loaded)
      ORDER BY extract(YEAR FROM date_loaded) DESC;

    EXTRACT(YEARFROMDATE_LOADED)
    ----------------------------
    JSON_DATAGUIDE(PO_DOCUMENT)
    ---------------------------
                            2016
    [
      {
        "o:path" : "$.PO_ID",
        "type" : "number",
        "o:length" : 4
      },
      {
        "o:path" : "$.PO_Ref",
        "type" : "string",
        "o:length" : 16
      },
      {
        "o:path" : "$.PO_Items",
        "type" : "array",
        "o:length" : 64
      },
      {
        "o:path" : "$.PO_Items.Part_No",
        "type" : "number",
        "o:length" : 16
      },
      {
        "o:path" : "$.PO_Items.Item_Quantity",
        "type" : "number",
        "o:length" : 2
      }
    ]

                            2015
    [
      {
        "o:path" : "$.PO_Number",
        "type" : "number",
        "o:length" : 4
      },
      {
        "o:path" : "$.PO_LineItems",
        "type" : "array",
        "o:length" : 64
      },
      {
        "o:path" : "$.PO_LineItems.Quantity",
        "type" : "number",
        "o:length" : 4
      },
      {
        "o:path" : "$.PO_LineItems.Part_Number",
        "type" : "number",
        "o:length" : 16
      },
      {
        "o:path" : "$.PO_Reference",
        "type" : "string",
        "o:length" : 16
      }
    ]

                            2014
    [
      {
        "o:path" : "$.User",
        "type" : "string",
        "o:length" : 8
      },
      {
        "o:path" : "$.PONumber",
        "type" : "number",
        "o:length" : 4
      },
    ...
      {
        "o:path" : "$.\"Special Instructions\"",
        "type" : "string",
        "o:length" : 8
      }
    ]

    3 rows selected.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/JSON_DATAGUIDE.md) for information about SQL function `json_dataguide`

**Parent topic:** JSON Data Guide

### 22.11 Querying a Data Guide

A data guide is information about a set of JSON documents. You can query it from a flat data guide that you obtain using either Oracle SQL function `json_dataguide` or PL/SQL function `DBMS_JSON.get_index_dataguide`. In the latter case, a data guide-enabled JSON search index must be defined on the JSON data.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/JSON_DATAGUIDE.md) for information about SQL function `json_dataguide`

- [Oracle Database SQL Language Reference](../sqlrf/JSON_TABLE.md) for information about SQL/JSON function `json_table`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.get_index_dataguide`

- [Oracle Database SQL Language Reference](../arpls/DBMS_JSON.md) for information about PL/SQL constant `DBMS_JSON.FORMAT_FLAT`

Example 22-21 Querying a Data Guide Obtained Using JSON_DATAGUIDE

This example uses SQL/JSON function `json_dataguide` to obtain a flat data guide. It then queries the relational columns projected on the fly by SQL/JSON function `json_table` from fields `o:path`, `type`, and `o:length`. It returns the projected columns ordered lexicographically by the path column created, `jpath`.

    WITH dg_t AS (SELECT json_dataguide(po_document) dg_doc FROM j_purchaseorder)
      SELECT jt.*
        FROM dg_t,
             json_table(dg_doc, '$[*]'
               COLUMNS
                 jpath   VARCHAR2(40) PATH '$."o:path"',
                 type    VARCHAR2(10) PATH '$."type"',
                 tlength NUMBER       PATH '$."o:length"') jt
       ORDER BY jt.jpath;

    JPATH                                    TYPE          TLENGTH
    ---------------------------------------- ------------- -------
    $."Special Instructions"                 string              8
    $.AllowPartialShipment                   boolean             4
    $.CostCenter                             string              4
    $.LineItems                              array             512
    $.LineItems.ItemNumber                   number              1
    $.LineItems.Part                         object            128
    $.LineItems.Part.Description             string             32
    $.LineItems.Part.UPCCode                 number             16
    $.LineItems.Part.UnitPrice               number              8
    $.LineItems.Quantity                     number              4
    $.PONumber                               number              4
    $.PO_LineItems                           array              64
    $.Reference                              string             16
    $.Requestor                              string             16
    $.ShippingInstructions                   object            256
    $.ShippingInstructions.Address           object            128
    $.ShippingInstructions.Address.city      string             32
    $.ShippingInstructions.Address.country   string             32
    $.ShippingInstructions.Address.state     string              2
    $.ShippingInstructions.Address.street    string             32
    $.ShippingInstructions.Address.zipCode   number              8
    $.ShippingInstructions.Phone             array             128
    $.ShippingInstructions.Phone             string             16
    $.ShippingInstructions.Phone.number      string             16
    $.ShippingInstructions.Phone.type        string              8
    $.ShippingInstructions.name              string             16
    $.User                                   string              8

Example 22-22 Querying a Data Guide With Index Data For Paths With Frequency at Least 80%

This example uses PL/SQL function `DBMS_JSON.get_index_dataguide` with format value `DBMS_JSON.FORMAT_FLAT` to obtain a flat data guide from the data-guide information stored in a data guide-enabled JSON search index. It then queries the relational columns projected on the fly from fields `o:path`, `type`, `o:length`, and `o:frequency` by SQL/JSON function `json_table`.

The value of field `o:frequency` is a statistic that records the frequency of occurrence, across the document set, of each field in a document. It is available only if you have gathered statistics on the document set. The frequency of a given field is the number of documents containing that field divided by the total number of documents in the JSON column, expressed as a percentage.

    WITH dg_t AS (SELECT DBMS_JSON.get_index_dataguide('J_PURCHASEORDER',
                                                       'PO_DOCUMENT',
                                                       DBMS_JSON.FORMAT_FLAT) dg_doc
                    FROM DUAL)
     SELECT jt.*
       FROM dg_t,
            json_table(dg_doc, '$[*]'
              COLUMNS
                jpath     VARCHAR2(40) PATH '$."o:path"',
                type      VARCHAR2(10) PATH '$."type"',
                tlength   NUMBER       PATH '$."o:length"',
                frequency NUMBER       PATH '$."o:frequency"') jt
       WHERE jt.frequency > 80;

    JPATH                                    TYPE          TLENGTH  FREQUENCY
    ---------------------------------------- ------------- -------- ---------
    $.User                                   string              8        100
    $.PONumber                               number              4        100
    $.LineItems                              array             512        100
    $.LineItems.Part                         object            128        100
    $.LineItems.Part.UPCCode                 number             16        100
    $.LineItems.Part.UnitPrice               number              8        100
    $.LineItems.Part.Description             string             32        100
    $.LineItems.Quantity                     number              4        100
    $.LineItems.ItemNumber                   number              1        100
    $.Reference                              string             16        100
    $.Requestor                              string             16        100
    $.CostCenter                             string              4        100
    $.ShippingInstructions                   object            256        100
    $.ShippingInstructions.name              string             16        100
    $.ShippingInstructions.Address           object            128        100
    $.ShippingInstructions.Address.city      string             32        100
    $.ShippingInstructions.Address.state     string              2        100
    $.ShippingInstructions.Address.street    string             32        100
    $.ShippingInstructions.Address.country   string             32        100
    $.ShippingInstructions.Address.zipCode   number              8        100
    $."Special Instructions"                 string              8        100

**Related Topics**

- JSON Data-Guide Fields

**Parent topic:** JSON Data Guide

### 22.12 A Flat Data Guide For Purchase-Order Documents

The fields of a sample flat data guide are described. It corresponds to a set of purchase-order documents.

The only JSON Schema keyword used in a flat data guide is `type`. The other fields are all Oracle data-guide fields, which have prefix `o:`.

Example 22-23 shows a flat data guide for the purchase-order documents in table `j_purchaseorder`. Things to note:

- The values of `o:preferred_column_name` use prefix `PO_DOCUMENT$`. This prefix comes from using `DBMS_JSON.get_index_dataguide` to obtain this data guide.

- The value of `o:length` is 8 for path `$.User`, for example, in spite of the fact that the actual lengths of the field values are 5. This is because the value of `o:length` is always a power of two.

- The value of `o:path` for field `Special Instructions` is wrapped in double quotation marks (`"Special Instructions"`) because of the embedded space character.

Example 22-23 Flat Data Guide For Purchase Orders

Paths are `bold`. JSON schema keywords are `italic`. Preferred column names that result from using `DBMS_JSON.rename_column` are also `italic`. The formatting used is similar to that produced by using SQL/JSON function `json_dataguide` with format arguments `DBMS_JSON.FORMAT_FLAT` and `DBMS_JSON.PRETTY`.

Note that fields `o:frequency`, `o:low_value`, `o:high_value`, `o:num_nulls`, and `o:last_analyzed` are present. This can only be because statistics were gathered on the document set. Their values reflect the state as of the last statistics gathering. See Example 22-3 for an example of gathering statistics for this data.

    [
      {
        "o:path": "$.User",
        "type": "string",
        "o:length": 8,
        "o:preferred_column_name": "PO_DOCUMENT$User",
        "o:frequency": 100,
        "o:low_value": "ABULL",
        "o:high_value": "SBELL",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.PONumber",
        "type": "number",
        "o:length": 4,
        "o:preferred_column_name": "PONumber",
        "o:frequency": 100,
        "o:low_value": "672",
        "o:high_value": "1600",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.LineItems",
        "type": "array",
        "o:length": 512,
        "o:preferred_column_name": "PO_DOCUMENT$LineItems",
        "o:frequency": 100,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.LineItems.Part",
        "type": "object",
        "o:length": 128,
        "o:preferred_column_name": "PO_DOCUMENT$Part",
        "o:frequency": 100,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.LineItems.Part.UPCCode",
        "type": "number",
        "o:length": 16,
        "o:preferred_column_name": "PO_DOCUMENT$UPCCode",
        "o:frequency": 100,
        "o:low_value": "13131092899",
        "o:high_value": "717951002396",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.LineItems.Part.UnitPrice",
        "type": "number",
        "o:length": 8,
        "o:preferred_column_name": "PO_DOCUMENT$UnitPrice",
        "o:frequency": 100,
        "o:low_value": "20",
        "o:high_value": "19.95",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.LineItems.Part.Description",
        "type": "string",
        "o:length": 32,
        "o:preferred_column_name": "PartDescription",
        "o:frequency": 100,
        "o:low_value": "Nixon",
        "o:high_value": "Eric Clapton: Best Of 1981-1999",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.LineItems.Quantity",
        "type": "number",
        "o:length": 4,
        "o:preferred_column_name": "PO_DOCUMENT$Quantity",
        "o:frequency": 100,
        "o:low_value": "5",
        "o:high_value": "9.0",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.LineItems.ItemNumber",
        "type": "number",
        "o:length": 1,
        "o:preferred_column_name": "ItemNumber",
        "o:frequency": 100,
        "o:low_value": "1",
        "o:high_value": "3",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.Reference",
        "type": "string",
        "o:length": 16,
        "o:preferred_column_name": "PO_DOCUMENT$Reference",
        "o:frequency": 100,
        "o:low_value": "ABULL-20140421",
        "o:high_value": "SBELL-20141017",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.Requestor",
        "type": "string",
        "o:length": 16,
        "o:preferred_column_name": "PO_DOCUMENT$Requestor",
        "o:frequency": 100,
        "o:low_value": "Sarah Bell",
        "o:high_value": "Alexis Bull",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.CostCenter",
        "type": "string",
        "o:length": 4,
        "o:preferred_column_name": "PO_DOCUMENT$CostCenter",
        "o:frequency": 100,
        "o:low_value": "A50",
        "o:high_value": "A50",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.AllowPartialShipment",
        "type": "boolean",
        "o:length": 4,
        "o:preferred_column_name": "PO_DOCUMENT$AllowPartialShipment",
        "o:frequency": 50,
        "o:low_value": "true",
        "o:high_value": "true",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.ShippingInstructions",
        "type": "object",
        "o:length": 256,
        "o:preferred_column_name": "PO_DOCUMENT$ShippingInstructions",
        "o:frequency": 100,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.ShippingInstructions.name",
        "type": "string",
        "o:length": 16,
        "o:preferred_column_name": "PO_DOCUMENT$name",
        "o:frequency": 100,
        "o:low_value": "Sarah Bell",
        "o:high_value": "Alexis Bull",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.ShippingInstructions.Phone",
        "type": "string",
        "o:length": 16,
        "o:preferred_column_name": "Phone",
        "o:frequency": 50,
        "o:low_value": "983-555-6509",
        "o:high_value": "983-555-6509",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.ShippingInstructions.Phone",
        "type": "array",
        "o:length": 128,
        "o:preferred_column_name": "PO_DOCUMENT$Phone_1",
        "o:frequency": 50,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.ShippingInstructions.Phone.type",
        "type": "string",
        "o:length": 8,
        "o:preferred_column_name": "PhoneType",
        "o:frequency": 50,
        "o:low_value": "Mobile",
        "o:high_value": "Office",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.ShippingInstructions.Phone.number",
        "type": "string",
        "o:length": 16,
        "o:preferred_column_name": "PhoneNumber",
        "o:frequency": 50,
        "o:low_value": "415-555-1234",
        "o:high_value": "909-555-7307",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.ShippingInstructions.Address",
        "type": "object",
        "o:length": 128,
        "o:preferred_column_name": "PO_DOCUMENT$Address",
        "o:frequency": 100,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.ShippingInstructions.Address.city",
        "type": "string",
        "o:length": 32,
        "o:preferred_column_name": "PO_DOCUMENT$city",
        "o:frequency": 100,
        "o:low_value": "South San Francisco",
        "o:high_value": "South San Francisco",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.ShippingInstructions.Address.state",
        "type": "string",
        "o:length": 2,
        "o:preferred_column_name": "PO_DOCUMENT$state",
        "o:frequency": 100,
        "o:low_value": "CA",
        "o:high_value": "CA",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.ShippingInstructions.Address.street",
        "type": "string",
        "o:length": 32,
        "o:preferred_column_name": "PO_DOCUMENT$street",
        "o:frequency": 100,
        "o:low_value": "200 Sporting Green",
        "o:high_value": "200 Sporting Green",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.ShippingInstructions.Address.country",
        "type": "string",
        "o:length": 32,
        "o:preferred_column_name": "PO_DOCUMENT$country",
        "o:frequency": 100,
        "o:low_value": "United States of America",
        "o:high_value": "United States of America",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.ShippingInstructions.Address.zipCode",
        "type": "number",
        "o:length": 8,
        "o:preferred_column_name": "PO_DOCUMENT$zipCode",
        "o:frequency": 100,
        "o:low_value": "99236",
        "o:high_value": "99236",
        "o:num_nulls": 0,
        "o:last_analyzed": "2016-03-31T12:17:53"
      },
      {
        "o:path": "$.\"Special Instructions\"",
        "type": "string",
        "o:length": 8,
        "o:preferred_column_name": "PO_DOCUMENT$SpecialInstructions",
        "o:frequency": 100,
        "o:low_value": "Courier",
        "o:high_value": "Courier",
        "o:num_nulls": 1,
        "o:last_analyzed": "2016-03-31T12:17:53"
      }
    ]

**Related Topics**

- JSON Data-Guide Fields
- Specifying a Preferred Name for a Field Column

**See Also:**

- [Example 4-2](creating-a-table-with-a-json-column.md)

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.get_index_dataguide`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.rename_column`

**Parent topic:** JSON Data Guide

### 22.13 A Hierarchical Data Guide For Purchase-Order Documents

The fields of a sample hierarchical data guide are described. It corresponds to a set of purchase-order documents.

Example 22-24 shows a hierarchical data guide for the purchase-order documents in table `j_purchaseorder`.

Example 22-24 Hierarchical Data Guide For Purchase Orders

Field names are `bold`. JSON Schema keywords are `italic`. Preferred column names that result from using `DBMS_JSON.rename_column` are also `italic`. The formatting used is similar to that produced by using SQL/JSON function `json_dataguide` with format arguments `DBMS_JSON.FORMAT_HIERARCHICAL` and `DBMS_JSON.PRETTY`.

Note that fields `o:frequency`, `o:low_value`, `o:high_value`, `o:num_nulls`, and `o:last_analyzed` are present in this example. This can only be because statistics were gathered on the document set. Their values reflect the state as of the last statistics gathering. See Example 22-3 for an example of gathering statistics for this data.

    {
      "type": "object",
      "properties": {
        "User": {
          "type": "string",
          "o:length": 8,
          "o:preferred_column_name": "PO_DOCUMENT$User",
          "o:frequency": 100,
          "o:low_value": "ABULL",
          "o:high_value": "SBELL",
          "o:num_nulls": 0,
          "o:last_analyzed": "2016-03-31T12:17:53"
        },
        "PONumber": {
          "type": "number",
          "o:length": 4,
          "o:preferred_column_name": "PONumber",
          "o:frequency": 100,
          "o:low_value": "672",
          "o:high_value": "1600",
          "o:num_nulls": 0,
          "o:last_analyzed": "2016-03-31T12:17:53"
        },
        "LineItems": {
          "type": "array",
          "o:length": 512,
          "o:preferred_column_name": "PO_DOCUMENT$LineItems",
          "o:frequency": 100,
          "o:last_analyzed": "2016-03-31T12:17:53",
          "items": {
            "properties": {
              "Part": {
                "type": "object",
                "o:length": 128,
                "o:preferred_column_name": "PO_DOCUMENT$Part",
                "o:frequency": 100,
                "o:last_analyzed": "2016-03-31T12:17:53",
                "properties": {
                  "UPCCode": {
                    "type": "number",
                    "o:length": 16,
                    "o:preferred_column_name": "PO_DOCUMENT$UPCCode",
                    "o:frequency": 100,
                    "o:low_value": "13131092899",
                    "o:high_value": "717951002396",
                    "o:num_nulls": 0,
                    "o:last_analyzed": "2016-03-31T12:17:53"
                  },
                  "UnitPrice": {
                    "type": "number",
                    "o:length": 8,
                    "o:preferred_column_name": "PO_DOCUMENT$UnitPrice",
                    "o:frequency": 100,
                    "o:low_value": "20",
                    "o:high_value": "19.95",
                    "o:num_nulls": 0,
                    "o:last_analyzed": "2016-03-31T12:17:53"
                  },
                  "Description": {
                    "type": "string",
                    "o:length": 32,
                    "o:preferred_column_name": "PartDescription",
                    "o:frequency": 100,
                    "o:low_value": "Nixon",
                    "o:high_value": "Eric Clapton: Best Of 1981-1999",
                    "o:num_nulls": 0,
                    "o:last_analyzed": "2016-03-31T12:17:53"
                  }
                }
              },
              "Quantity": {
                "type": "number",
                "o:length": 4,
                "o:preferred_column_name": "PO_DOCUMENT$Quantity",
                "o:frequency": 100,
                "o:low_value": "5",
                "o:high_value": "9.0",
                "o:num_nulls": 0,
                "o:last_analyzed": "2016-03-31T12:17:53"
              },
              "ItemNumber": {
                "type": "number",
                "o:length": 1,
                "o:preferred_column_name": "ItemNumber",
                "o:frequency": 100,
                "o:low_value": "1",
                "o:high_value": "3",
                "o:num_nulls": 0,
                "o:last_analyzed": "2016-03-31T12:17:53"
              }
            }
          }
        },
        "Reference": {
          "type": "string",
          "o:length": 16,
          "o:preferred_column_name": "PO_DOCUMENT$Reference",
          "o:frequency": 100,
          "o:low_value": "ABULL-20140421",
          "o:high_value": "SBELL-20141017",
          "o:num_nulls": 0,
          "o:last_analyzed": "2016-03-31T12:17:53"
        },
        "Requestor": {
          "type": "string",
          "o:length": 16,
          "o:preferred_column_name": "PO_DOCUMENT$Requestor",
          "o:frequency": 100,
          "o:low_value": "Sarah Bell",
          "o:high_value": "Alexis Bull",
          "o:num_nulls": 0,
          "o:last_analyzed": "2016-03-31T12:17:53"
        },
        "CostCenter": {
          "type": "string",
          "o:length": 4,
          "o:preferred_column_name": "PO_DOCUMENT$CostCenter",
          "o:frequency": 100,
          "o:low_value": "A50",
          "o:high_value": "A50",
          "o:num_nulls": 0,
          "o:last_analyzed": "2016-03-31T12:17:53"
        },
        "AllowPartialShipment": {
          "type": "boolean",
          "o:length": 4,
          "o:preferred_column_name": "PO_DOCUMENT$AllowPartialShipment",
          "o:frequency": 50,
          "o:last_analyzed": "2016-03-31T12:17:53"
        },
        "ShippingInstructions": {
          "type": "object",
          "o:length": 256,
          "o:preferred_column_name": "PO_DOCUMENT$ShippingInstructions",
          "o:frequency": 100,
          "o:last_analyzed": "2016-03-31T12:17:53",
          "properties": {
            "name": {
              "type": "string",
              "o:length": 16,
              "o:preferred_column_name": "PO_DOCUMENT$name",
              "o:frequency": 100,
              "o:low_value": "Sarah Bell",
              "o:high_value": "Alexis Bull",
              "o:num_nulls": 0,
              "o:last_analyzed": "2016-03-31T12:17:53"
            },
            "Phone": {
              "oneOf": [
                {
                  "type": "string",
                  "o:length": 16,
                  "o:preferred_column_name": "Phone",
                  "o:frequency": 50,
                  "o:low_value": "983-555-6509",
                  "o:high_value": "983-555-6509",
                  "o:num_nulls": 0,
                  "o:last_analyzed": "2016-03-31T12:17:53"
                },
                {
                  "type": "array",
                  "o:length": 128,
                  "o:preferred_column_name": "PO_DOCUMENT$Phone_1",
                  "o:frequency": 50,
                  "o:last_analyzed": "2016-03-31T12:17:53",
                  "items": {
                    "properties": {
                      "type": {
                        "type": "string",
                        "o:length": 8,
                        "o:preferred_column_name": "PhoneType",
                        "o:frequency": 50,
                        "o:low_value": "Mobile",
                        "o:high_value": "Office",
                        "o:num_nulls": 0,
                        "o:last_analyzed": "2016-03-31T12:17:53"
                      },
                      "number": {
                        "type": "string",
                        "o:length": 16,
                        "o:preferred_column_name": "PhoneNumber",
                        "o:frequency": 50,
                        "o:low_value": "415-555-1234",
                        "o:high_value": "909-555-7307",
                        "o:num_nulls": 0,
                        "o:last_analyzed": "2016-03-31T12:17:53"
                      }
                    }
                  }
                }
              ]
            },
            "Address": {
              "type": "object",
              "o:length": 128,
              "o:preferred_column_name": "PO_DOCUMENT$Address",
              "o:frequency": 100,
              "o:last_analyzed": "2016-03-31T12:17:53",
              "properties": {
                "city": {
                  "type": "string",
                  "o:length": 32,
                  "o:preferred_column_name": "PO_DOCUMENT$city",
                  "o:frequency": 100,
                  "o:low_value": "South San Francisco",
                  "o:high_value": "South San Francisco",
                  "o:num_nulls": 0,
                  "o:last_analyzed": "2016-03-31T12:17:53"
                },
                "state": {
                  "type": "string",
                  "o:length": 2,
                  "o:preferred_column_name": "PO_DOCUMENT$state",
                  "o:frequency": 100,
                  "o:low_value": "CA",
                  "o:high_value": "CA",
                  "o:num_nulls": 0,
                  "o:last_analyzed": "2016-03-31T12:17:53"
                },
                "street": {
                  "type": "string",
                  "o:length": 32,
                  "o:preferred_column_name": "PO_DOCUMENT$street",
                  "o:frequency": 100,
                  "o:low_value": "200 Sporting Green",
                  "o:high_value": "200 Sporting Green",
                  "o:num_nulls": 0,
                  "o:last_analyzed": "2016-03-31T12:17:53"
                },
                "country": {
                  "type": "string",
                  "o:length": 32,
                  "o:preferred_column_name": "PO_DOCUMENT$country",
                  "o:frequency": 100,
                  "o:low_value": "United States of America",
                  "o:high_value": "United States of America",
                  "o:num_nulls": 0,
                  "o:last_analyzed": "2016-03-31T12:17:53"
                },
                "zipCode": {
                  "type": "number",
                  "o:length": 8,
                  "o:preferred_column_name": "PO_DOCUMENT$zipCode",
                  "o:frequency": 100,
                  "o:low_value": "99236",
                  "o:high_value": "99236",
                  "o:num_nulls": 0,
                  "o:last_analyzed": "2016-03-31T12:17:53"
                }
              }
            }
          }
        },
        "Special Instructions": {
          "type": "string",
          "o:length": 8,
          "o:preferred_column_name": "PO_DOCUMENT$SpecialInstructions",
          "o:frequency": 100,
          "o:low_value": "Courier",
          "o:high_value": "Courier",
          "o:num_nulls": 1,
          "o:last_analyzed": "2016-03-31T12:17:53"
        }
      }
    }

**Related Topics**

- JSON Data-Guide Fields
- Specifying a Preferred Name for a Field Column

**See Also:**

- [Example 4-2](creating-a-table-with-a-json-column.md)

- [Oracle Database SQL Language Reference](../sqlrf/JSON_DATAGUIDE.md) for information about SQL function `json_dataguide`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_JSON.md) for information about `DBMS_JSON.rename_column`

**Parent topic:** JSON Data Guide

------------------------------------------------------------------------



Footnote Legend

Footnote 1: If function json_dataguide were passed DBMS_JSON.FORMAT_HIERARCHICAL as optional second argument then the result would be three hierarchical data guides.
