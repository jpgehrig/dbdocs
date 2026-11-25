## 16 Using Oracle Data Redaction with Oracle Database Features

Oracle Data Redaction can be used with other Oracle features, but some Oracle features may have restrictions with regard to Oracle Data Redaction.

- Oracle Data Redaction General Usage Guidelines
  It is important to understand usage guidelines for using Oracle Data Redaction.
- Oracle Data Redaction and DML and DDL Operations
  Oracle Data Redaction affects DML and DDL operations, especially for users who issue ad-hoc SQL against tables with redacted columns.
- Oracle Data Redaction and Nested Functions, Inline Views, and the WHERE Clause
  You can use Oracle Data Redaction with nested functions, inline views, and the `WHERE` clause in `SELECT` statements.
- Oracle Data Redaction and Queries on Columns Protected by Data Redaction Policies
  Queries that include the `DISTINCT` or `ORDER BY` clause on columns that are protected by Oracle Data Redaction policies may return 0 rows.
- Oracle Data Redaction and Database Links
  Do not create Oracle Data Redaction policies on database views that reference database links.
- Oracle Data Redaction and Aggregate Functions
  Aggregate functions can affect performance overhead on Oracle Data Redaction policies.
- Oracle Data Redaction and Object Types
  You can use object types to model real-world entities such as customer accounts.
- Oracle Data Redaction and XML Generation
  You cannot use XML generation functions on columns that have Oracle Data Redaction policies defined on them.
- Oracle Data Redaction and Editions
  You cannot redact editioned views.
- Oracle Data Redaction and Oracle Data Warehouse Query Rewrite Operation
  Oracle Data Warehouse request queries are subject to any Oracle Data Redaction policies that are present against the relations that are specified in the query.
- Oracle Data Redaction in a Multitenant Environment
  In a multitenant environment, Oracle Data Redaction policies apply only to the objects within the current pluggable database (PDB).
- Oracle Data Redaction and Oracle Virtual Private Database
  Oracle Data Redaction does not affect Oracle Virtual Private Database policies because the VPD inline view, which contains the VPD predicate, acts on actual values.
- Oracle Data Redaction and Oracle Database Real Application Security
  Oracle Data Redaction differs from Oracle Database Real Application Security because of how security is implemented for applications.
- Oracle Data Redaction and Oracle Database Vault
  You can use Oracle Data Redaction in an Oracle Database Vault environment.
- Oracle Data Redaction and Oracle Data Pump
  Oracle Data Pump export operations can affect objects that have Oracle Data Redaction policies.
- Oracle Data Redaction and Data Masking and Subsetting Pack
  Oracle Enterprise Manager Data Masking and Subsetting Pack can be used to create a development or test copy of a production database.
- Oracle Data Redaction and JSON
  JavaScript Object Notation (JSON) can be used to create `is json` constraints on table columns.

**Parent topic:** [Using Oracle Data Redaction](asopart2.md)

### 16.1 Oracle Data Redaction General Usage Guidelines

It is important to understand usage guidelines for using Oracle Data Redaction.

- Do not include any redacted columns in a SQL expression that is used in a `GROUP BY` clause in a SQL statement. Oracle does not support this, and raises an `ORA-00979: not a GROUP BY expression` error. This happens because internally the expression in the `SELECT` list must be modified by Data Redaction, but this causes it to no longer be found when it comes time to process the `GROUP BY` clause (which is currently not updated by Data Redaction) leading to this unintended error message.

- Do not include any redacted columns in a SQL expression that is used in both the `DISTINCT` clause and `ORDER BY` clause in a SQL statement. Oracle does not support this, and raises an error: `ORA-01791: not a SELECTed expression`. This happens because internally the expression in the `SELECT` list must be modified by Data Redaction, but this causes it to no longer be found when it comes time to process the `GROUP BY` clause, leading to this unintended error message.

