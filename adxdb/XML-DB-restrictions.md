The restrictions associated with Oracle XML DB are listed here.

- Thin JDBC Driver Not Supported by Some `XMLType` Functions – `XMLType` method `transform()` works only with the OCI driver. Not all `oracle.xdb.XMLType` functions are supported by the thin JDBC driver. If you do not use `oracle.xdb.XMLType` classes and the OCI driver, you can lose performance benefits.

- NCHAR, NVARCHAR2, and NCLOB Not Supported – Oracle XML DB does not support the use of SQL data types `NCHAR`, `NVARCHAR2`, and `NCLOB` for any of the following:

  - Mapping XML elements or attributes to these data types using the `SQLType` annotation in an XML schema

  - Generating XML data from these data types using SQL/XML functions `XMLElement`, `XMLAttributes`, and `XMLForest`

  - Within SQL/XML functions `XMLQuery` and `XMLTable`, using XQuery functions `ora:view` (desupported), `fn:doc`, and `fn:collection` on tables that contain columns with these data types

  To handle, store, or generate XML data that contains multibyte characters, Oracle strongly recommends that you use AL32UTF8 as the database character set.

- XML Identifier Length Limit – Oracle XML DB supports only XML identifiers that are a maximum of 32767 bytes or 4000 bytes, depending on the value of initialization parameter `MAX_STRING_SIZE`. See [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md).

- Repository File Size Limit – The maximum size of a file in Oracle XML DB Repository is 4 gigabytes. This implies the following limits for different kinds of file data:

  - 4 gigabytes for any LOB, which means 2 gigacharacters for a `CLOB` stored in the database character set AL32UTF8.

  - 4 gigabytes for binary XML encoded data, which typically means more than 4 gigabytes of external XML data before encoding.

  - Indeterminate for XML data stored object-relationally.

- Repository-Wide Resource Configuration File Limit – You cannot create more than 125 resource configuration files for repository-wide configuration.

- Recursive Folder Deletion – You cannot delete more than 50 levels of nested folders using the option for recursive deletion.

- No Column-Level Encryption for `XMLType` – Column-level encryption is not supported for `XMLType`. Tablespace-level encryption is supported for all `XMLType` storage models.

- No Composite Partitioning for `XMLType` – Composite partitioning is not supported for `XMLType` tables or columns (regardless of the `XMLType` storage model).

- No Partitioning for Hierarchically Enabled Tables – You cannot partition a hierarchy-enabled table. (See [Repository Resources and Database Table Security](repository-access-control.md) for information about hierarchy-enabled tables.)

- No Oracle Real Application Testing (RAT) for `XMLType`– Oracle Real Application Testing (RAT) is not supported for `XMLType`.

- No `XMLType` Access over Database Links – Access to remote `XMLType` tables or columns is not supported.

- Oracle JVM Needed for Some Features – In general, the behavior of Oracle XML DB does not depend on whether or not you have Oracle JVM (Java Virtual Machine) installed. However, if you use Java servlets then you must install Oracle JVM.

- Editioning Views Not Compatible with `XMLType` – Editioning views are not compatible with `XMLType` data that is stored object-relationally. They cannot be enabled in database schemas that contain persisted object types.

- Transportable tablespaces and database consolidation – If your Oracle XML DB Repository in Oracle Database 11g Release 2 (11.2) has existing data then you cannot use transportable tablespaces to plug that database directly into a container database (CDB). Instead, upgrade the 11.2 database to 12.1, unplug it, and then plug it in.

- No `XMLType` virtual columns for object-relational storage of `XMLType` – You cannot add a virtual `XMLType` column to an object-relational `XMLType` table or to a table that has an object-relational `XMLType` column.

- No sharding for XMLType or repository – Sharding is not supported for `XMLType` data or for Oracle XML DB Repository.

- Use heap tables, not index-organized tables (IOTs) – For best results, Oracle recommends that you use heap tables, not IOTs, with Oracle XML DB.

- XML schema URL uniqueness ignores protocol part – Attribute `schemaurl` for a registered XML schema must be unique apart from the protocol part. The protocol part (for example, `http` or `https`) is ignored in the test for uniqueness.

**Related Topics**

- [Oracle XML DB Support for XQuery](xquery-and-XML-DB.md)

**Parent topic:** [Appendixes](appendices.md)
