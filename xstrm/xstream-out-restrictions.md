Restrictions apply to XStream Out.

- Capture Process Restrictions
  Restrictions apply to capture processes.
- Propagation Restrictions
  Restrictions apply to propagations.
- Outbound Server Restrictions
  Restrictions apply to outbound servers.
- XStream Out Rule Restrictions
  Restrictions apply to rules.
- XStream Out Rule-Based Transformation Restrictions
  Restrictions apply to rule-based transformations in XStream Out.
- XStream Out Limitations for Extended Data Types
  Some restrictions apply to extended data types in XStream Out.

**Parent topic:** [Appendixes](appendixes.md)

### B.1 Capture Process Restrictions

Restrictions apply to capture processes.

- Unsupported Data Types for Capture Processes
  Capture processes do not support some data types.
- Unsupported Changes for Capture Processes
  Capture processes do not support some changes.
- Supplemental Logging Data Type Restrictions
  Some types of columns cannot be part of a supplemental log group.
- Operational Requirements for Downstream Capture with XStream Out
  There are operational requirements for downstream capture with XStream Out.
- Capture Processes Do Not Support Oracle Label Security
  Capture processes do not support database objects that use Oracle Label Security (OLS).

**Parent topic:** XStream Out Restrictions

#### B.1.1 Unsupported Data Types for Capture Processes

Capture processes do not support some data types.

A capture process does not capture the results of DML changes to columns of the following data types:

- `ROWID`

- Nested tables

- The following Oracle-supplied types: `ANYTYPE`, `ANYDATASET`, URI types, `SDO_TOPO_GEOMETRY`, `SDO_GEORASTER`, and `Expression`

These data type restrictions pertain to both ordinary (heap-organized) tables and index-organized tables.

**Note:**

XStream does not support `LONG` columns in databases with varying width multibyte character sets.

**See Also:**

"[Data Types Captured by a Capture Process](xstream-out-concepts.md)"

Capture processes can capture changes to SecureFiles LOB columns only if the source database compatibility level is set to 11.2.0.0 or higher. Also, capture processes do not support capturing changes resulting from fragment-based operations on SecureFiles LOB columns or capturing changes resulting from SecureFiles archive manager operations.

When a capture process tries to create a row LCR for a DML change to a column of an unsupported data type, the capture process can either ignore the change to the table or raise an error. The behavior of the capture process depends on the setting for the `ignore_unsupported_table` capture process parameter.

When the capture process ignores the change to the table, it does not capture the change, and it records the table name in the alert log. When the capture process raises an error, it writes the LCR that caused the error into its trace file, raises an ORA-26744 error, and becomes disabled. In either case, modify the rules used by the capture process to avoid recording messages in the alert log or capture process errors. After modifying the capture process's rules, restart the capture process.

**Note:**

- You can add rules to a negative rule set for a capture process that instruct the capture process to discard changes to tables with columns of unsupported data types.

- Capture processes do not support primary keys that contain object type attributes.

- A capture process raises an error if it attempts to capture an `INSERT` operation with an `APPEND` hint if the `INSERT` operation includes a column of either of the following types: XMLType stored as object relational or XMLType stored as binary XML

**See Also:**

- "[Rules and Rule Sets](general-xstream-concepts.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_CAPTURE_ADM.md) for more information about the `ignore_unsupported_table` capture process parameter