- An `ORA-28094: SQL construct not supported by data redaction` error is raised if a query involves a `UNION` of redacted columns and each branch of the `UNION` does not have the same redaction policy. Although Oracle Database does not support complex SQL that involves redacted columns, this error is not raised if the user who is executing a query with complex SQL has the `EXEMPT REDACTION POLICY` system privilege. This error is only raised for users who are not exempt from the redaction policy, and they cannot execute complex SQL that involves redacted columns, whereas users who are exempt from the policy are allowed to.

  To avoid the `ORA-28094` error, ensure that the query has the following properties:

  - When a column in the `UNION` has a redaction policy, the corresponding column in each branch of the `UNION` must use a redaction policy with the same values for all of its properties:

    - Function type

    - Function parameters or `REGEXP` parameters

    - Policy expression

    - Enable flag

    It can be a different redaction policy, but all these properties must be the same.

  - In an inline view, a `UNION` cannot have a subquery.

  - In a `CREATE VIEW` definition or an inline view, there cannot be any SQL expression that involves a redacted column.

- An `ORA-28093: operation on column %s is not supported by data redaction` error is raised if a user issues a query that involves XML syntax and if the user does not have the `EXEMPT REDACTION POLICY` system privilege. The `ORA-28093` is raised only for users who are not exempt from the redaction policy, and they cannot use XML syntax that involves redacted columns, whereas, user who are exempt from the redaction policy are allowed to.

- Oracle does not support the following:

  - Adding a Data Redaction policy on a virtual column
  - Adding a Data Redaction policy on the base column of a virtual column
  - Adding a virtual column whose base column has a Data Redaction policy defined on it
  - Creating a functional index on a column with Data Redaction policy

- In a `CREATE VIEW` definition or an inline view, there cannot be any SQL expressions (such as `concat`, `sum`, `trim`, `min`, `max`, and so on) that involve a redacted column.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.2 Oracle Data Redaction and DML and DDL Operations

Oracle Data Redaction affects DML and DDL operations, especially for users who issue ad-hoc SQL against tables with redacted columns.

Note the following:

- Oracle Data Redaction treats the `RETURNING INTO` clause of a DML statement as a query, even though the result is not displayed. The result that is sent to the buffer is what would have been displayed had the `RETURNING INTO` clause been run as an ordinary SQL query, rather than as part of a DML statement. If your application performs further processing on the buffer that contains the `RETURNING INTO` value, then consider changing the application because it may not expect to find a redacted value in the buffer.

- If a redacted column appears as the source in a DML or DDL operation, then Oracle Data Redaction considers this as an attempt to circumvent the policy and prevents it with an `ORA-28081: Insufficient privileges - the command references a redacted object` error unless you have the `EXEMPT REDACTION POLICY` system privilege. Internally, Oracle Data Pump issues these kinds of operations, so you may also need to grant the `EXEMPT REDACTION POLICY` system privilege to a user if they need to perform schema-level exports of tables that have redacted columns.

- Internally, Oracle Data Mining issues DML and DDL operations, so you may need to grant the `EXEMPT REDACTION POLICY` system privilege to a user if the user must create data mining models on tables that have redacted columns.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.3 Oracle Data Redaction and Nested Functions, Inline Views, and the WHERE Clause

You can use Oracle Data Redaction with nested functions, inline views, and the `WHERE` clause in `SELECT` statements.

Oracle Data Redaction policies work as follows:

- Nested functions are redacted innermost. For example, in `SELECT SUM(AVG(TO_NUMBER(((X))) FROM HR.EMPLOYEES WHERE ...`, the `TO_NUMBER` function is redacted first, followed by `AVG`, and then last the `SUM` function.

- Inline views are redacted outermost. For example, in `SELECT XYZ … AS SELECT A… AS SELECT B… AS SELECT C…`, `SELECT XYZ` is redacted first, followed by `AS SELECT A`, then `AS SELECT B`, and so on. `AS SELECT C` is redacted last.

