Restrictions apply to XStream In.

- Inbound Server Restrictions
  Restrictions apply to inbound servers.
- XStream In Rule Restrictions
  Restrictions apply to rules.
- XStream In Rule-Based Transformation Restrictions
  Restrictions apply to rule-based transformations in XStream In.
- XStream In Limitations for Extended Data Types
  Limitations apply to extended data types in XStream In.

**Parent topic:** [Appendixes](appendixes.md)

### C.1 Inbound Server Restrictions

Restrictions apply to inbound servers.

- Unsupported Data Types for Inbound Servers
  Inbound servers do not support some data types.
- Unsupported Data Types for Apply Handlers
  Apply handlers do not support some data types.
- Types of DDL Changes Ignored by an Inbound Server
  Inbound servers ignore some types of DDL changes.
- Current Schema User Must Exist at Destination Database
  For a DDL LCR to be applied at a destination database successfully, the user specified as the `current_schema` in the DDL LCR must exist at the destination database.
- Inbound Servers Do Not Support Oracle Label Security
  Inbound servers do not support database objects that use Oracle Label Security (OLS).

**Parent topic:** XStream In Restrictions

#### C.1.1 Unsupported Data Types for Inbound Servers

Inbound servers do not support some data types.

An inbound server does not apply row LCRs containing the results of DML changes in columns of the following data types:

- `ROWID`

- Nested tables

- The following Oracle-supplied types: `ANYTYPE`, `ANYDATASET`, URI types, `SDO_TOPO_GEOMETRY`, `SDO_GEORASTER`, and `Expression`

**Note:**

XStream does not support `LONG` columns in databases with varying width multibyte character sets.

An inbound server raises an error if it attempts to apply a row LCR that contains information about a column of an unsupported data type. In addition, an inbound server cannot apply DML changes to the following types of tables:

- Temporary tables

- Object tables that include unsupported data types

An inbound server raises an error if it attempts to apply such changes. When an inbound server raises an error for an LCR, it moves the transaction that includes the LCR into the error queue.

These data type restrictions pertain to both ordinary (heap-organized) tables and index-organized tables.

**See Also:**

- "[Data Types Applied by Inbound Servers](xstream-in-concepts.md)"

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for information about data types

**Parent topic:** Inbound Server Restrictions

#### C.1.2 Unsupported Data Types for Apply Handlers

Apply handlers do not support some data types.

Procedure DML handlers and error handlers cannot process `LONG` or `LONG` `RAW` column data in row LCRs. However, procedure DML handlers and error handlers can process both nonassembled and assembled LOB column data in row LCRs, but these handlers cannot modify nonassembled LOB column data.

**See Also:**

- "[LCR Processing Options for Inbound Servers](xstream-in-concepts.md)"

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for more information about data types

**Parent topic:** Inbound Server Restrictions

#### C.1.3 Types of DDL Changes Ignored by an Inbound Server

Inbound servers ignore some types of DDL changes.

The following types of DDL changes are not supported by an inbound server. These types of DDL changes are not applied:

- `ALTER` `MATERIALIZED` `VIEW`

- `ALTER` `MATERIALIZED` `VIEW` `LOG`

- `CREATE` `DATABASE` `LINK`

- `CREATE` `SCHEMA` `AUTHORIZATION`

- `CREATE` `MATERIALIZED` `VIEW`

- `CREATE` `MATERIALIZED` `VIEW` `LOG`

- `DROP` `DATABASE` `LINK`

- `DROP` `MATERIALIZED` `VIEW`

- `DROP` `MATERIALIZED` `VIEW` `LOG`

- `FLASHBACK` `DATABASE`

- `RENAME`

If an inbound server receives a DDL LCR that specifies an operation that cannot be applied, then the inbound server ignores the DDL LCR and records the following message in the inbound server trace file, followed by the DDL text that was ignored:

    Inbound server ignored the following DDL:

An inbound server applies all other types of DDL changes if the DDL LCRs containing the changes should be applied according to the inbound server rule sets.

**Note:**

- An inbound server applies `ALTER` `object_type` `object_name` `RENAME` changes, such as `ALTER` `TABLE` `jobs` `RENAME`. Therefore, if you want DDL changes that rename objects to be applied, then use `ALTER` `object_type` `object_name` `RENAME` statements instead of `RENAME` statements. After changing the name of a database object, new rules that specify the new database object name might be needed to replicate changes to the database object.

- The name "materialized view" is synonymous with the name "snapshot". Snapshot equivalents of the statements on materialized views are ignored by an inbound server.