- [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for more information about LogMiner restrictions for SecureFiles LOB columns

- [Oracle Database Upgrade Guide](../upgrd/compatibility-interoperability-between-database-releases.md) for information about database compatibility

**Parent topic:** Capture Process Restrictions

#### B.1.2 Unsupported Changes for Capture Processes

Capture processes do not support some changes.

- Unsupported Schemas for Capture Processes
  Capture processes do not support some schemas.
- Unsupported Table Types for Capture Processes
  Capture processes do not support some table types.
- Unsupported DDL Changes for Capture Processes
  Capture processes do not support some data definition language (DDL) changes.
- Changes Ignored by a Capture Process
  Capture processes ignore some types of changes.
- NOLOGGING and UNRECOVERABLE Keywords for SQL Operations
  If you use the `NOLOGGING` or `UNRECOVERABLE` keyword for a SQL operation, then the changes resulting from the SQL operation cannot be captured by a capture process.
- UNRECOVERABLE Clause for Direct Path Loads
  If you use the `UNRECOVERABLE` clause in the SQL\*Loader control file for a direct path load, then a capture process cannot capture the changes resulting from the direct path load.

**Parent topic:** Capture Process Restrictions

##### B.1.2.1 Unsupported Schemas for Capture Processes

Capture processes do not support some schemas.

By default, a capture process does not capture changes made to the following schemas:

- `CTXSYS`

- `DBSNMP`

- `DMSYS`

- `DVSYS`

- `EXFSYS`

- `LBACSYS`

- `MDDATA`

- `MDSYS`

- `OLAPSYS`

- `ORDDATA`

- `ORDPLUGINS`

- `ORDSYS`

- `OUTLN`

- `SI_INFORMTN_SCHEMA`

- `SYS`

- `SYSMAN`

- `SYSTEM`

- `WMSYS`

- `XDB`

If the `include_objects` capture process parameter specifies one or more of these schemas, then the capture process captures changes made to the specified schemas. If the `include_objects` capture process parameter specifies one or more tables in these schemas, then the capture process captures changes made to the specified tables.

By default, the `include_objects` capture process parameter is set to `NULL`. Therefore, the capture process does not capture changes made to these schemas.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_CAPTURE_ADM.md) for more information about the `include_objects` capture process parameter

**Parent topic:** Unsupported Changes for Capture Processes

##### B.1.2.2 Unsupported Table Types for Capture Processes

Capture processes do not support some table types.

A capture process cannot capture DML changes made to the following types of tables:

- Temporary tables

- Object tables that include the unsupported data types described in "Unsupported Data Types for Capture Processes"

**Note:**

- A capture process can capture changes to tables compressed with basic table compression and OLTP table compression only if the compatibility level at both the source database and the capture database is set to 11.2.0.0.0 or higher.

- A capture process can capture changes to tables compressed with hybrid columnar compression if all of the following conditions are met: both the source database and the capture database must be running Oracle Database 11g Release 2 (11.2.0.2), and the compatibility level at both the source database and the capture database is set to 11.2.0.0.0 or higher.

**See Also:**

- "[Data Types Captured by a Capture Process](xstream-out-concepts.md)"

- [Oracle Database Administrator’s Guide](../admin/managing-tables.md) for information about compressed tables

**Parent topic:** Unsupported Changes for Capture Processes

##### B.1.2.3 Unsupported DDL Changes for Capture Processes

Capture processes do not support some data definition language (DDL) changes.

A capture process captures the DDL changes that satisfy its rule sets, except for the following types of DDL changes:

- `ALTER` `DATABASE`

- `CREATE` `CONTROLFILE`

- `CREATE` `DATABASE`

- `CREATE` `PFILE`

- `CREATE` `SPFILE`

A capture process can capture DDL statements, but not the results of DDL statements, unless the DDL statement is a `CREATE` `TABLE` `AS` `SELECT` statement. For example, when a capture process captures an `ANALYZE` statement, it does not capture the statistics generated by the `ANALYZE` statement. However, when a capture process captures a `CREATE` `TABLE` `AS` `SELECT` statement, it captures the statement itself and all of the rows selected (as `INSERT` row LCRs).

Some types of DDL changes that are captured by a capture process cannot be applied by an outbound server. If an outbound server receives a DDL LCR that specifies an operation that cannot be processed, then the outbound server ignores the DDL LCR and records information about it in its trace file.

**See Also:**

"[Rules and Rule Sets](general-xstream-concepts.md)"

**Parent topic:** Unsupported Changes for Capture Processes

##### B.1.2.4 Changes Ignored by a Capture Process

Capture processes ignore some types of changes.

A capture process ignores the following types of changes:

- The session control statements `ALTER` `SESSION` and `SET` `ROLE`.

- The system control statement `ALTER` `SYSTEM`.

- `CALL`, `EXPLAIN` `PLAN`, and `LOCK` `TABLE` statements.

- `GRANT` statements on views.

- Changes made to a table or schema by online redefinition using the `DBMS_REDEFINITION` package. Online table redefinition is supported on a table for which a capture process captures changes, but the logical structure of the table before online redefinition must be the same as the logical structure after online redefinition.

- Changes to sequence values. For example, if a user references a `NEXTVAL` or sets the sequence, then a capture process does not capture changes resulting from these operations. Also, if you share a sequence at multiple databases, then sequence values used for individual rows at these databases might vary.

- Invocations of PL/SQL procedures, which means that a call to a PL/SQL procedure is not captured. However, if a call to a PL/SQL procedure causes changes to database objects, then these changes can be captured by a capture process if the changes satisfy the capture process rule sets.