- The WHERE clause is never redacted. Data Redaction redacts only data in the column `SELECT` list.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.4 Oracle Data Redaction and Queries on Columns Protected by Data Redaction Policies

Queries that include the `DISTINCT` or `ORDER BY` clause on columns that are protected by Oracle Data Redaction policies may return 0 rows.

This happens because redaction preserves the semantics of the query. For example, a query such as `SELECT * ``table_name`` WHERE ``sensitive_column`` LIKE '``value``';` would likely result in 0 rows returned, because the redacted value would not match the `'``value``'` value entered in the `WHERE` clause. To work around this issue, rewrite the query to include an inline view so that the semantic layer can find the column. For example, instead of the following query:

    SELECT DISTINCT sensitive_column
    FROM table_name
    ORDER BY sensitive_column;

Write the query as follows:

    SELECT sensitive_column FROM
    (SELECT DISTINCT sensitive_column
     FROM table_name
     ORDER BY sensitive_column);

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.5 Oracle Data Redaction and Database Links

Do not create Oracle Data Redaction policies on database views that reference database links.

You can find information about existing database links by querying the `DBA_DB_LINKS` data dictionary view.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/distributed-database-concepts.md) for detailed information about database links

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.6 Oracle Data Redaction and Aggregate Functions

Aggregate functions can affect performance overhead on Oracle Data Redaction policies.

Because Oracle Data Redaction dynamically modifies the value of each row in a column, certain SQL queries that use aggregate functions cannot take full advantage of database optimizations that presume the row values to be static.

In the case of SQL queries that call aggregate functions, it may be possible to notice performance overhead due to redaction.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.7 Oracle Data Redaction and Object Types

You can use object types to model real-world entities such as customer accounts.

An object type is a user-defined type. You cannot redact object types. This is because Database Redaction cannot handle all of the possible ways that object types can be configured, because they are user defined. You can find the type that an object uses by querying the `OBJECT_NAME` and `OBJECT_TYPE` columns of the `ALL_OBJECTS` data dictionary view.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.8 Oracle Data Redaction and XML Generation

You cannot use XML generation functions on columns that have Oracle Data Redaction policies defined on them.

[Oracle XML DB Developer’s Guide](../adxdb/generation-of-XML-data-from-relational-data.md) describes the kinds of SQL functions to which this restriction applies. This restriction applies irrespective of whether the Oracle Data Redaction policy has been enabled or disabled, or is active for the querying user.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.9 Oracle Data Redaction and Editions

You cannot redact editioned views.

In addition to not being able to redact editioned views, you cannot use a redacted column in the definition of any editioned view. You can find information about editions by querying the `DBA_EDITIONS` data dictionary view.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.10 Oracle Data Redaction and Oracle Data Warehouse Query Rewrite Operation

Oracle Data Warehouse request queries are subject to any Oracle Data Redaction policies that are present against the relations that are specified in the query.

Query rewrite may rewrite the query to use a materialized view instead of accessing the detail relations, but only if it can guarantee to deliver exactly the same results as if the rewrite had not occurred. Specifically, the query rewrite must retain and respect any Oracle Data Redaction policies against the relations that are specified in the request query. However, any Oracle Data Redaction policies against the materialized view itself do not have any effect when the materialized view is accessed during query rewrite. This is because the data is already protected by the Oracle Data Redaction policies against the relations in the request query.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.11 Oracle Data Redaction in a Multitenant Environment

In a multitenant environment, Oracle Data Redaction policies apply only to the objects within the current pluggable database (PDB).

You cannot create a Data Redaction policy for a multitenant container database (CDB). This is because the objects for which you create Data Redaction policies typically reside in a PDB. If you have the `SYSDBA` privilege, then you can list all the PDBs in a CDB by running the `SHOW PDBS` command.

As with the CDB root, you cannot create Data Redaction policies in an application root.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.12 Oracle Data Redaction and Oracle Virtual Private Database

