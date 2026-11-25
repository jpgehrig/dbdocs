Oracle Database supports JavaScript Object Notation (JSON) data natively with relational database features, including transactions, indexing, declarative querying, and views.

This documentation covers the use of database languages and features to work with JSON data that is stored in Oracle Database. In particular, it covers how to use SQL and PL/SQL with JSON data.

**Note:**

Oracle also provides a family of **Simple Oracle Document Access** (**SODA**) APIs for access to JSON data stored in the database. SODA is designed for schemaless application development without knowledge of relational database features or languages such as SQL and PL/SQL. It lets you create and store collections of documents in Oracle Database, retrieve them, and query them, without needing to know how the documents are stored in the database.

There are several implementations of SODA:

- SODA for REST — Representational state transfer (REST) requests perform collection and document operations, using any language capable of making HTTP calls.

- SODA for Java — Java classes and interfaces represent databases, collections, and documents.

- SODA for PL/SQL — PL/SQL object types represent collections and documents.

- SODA for C — Oracle Call Interface (OCI) handles represent collections and documents.

For information about SODA see [Oracle as a Document Store](http://www.oracle.com/technetwork/database/application-development/oracle-document-store/index.html).

- Overview of JSON in Oracle Database
  Oracle Database supports JSON natively with relational database features, including transactions, indexing, declarative querying, and views. Unlike relational data, JSON data can be stored in the database, indexed, and queried without any need for a schema that defines the data.
- Getting Started Using JSON with Oracle Database
  In general, you will perform the following tasks when working with JSON data in Oracle Database: (1) create a JSON column with an `is json` check constraint, (2) insert JSON data into the column, and (3) query the JSON data.
- Oracle Database Support for JSON
  Oracle Database support for JavaScript Object Notation (JSON) is designed to provide the best fit between the worlds of relational storage and querying JSON data, allowing relational and JSON queries to work well together. Oracle SQL/JSON support is closely aligned with the JSON support in the SQL Standard.

**Parent topic:** [Introduction to JSON Data and Oracle Database](intro-to-json-data-and-oracle-database.md)

### 1.1 Overview of JSON in Oracle Database

Oracle Database supports JSON natively with relational database features, including transactions, indexing, declarative querying, and views. Unlike relational data, JSON data can be stored in the database, indexed, and queried without any need for a schema that defines the data.

(The JSON data is schemaless, even though a database schema is used to define the table and column in which it is stored. Nothing in that schema specifies the structure of the JSON data itself.)

JSON data has often been stored in NoSQL databases such as Oracle NoSQL Database and Oracle Berkeley DB. These allow for storage and retrieval of data that is not based on any schema, but they do not offer the rigorous consistency models of relational databases.

To compensate for this shortcoming, a relational database is sometimes used in parallel with a NoSQL database. Applications using JSON data stored in the NoSQL database must then ensure data integrity themselves.

Native support for JSON by Oracle Database obviates such workarounds. It provides all of the benefits of relational database features for use with JSON, including transactions, indexing, declarative querying, and views.

Database queries with Structured Query Language (SQL) are declarative. With Oracle Database you can use SQL to join JSON data with relational data. And you can project JSON data relationally, making it available for relational processes and tools. You can also query, from within the database, JSON data that is stored outside Oracle Database in an external table.

You can access JSON data stored in the database the same way you access other database data, including using Oracle Call Interface (OCI), and Java Database Connectivity (JDBC).

The JSON-language standard defines JSON data in a textual way: it is composed of Unicode characters in a standard syntax. In Oracle Database, you can store JSON data textually using the common SQL data types `VARCHAR2`, `CLOB`, and `BLOB`, as unparsed character data.

Oracle recommends that you always use an `is json` check constraint to ensure that column values are valid JSON instances. See [Example 4-1](creating-a-table-with-a-json-column.md).

#### JSON Columns in Database Tables

Oracle Database places no restrictions on the tables that can be used to store JSON documents. A column containing JSON documents can coexist with any other kind of database data. A table can also have multiple columns that contain JSON documents.

When using Oracle Database as a JSON document store, your tables that contain JSON columns typically also have a few non-JSON housekeeping columns. These typically track metadata about the JSON documents.

If you are using JSON to add flexibility to a primarily relational application then some of your tables likely also have a column for JSON documents, which you use to manage the application data that does not map directly to your relational model.

By definition, textual JSON data is encoded using a Unicode encoding, either UTF-8 or UTF-16. You can use textual data that is stored in a non-Unicode character set as if it were JSON data, but in that case Oracle Database automatically converts the character set to UTF-8 when processing the data.

#### Use SQL With JSON Data

In SQL, you can access JSON data stored in Oracle Database using either specialized functions and conditions or a simple dot notation. Most of the SQL functions and conditions belong to the SQL/JSON standard, but a few are Oracle-specific.

- SQL/JSON query functions `json_value`, `json_query`, and `json_table`.

  These evaluate SQL/JSON path expressions against JSON data to produce SQL values.

- Oracle SQL condition `json_textcontains` and SQL/JSON conditions `json_exists`, `is json`, and `is not json`.

  Condition `json_exists` checks for the existence of given JSON data; `json_textcontains` provides full-text querying of JSON data; and `is json` and `is not json` check whether given JSON data is well-formed.

  `json_exists` and `json_textcontains` check the data that matches a SQL/JSON path expression.

- A simple dot notation that acts similar to a combination of query functions `json_value` and `json_query`.

  This resembles a SQL object access expression, that is, attribute dot notation for an abstract data type (ADT). This is the easiest way to query JSON data in the database.

- SQL/JSON generation functions `json_object`, `json_array`, `json_objectagg`, and `json_arrayagg`.

  These gather SQL data to produce JSON object and array data (as a SQL value).

- Oracle SQL condition `json_equal`, which tests whether two JSON values are the same.

- Oracle SQL aggregate function `json_dataguide`.

  This produces JSON data that is a data guide, which you can use to discover information about the structure and content of other JSON data in the database.

As a simple illustration of querying, here is a dot-notation query of the documents stored in JSON column `po_document` of table `j_purchaseorder` (aliased here as `po`). It obtains all purchase-order requestors (JSON field `Requestor`).

    SELECT po.po_document.Requestor FROM j_purchaseorder po;

#### Use PL/SQL With JSON Data

You can manipulate JSON data within PL/SQL code using SQL code or PL/SQL object types for JSON. (You cannot use an empty JSON field name in any SQL code that you use in PL/SQL.)

The following SQL functions and conditions are also available as built-in PL/SQL functions: `json_value`, `json_query`, `json_object`, `json_array`, `json_exists`, `is json`, `is not json`, and `json_equal`.

Unlike the case for Oracle SQL, which has no `BOOLEAN` data type, in PL/SQL:

- `json_exists`, `is json`, `is not json`, and `json_equal` are Boolean functions.

- `json_value` can return a `BOOLEAN` value.

There are also PL/SQL object types for JSON, which you can use for fine-grained construction and manipulation of In-Memory JSON data. You can introspect it, modify it, and serialize it back to textual JSON data.

**Related Topics**

- [Simple Dot-Notation Access to JSON Data](simple-dot-notation-access-to-json-data.md)
- [Overview of SQL/JSON Path Expressions](json-path-expressions.md)
- [JSON Data Guide](json-dataguide.md)
- Oracle Database Support for JSON
- [Character Sets and Character Encoding for JSON Data](json-character-sets-and-encoding.md)
- [PL/SQL Object Types for JSON](pl-sql-object-types-for-json.md)
- [Overview of Storing and Managing JSON Data](overview-of-storage-and-management-of-JSON-data.md)

**Parent topic:** JSON in Oracle Database

### 1.2 Getting Started Using JSON with Oracle Database

In general, you will perform the following tasks when working with JSON data in Oracle Database: (1) create a JSON column with an `is json` check constraint, (2) insert JSON data into the column, and (3) query the JSON data.

1.  Create a table with a primary-key column and a JSON column, and add an `is json` check constraint to ensure that the JSON column contains only well-formed JSON data.
    The following statement creates table `j_purchaseorder` with primary key `id` and with JSON column `po_document` (see also [Example 4-1](creating-a-table-with-a-json-column.md)).

        CREATE TABLE j_purchaseorder
          (id          VARCHAR2 (32) NOT NULL PRIMARY KEY,
           date_loaded TIMESTAMP (6) WITH TIME ZONE,
           po_document VARCHAR2 (32767)
           CONSTRAINT ensure_json CHECK (po_document IS JSON));
2.  Insert JSON data into the JSON column, using any of the methods available for Oracle Database.
    The following statement uses a SQL `INSERT` statement to insert some simple JSON data into the third column of table `j_purchaseorder` (which is column `po_document` — see previous). Some of the JSON data is elided here (`...`). See [Example 4-2](creating-a-table-with-a-json-column.md) for these details.

        INSERT INTO j_purchaseorder
          VALUES (SYS_GUID(),
                  to_date('30-DEC-2014'),
                  '{"PONumber"             : 1600,
                    "Reference"            : "ABULL-20140421",
                    "Requestor"            : "Alexis Bull",
                    "User"                 : "ABULL",
                    "CostCenter"           : "A50",
                    "ShippingInstructions" : {...},
                    "Special Instructions" : null,
                    "AllowPartialShipment" : true,
                    "LineItems"            : [...]}');
3.  Query the JSON data. The return value is always a `VARCHAR2` instance that represents a JSON value. Here are some simple examples.
    The following query extracts, from each document in JSON column `po_document`, a scalar value, the JSON number that is the value of field `PONumber` for the objects in JSON column `po_document` (see also [Example 14-1](simple-dot-notation-access-to-json-data.md)):

        SELECT po.po_document.PONumber FROM j_purchaseorder po;

    The following query extracts, from each document, an array of JSON phone objects, which is the value of field `Phone` of the object that is the value of field `ShippingInstructions` (see also [Example 14-2](simple-dot-notation-access-to-json-data.md)):

        SELECT po.po_document.ShippingInstructions.Phone FROM j_purchaseorder po;

    The following query extracts, from each document, multiple values as an array: the value of field `type` for each object in array `Phone`. The returned array is not part of the stored data but is constructed automatically by the query. (The order of the array elements is unspecified.)

        SELECT po.po_document.ShippingInstructions.Phone.type FROM j_purchaseorder po;

**Related Topics**

- [Creating a Table With a JSON Column](creating-a-table-with-a-json-column.md)
- [Simple Dot-Notation Access to JSON Data](simple-dot-notation-access-to-json-data.md)

**Parent topic:** JSON in Oracle Database

### 1.3 Oracle Database Support for JSON

Oracle Database support for JavaScript Object Notation (JSON) is designed to provide the best fit between the worlds of relational storage and querying JSON data, allowing relational and JSON queries to work well together. Oracle SQL/JSON support is closely aligned with the JSON support in the SQL Standard.

**See Also:**

- ISO/IEC 9075-2:2016, Information technology—Database languages—SQL—Part 2: Foundation (SQL/Foundation)

- [ISO/IEC TR 19075–6](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=iso_iec_tr_19075_6)

- [Oracle Database SQL Language Reference](../sqlrf/Oracle-and-Standard-SQL.md)

- [JSON.org](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=json_org)

- [ECMA International](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=ecma_international)

**Parent topic:** JSON in Oracle Database