**Note:**

- If an Oracle-supplied package related to XML makes changes to database objects, then these changes are not captured by capture processes.

- If an Oracle-supplied package related to Oracle Text makes changes to database objects, then these changes are not captured by capture processes.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/index.md) for information about packages related to XML

- [Oracle Text Reference](../ccref/index.md) for information about packages related to Oracle Text

**Parent topic:** Unsupported Changes for Capture Processes

##### B.1.2.5 NOLOGGING and UNRECOVERABLE Keywords for SQL Operations

If you use the `NOLOGGING` or `UNRECOVERABLE` keyword for a SQL operation, then the changes resulting from the SQL operation cannot be captured by a capture process.

Therefore, do not use these keywords to capture the changes that result from a SQL operation.

If the object for which you are specifying the logging attributes resides in a database or tablespace in `FORCE` `LOGGING` mode, then Oracle Database ignores any `NOLOGGING` or `UNRECOVERABLE` setting until the database or tablespace is taken out of `FORCE` `LOGGING` mode. You can determine the current logging mode for a database by querying the `FORCE_LOGGING` column in the `V$DATABASE` dynamic performance view. You can determine the current logging mode for a tablespace by querying the `FORCE_LOGGING` column in the `ALL_TABLESPACES` static data dictionary view.

**Note:**

The `UNRECOVERABLE` keyword is deprecated and has been replaced with the `NOLOGGING` keyword in the `logging_clause`. Although `UNRECOVERABLE` is supported for backward compatibility, Oracle strongly recommends that you use the `NOLOGGING` keyword, when appropriate.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md)for more information about the `NOLOGGING` and `UNRECOVERABLE` keywords, `FORCE` `LOGGING` mode, and the `logging_clause`

**Parent topic:** Unsupported Changes for Capture Processes

##### B.1.2.6 UNRECOVERABLE Clause for Direct Path Loads

If you use the `UNRECOVERABLE` clause in the SQL\*Loader control file for a direct path load, then a capture process cannot capture the changes resulting from the direct path load.

Therefore, if the changes resulting from a direct path load should be captured by a capture process, then do not use the `UNRECOVERABLE` clause.

If you load objects into a database or tablespace that is in `FORCE` `LOGGING` mode, then Oracle Database ignores any `UNRECOVERABLE` clause during a direct path load, and the loaded changes are logged. You can determine the current logging mode for a database by querying the `FORCE_LOGGING` column in the `V$DATABASE` dynamic performance view. You can determine the current logging mode for a tablespace by querying the `FORCE_LOGGING` column in the `DBA_TABLESPACES` static data dictionary view.

**See Also:**

[Oracle Database Utilities](../sutil/oracle-sql-loader-concepts.md) for information about direct path loads and SQL\*Loader

**Parent topic:** Unsupported Changes for Capture Processes

#### B.1.3 Supplemental Logging Data Type Restrictions

Some types of columns cannot be part of a supplemental log group.

Columns of the following data types cannot be part of a supplemental log group: LOB, `LONG`, `LONG` `RAW`, user-defined types (including object types, `REF`s, varrays, nested tables), and Oracle-supplied types (including `Any` types, XML types, spatial types, and media types).

**See Also:**

- "[If Required, Configure Supplemental Logging](configuring-xstream-out.md)"

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for information about data types

**Parent topic:** Capture Process Restrictions

#### B.1.4 Operational Requirements for Downstream Capture with XStream Out

There are operational requirements for downstream capture with XStream Out.

The following are operational requirements for using downstream capture:

- The source database must be running at least Oracle Database 10g Release 2 (10.2).

- The downstream database must be running Oracle Database 11g Release 2 (11.2.0.3) or later and the source database must be running Oracle Database 10g Release 2 (10.2) or later.

- The operating system on the source and downstream capture sites must be the same, but the operating system release does not need to be the same. In addition, the downstream sites can use a different directory structure than the source site.

- The hardware architecture on the source and downstream capture sites must be the same. For example, a downstream capture configuration with a source database on a 64-bit Sun system must have a downstream database that is configured on a 64-bit Sun system. Other hardware elements, such as the number of CPUs, memory size, and storage configuration, can be different between the source and downstream sites.

**See Also:**

"[Local Capture and Downstream Capture](xstream-out-concepts.md)"

**Parent topic:** Capture Process Restrictions