Oracle Data Redaction does not affect Oracle Virtual Private Database policies because the VPD inline view, which contains the VPD predicate, acts on actual values.

Oracle Data Redaction differs from Oracle Virtual Private Database in the following ways:

- Oracle Data Redaction provides more redacting features than Oracle Virtual Private Database, which only supports `NULL` redacting. Many applications cannot use `NULL` redacting, so Data Redaction is a good solution for these applications.

- Oracle Virtual Private Database policies can be static, dynamic, and context sensitive, whereas Data Redaction policies only allow static and context-sensitive policy expressions.

- Data Redaction permits only one policy to be defined on a table or view, whereas you can define multiple Virtual Private Database policies on an object.

- Data Redaction is when application users try to access an object that is protected by a Data Redaction policy using a synonym, but (unlike Oracle Virtual Private Database) Data Redaction does not support the creation of policies directly on the synonyms themselves.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.13 Oracle Data Redaction and Oracle Database Real Application Security

Oracle Data Redaction differs from Oracle Database Real Application Security because of how security is implemented for applications.

Oracle Data Redaction differs from Oracle Database Real Application Security in that Real Application Security provides a comprehensive authorization framework for application security.

Column security within Real Application Security is based on application privileges that are defined by applications using the Real Application Security framework.

**See Also:**

[Oracle Database Real Application Security Administrator's and Developer's Guide](../dbfsg/configuring-data-security.md) for information about how you can protect table columns with custom application privileges

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.14 Oracle Data Redaction and Oracle Database Vault

You can use Oracle Data Redaction in an Oracle Database Vault environment.

For example, if there is an Oracle Database Vault realm around an object, a user who does not belong to the authorized list of realm owners or participants cannot see the object data, regardless of whether the user was granted the `EXEMPT REDACTION POLICY` privilege. If the user attempts a DML or DDL statement on the data, error messages result.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.15 Oracle Data Redaction and Oracle Data Pump

Oracle Data Pump export operations can affect objects that have Oracle Data Redaction policies.

- Oracle Data Pump Security Model for Oracle Data Redaction
  The `DATAPUMP_EXP_FULL_DATABASE` role includes the powerful `EXEMPT REDACTION POLICY` system privilege.
- Export of Objects That Have Oracle Data Redaction Policies Defined
  You can export objects that have already had Oracle Data Redaction policies defined on them.
- Export of Data Using the EXPDP Utility access_method Parameter
  Oracle Data Pump can export data from a schema that contains an object that has a Data Redaction policy.
- Import of Data into Objects Protected by Oracle Data Redaction
  During import operations into Oracle Data Redaction-protected objects, be aware of issues that may occur.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

#### 16.15.1 Oracle Data Pump Security Model for Oracle Data Redaction

The `DATAPUMP_EXP_FULL_DATABASE` role includes the powerful `EXEMPT REDACTION POLICY` system privilege.

Remember that by default the `DBA` role is granted the `DATAPUMP_EXP_FULL_DATABASE` role as well as `DATAPUMP_IMP_FULL_DATABASE`.

This enables users who were granted these roles to be exempt from Data Redaction policies. This means that, when you export objects with Data Redaction policies defined on them, the [actual data](glossary.md) in the protected tables is copied to the Data Pump target system without being redacted. Users with these roles, including users who were granted the `DBA` role, are able to see the actual data in the target system.

However, by default, all of the Data Redaction policies associated with any tables and views in the Data Pump source system are also included in the export and import operation (along with the objects themselves) and applied to the objects in the target system, so the data is still redacted when users query the objects in the target system.

**Related Topics**

- [Exemption of Users from Oracle Data Redaction Policies](configuring-oracle-data-redaction-policies.md)

**Parent topic:** Oracle Data Redaction and Oracle Data Pump

#### 16.15.2 Export of Objects That Have Oracle Data Redaction Policies Defined