**See Also:**

"[Rules and Rule Sets](general-xstream-concepts.md)"

**Parent topic:** Inbound Server Restrictions

#### C.1.4 Current Schema User Must Exist at Destination Database

For a DDL LCR to be applied at a destination database successfully, the user specified as the `current_schema` in the DDL LCR must exist at the destination database.

The current schema is the schema that is used if no schema is specified for an object in the DDL text.

**See Also:**

- [Oracle Database Concepts](../cncpt/index.md)for more information about database structures

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/Logical-Change-Record-TYPEs.md)for more information about the `current_schema` attribute in DDL LCRs

**Parent topic:** Inbound Server Restrictions

#### C.1.5 Inbound Servers Do Not Support Oracle Label Security

Inbound servers do not support database objects that use Oracle Label Security (OLS).

**See Also:**

[Oracle Label Security Administrator’s Guide](../olsag/index.md)

**Parent topic:** Inbound Server Restrictions

### C.2 XStream In Rule Restrictions

Restrictions apply to rules.

- Restrictions for Subset Rules
  Restrictions apply to subset rules.

**Parent topic:** XStream In Restrictions

#### C.2.1 Restrictions for Subset Rules

Restrictions apply to subset rules.

The following restrictions apply to subset rules:

- A table with the table name referenced in the subset rule must exist in the same database as the subset rule, and this table must be in the same schema referenced for the table in the subset rule.

- If the subset rule is in the positive rule set for an inbound server, then the table must contain the columns specified in the subset condition, and the data type of each column must match the data type of the corresponding column in row LCRs that evaluate to `TRUE` for the subset rule.

- Creating subset rules for tables that have one or more columns of the following data types is not supported: LOB, `LONG`, `LONG` `RAW`, user-defined types (including object types, `REF`s, varrays, nested tables), and Oracle-supplied types (including `Any` types, XML types, spatial types, and media types).

**See Also:**

- "[Subset Rules](general-xstream-concepts.md)"

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for more information about data types

**Parent topic:** XStream In Rule Restrictions

### C.3 XStream In Rule-Based Transformation Restrictions

Restrictions apply to rule-based transformations in XStream In.

- Unsupported Data Types for Declarative Rule-Based Transformations
  Except for add column transformations, declarative rule-based transformations that operate on columns support the same data types that are supported by inbound servers.

**See Also:**

"[Rule-Based Transformations](general-xstream-concepts.md)"

**Parent topic:** XStream In Restrictions

#### C.3.1 Unsupported Data Types for Declarative Rule-Based Transformations

Except for add column transformations, declarative rule-based transformations that operate on columns support the same data types that are supported by inbound servers.

Add column transformations cannot add columns of the following data types: `BLOB`, `CLOB`, `NCLOB`, `BFILE`, `LONG`, `LONG` `RAW`, `ROWID`, user-defined types (including object types, `REF`s, varrays, nested tables), and Oracle-supplied types (including `Any` types, XML types, spatial types, and media types).

**See Also:**

- "[Data Types Applied by Inbound Servers](xstream-in-concepts.md)"

- "Unsupported Data Types for Inbound Servers"

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for information about data types

**Parent topic:** XStream In Rule-Based Transformation Restrictions

### C.4 XStream In Limitations for Extended Data Types

Limitations apply to extended data types in XStream In.

The maximum size of the `VARCHAR2`, `NVARCHAR2`, and `RAW` data types has been increased in Oracle Database 12c when the `COMPATIBLE` initialization parameter is set to `12.0.0` and the `MAX_STRING_SIZE` initialization parameter is set to `EXTENDED`. XStream In supports these extended data types.

However, the following limitations apply to the extended data types:

- Information about an extended data type column might not be contained in the original LCR for a data manipulation language (DML) operation. Instead, XStream In might treat the extended data type column similar to the way it treats LOB columns. Specifically, additional LCRs might contain the information for the extended data type column.

- XStream rules cannot access data in LCRs for extended data type columns.

- Extended data type columns cannot be specified in a subset rule clause.

- Extended data type columns cannot be used for conflict detection.

- Extended data type columns cannot be used for a substitute primary key for apply purposes with the `DBMS_APPLY_ADM.SET_KEY_COLUMNS` procedure.

- Extended data type columns cannot be used in the following types of declarative rule-based transformations:

  - Add column

  - Keep columns

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for more information about extended data types

**Parent topic:** XStream In Restrictions