#### B.1.5 Capture Processes Do Not Support Oracle Label Security

Capture processes do not support database objects that use Oracle Label Security (OLS).

**See Also:**

[Oracle Label Security Administrator’s Guide](../olsag/index.md)

**Parent topic:** Capture Process Restrictions

### B.2 Propagation Restrictions

Restrictions apply to propagations.

- Connection Qualifiers and Propagations
  Connection qualifiers cannot be specified in the database links that are used by propagations.

**Parent topic:** XStream Out Restrictions

#### B.2.1 Connection Qualifiers and Propagations

Connection qualifiers cannot be specified in the database links that are used by propagations.

**Parent topic:** Propagation Restrictions

### B.3 Outbound Server Restrictions

Restrictions apply to outbound servers.

- Unsupported Data Types for Outbound Servers
  Outbound servers do not support some data types.
- Types of DDL Changes Ignored by an Outbound Server
  Outbound servers do not support some types of DDL changes.
- Apply Process Features That Are Not Applicable to Outbound Servers
  Some features cannot be used with outbound servers.

**Parent topic:** XStream Out Restrictions

#### B.3.1 Unsupported Data Types for Outbound Servers

Outbound servers do not support some data types.

An outbound server does not process row LCRs containing the results of DML changes in columns of the following data types:

- `ROWID`

- Nested tables

- The following Oracle-supplied types: `ANYTYPE`, `ANYDATASET`, URI types, `SDO_TOPO_GEOMETRY`, `SDO_GEORASTER`, and `Expression`

**Note:**

XStream does not support `LONG` columns in databases with varying width multibyte character sets.

An outbound server raises an error if it attempts to process a row LCR that contains information about a column of an unsupported data type. In addition, an outbound server cannot process DML changes to the following types of tables:

- Temporary tables

- Object tables that include unsupported data types

An outbound server raises an error if it attempts to process such changes. When an outbound server raises an error for an LCR, it moves the transaction that includes the LCR into the error queue.

**See Also:**

- "[Data Types Supported by Outbound Servers](xstream-out-concepts.md)"

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for information about data types

**Parent topic:** Outbound Server Restrictions

#### B.3.2 Types of DDL Changes Ignored by an Outbound Server

Outbound servers do not support some types of DDL changes.

The following types of DDL changes are not supported by an outbound server:

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

If an outbound server receives a DDL LCR that specifies an operation that cannot be processed, then the outbound server ignores the DDL LCR and records the following message in the outbound server trace file, followed by the DDL text that was ignored:

    Apply process ignored the following DDL:

An outbound server applies all other types of DDL changes if the DDL LCRs containing the changes should be applied according to the outbound server rule sets.

**Note:**

- An outbound server processes `ALTER` `object_type` `object_name` `RENAME` changes, such as `ALTER` `TABLE` `jobs` `RENAME`. Therefore, if you want DDL changes that rename objects to be processed, then use `ALTER` `object_type` `object_name` `RENAME` statements instead of `RENAME` statements.

- The name "materialized view" is synonymous with the name "snapshot". Snapshot equivalents of the statements on materialized views are ignored by an outbound server.

**See Also:**

"[Rules and Rule Sets](general-xstream-concepts.md)"

**Parent topic:** Outbound Server Restrictions

#### B.3.3 Apply Process Features That Are Not Applicable to Outbound Servers

Some features cannot be used with outbound servers.

The following apply process features cannot be used with outbound servers:

- Apply handlers

  You cannot specify an apply handler for an outbound server. The client application can perform custom processing of the LCRs instead if necessary. However, if apply processes are configured in the same database as the outbound server, then you can specify apply handlers for these apply processes. In addition, you can configure general apply handlers for the database. An outbound server ignores general apply handlers.

- The following apply parameters:

  - `allow_duplicate_rows`

  - `commit_serialization`

  - `compare_key_only`

  - `disable_on_error`

  - `parallelism`

  - `preserve_encryption`

  - `rtrim_on_implicit_conversion`

  Outbound servers ignore the settings for these apply parameters.

  The `commit_serialization` parameter is always set to `FULL` for an outbound server, and the `parallelism` parameter is always set to `1` for an outbound server.

  **See Also:**

  [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md)

- Apply tags

  An outbound server cannot set an apply tag for the changes it processes.

- Apply database links

  Outbound servers cannot use database links.

- Conflict detection and resolution

  An outbound server does not detect conflicts, and conflict resolution cannot be set for an outbound server.