You can export objects that have already had Oracle Data Redaction policies defined on them.

- Finding Type Names Used by Oracle Data Pump
  You must find the type names Oracle Data Pump uses before exporting objects that have Oracle Data Redaction policies defined on these objects.
- Exporting Only the Data Dictionary Metadata Related to Data Redaction Policies
  You can export only the data dictionary metadata that is related to data redaction policies and full redaction settings.
- Importing Objects Using the INCLUDE Parameter in IMPDP
  You can import objects using Oracle Database Pump.

**Parent topic:** Oracle Data Redaction and Oracle Data Pump

##### 16.15.2.1 Finding Type Names Used by Oracle Data Pump

You must find the type names Oracle Data Pump uses before exporting objects that have Oracle Data Redaction policies defined on these objects.

After you find these types, you should use these types as parameters for the `INCLUDE` directive to the `IMPDP` utility, to selectively export only metadata of these specific types to the dump file.

- To find type names, query the `DATABASE_EXPORT_OBJECTS` view.

For example:

    SELECT OBJECT_PATH
    FROM DATABASE_EXPORT_OBJECTS
    WHERE OBJECT_PATH LIKE 'RADM_%';

Output similar to the following appears:

    OBJECT_PATH
    ------------
    RADM_FPTM
    RADM_POLICY

**Parent topic:** Export of Objects That Have Oracle Data Redaction Policies Defined

##### 16.15.2.2 Exporting Only the Data Dictionary Metadata Related to Data Redaction Policies

You can export only the data dictionary metadata that is related to data redaction policies and full redaction settings.

This kind of Data Pump export could, for example, be used if you must use the same set of Data Redaction policies and settings across development, test, and production databases. Because the flag `content=metadata_only` is specified, the dump file does not contain any actual data.

- To export only the data dictionary metadata related to data redaction policies and full redaction settings, enter an `EXPDP` utility command similar to the following:

      expdp system/password \
      full=y \
      COMPRESSION=NONE \
      content=metadata_only \
      INCLUDE=RADM_FPTM,RADM_POLICY\
      directory=my_directory \
      job_name=my_job_name \
      dumpfile=my_data_redaction_policy_metadata.dmp

**See Also:**

- [Oracle Database Utilities](../sutil/oracle-data-pump-export-utility.md) for detailed information about the `INCLUDE` parameter of the `EXPDP` utility

- [Oracle Database Utilities](../sutil/oracle-data-pump-export-utility.md) for detailed information about metadata filters

**Parent topic:** Export of Objects That Have Oracle Data Redaction Policies Defined

##### 16.15.2.3 Importing Objects Using the INCLUDE Parameter in IMPDP

You can import objects using Oracle Database Pump.

- To import the objects, include these names in the `INCLUDE` parameter in the `IMPDP` utility command, based on the output from querying the `OBJECT_PATH` column in the `DATABASE_EXPORT_OBJECTS` view.

**Parent topic:** Export of Objects That Have Oracle Data Redaction Policies Defined

#### 16.15.3 Export of Data Using the EXPDP Utility access_method Parameter

Oracle Data Pump can export data from a schema that contains an object that has a Data Redaction policy.

If you are using Oracle Data Pump to perform full database export operations using the Data Pump default settings (`direct_path`), and if you receive error messages that you do not understand, then use this section to repeat the operation in such a way as to better understand the error.

If you try to use the Oracle Data Pump Export (`EXPDP`) utility with the `access_method` parameter set to `direct_path` to export data from a schema that contains an object that has a Data Redaction policy defined on it, then the following error message may appear and the export operation fails:

    ORA-31696: unable to export/import TABLE_DATA:"schema.table" using client specified DIRECT_PATH method

This problem only occurs when you perform a schema-level export as a user who was not granted the `EXP_FULL_DATABASE` role. It does not occur during a full database export, which requires the `EXP_FULL_DATABASE` role. The `EXP_FULL_DATABASE` role includes the `EXEMPT REDACTION POLICY` system privilege, which bypasses Data Redaction policies.

To find the underlying problem, try the `EXPDP` invocation again, but do not set the `access_method` parameter to `direct_path`. Instead, use either `automatic` or `external_table`. The underlying problem could be a permissions problem, for example:

    ORA-28081: Insufficient privileges - the command references a redacted object.

**See Also:**

[Oracle Database Utilities](../sutil/oracle-data-pump-export-utility.md) for more information about using Data Pump Export.

**Parent topic:** Oracle Data Redaction and Oracle Data Pump

#### 16.15.4 Import of Data into Objects Protected by Oracle Data Redaction

During import operations into Oracle Data Redaction-protected objects, be aware of issues that may occur.

##### Inadvertent Drop of Oracle Data Redaction Policies

During an import operation, be careful that you do not inadvertently drop data redaction policies that protect imported data.

Consider a scenario in which the source tables that were exported using the Oracle Data Pump Export (`EXPDP`) utility do not have Oracle Data Redaction polices. However, the destination tables to which the data is to be imported by using Oracle Data Pump Import (`IMPDP`) have Oracle Data Redaction policies.

During the Data Pump import operation, the status of the Data Redaction policies on the objects being imported depends on the `CONTENT` option of `IMPDP` command.

- If you use the `CONTENT=ALL` or `CONTENT=METADATA_ONLY` option in the `IMPDP` command, then the Data Redaction policies on the destination tables are dropped. You must recreate the Data Redaction policies.

- If you use `CONTENT=DATA_ONLY` in the `IMPDP` command, then the Data Redaction polices on the destination tables are not dropped.

##### Data Redaction Policy Not Being Imported

During an import operation, you could get an `ORA-28069: A Data Redaction Policy Already Exists On This Object` error.

Consider a scenario in which the source tables that were exported using the Oracle Data Pump Export (`EXPDP`) utility have Oracle Data Redaction policies. The destination tables to which the data is being imported by using Oracle Data Pump (`IMPDP`) also have Oracle Data Redaction policies.

During the Data Pump import operation, you could get the `ORA-28069` error. To avoid this error, you must import only the data using the `CONTENT=DATA_ONLY` parameter. Alternatively, you can drop the redaction policies on the target objects and then import all the data.

**Related Topics**

- [Oracle Database Utilities](../sutil/datapump-import-utility.md)

**Parent topic:** Oracle Data Redaction and Oracle Data Pump

### 16.16 Oracle Data Redaction and Data Masking and Subsetting Pack

Oracle Enterprise Manager Data Masking and Subsetting Pack can be used to create a development or test copy of a production database.

To accomplish this, you can mask this data in bulk, and then put the resulting masked data in the development or test copy.

You can still apply Data Redaction policies to the non-production database, in order to redact columns that contain data that was already masked by Oracle Enterprise Manager Data Masking and Subsetting Pack.

Remember that Oracle Enterprise Manager Data Masking and Subsetting Pack is used to mask data sets when you want to move the data to development and test environments. Data Redaction is mainly designed for redacting at runtime for production applications in a consistent fashion across multiple applications, without having to make application code changes.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features

### 16.17 Oracle Data Redaction and JSON

JavaScript Object Notation (JSON) can be used to create `is json` constraints on table columns.

However, you cannot create an Oracle Data Redaction policy on a table column that has the `is json` constraint. If you attempt to do so, an `ORA-28073 - The column column_name has an unsupported datatype` error is raised. As a workaround solution, Oracle recommends that you create a relational view that uses the `JSON_TABLE` row source operator on top of the JSON object, and then apply the Data Redaction policy to this view.

See [Oracle Database SQL Language Reference](../sqlrf/JSON_TABLE.md) for more information about `JASON_TABLE`.

**Parent topic:** Using Oracle Data Redaction with Oracle Database Features