- Dependency scheduling

  An outbound server does not evaluate dependencies because its parallelism must be 1.

- Substitute key column settings

  An outbound server ignores substitute key column settings.

- Enqueue directives specified by the `SET_ENQUEUE_DESTINATION` procedure in the `DBMS_APPLY_ADM` package

  An outbound server cannot enqueue changes into an Oracle database queue automatically using the `SET_ENQUEUE_DESTINATION` procedure.

  **See Also:**

  [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md)

- Execute directives specified by the `SET_EXECUTE` procedure in the `DBMS_APPLY_ADM` package

  An outbound server ignores execute directives.

  **See Also:**

  [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md)

- Error creation and execution

  An outbound server does not create an error transaction when it encounters an error. It records information about errors in the `ALL_APPLY` view, but it does not enqueue the transaction into an error queue.

**Parent topic:** Outbound Server Restrictions

### B.4 XStream Out Rule Restrictions

Restrictions apply to rules.

- Restrictions for Subset Rules
  Restrictions apply to subset rules.

**Parent topic:** XStream Out Restrictions

#### B.4.1 Restrictions for Subset Rules

Restrictions apply to subset rules.

The following restrictions apply to subset rules:

- A table with the table name referenced in the subset rule must exist in the same database as the subset rule, and this table must be in the same schema referenced for the table in the subset rule.

- If the subset rule is in the positive rule set for a capture process, then the table must contain the columns specified in the subset condition, and the data type of each of these columns must match the data type of the corresponding column at the source database.

- If the subset rule is in the positive rule set for a propagation, then the table must contain the columns specified in the subset condition, and the data type of each column must match the data type of the corresponding column in row LCRs that evaluate to `TRUE` for the subset rule.

- Creating subset rules for tables that have one or more columns of the following data types is not supported: LOB, `LONG`, `LONG` `RAW`, nested tables, and Oracle-supplied types (including `Any` types, XML types, spatial types, and media types).

**See Also:**

- "[Subset Rules](general-xstream-concepts.md)"

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for more information about data types

**Parent topic:** XStream Out Rule Restrictions

### B.5 XStream Out Rule-Based Transformation Restrictions

Restrictions apply to rule-based transformations in XStream Out.

- Unsupported Data Types for Declarative Rule-Based Transformations
  Except for add column transformations, declarative rule-based transformations that operate on columns support the same data types that are supported by capture processes.

**See Also:**

"[Rule-Based Transformations](general-xstream-concepts.md)"

**Parent topic:** XStream Out Restrictions

#### B.5.1 Unsupported Data Types for Declarative Rule-Based Transformations

Except for add column transformations, declarative rule-based transformations that operate on columns support the same data types that are supported by capture processes.

Add column transformations cannot add columns of the following data types: `BLOB`, `CLOB`, `NCLOB`, `BFILE`, `LONG`, `LONG` `RAW`, `ROWID`, nested tables, and Oracle-supplied types (including `Any` types, XML types, spatial types, and media types).

Extended data type columns cannot be used in the following types of declarative rule-based transformations:

- Add column

- Keep columns

**See Also:**

- "[Data Types Captured by a Capture Process](xstream-out-concepts.md)"

- "Unsupported Data Types for Capture Processes"

- "XStream Out Limitations for Extended Data Types"

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for information about data types

**Parent topic:** XStream Out Rule-Based Transformation Restrictions

### B.6 XStream Out Limitations for Extended Data Types

Some restrictions apply to extended data types in XStream Out.

The maximum size of the `VARCHAR2`, `NVARCHAR2`, and `RAW` data types has been increased in Oracle Database 12c when the `COMPATIBLE` initialization parameter is set to `12.0.0` and the `MAX_STRING_SIZE` initialization parameter is set to `EXTENDED`. XStream Out supports these extended data types.

However, the following limitations apply to the extended data type:

- Information about an extended data type column might not be contained in the original LCR for a data manipulation language (DML) operation. Instead, XStream Out might treat the extended data type column similar to the way it treats LOB columns. Specifically, additional LCRs might contain the information for the extended data type column.

- XStream rules cannot access data in LCRs for extended data type columns.

- Extended data type columns cannot be specified in a subset rule clause.

- Extended data type columns cannot be used in the following types of declarative rule-based transformations:

  - Add column

  - Keep columns

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for more information about extended data types

**Parent topic:** XStream Out Restrictions
