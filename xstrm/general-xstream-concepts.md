General XStream concepts apply to both XStream Out and XStream In.

- Logical Change Records (LCRs)
  An LCR is a message with a specific format that describes a database change.
- Rules and Rule Sets
  XStream uses rules and rule sets.
- Rule-Based Transformations
  In XStream, a rule-based transformation is any modification to a logical change record (LCR) when a rule in a positive rule set evaluates to `TRUE`.
- XStream and the Oracle Replication Performance Advisor
  The Oracle Replication Performance Advisor consists a collection of data dictionary views.
- XStream and SQL Generation
  SQL generation is the ability to generate the SQL statement required to perform the change encapsulated in a row LCR.

**See Also:**

- [XStream Out Concepts](xstream-out-concepts.md)

- [XStream In Concepts](xstream-in-concepts.md)

**Parent topic:** [XStream General Concepts and Use Cases](xstream-general-concepts-and-use-cases.md)

### 2.1 Logical Change Records (LCRs)

An LCR is a message with a specific format that describes a database change.

There are three types of LCRs: row LCRs, DDL LCRs, and sequence LCRs. In XStream, an LCR is the basic unit of information that describes a database change.

In an XStream Out configuration, a capture process can capture LCRs and send them to an outbound server. The outbound server can send the LCRs to the XStream client application.

In an XStream In configuration, an XStream client application can construct LCRs and send them to an inbound server. The inbound server can apply the database changes directly to the database object in the database, or the inbound server can process the LCRs in a customized way.

- Row LCRs
  A row LCR describes a change to the data in a single row or a change to a single LOB column, `LONG` column, `LONG` `RAW` column, or `XMLType` column in a row.
- DDL LCRs
  A DDL LCR describes a data definition language (DDL) change.
- Extra Information in Row LCRs and DDL LCRs
  In addition to the information discussed in the previous sections, row LCRs and DDL LCRs optionally can include extra information (or LCR attributes).
- Sequence LCRs
  A sequence LCR is a row LCR that includes information about sequence values. Sequence database objects generate sequence values.
- Position Order in an LCR Stream
  Each LCR has a position attribute. The position of an LCR identifies its placement in the stream of LCRs in a transaction.
- LCRIDs and the Position of LCRs
  An LCRID is the raw value that specifies the position of an LCR for XStream Out. It is strictly increasing, uniquely identifies an LCR, and is persistent across restart. XStream uses LCRID values for ordering logical change records (LCRs) and for determining which LCRs and transactions have been received and applied.

**Parent topic:** General XStream Concepts

#### 2.1.1 Row LCRs

A row LCR describes a change to the data in a single row or a change to a single LOB column, `LONG` column, `LONG` `RAW` column, or `XMLType` column in a row.

The change results from a data manipulation language (DML) statement or a piecewise operation. It may help to think of a row LCR as a DML LCR. For example, a single DML statement can insert or merge multiple rows into a table, can update multiple rows in a table, or can delete multiple rows from a table.

Since a single DML statement can affect more than one row, the capture process creates a row LCR for each row that is changed by the DML statement. Row LCRs represent the data changes made by a SQL or PL/SQL procedure invocation.

Each row LCR is encapsulated in an object of `LCR$_ROW_RECORD` type. The following table describes the attributes that are present in each row LCR.

Table 2-1 Attributes Present in All Row LCRs

| Attribute              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `source_database_name` | The name of the source database where the row change occurred.<br>If the LCRs originated in a multitenant container database (CDB), then this attribute specifies the global name container where the row change occurred.                                                                                                                                                                                                                                                                       |
| `command_type`         | The type of DML statement that produced the change, either `INSERT`, `UPDATE`, `DELETE`, `LOB` `ERASE`, `LOB` `WRITE`, or `LOB` `TRIM`.                                                                                                                                                                                                                                                                                                                                                          |
| `object_owner`         | The schema name that contains the table with the changed row.                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `object_name`          | The name of the table that contains the changed row.                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `tag`                  | A raw tag that you can use to track the LCR.                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `transaction_id`       | The identifier of the transaction in which the DML statement was run.                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `scn`                  | The system change number (SCN) at the time when the change was made.                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `old_values`           | The old column values related to the change. These are the column values for the row before the DML change. If the type of the DML statement is `UPDATE` or `DELETE`, then these old values include some or all of the columns in the changed row before the DML statement. If the type of the DML statement is `INSERT`, then there are no old values. For `UPDATE` and `DELETE` statements, row LCRs created by a capture process can include some or all of the old column values in the row. |
| `new_values`           | The new column values related to the change. These are the column values for the row after the DML change. If the type of the DML statement is `UPDATE` or `INSERT`, then these new values include some or all of the columns in the changed row after the DML statement. If the type of the DML statement is `DELETE`, then there are no new values. For `UPDATE` and `INSERT` statements, row LCRs created by a capture process can include some or all of the new column values in the row.   |
| `position`             | A unique identifier of `RAW` data type for each LCR. The position is strictly increasing within a transaction and across transactions.<br>LCR position is commonly used in XStream configurations.<br>See "Position Order in an LCR Stream".                                                                                                                                                                                                                                                     |
| `root_name`            | If the LCR originated in a CDB, then this attribute specifies the global name of the root in the CDB.<br>If the LCR originated in a non-CDB, then this attribute is the same as the `source_database_name` attribute.                                                                                                                                                                                                                                                                            |

Row LCRs that were captured by a capture process in an XStream Out configuration contain additional attributes. The following table describes these additional attributes. These attributes are not present in row LCRs constructed by an XStream client application in an XStream In configuration.

Table 2-2 Additional Attributes in LCRs Captured by a Capture Process

| Attribute                  | Description                                                                                                                                                                                                      |
|:---------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `commit_scn`               | The commit system change number (SCN) of the transaction to which the LCR belongs.                                                                                                                               |
| `commit_scn_from_position` | The commit system change number (SCN) of a transaction determined by the input position, which is generated by an XStream outbound server.                                                                       |
| `commit_time`              | The commit time of the transaction to which the LCR belongs.                                                                                                                                                     |
| `compatible`               | The minimal database compatibility required to support the LCR.                                                                                                                                                  |
| `instance_number`          | The instance number of the database instance that made the change that is encapsulated in the LCR. Typically, the instance number is relevant in an Oracle Real Application Clusters (Oracle RAC) configuration. |
| `lob_information`          | The LOB information for the column, such as `NOT_A_LOB` or `LOB_CHUNK`.                                                                                                                                          |
| `lob_offset`               | The LOB offset for the specified column in the number of characters for `CLOB` columns and the number of bytes for `BLOB` columns.                                                                               |
| `lob_operation_size`       | The operation size for the LOB column in the number of characters for `CLOB` columns and the number of bytes for `BLOB` columns.                                                                                 |
| `long_information`         | The `LONG` information for the column, such as `NOT_A_LONG` or `LONG_CHUNK`.                                                                                                                                     |
| `row_text`                 | The SQL statement for the change that is encapsulated in the row LCR.                                                                                                                                            |
| `scn_from_position`        | The SCN of the LCR.                                                                                                                                                                                              |
| `source_time`              | The time when the change in an LCR captured by a capture process was generated in the redo log of the source database, or the time when a persistent LCR was created.                                            |
| `xml_information`          | The XML information for the column, such as `NOT_XML`, `XML_DOC`, or `XML_DIFF`.                                                                                                                                 |

- Row LCR Subtypes
  A row LCR can also contain transaction control statements. These row LCRs contain transaction control directives such as `COMMIT` and `ROLLBACK`.

**Parent topic:** Logical Change Records (LCRs)

##### 2.1.1.1 Row LCR Subtypes

A row LCR can also contain transaction control statements. These row LCRs contain transaction control directives such as `COMMIT` and `ROLLBACK`.

Such row LCRs are internal and can be used by outbound servers, inbound servers, and XStream client applications to maintain transaction consistency.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/Logical-Change-Record-TYPEs.md)

**Parent topic:** Row LCRs

#### 2.1.2 DDL LCRs

A DDL LCR describes a data definition language (DDL) change.

A DDL statement changes the structure of the database. For example, a DDL statement can create, alter, or drop a database object.

Each DDL LCR is encapsulated in an object of `LCR$_DDL_RECORD` type. The following table describes the attributes that are present in each DDL LCR.

Table 2-3 Attributes Present in All DDL LCRs

| Attribute              | Description                                                                                                                                                                                                                                  |
|:-----------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `source_database_name` | The name of the source database where the DDL change occurred.<br>If the LCRs originated in a CDB, then this attribute specifies the global name of the container where the DDL change occurred.                                             |
| `command_type`         | The type of DDL statement that produced the change, for example `ALTER` `TABLE` or `CREATE` `INDEX`.                                                                                                                                         |
| `object_owner`         | The schema name of the user who owns the database object on which the DDL statement was run.                                                                                                                                                 |
| `object_name`          | The name of the database object on which the DDL statement was run.                                                                                                                                                                          |
| `object_type`          | The type of database object on which the DDL statement was run, for example `TABLE` or `PACKAGE`.                                                                                                                                            |
| `ddl_text`             | The text of the DDL statement.                                                                                                                                                                                                               |
| `logon_user`           | The logon user, which is the user whose session executed the DDL statement.                                                                                                                                                                  |
| `current_schema`       | The schema that is used if no schema is specified for an object in the DDL text.                                                                                                                                                             |
| `base_table_owner`     | The base table owner. If the DDL statement is dependent on a table, then the base table owner is the owner of the table on which it is dependent.                                                                                            |
| `base_table_name`      | The base table name. If the DDL statement is dependent on a table, then the base table name is the name of the table on which it is dependent.                                                                                               |
| `tag`                  | A raw tag that you can use to track the LCR.                                                                                                                                                                                                 |
| `transaction_id`       | The identifier of the transaction in which the DDL statement was run.                                                                                                                                                                        |
| `scn`                  | The system change number (SCN) at the time when the change was made.                                                                                                                                                                         |
| `position`             | A unique identifier of `RAW` data type for each LCR. The position is strictly increasing within a transaction and across transactions.<br>LCR position is commonly used in XStream configurations.<br>See "Position Order in an LCR Stream". |
| `edition_name`         | The name of the edition in which the DDL statement was executed.                                                                                                                                                                             |
| `root_name`            | If the LCR originated in a CDB, then this attribute specifies the global name of the root in the CDB.<br>If the LCR originated in a non-CDB, then this attribute is the same as the `source_database_name` attribute.                        |

DDL LCRs that were captured by a capture process contain additional attributes. The following table describes these additional attributes. These attributes are not present in DDL LCRs constructed by an XStream client application in an XStream In configuration.

Table 2-4 Additional Attributes in DDL LCRs Captured by a Capture Process

| Attribute                  | Description                                                                                                                                                                                                      |
|:---------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `commit_scn`               | The commit system change number (SCN) of the transaction to which the LCR belongs.                                                                                                                               |
| `commit_scn_from_position` | The commit SCN of a transaction determined by the input position, which is generated by an XStream outbound server.                                                                                              |
| `commit_time`              | The commit time of the transaction to which the LCR belongs.                                                                                                                                                     |
| `compatible`               | The minimal database compatibility required to support the LCR.                                                                                                                                                  |
| `instance_number`          | The instance number of the database instance that made the change that is encapsulated in the LCR. Typically, the instance number is relevant in an Oracle Real Application Clusters (Oracle RAC) configuration. |
| `scn_from_position`        | The SCN of the LCR.                                                                                                                                                                                              |
| `source_time`              | The time when the change in an LCR captured by a capture process was generated in the redo log of the source database, or the time when a persistent LCR was created.                                            |

**Note:**

Both row LCRs and DDL LCRs contain the source database name of the database where a change originated. To avoid problems, Oracle recommends that you do not change the global name of the source database after a capture process has started capturing changes.

**See Also:**

- [Oracle Call Interface Programmer's Guide](../lnoci/handle-and-descriptor-attributes.md) for a complete list of the types of DDL statements in the "SQL Command Codes" table

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/Logical-Change-Record-TYPEs.md)

**Parent topic:** Logical Change Records (LCRs)

#### 2.1.3 Extra Information in Row LCRs and DDL LCRs

In addition to the information discussed in the previous sections, row LCRs and DDL LCRs optionally can include extra information (or LCR attributes).

The extra attributes in LCRs are described in the following table.

Table 2-5 Extra Attributes in LCRs

| Attribute  | Description                                                                                                                                                                                             |
|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `row_id`   | The rowid of the row changed in a row LCR. This attribute is not included in DDL LCRs or row LCRs for index-organized tables.                                                                           |
| `serial#`  | The serial number of the session that performed the change captured in the LCR.                                                                                                                         |
| `session#` | The identifier of the session that performed the change captured in the LCR.                                                                                                                            |
| `thread#`  | The thread number of the instance in which the change captured in the LCR was performed. Typically, the thread number is relevant only in an Oracle Real Application Clusters (Oracle RAC) environment. |
| `tx_name`  | The name of the transaction that includes the LCR.                                                                                                                                                      |
| `username` | The name of the current user who performed the change captured in the LCR.                                                                                                                              |

You can use the `INCLUDE_EXTRA_ATTRIBUTE` procedure in the `DBMS_CAPTURE_ADM` package to instruct a capture process to capture one or more extra attributes.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_CAPTURE_ADM.md) for more information about the `INCLUDE_EXTRA_ATTRIBUTE` procedure

- [Oracle Database PL/SQL Language Reference](../lnpls/invokers-rights-and-definers-rights-authid-property.md) for more information about the current user

**Parent topic:** Logical Change Records (LCRs)

#### 2.1.4 Sequence LCRs

A sequence LCR is a row LCR that includes information about sequence values. Sequence database objects generate sequence values.

You can stream sequence LCRs in the following ways:

- To capture sequence LCRs using a capture process, set the capture process parameter `capture_sequence_nextval` to `Y`.

- To construct sequence LCRs using the OCI interface, use the `OCILCRNew` function and the `OCILCRHeaderSet` function with the `OCI_ROWLCR_SEQ_LCR` flag.

- To construct sequence LCRs using the Java interface, use the `DefaultRowLCR` constructor and `setSequenceLCRFlag` method.

An XStream inbound server or an Oracle Apply process can use sequence LCRs to ensure that the sequence values at a destination database use the appropriate values. For increasing sequences, the sequence values at the destination are equal to or greater than the sequence values at the source database. For decreasing sequences, the sequence values at the destination are less than or equal to the sequence values at the source database. To instruct an inbound server or apply process to use sequence LCRs, set the `apply_sequence_nextval` apply parameter to `Y`.

**Note:**

Sequence LCRs are intended for one-way replication configurations. Sequence LCRs cannot be used in bidirectional replication configurations.

**See Also:**

- "[Setting a Capture Process Parameter](managing-xstream-out.md)"

- [Oracle Call Interface Programmer's Guide](../lnoci/oci-XStream.md) for more information about the OCI interface

- [Oracle Database XStream Java API Reference](../stxjv/index.md) for more information about the Java interface

- [Oracle Database Administrator’s Guide](../admin/managing-views-sequences-and-synonyms.md) for information about sequences

**Parent topic:** Logical Change Records (LCRs)

#### 2.1.5 Position Order in an LCR Stream

Each LCR has a position attribute. The position of an LCR identifies its placement in the stream of LCRs in a transaction.

Both XStream Out and XStream In use LCR streams to share transactions. XStream Out sends LCR streams to a client application. XStream In receives LCR streams from a client application.

Each LCR position has the following properties:

- The position is unique for each LCR.

- The position is of `RAW` data type.

- The position is strictly increasing within the LCR stream, within a transaction, and across transactions.

- The position is byte-comparable, and the comparison results for multiple positions determines the ordering of the LCRs in the stream.

- The position of an LCR remains identical when the database, the client application, or an XStream component restarts.

- The position is not affected by any rule changes that might reduce or increase the number of LCRs in the stream.

XStream Out only sends committed data, and XStream In only receives committed data.

The following are the properties related to an LCR stream:

- An LCR stream must be repeatable.

- An LCR stream must contain a list of assembled, committed transactions. LCRs from one transaction are contiguous. There is no interleaving of transactions in an LCR stream.

- Each transaction within an LCR stream must have an ordered list of LCRs and a transaction ID.

- The last LCR in each transaction must be a commit LCR.

- Each LCR must have a unique position.

- The position of all LCRs within a single transaction and across transactions must be strictly increasing.

An LCR stream can batch LCRs from multiple transactions and arrange them in increasing position order. LCRs from one transaction are contiguous, and the position must be increasing in the transaction. Also, the position must be nonzero for all LCRs.

**See Also:**

- "[Position of LCRs and XStream Out](xstream-out-concepts.md)"

- "[Position of LCRs and XStream In](xstream-in-concepts.md)"

**Parent topic:** Logical Change Records (LCRs)

#### 2.1.6 LCRIDs and the Position of LCRs

An LCRID is the raw value that specifies the position of an LCR for XStream Out. It is strictly increasing, uniquely identifies an LCR, and is persistent across restart. XStream uses LCRID values for ordering logical change records (LCRs) and for determining which LCRs and transactions have been received and applied.

Starting with Oracle Database 12c Release 2 (12.2.0.1), the LCRID is versioned. When you create or add an outbound server, you can choose the LCRID version it uses. To specify version 2, the database compatibility level must be at 12.2.0 or higher. By default, an outbound server created or added when database compatibility is lower than 12.2.0 uses LCRID version 1, and an outbound server created or added when database compatibility is at 12.2.0 or higher uses LCRID version 2. You might choose to use LCRID version 1 for an outbound server if, for example, the outbound server captures LCRs that will be applied at a database that is at a lower compatibility level.

After an outbound server is created or added, its LCRID version cannot be changed. To change the LCRID version, you must drop and re-create the outbound server. If the outbound server was sending LCRs to an inbound server, then you must drop and re-create the inbound server.

The same database change has different LCRID values for version 1 and version 2. New functions in the `DBMS_XSTREAM_ADM` package enable you to compare any stored LCRID values in different versions and convert LCRID values from one version to another. Specifically, the `COMPARE_POSITION` function compares two LCRID values, and the `CONVERT_POSITION` function converts LCRID values from one version to another.

**Related Topics**

- [Configuring XStream Out](configuring-xstream-out.md)

**Parent topic:** Logical Change Records (LCRs)

### 2.2 Rules and Rule Sets

XStream uses rules and rule sets.

- Rules and Rule Sets Defined
  A rule is a database object that enables a client to perform an action when an event occurs and a condition is satisfied. In an XStream configuration, rules identify which LCRs to stream from one component to another.
- Rule Sets and XStream Components
  An XStream component performs its task if a database change satisfies its rule sets.
- System-Created Rules and XStream
  An XStream component performs its task for an LCR if the LCR satisfies its rule sets. A system-created rule is created by the `DBMS_XSTREAM_ADM` package.

**See Also:**

- "[Managing Rules for an XStream Out Configuration](managing-xstream-out.md)"

- "[Monitoring XStream Rules](monitoring-xstream-out.md)"

**Parent topic:** General XStream Concepts

#### 2.2.1 Rules and Rule Sets Defined

A rule is a database object that enables a client to perform an action when an event occurs and a condition is satisfied. In an XStream configuration, rules identify which LCRs to stream from one component to another.

Capture processes, propagations, outbound servers and inbound servers can use rules. You can configure rules for each XStream component independently, and the rules for different XStream components do not need to match.

A rule set is a collection of rules. The behavior of each XStream component is determined by the rules in the rule sets that are associated with it. You can associate a positive rule set and a negative rule set with each XStream component.

In addition, a single rule pertains to either the results of data manipulation language (DML) changes or data definition language (DDL) changes. So, for example, you must use at least two rules to include all of the changes to a particular table: one rule for the results of DML changes and another rule for DDL changes.

The results of a DML change are row changes, and an LCR that encapsulates a row change is called a row LCR. A single DML change can result in multiple row changes. Therefore, a single DML change can result in multiple row LCRs. An LCR that encapsulates a DDL change is called a DDL LCR.

**Parent topic:** Rules and Rule Sets

#### 2.2.2 Rule Sets and XStream Components

An XStream component performs its task if a database change satisfies its rule sets.

In general, a change satisfies the rule sets when no rules in the negative rule set evaluate to `TRUE` for the change and at least one rule in the positive rule set evaluates to `TRUE` for the change. The negative rule set is always evaluated first.

You use rule sets in an XStream configuration to specify the following:

- Changes that a capture process captures from the redo log or discards. If a change found in the redo log satisfies the rule sets for a capture process, then the capture process captures the change. If a change found in the redo log does not satisfy the rule sets for a capture process, then the capture process discards the change.

  In XStream Out configurations that share one capture process among several outbound servers, the rules for the capture process must pass the LCRs that are needed by any of the outbound servers that share the capture process.

- The LCRs that a propagation sends from one queue to another or discards. If an LCR in a queue satisfies the rule sets for a propagation, then the propagation sends the LCR. If an LCR in a queue does not satisfy the rule sets for a propagation, then the propagation discards the LCR.

- The LCRs that an outbound server sends to an XStream client application or discards. If an LCR satisfies the rule sets for an outbound server, then the outbound server sends the LCR to the XStream client application. If an LCR does not satisfy the rule sets for an outbound server, then the outbound server discards the LCR.

- The LCRs that an inbound server applies or discards. If an LCR satisfies the rule sets for an inbound server, then the inbound server applies the LCR. If an LCR in not satisfy the rule sets for an inbound server, then the inbound server discards the LCR.

When an XStream component has no rule sets, the component performs its task for all database changes. For example, if an inbound server has no rule sets, then it applies all of the LCRs sent to it by an XStream client application.

**Parent topic:** Rules and Rule Sets

#### 2.2.3 System-Created Rules and XStream

An XStream component performs its task for an LCR if the LCR satisfies its rule sets. A system-created rule is created by the `DBMS_XSTREAM_ADM` package.

A system-created rule can specify one of the following levels of granularity: table, schema, or global.

- XStream System-Created Rule Procedures
  Several PL/SQL procedures in the `DBMS_XSTREAM_ADM` package can create system-generated rules.
- Global Rules
  When you use a rule to specify a task that is relevant to an entire database, you are specifying a global rule.
- Schema Rules
  When you use a rule to specify a task that is relevant to a schema, you are specifying a schema rule.
- Table Rules
  When you use a rule to specify a task that is relevant to a table, you are specifying a table rule.
- Subset Rules
  A subset rule is a special type of table rule for DML changes that is relevant only to a subset of the rows in a table.
- System-Created Rules and a Multitenant Environment
  A multitenant environment enables an Oracle database to contain a portable set of schemas, objects, and related structures that appears logically to an application as a separate database. This self-contained collection is called a pluggable database (PDB). A CDB contains PDBs.

**See Also:**

- "[Managing Rules for an XStream Out Configuration](managing-xstream-out.md)"

- "[Monitoring XStream Rules](monitoring-xstream-out.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

**Parent topic:** Rules and Rule Sets

##### 2.2.3.1 XStream System-Created Rule Procedures

Several PL/SQL procedures in the `DBMS_XSTREAM_ADM` package can create system-generated rules.

There are three types of procedures that create system-created rules:

- Procedures that create or alter an outbound server and the rules for the outbound server

  These procedures include `CREATE_OUTBOUND`, `ADD_OUTBOUND`, and `ALTER_OUTBOUND`. These procedures make it easy to configure XStream Out quickly. If they meet your needs, then you should use these procedures to simplify XStream Out configuration. The `CREATE_OUTBOUND` procedure creates the queue and capture process used by the outbound server in addition to the outbound server.

- Procedures that create a propagation or add rules to an existing propagation

  These procedures include the `ADD_*_PROPAGATION_RULES` procedures. If the specified propagation does not exist, then these procedures create the propagation and add rules to the propagation's rule sets. If the specified propagation exists, then these procedures add rules to the existing propagation's rule sets.

- Procedures that add rules to an existing XStream component, such as a capture process, outbound server, or inbound server

  These procedures include the `ADD_*_RULES` procedures. These procedure provide more flexibility and fine-grained control over the system-created rules. You should use these procedures when necessary to add rules to your XStream configuration.

The following table describes which procedures can create rules for which XStream components.

Table 2-6 XStream System-Created Rule Procedures

| Procedure                      | Capture Process | Propagation | Outbound Server | Inbound Server |
|:-------------------------------|:----------------|:------------|:----------------|:---------------|
| `CREATE_OUTBOUND`              | Yes             | No          | Yes             | No             |
| `ADD_OUTBOUND`                 | No              | No          | Yes             | No             |
| `ALTER_OUTBOUND`               | Yes             | No          | Yes             | No             |
| `ADD_GLOBAL_RULES`             | Yes             | No          | Yes             | Yes            |
| `ADD_GLOBAL_PROPAGATION_RULES` | No              | Yes         | No              | No             |
| `ADD_SCHEMA_RULES`             | Yes             | No          | Yes             | Yes            |
| `ADD_SCHEMA_PROPAGATION_RULES` | No              | Yes         | No              | No             |
| `ADD_GLOBAL_RULES`             | Yes             | No          | Yes             | Yes            |
| `ADD_SUBSET_OUTBOUND_RULES`    | No              | No          | Yes             | No             |
| `ADD_SUBSET_RULES`             | Yes             | No          | Yes             | Yes            |
| `ADD_SUBSET_PROPAGATION_RULES` | No              | Yes         | No              | No             |
| `ADD_TABLE_RULES`              | Yes             | No          | Yes             | Yes            |
| `ADD_TABLE_PROPAGATION_RULES`  | No              | Yes         | No              | No             |

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md) for detailed information about these procedures

**Parent topic:** System-Created Rules and XStream

##### 2.2.3.2 Global Rules

When you use a rule to specify a task that is relevant to an entire database, you are specifying a global rule.

You can specify a global rule for DML changes, a global rule for DDL changes, or a global rule for each type of change (two rules total).

A single global rule in the positive rule set for a capture process means that the capture process captures the results of either all DML changes or all DDL changes to the source database. A single global rule in the negative rule set for a capture process means that the capture process discards the results of either all DML changes or all DDL changes to the source database.

A single global rule in the positive rule set for a propagation means that the propagation rule controls the set of LCRs that are applicable to a specific outbound server. If a single capture services multiple outbound servers, the set of changes distributed to each outbound server is controlled by the propagation rules (the capture rules are the superset of all changes). A single global rule in the negative rule set for a propagation means that the propagation discards either all row LCRs or all DDL LCRs from the capture process.

A single global rule in the positive rule set for an outbound server means that the outbound server sends either all row LCRs or all DDL LCRs that it receives to an XStream client application. A single global rule in the negative rule set for an outbound server means that the outbound server discards either all row LCRs or all DDL LCRs that it receives.

A single global rule in the positive rule set for an inbound server means that the inbound server applies either all row LCRs or all DDL LCRs sent to it by the XStream client application. A single global rule in the negative rule set for an inbound server means that the inbound server discards either all row LCRs or all DDL LCRs sent to it by the XStream client application.

When an inbound server should apply all of the LCRs it receives from its client application, you can configure the inbound server with no rule sets instead of using global rules. Also, for an inbound server to perform best, it should not receive LCRs that it should not apply.

To specify global rules for an outbound server, use the `ALTER_OUTBOUND` procedure or, for specifying a greater level of detail, the `ADD_GLOBAL_RULES` procedure in the `DBMS_XSTREAM_ADM` package.

To specify global rules for an inbound server, use the `ALTER_INBOUND` procedure or, for specifying a greater level of detail, the `ADD_GLOBAL_RULES` procedure in the `DBMS_XSTREAM_ADM` package.

**See Also:**

- "[Managing Rules for an XStream Out Configuration](managing-xstream-out.md)"

- "[Monitoring XStream Rules](monitoring-xstream-out.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

**Parent topic:** System-Created Rules and XStream

##### 2.2.3.3 Schema Rules

When you use a rule to specify a task that is relevant to a schema, you are specifying a schema rule.

You can specify a schema rule for DML changes, a schema rule for DDL changes, or a schema rule for each type of change to the schema (two rules total).

A single schema rule in the positive rule set for a capture process means that the capture process captures either the DML changes or the DDL changes to the schema. A single schema rule in the negative rule set for a capture process means that the capture process discards either the DML changes or the DDL changes to the schema.

A single schema rule in the positive rule set for a propagation means that the propagation propagates either the row LCRs or the DDL LCRs in the source queue that contain changes to the schema. A single schema rule in the negative rule set for a propagation means that the propagation discards either the row LCRs or the DDL LCRs in the source queue that contain changes to the schema.

A single schema rule in the positive rule set for an outbound server means that the outbound server sends either the row LCRs or the DDL LCRs that it receives that contain changes to the schema to an XStream client application. A single schema rule in the negative rule set for an outbound server means that the outbound server discards either the row LCRs or the DDL LCRs that it receives that contain changes to the schema.

A single schema rule in the positive rule set for an inbound server means that the inbound server applies either the row LCRs or the DDL LCRs that it receives from an XStream client application that contain changes to the schema. A single schema rule in the negative rule set for an inbound server means that the inbound server discards either the row LCRs or the DDL LCRs that it receives from an XStream client application that contain changes to the schema.

To specify schema rules for either an outbound server or an inbound server, use the `ALTER_OUTBOUND` procedure or the `ADD_SCHEMA_RULES` procedure in the `DBMS_XSTREAM_ADM` package.

**See Also:**

- "[Managing Rules for an XStream Out Configuration](managing-xstream-out.md)"

- "[Monitoring XStream Rules](monitoring-xstream-out.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

**Parent topic:** System-Created Rules and XStream

##### 2.2.3.4 Table Rules

When you use a rule to specify a task that is relevant to a table, you are specifying a table rule.

You can specify a table rule for DML changes, a table rule for DDL changes, or a table rule for each type of change to the table (two rules total).

A single table rule in the positive rule set for a capture process means that the capture process captures either the DML changes or the DDL changes to the table. A single table rule in the negative rule set for a capture process means that the capture process discards either the DML changes or the DDL changes to the table.

A single table rule in the positive rule set for a propagation means that the propagation propagates either the row LCRs or the DDL LCRs in the source queue that contain changes to the table. A single table rule in the negative rule set for a propagation means that the propagation discards either the row LCRs or the DDL LCRs in the source queue that contain changes to the table.

A single table rule in the positive rule set for an outbound server means that the outbound server sends either the row LCRs or the DDL LCRs that it receives that contain changes to the table to an XStream client application. A single table rule in the negative rule set for an outbound server means that the outbound server discards either the row LCRs or the DDL LCRs that it receives that contain changes to the table.

A single table rule in the positive rule set for an inbound server means that the inbound server applies either the row LCRs or the DDL LCRs that it receives from an XStream client application that contain changes to the table. A single table rule in the negative rule set for an inbound server means that the inbound server discards either the row LCRs or the DDL LCRs that it receives from an XStream client application that contain changes to the table.

To specify table rules for an outbound server or inbound server, use either the `ALTER_OUTBOUND` procedure or `ADD_TABLE_RULES` in the `DBMS_XSTREAM_ADM` package.

**Parent topic:** System-Created Rules and XStream

##### 2.2.3.5 Subset Rules

A subset rule is a special type of table rule for DML changes that is relevant only to a subset of the rows in a table.

When you create a subset rule, you use a condition similar to a `WHERE` clause in a `SELECT` statement to specify the following:

- That a capture process only captures a subset of the row changes resulting from DML changes to a particular table

- That a propagation only propagates a subset of the row LCRs relating to a particular table

- That an outbound server only sends a subset of the row LCRs relating to a particular table to an XStream client application

- That an inbound server only applies a subset of the row LCRs relating to a particular table

Supplemental logging is required when you specify the following types of subset rules:

- Subset rules for a capture process

- Subset rules for a propagation that will propagate LCRs captured by a capture process

- Subset rules for an outbound server that will send LCRs captured by a capture process to an XStream client application

In any of these cases, an unconditional supplemental log group must be specified at the source database for all the columns in the subset condition. In some cases, when a subset rule is specified, an update can be converted to an insert, and, in these cases, supplemental information might be needed for some or all of the columns.

To specify subset rules for an outbound server, use the `ADD_SUBSET_OUTBOUND_RULES`, `ADD_SUBSET_RULES,` or the `REMOVE_SUBSET_OUTBOUND_RULES` procedures in the `DBMS_XSTREAM_ADM` package.

**See Also:**

- "[If Required, Configure Supplemental Logging](configuring-xstream-out.md)"

- "[Adding Subset Rules to an Outbound Server's Positive Rule Set](managing-xstream-out.md)"

- "[Removing Subset Rules from an Outbound Server's Positive Rule Set](managing-xstream-out.md)"

- "[Monitoring XStream Rules](monitoring-xstream-out.md)"

**Parent topic:** System-Created Rules and XStream

##### 2.2.3.6 System-Created Rules and a Multitenant Environment

A multitenant environment enables an Oracle database to contain a portable set of schemas, objects, and related structures that appears logically to an application as a separate database. This self-contained collection is called a pluggable database (PDB). A CDB contains PDBs.

It can also contain application containers. An application container is an optional component of a CDB that consists of an application root and the application PDBs associated with it. An application container stores data for one or more applications. An application container shares application metadata and common data. In a CDB, each of the following is a container: the CDB root, each PDB, each application root, and each application PDB.

In a CDB, LCRs can contain the global name of the container where the change originated in the `source_database_name` attribute and the global name of the CDB root in the `root_name` attribute. The rules for XStream components can consider these attributes.

- System-Created Rules in a CDB and XStream Out
  In a CDB, XStream Out must be configured in the CDB root. Therefore, the PL/SQL procedures in the `DBMS_XSTREAM_ADM` package that create system-created rules must be run in the CDB root while connected as a common user.
- System-Created Rules in a CDB and XStream In
  You can configure XStream In in the root or in any container in a CDB.

**Related Topics**

- [Oracle Multitenant Administrator's Guide](../multi/multitenant-architecture.md)

**Parent topic:** System-Created Rules and XStream

###### 2.2.3.6.1 System-Created Rules in a CDB and XStream Out

In a CDB, XStream Out must be configured in the CDB root. Therefore, the PL/SQL procedures in the `DBMS_XSTREAM_ADM` package that create system-created rules must be run in the CDB root while connected as a common user.

Excluding the procedures that create rules for propagations, the procedures that create system-created rules for XStream Out, such as the `ADD_GLOBAL_RULES` procedure, include the key parameters in the following table:

Table 2-7 Key Procedure Parameters for System-Created Rules in a CDB

| Parameter               | Description                                                                                                                                                                                                                                                                          |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `source_database`       | The global name of the source database. In a CDB, specify the global name of the container to which the rules pertain. The container can be the CDB root, a PDB, an application root, or an application PDB. The following are examples: `mycdb.example.com` or `hrpdb.example.com`. |
| `source_root_name`      | The global name of the CDB root in the source CDB. The following are examples: `mycdb.example.com`.                                                                                                                                                                                  |
| `source_container_name` | The short name of the source container. The container can be the CDB root, a PDB, an application root, or an application PDB. The following are examples: `CDB$ROOT` or `hrpdb`.                                                                                                     |

If you do not include the domain name when you specify `source_database` or `source_root_name`, then the procedure appends it to the name automatically. For example, if you specify `DBS1` and the domain is `.EXAMPLE.COM`, then the procedure specifies `DBS1.EXAMPLE.COM` automatically.

The combination of these key parameters determines which containers' changes XStream Out captures and streams to the client application, based on the rules generated by the procedures. Regardless of the settings for these parameters, system-generated rules can still limit the changes captured and streamed to specific schemas and tables.

Local capture means that a capture process runs on the source CDB. In a local capture configuration, the `source_root_name` parameter specifies the global name of the CDB root in the local CDB. If this parameter is `NULL`, then the global name of the CDB root in the local CDB is specified automatically. The resulting rules include a condition for the global name of the CDB root in the current CDB.

Downstream capture means that a capture process runs on a CDB other than the source CDB. In a downstream capture configuration, the `source_root_name` parameter must be non-`NULL`, and it must specify the global name of the CDB root in the remote source CDB. The resulting rules include a condition for the global name of the CDB root in the remote CDB. If this parameter is `NULL`, then local capture is assumed.

The following table describes the rule conditions for various `source_database` and `source_container_name` parameter settings in a local capture configuration.

Table 2-8 Local Capture and XStream Out Container Rule Conditions

| source_database Parameter Setting | source_container_name Parameter Setting | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:----------------------------------|:----------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NULL`                            | `NULL`                                  | XStream Out captures and streams changes made in any container in the local CDB, including the CDB root, all PDBs, all application roots, and all application PDBs.                                                                                                                                                                                                                                                                                                            |
| non-`NULL`                        | `NULL`                                  | XStream Out captures and streams changes made in the specified source container of the local CDB. The source container can be the CDB root, a PDB, an application root, or an application PDB. The `DBMS_XSTREAM_ADM` procedure queries the `CDB_PDBS` view and `CDB_PROPERTIES` view to determine the `source_container_name` value.                                                                                                                                          |
| `NULL`                            | non-`NULL`                              | XStream Out captures and streams changes made in the specified source container of the local CDB. The source container can be the CDB root, a PDB, an application root, or an application PDB. The `DBMS_XSTREAM_ADM` procedure queries the `CDB_PDBS` view and `CDB_PROPERTIES` view to determine the `source_database` value.                                                                                                                                                |
| non-`NULL`                        | non-`NULL`                              | XStream Out captures and streams changes made in the specified source container of the local CDB. The source container can be the CDB root, a PDB, an application root, or an application PDB.<br>If the prefix of the `source_database` value is different from the `source_container_name` value, then the resulting rules include a condition for the `source_database` value, and an internal table maps the `source_database` value to the `source_container_name` value. |

The following table describes the rule conditions for various `source_database` and `source_container_name` parameter settings in a downstream capture configuration.

Table 2-9 Downstream Capture and XStream Out Container Rule Conditions

| source_database Parameter Setting | source_container_name Parameter Setting | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------------------------------|:----------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NULL`                            | `NULL`                                  | XStream Out captures and streams changes made in any container in the remote source CDB, including the CDB root, all PDBs, all application roots, and all application PDBs.                                                                                                                                                                                                                                                                                                            |
| non-`NULL`                        | `NULL`                                  | XStream Out captures and streams changes made in the specified source container of the remote source CDB. The source container can be the CDB root, a PDB, an application root, or an application PDB. The `DBMS_XSTREAM_ADM` procedure derives the `source_container_name` value from the prefix of `source_database` value.                                                                                                                                                          |
| `NULL`                            | non-`NULL`                              | The `DBMS_XSTREAM_ADM` procedure raises an error.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| non-`NULL`                        | non-`NULL`                              | XStream Out captures and streams changes made in the specified source container of the remote source CDB. The source container can be the CDB root, a PDB, an application root, or an application PDB.<br>If the prefix of the `source_database` value is different from the `source_container_name` value, then the resulting rules include a condition for the `source_database` value, and an internal table maps the `source_database` value to the `source_container_name` value. |

**Related Topics**

- [Local Capture and Downstream Capture](xstream-out-concepts.md)
- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_XSTREAM_ADM.md)

**Parent topic:** System-Created Rules and a Multitenant Environment

###### 2.2.3.6.2 System-Created Rules in a CDB and XStream In

You can configure XStream In in the root or in any container in a CDB.

Typically, an inbound server does not use rule sets or rules. Instead, it usually processes all LCRs that it receives from its client application. An inbound server can apply changes to the current container only. Therefore, if an inbound server is configured in the CDB root, then it can apply changes only to the CDB root. If an inbound server is configured in a PDB, then it can apply changes only to that PDB. If an inbound server is configured in an application root, then it can apply changes only to that application root, and if an inbound server is configured in an application PDB, then it can apply changes only to that application PDB.

**Related Topics**

- [Oracle Multitenant Administrator's Guide](../multi/managing-a-multitenant-environment.md)

**Parent topic:** System-Created Rules and a Multitenant Environment

### 2.3 Rule-Based Transformations

In XStream, a rule-based transformation is any modification to a logical change record (LCR) when a rule in a positive rule set evaluates to `TRUE`.

In general, it is best for the client application to perform transformations of the data. If this is not possible, then the database can perform some simple transformations on DML LCRs.

- Declarative Rule-Based Transformations
  Declarative rule-based transformations cover a set of common transformation scenarios for row LCRs.
- Declarative Rule-Based Transformation Ordering
  The order in which different types of rule-based transformations is evaluated is important as results will vary.
- Evaluating Transformation Ordering
  You can evaluate transformation ordering.

**Parent topic:** General XStream Concepts

#### 2.3.1 Declarative Rule-Based Transformations

Declarative rule-based transformations cover a set of common transformation scenarios for row LCRs.

You specify (or declare) such a transformation using one of the following procedures in the `DBMS_XSTREAM_ADM` package:

- `ADD_COLUMN` either adds or removes a declarative transformation that adds a column to a row LCR.

- `DELETE_COLUMN` either adds or removes a declarative transformation that deletes a column from a row LCR.

- `KEEP_COLUMNS` either adds or removes a declarative transformation that keeps a list of columns in a row LCR. The transformation removes columns that are not in the list from the row LCR.

- `RENAME_COLUMN` either adds or removes a declarative transformation that renames a column in a row LCR.

- `RENAME_SCHEMA` either adds or removes a declarative transformation that renames the schema in a row LCR.

- `RENAME_TABLE` either adds or removes a declarative transformation that renames the table in a row LCR.

When you specify a declarative rule-based transformation, you specify the rule that is associated with it. When the specified rule evaluates to `TRUE` for a row LCR, XStream performs the declarative transformation internally on the row LCR, without invoking PL/SQL.

Declarative rule-based transformations provide the following advantages:

- Performance is improved because the transformations are run internally without using PL/SQL.

- Complexity is reduced because custom PL/SQL functions are not required.

Declarative rule-based transformations can transform row LCRs only. Therefore, a DML rule must be specified when you run one of the procedures to add a declarative transformation. If a DDL rule is specified, then an error is raised.

**Parent topic:** Rule-Based Transformations

#### 2.3.2 Declarative Rule-Based Transformation Ordering

The order in which different types of rule-based transformations is evaluated is important as results will vary.

By default, Oracle Database performs declarative transformations in the following order when the rule evaluates to `TRUE`:

1.  Keep columns

2.  Delete column

3.  Rename column

4.  Add column

5.  Rename table

6.  Rename schema

The results of a declarative transformation are used in each subsequent declarative transformation. For example, suppose the following declarative transformations are specified for a single rule:

- Delete column address

- Add column address

Assuming column address exists in a row LCR, both declarative transformations should be performed in this case because the column address is deleted from the row LCR before column address is added back to the row LCR. The following table shows the transformation ordering for this example.

| Step Number | Transformation Type | Transformation Details               | Transformation Performed? |
|:------------|:--------------------|:-------------------------------------|:--------------------------|
| 1           | Keep columns        | \-                                   | \-                        |
| 2           | Delete column       | Delete column `address` from row LCR | Yes                       |
| 3           | Rename column       | \-                                   | \-                        |
| 4           | Add column          | Add column `address` to row LCR      | Yes                       |
| 5           | Rename table        | \-                                   | \-                        |
| 6           | Rename schema       | \-                                   | \-                        |

Another scenario might rename a table and then rename a schema. For example, suppose the following declarative transformations are specified for a single rule:

- Rename table `john.customers` to `sue.clients`

- Rename schema `sue` to `mary`

Notice that the rename table transformation also renames the schema for the table. In this case, both transformations should be performed and, after both transformations, the table name becomes `mary.clients`. The following table shows the transformation ordering for this example.

| Step Number | Transformation Type | Transformation Details                         | Transformation Performed? |
|:------------|:--------------------|:-----------------------------------------------|:--------------------------|
| 1           | Keep columns        | \-                                             | \-                        |
| 2           | Delete column       | \-                                             | \-                        |
| 3           | Rename column       | \-                                             | \-                        |
| 4           | Add column          | \-                                             | \-                        |
| 5           | Rename table        | Rename table `john.customers` to `sue.clients` | Yes                       |
| 6           | Rename schema       | Rename schema `sue` to `mary`                  | Yes                       |

Consider a similar scenario in which the following declarative transformations are specified for a single rule:

- Rename table `john.customers` to `sue.clients`

- Rename schema `john` to `mary`

In this case, the first transformation is performed, but the second one is not. After the first transformation, the table name is `sue.clients`. The second transformation is not performed because the schema of the table is now `sue`, not `john`. The following table shows the transformation ordering for this example.

| Step Number | Transformation Type | Transformation Details                         | Transformation Performed? |
|:------------|:--------------------|:-----------------------------------------------|:--------------------------|
| 1           | Keep columns        | \-                                             | \-                        |
| 2           | Delete column       | \-                                             | \-                        |
| 3           | Rename column       | \-                                             | \-                        |
| 4           | Add column          | \-                                             | \-                        |
| 5           | Rename table        | Rename table `john.customers` to `sue.clients` | Yes                       |
| 6           | Rename schema       | Rename schema `john` to `mary`                 | No                        |

The rename schema transformation is not performed, but it does not result in an error. In this case, the row LCR is transformed by the rename table transformation, and a row LCR with the table name `sue.clients` is returned.

**Parent topic:** Rule-Based Transformations

#### 2.3.3 Evaluating Transformation Ordering

You can evaluate transformation ordering.

- Row Migration Transformation Ordering
  In addition to declarative rule-based transformations, a row migration is an internal transformation that takes place when a subset rule evaluates to `TRUE`.
- User-Specified Declarative Transformation Ordering
  If you do not want to use the default declarative rule-based transformation ordering for a particular rule, then you can specify step numbers for each declarative transformation specified for the rule.
- Considerations for Rule-Based Transformations
  Several considerations apply to declarative rule-based transformations.

**Parent topic:** Rule-Based Transformations

##### 2.3.3.1 Row Migration Transformation Ordering

In addition to declarative rule-based transformations, a row migration is an internal transformation that takes place when a subset rule evaluates to `TRUE`.

You can use the `DBMS_XSTREAM_ADM.ADD_SUBSET_RULES` procedure to add subset rules. If both types of transformations are specified for a single rule, then Oracle Database performs the transformations in the following order when the rule evaluates to `TRUE`:

1.  Row migration

2.  Declarative rule-based transformation

**Parent topic:** Evaluating Transformation Ordering

##### 2.3.3.2 User-Specified Declarative Transformation Ordering

If you do not want to use the default declarative rule-based transformation ordering for a particular rule, then you can specify step numbers for each declarative transformation specified for the rule.

If you specify a step number for one or more declarative transformations for a particular rule, then the declarative transformations for the rule behave in the following way:

- Declarative transformations are performed in order of increasing step number.

- The default step number for a declarative transformation is 0 (zero). A declarative transformation uses this default if no step number is explicitly specified for it.

- If two or more declarative transformations have the same step number, then these declarative transformations follow the default ordering described in "Declarative Rule-Based Transformation Ordering".

For example, you can reverse the default ordering for declarative transformations by specifying the following step numbers for transformations associated with a particular rule:

- Keep columns with step number 6

- Delete column with step number 5

- Rename column with step number 4

- Add column with step number 3

- Rename table with step number 2

- Rename schema with step number 1

With this ordering specified, rename schema transformations are performed first, and delete column transformations are performed last.

**Parent topic:** Evaluating Transformation Ordering

##### 2.3.3.3 Considerations for Rule-Based Transformations

Several considerations apply to declarative rule-based transformations.

These considerations include the following:

- For a rule-based transformation to be performed by an XStream component, the rule must be in the positive rule set for the XStream component. If the rule is in the negative rule set for the XStream component, then the XStream component ignores the rule-based transformation.

- Rule-based transformations are different from transformations performed using the `DBMS_TRANSFORM` package. This document does not discuss transformations performed with the `DBMS_TRANSFORM` package.

- If a large percentage of row LCRs will be transformed in an XStream In configuration, you can use DML handlers with XStream In. Be aware that this method may not perform as well as making the changes in the XStream In client application. If you are performing multiple or complex transformations on row LCRs in an XStream In configuration, then consider reducing the XStream In processing time by making these modifications in the client application prior to sending the changes to XStream In.

**Parent topic:** Evaluating Transformation Ordering

### 2.4 XStream and the Oracle Replication Performance Advisor

The Oracle Replication Performance Advisor consists a collection of data dictionary views.

The Performance Advisor enables you to monitor the topology and performance of an XStream environment. The XStream topology includes information about the components in an XStream environment, the links between the components, and the way information flows from capture to consumption. The Performance Advisor also provides information about how Oracle Replication components are performing.

Apply processes function as XStream outbound servers and inbound servers. In general, the Performance Advisor works the same way for an Oracle Replication environment with apply processes and an XStream environment with outbound servers or inbound servers. This section describes important considerations about using the Performance Advisor in an XStream environment.

- XStream Components
  The Performance Advisor tracks several XStream components.
- Topology and Stream Paths
  In the Oracle Replication topology, a stream path is a flow of LCRs from a source to a destination.
- XStream and Component-Level Statistics
  The Performance Advisor tracks component-level statistics.
- The UTL_RPADV Package
  The `UTL_RPADV` package automates the collection of statistics associated with XStream performance.

**Parent topic:** General XStream Concepts

#### 2.4.1 XStream Components

The Performance Advisor tracks several XStream components.

The Performance Advisor tracks the following types of components in an XStream environment:

- `QUEUE`

- `CAPTURE`

- `PROPAGATION` `SENDER`

- `PROPAGATION` `RECEIVER`

- `APPLY`

The preceding types are the same in an Oracle Replication environment and an XStream environment, except for `APPLY`. The `APPLY` component type can be an XStream outbound server or inbound server.

In addition, the Performance Advisor identifies a bottleneck component as the busiest component or the component with the least amount of idle time. In an XStream configuration, the XStream client application might be the bottleneck when `EXTERNAL` appears in the `ACTION_NAME` column of the `DBA_STREAMS_TP_PATH_BOTTLENECK` view.

- XStream Out Apply Subcomponents
  There are several XStream Out apply subcomponents types.
- XStream In Apply Subcomponents
  There are several XStream In apply subcomponents types.

**Parent topic:** XStream and the Oracle Replication Performance Advisor

##### 2.4.1.1 XStream Out Apply Subcomponents

There are several XStream Out apply subcomponents types.

The following subcomponent types are possible:

- `PROPAGATION` `SENDER+RECEIVER` for sending LCRs from a capture process to an outbound server where the capture process and outbound server are in different databases.

- `APPLY` `READER` for a reader server. `APPLY READER` receives LCRs from the capture process, organizes them into transactions, does dependency calculations, and passes the LCRs to the apply coordinator.

- `APPLY` `COORDINATOR` for a coordinator process. It takes the transactions from the capture process, uses the dependency information to determine how to schedule the transactions and sends the LCRs to the apply server.

- `APPLY` `SERVER` for an apply server. It delivers the LCRs to the client application.

**Parent topic:** XStream Components

##### 2.4.1.2 XStream In Apply Subcomponents

There are several XStream In apply subcomponents types.

The following subcomponent types are possible:

- `APPLY` `READER` for a reader server. It takes the LCRs from client application converts them into transactions, checks the transactional order and does dependency calculations.

- `APPLY` `COORDINATOR` for a coordinator process. It takes the transactions from the reader server, uses the dependency information to determine how to schedule the transactions and sends the LCRs to the apply server.

- `APPLY` `SERVER` for an apply server. It applies the LCRs to an apply handler. If the LCR cannot be applied, it is placed into an error queue.

**Parent topic:** XStream Components

#### 2.4.2 Topology and Stream Paths

In the Oracle Replication topology, a stream path is a flow of LCRs from a source to a destination.

A stream path begins with a capture process or XStream In client application. A stream path ends where an apply process, outbound server, or inbound server receives the LCRs. The stream path might flow through multiple source and destination components before it reaches an apply process, outbound server, or inbound server. Therefore, a single stream path can consist of multiple source/destination component pairs before it reaches last component.

The Oracle Replication topology only gathers information about a stream path if the stream path ends with an apply process, an outbound server, or an inbound server.

**Parent topic:** XStream and the Oracle Replication Performance Advisor

#### 2.4.3 XStream and Component-Level Statistics

The Performance Advisor tracks component-level statistics.

The Performance Advisor tracks the following component-level statistics:

- The `MESSAGE` `APPLY` `RATE` is the average number of LCRs applied each second by the apply process, outbound server, or inbound server.

- The `TRANSACTION` `APPLY` `RATE` is the average number of transactions applied by the apply process, outbound server, or inbound server each second. Transactions typically include multiple LCRs.

An LCR can be applied in one of the following ways:

- An apply process or inbound server makes the change encapsulated in the LCR to a database object.

- An apply process or inbound server passes the LCR to an apply handler.

- If the LCR raises an error, then an apply process or inbound server sends the LCR to the error queue.

- An outbound server passes the LCR to an XStream client application. If the LCR raises an error, then the outbound server also reports the error to the client application.

Also, the Performance Advisor tracks the `LATENCY` component-level statistics. `LATENCY` is defined in the following ways:

- For apply processes, the `LATENCY` is the amount of time between when the LCR was created at a source database and when the LCR was applied by the apply process at the destination database.

- For outbound servers, the apply `LATENCY` is amount of time between when the LCR was created at a source database and when the LCR was sent to the XStream client application.

- For inbound servers, the apply `LATENCY` is amount of time between when the LCR was created by the XStream client application and when the LCR was applied by the apply process.

When a capture process creates an LCR, the message creation time is the time when the redo entry for the database change was recorded. When an XStream client application creates an LCR, the message creation time is the time when the LCR was constructed.

**Parent topic:** XStream and the Oracle Replication Performance Advisor

#### 2.4.4 The UTL_RPADV Package

The `UTL_RPADV` package automates the collection of statistics associated with XStream performance.

`UTL_RPADV` provides a series of subprograms that collect and analyze statistics for the XStream components in a distributed database environment. The package uses the Performance Advisor and the `COLLECT_STATS` procedure to automate the collection of statistics.

The output is formatted so that it can be imported into a spreadsheet easily and analyzed. You can examine XStream performance statistics output with the `UTL_RPADV.SHOW_STATS` procedure or view the same information in an HTML-formatted report with the `UTL_RPADV.SHOW_STATS_HTML` procedure.

The `UTL_RPADV` package works essentially the same way for an Oracle Replication environment with apply processes as it does for an XStream environment with outbound servers or inbound servers. Since XStream is concerned with data changes to or from a client application, the output of the `SHOW_STATS` procedure is different for XStream than for Oracle Replication.

- Collecting XStream Statistics Using the UTL_RPADV Package
  You can collect XStream statistics with the `UTL_RPADV` package.
- Showing XStream Statistics on the Command Line
  The `SHOW_STATS` procedure in the `UTL_RPADV` package displays the statistics that the Performance Advisor gathered and stored.
- Interpreting SHOW_STATS Output
  There are differences between the output for apply processes and the output for XStream outbound servers and inbound servers.
- Showing XStream Statistics in an HTML Report
  The `SHOW_STATS_HTML` procedure in the `UTL_RPADV` package creates an HTML report that contains the statistics that the Performance Advisor gathered and stored.
- Interpreting the HTML Report From SHOW_STATS_HTML
  The `SHOW_STATS_HTML` procedure in the `UTL_RPADV` package can generate the same output as the `SHOW_STATS` procedure, but it formats the output as HTML in HTML files.

**Parent topic:** XStream and the Oracle Replication Performance Advisor

##### 2.4.4.1 Collecting XStream Statistics Using the UTL_RPADV Package

You can collect XStream statistics with the `UTL_RPADV` package.

To collect XStream statistics using the `UTL_RPADV` package, complete the following steps:

1.  Identify the database that you will use to gather the information. An administrative user at this database must meet the following requirements:
    - If you want to gather XStream statistics for more than one database, the user must have access to a database link to each database that contains XStream components to monitor.

    - The user must have been granted privileges using the `DBMS_XSTREAM_AUTH.GRANT_ADMIN_PRIVILEGE` procedure. If you want to gather XStream statistics for more than one database, each database link must connect to a user at the remote database that has been granted privileges using the `DBMS_XSTREAM_AUTH.GRANT_ADMIN_PRIVILEGE` procedure.

      If you configure an XStream administrator at each database with XStream components, then the XStream administrator has the necessary privileges.

    - The user must have the necessary privileges to create tables and procedures. If you want to gather XStream statistics for more than one database, each database link must connect to a user at the remote database that has the necessary privileges to create tables and procedures.

    If no database in your environment meets these requirements, then choose a database, configure the necessary database links, and grant the necessary privileges to the users before proceeding.
2.  In SQL\*Plus, connect to the database you identified in Step 1 as a user that meets the requirements listed in Step 1.
    See [Oracle Database Administrator’s Guide](../admin/index.md) for information about connecting to a database in SQL\*Plus.
3.  Run the `utlrpadv.sql` script in the rdbms/admin directory in `ORACLE_HOME` to load the `UTL_RPADV` package. For example:
        @utlrpadv.sql
4.  Either collect the current XStream performance statistics once, or create a job that continually monitors XStream performance:
    - To collect the current XStream performance statistics once, run the `COLLECT_STATS` procedure:

          exec UTL_RPADV.COLLECT_STATS

      This example uses the default values for the parameters in the `COLLECT_STATS` procedure. Therefore, this example runs the Performance Advisor 10 times with 60 seconds between each run. These values correspond with the default values for the `num_runs` and `interval` parameters, respectively, in the `COLLECT_STATS` procedure.

    - To create a job that continually monitors XStream performance:

          exec UTL_RPADV.START_MONITORING

      This example creates a monitoring job, and the monitoring job gathers performance statistics continually at set intervals. This example uses the default values for the parameters in the `START_MONITORING` procedure. Therefore, this example runs the Performance Advisor every 60 seconds. This value corresponds with the default value for the `interval` parameter in the `START_MONITORING` procedure. If an interval is specified in the `START_MONITORING` procedure, then the specified interval is used for the `interval` parameter in the `COLLECT_STATS` procedure.

    These procedures include several parameters that you can use to adjust the way performance statistics are gathered. See [Oracle Database PL/SQL Packages and Types Reference](../arpls/UTL_RPADV.md) for more information.

You can show the statistics by running the `SHOW_STATS` procedure. See "Showing XStream Statistics on the Command Line".

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/UTL_RPADV.md) for more information about the `UTL_RPADV` package

**Parent topic:** The UTL_RPADV Package

##### 2.4.4.2 Showing XStream Statistics on the Command Line

The `SHOW_STATS` procedure in the `UTL_RPADV` package displays the statistics that the Performance Advisor gathered and stored.

Use the `path_stat_table` parameter to specify the table that contains the statistics.

When you gather statistics using the `COLLECT_STATS` procedure, this table is specified in the `path_stat_table` parameter in the `COLLECT_STATS` procedure. By default, the table name is `STREAMS$_ADVISOR_PATH_STAT`.

When you gather statistics using the `START_MONITORING` procedure, you can determine the name for this table by querying the `SHOW_STATS_TABLE` column in the `STREAMS$_PA_MONITORING` view. The default table for a monitoring job is `STREAMS$_PA_SHOW_PATH_STAT`.

To show statistics collected using the `UTL_RPADV` package and stored in the `STREAMS$_ADVISOR_PATH_STAT` table, complete the following steps:

1.  Collect statistics by completing the steps described in "Collecting XStream Statistics Using the UTL_RPADV Package".
2.  Connect to the database as the user who collected the statistics.
3.  If you are using a monitoring job, then query the `SHOW_STATS_TABLE` column in the `STREAMS$_PA_MONITORING` view to determine the name of this table that stores the statistics:
        SELECT SHOW_STATS_TABLE FROM STREAMS$_PA_MONITORING;
4.  Run the `SHOW_STATS` procedure.
    For example, if you are using a monitoring job and the default storage table, then run the following procedure:

        SET SERVEROUTPUT ON SIZE 50000
        BEGIN
          UTL_RPADV.SHOW_STATS(
            path_stat_table => 'STREAMS$_PA_SHOW_PATH_STAT');
        END;
        /

**Parent topic:** The UTL_RPADV Package

##### 2.4.4.3 Interpreting SHOW_STATS Output

There are differences between the output for apply processes and the output for XStream outbound servers and inbound servers.

**Note:**

The rest of this section assumes that you are familiar with the `UTL_RPADV` package and the `SHOW_STATS` output for apply processes.

- Sample Output When an Outbound Server Is the Last Component in a Path
  Here is sample output for when an outbound server is the last component in a path.
- Sample Output When an Inbound Server Is the Last Component in a Path
  Here is sample output for when an inbound server is the last component in a path.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/UTL_RPADV.md) for detailed information about using the `UTL_RPADV` package

**Parent topic:** The UTL_RPADV Package

###### 2.4.4.3.1 Sample Output When an Outbound Server Is the Last Component in a Path

Here is sample output for when an outbound server is the last component in a path.

    LEGEND
    <statistics>=<capture>  [<queue>  <psender>  <preceiver>  <queue>  ]<apply>
    <bottleneck>
    <capture>    = '|<C>'<name>  <msgs captured/sec>  <msgs enqueued/sec>  <latency>
        'LMR'<idl%>  <flwctrl%>  <topevt%>  <topevt>
        'LMP' (<parallelism>)<idl%>  <flwctrl%>  <topevt%>  <topevt>
        'LMB'<idl%>  <flwctrl%>  <topevt%>  <topevt>
        'CAP'<idl%>  <flwctrl%>  <topevt%>  <topevt>
        'CAP+PS'<msgs sent/sec>  <bytes sent/sec>  <latency>  <idl%>
    <flwctrl%>  <topevt%>  <topevt>
    <apply>      = '|<A>'<name>  <msgs applied/sec>  <txns applied/sec>  <latency>
        'PS+PR'<idl%>  <flwctrl%>  <topevt%>  <topevt>
        'APR'<idl%>  <flwctrl%>  <topevt%>  <topevt>
        'APC'<idl%>  <flwctrl%>  <topevt%>  <topevt>
        'APS' (<parallelism>)<idl%>  <flwctrl%>  <topevt%>  <topevt>
    <queue>      = '|<Q>'<name>  <msgs enqueued/sec>  <msgs spilled/sec>  <msgs in
    queue>
    <psender>    = '|<PS>'<name>  <msgs sent/sec>  <bytes sent/sec>  <latency>  <idl%>
    <flwctrl%>  <topevt%>  <topevt>
    <preceiver>  = '|<PR>'<name>  <idl%>  <flwctrl%>  <topevt%>  <topevt>
    <bottleneck>= '|<B>'<name>  <sub_name>  <sessionid>  <serial#>  <topevt%>  <topevt>

    OUTPUT

    PATH 1 RUN_ID 2 RUN_TIME 2009-MAY-15 12:20:55 CCA Y
    |<C> CAP$_XOUT_1 2733 2730 3392 LMR 8.3% 91.7% 0% "" LMP (1) 8.3% 91.7% 0% ""
    LMB 8.3% 91.7% 0% "" CAP 8.3% 91.7% 0% "" |<Q> "XSTRMADMIN"."Q$_XOUT_2" 2730 0.01
    4109 |<A> XOUT 2329 2.73 0 -1 PS+PR 8.3% 91.7% 0% "" APR 8.3% 91.7% 0% "" APC
    100% 0% 0% "" APS (1) 8.3% 83.3% 8.3% "" |<B> "EXTERNAL"
    .
    .
    .

**Note:**

This output is for illustrative purposes only. Actual performance characteristics vary depending on individual configurations and conditions.

In this output, the `A` component is the outbound server `XOUT`. The output for when an outbound server is the last component in a path is similar to the output for when an apply process is the last component in a path. However, the apply server (APS) is not the last component because the outbound server connects to a client application. Statistics are not collected for the client application.

In an XStream Out configuration, the output can indicate flow control for the network because the "SQL\*Net more data to client" performance metric for an apply server is measured like a flow control event. If the output indicates flow control for an apply server, then either the network or the client application is considered the bottleneck component. In the previous output, `EXTERNAL` indicates that either the network or the client application is the bottleneck.

Other than these differences, you can interpret the statistics in the same way that you would for a path that ends with an apply process. Use the legend and the abbreviations to determine the statistics in the output.

**Parent topic:** Interpreting SHOW_STATS Output

###### 2.4.4.3.2 Sample Output When an Inbound Server Is the Last Component in a Path

Here is sample output for when an inbound server is the last component in a path.

    OUTPUT

    PATH 1 RUN_ID 2 RUN_TIME 2009-MAY-16 10:11:38 CCA N
    |<PR> "clientcap"=> 75% 0% 8.3% "CPU + Wait for CPU" |<Q> "XSTRMADMIN"."QUEUE2"  467 0.01 1
    |<A> XIN 476 4.71 0 APR 100% 0% 0% "" APC 100% 0% 0% "" APS (4) 366.7% 0% 33.3% "CPU + Wait for CPU"
    |<B> "EXTERNAL"
    .
    .
    .

**Note:**

This output is for illustrative purposes only. Actual performance characteristics vary depending on individual configurations and conditions.

In this output, the `A` component is the inbound server `XIN`. When an inbound server is the last component in a path, the XStream client application connects to the inbound server, and the inbound server applies the changes in the LCRs. The client application is not shown in the output.

The propagation receiver receives the LCRs from the client application. So, the propagation receiver is the first component shown in the output. In the previous sample output, the propagation receiver is named `clientcap`. In this case, `clientcap` is the source name given by the client application when it attaches to the inbound server.

If the propagation receiver is idle for a significant percentage of time, then either the network or the client application is considered a bottleneck component. In the previous output, `EXTERNAL` indicates that either the network or the client application is the bottleneck.

Other than these differences, you can interpret the statistics in the same way that you would for a path that ends with an apply process. If you and the abbreviations to determine the statistics in the output.

**Parent topic:** Interpreting SHOW_STATS Output

##### 2.4.4.4 Showing XStream Statistics in an HTML Report

The `SHOW_STATS_HTML` procedure in the `UTL_RPADV` package creates an HTML report that contains the statistics that the Performance Advisor gathered and stored.

Use the `comp_stat_table` parameter to specify the table that contains the statistics.

When you gather statistics using the `COLLECT_STATS` procedure, this table is specified in the `comp_stat_table` parameter in the `COLLECT_STATS` procedure. By default, the table name is `STREAMS$_ADVISOR_COMP_STAT`.

When you gather statistics using the `START_MONITORING` procedure, you can determine the name for this table by querying the `SHOW_STATS_TABLE` column in the `STREAMS$_PA_MONITORING` view. The default table for a monitoring job is `STREAMS$_ADVISOR_COMP_STAT`.

The default for the `comp_stat_table` parameter is `STREAMS$_ADVISOR_COMP_STAT`. Ensure that you specify the correct table when you run the `SHOW_STATS_HTML` procedure.

The `SHOW_STATS_HTML` procedure must store the HTML report in a directory. Use the `directory` parameter to specify a directory object.

To show statistics collected using the `UTL_RPADV` package and stored in the `STREAMS$_ADVISOR_COMP_STAT` table, complete the following steps:

1.  Collect statistics by completing the steps described in "Collecting XStream Statistics Using the UTL_RPADV Package".
2.  Connect to the database as the user who collected the statistics.
3.  If you are using a monitoring job, then query the `SHOW_STATS_TABLE` column in the `STREAMS$_PA_MONITORING` view to determine the name of this table that stores the statistics:
        SELECT SHOW_STATS_TABLE FROM STREAMS$_PA_MONITORING;
4.  Create a directory object for the directory that will contain the files in the HTML report.
    For example, to create a directory object named `XSTREAM_STATS_HTML` for the /usr/xstream/reports directory, run the following SQL statement:

        CREATE DIRECTORY XSTREAM_STATS_HTML AS '/usr/xstream/reports';
5.  Run the `SHOW_STATS_HTML` procedure.
    For example, if you are using a monitoring job and the default storage table, then run the following procedure:

        BEGIN
          UTL_RPADV.SHOW_STATS_HTML(
            directory       => 'XSTREAM_STATS_HTML',
            reportname      => 'xstream_stats.html',
            comp_stat_table => 'STREAMS$_ADVISOR_COMP_STAT');
        END;
        /

**Parent topic:** The UTL_RPADV Package

##### 2.4.4.5 Interpreting the HTML Report From SHOW_STATS_HTML

The `SHOW_STATS_HTML` procedure in the `UTL_RPADV` package can generate the same output as the `SHOW_STATS` procedure, but it formats the output as HTML in HTML files.

The `SHOW_STATS_HTML` output is easier to read than the `SHOW_STATS` output. For example, the procedure generates multiple files, and each file begins with the report name. The report includes tables with the performance statistics. Statistics for different paths are in different rows in these tables, and you can click on a path for more detailed statistics about the path. The `report_name` parameter indicates the master HTML file with links to the other HTML files.

The following are considerations for using the `SHOW_STATS_HTML` procedure:

- The default table that stores the statistics is `STREAMS$_ADVISOR_COMP_STAT`. The `SHOW_STATS` procedure uses a different default table (`STREAMS$_ADVISOR_PATH_STAT`).

- You must specify a directory object in the `directory` parameter of the procedure. This directory stores the HTML files generated by the procedure.

  The specified directory object must be created using the SQL statement `CREATE` `DIRECTORY`, and the user who invokes the procedure must have `READ` and `WRITE` privilege on the directory.

**See Also:**

"Interpreting SHOW_STATS Output"

**Parent topic:** The UTL_RPADV Package

### 2.5 XStream and SQL Generation

SQL generation is the ability to generate the SQL statement required to perform the change encapsulated in a row LCR.

XStream outbound servers and XStream inbound servers can use SQL generation to generate the SQL statement necessary to perform the insert, update, or delete operation in a row LCR.

- Interfaces for Performing SQL Generation
  You can use different interfaces for SQL generation.
- SQL Generation Formats
  SQL statements can be generated in one of two formats: inline values or bind variables.
- SQL Generation and Data Types
  SQL generation supports most data types.
- SQL Generation and Character Sets
  When you use the LCR methods, the generated SQL is in the database character set.
- Sample Generated SQL Statements
  Examples illustrate generated SQL statements.
- SQL Generation Demo
  A demo that performs SQL generation is available.

**Parent topic:** General XStream Concepts

#### 2.5.1 Interfaces for Performing SQL Generation

You can use different interfaces for SQL generation.

You can use the following interfaces to perform SQL generation:

- The PL/SQL interface, which uses the `GET_ROW_TEXT` and `GET_WHERE_CLAUSE` member procedures for row LCRs

- The OCI for XStream

- The Java interface for XStream

The PL/SQL interface generates SQL in a `CLOB` data type, while the OCI and Java interfaces generate SQL in plain text. In the Java interface, the size of the text is limited by the size of `String` data type.

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/Logical-Change-Record-TYPEs.md) for information about the `GET_ROW_TEXT` and `GET_WHERE_CLAUSE` row LCR member procedures

- [Oracle Call Interface Programmer's Guide](../lnoci/intro-to-oci-interface-for-XStream.md)

- [Oracle Database XStream Java API Reference](../stxjv/index.md) for information about the Java interface for XStream

**Parent topic:** XStream and SQL Generation

#### 2.5.2 SQL Generation Formats

SQL statements can be generated in one of two formats: inline values or bind variables.

Use inline values when the returned SQL statement is relatively small. For larger SQL statements, use bind variables. In this case, the bind variables are passed to the client application in a separate list that includes pointers to both old and new column values.

For information about using bind variables with each interface, refer to the following documentation:

- The documentation for the `GET_ROW_TEXT` and `GET_WHERE_CLAUSE` row LCR member procedures in [Oracle Database PL/SQL Packages and Types Reference](../arpls/Logical-Change-Record-TYPEs.md)

- [Oracle Call Interface Programmer's Guide](../lnoci/oci-XStream-functions.md)

- The documentation for `DefaultRowLCR.getBinds()` in [Oracle Database XStream Java API Reference](../stxjv/index.md)

**Note:**

For generated SQL statements with the values inline, SQL injection is possible. SQL injection is a technique for maliciously exploiting applications that use client-supplied data in SQL statements, thereby gaining unauthorized access to a database to view or manipulate restricted data. Oracle strongly recommends using bind variables if you plan to execute the generated SQL statement.

**See Also:**

[Oracle Database PL/SQL Language Reference](../lnpls/sql-injection.md) for more information about SQL injection

**Parent topic:** XStream and SQL Generation

#### 2.5.3 SQL Generation and Data Types

SQL generation supports most data types.

SQL generation supports the following data types:

- `VARCHAR2`

- `NVARCHAR2`

- `NUMBER`

- `FLOAT`

- `DATE`

- `BINARY_FLOAT`

- `BINARY_DOUBLE`

- `LONG`

- `TIMESTAMP`

- `TIMESTAMP` `WITH` `TIME` `ZONE`

- `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE`

- `INTERVAL` `YEAR` `TO` `MONTH`

- `INTERVAL` `DAY` `TO` `SECOND`

- `RAW`

- `LONG` `RAW`

- `CHAR`

- `NCHAR`

- `CLOB` with `BASICFILE` storage

- `NCLOB` with `BASICFILE` storage

- `BLOB` with `BASICFILE` storage

- `XMLType` stored as `CLOB`, object relational, or as binary XML

**Note:**

- The maximum size of the `VARCHAR2`, `NVARCHAR2`, and` RAW` data types has been increased in Oracle Database 12c when the `COMPATIBLE` initialization parameter is set to `12.0.0` and the `MAX_STRING_SIZE` initialization parameter is set to `EXTENDED`.

- `XMLType` stored as a `CLOB` is deprecated in Oracle Database 12c Release 1 (12.1).

<!-- -->

- SQL Generation and Automatic Data Type Conversion
  An XStream outbound server or inbound server performs implicit data type conversion where it is possible, and the generated SQL follows ANSI standards where it is possible.
- SQL Generation and LOB, LONG, LONG RAW, and XMLType Data Types
  For `INSERT` and `UPDATE` operations on LOB columns, an outbound server automatically assembles the LOB chunks using LOB assembly.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for information about data types

**Parent topic:** XStream and SQL Generation

##### 2.5.3.1 SQL Generation and Automatic Data Type Conversion

An XStream outbound server or inbound server performs implicit data type conversion where it is possible, and the generated SQL follows ANSI standards where it is possible.

The following are considerations for automatic data type conversions:

- `NULL` is specified as `"NULL"`.

- Single quotation marks are converted into double quotation marks for the following data types when they are inline values: `CHAR`, `VARCHAR2`, `NVARCHAR2`, `NCHAR`, `CLOB`, and `NCLOB`.

- `LONG` data is converted into `CLOB` data.

- `LONG` `RAW` data is converted into `BLOB` data.

**Parent topic:** SQL Generation and Data Types

##### 2.5.3.2 SQL Generation and LOB, LONG, LONG RAW, and XMLType Data Types

For `INSERT` and `UPDATE` operations on LOB columns, an outbound server automatically assembles the LOB chunks using LOB assembly.

For these operations, the generated SQL includes a non-`NULL` empty value. The actual values of the chunked columns arrive in subsequent LCRs. For each chunk, you must perform the correct SQL operation on the correct column.

Similarly, for `LONG`, `LONG` `RAW`, and `XMLType` data types, an outbound server generates a non-`NULL` empty value, and the actual values of the column arrive in chunks in subsequent LCRs. For each chunk, you must perform the correct SQL operation on the correct column.

In the inline version of the generated SQL, for LOB, `LONG`, `LONG` `RAW`, and `XMLType` data type columns, the following SQL is generated for inserts and updates:

- For `CLOB`, `NCLOB`, and `LONG` data type columns:

      EMPTY_CLOB()

- For `BLOB` and `LONG` `RAW` data type columns:

      EMPTY_BLOB()

- For `XMLType` columns:

      XMLTYPE.CREATEXML('xml /')

  where `xml` `/` is the XML chunk.

After the LCR that contains the DML statement arrives, the data for these changes arrive in separate chunks. You can generate the `WHERE` clause for such a change and use the generated `WHERE` clause to identify the row for the modifications contained in the chunks. For example, in PL/SQL you can use the `GET_WHERE_CLAUSE` row LCR member procedure to generate the `WHERE` clause for a row change.

For `INSERT` and `UPDATE` operations, the generated `WHERE` clause identifies the row after the insert or update. For example, consider the following update to the `hr.departments` table:

    UPDATE hr.departments SET department_name='Management'
      WHERE department_name='Administration';

The generated `WHERE` clause for this change is the following:

    WHERE "DEPARTMENT_NAME"='Management'

For piecewise LOB operation performed by subprograms in the `DBMS_LOB` package (including the `WRITE`, `TRIM`, and `ERASE` procedures), the generated SQL includes a `SELECT` `FOR` `UPDATE` statement.

For example, a `LOB_WRITE` operation on a `clob_col` results in generated SQL similar to the following:

    SELECT "CLOB_COL" FROM "HR"."LOB_TAB" WHERE "N1"=2 FOR UPDATE

The selected `clob_col` must be defined. You can use the LOB locator to perform piecewise LOB operations with the LOB chunks that follow the row LCR.

**See Also:**

"Sample Generated SQL Statements"

**Parent topic:** SQL Generation and Data Types

#### 2.5.4 SQL Generation and Character Sets

When you use the LCR methods, the generated SQL is in the database character set.

SQL keywords, such as `INSERT`, `UPDATE`, and `INTO`, do not change with the character set.

**See Also:**

- [Oracle Database Globalization Support Guide](../nlspg/programming-with-unicode.md) for information about data conversion in JDBC

- [Oracle Database SQL Language Reference](../sqlrf/Database-Object-Names-and-Qualifiers.md) for information about SQL keywords

**Parent topic:** XStream and SQL Generation

#### 2.5.5 Sample Generated SQL Statements

Examples illustrate generated SQL statements.

- Sample Generated SQL Statements for the hr.employees Table
  Examples illustrate SQL statements generated by an outbound server for changes made to the `hr.employees` table.
- Sample Generated SQL Statements for a Table With LOB Columns
  Examples illustrate SQL statements generated by an outbound server for changes made ti a table with LOB columns.

**Parent topic:** XStream and SQL Generation

##### 2.5.5.1 Sample Generated SQL Statements for the hr.employees Table

Examples illustrate SQL statements generated by an outbound server for changes made to the `hr.employees` table.

**Note:**

Generated SQL is in a single line and is not formatted.

Example 2-1 Generated Insert

Assume the following insert is executed:

    INSERT INTO hr.employees (employee_id,
                               last_name,
                               email,
                               hire_date,
                               job_id,
                               salary,
                               commission_pct)
                       VALUES (207,
                               'Gregory',
                               'pgregory@example.com',
                               SYSDATE,
                               'PU_CLERK',
                               9000,
                               NULL);

The following is the generated SQL with inline values:

    INSERT INTO "HR"."EMPLOYEES"("EMPLOYEE_ID","FIRST_NAME","LAST_NAME",
    "EMAIL","PHONE_NUMBER","HIRE_DATE","JOB_ID","SALARY","COMMISSION_PCT",
    "MANAGER_ID","DEPARTMENT_ID" ) VALUES ( 207, NULL,'Gregory',
    'pgregory@example.com', NULL , TO_DATE(' 2009-04-15','syyyy-mm-dd'),
    'PU_CLERK',9000, NULL , NULL , NULL )

The following is the generated SQL with bind variables:

    INSERT INTO "HR"."EMPLOYEES"("EMPLOYEE_ID","FIRST_NAME","LAST_NAME",
    "EMAIL","PHONE_NUMBER","HIRE_DATE","JOB_ID","SALARY",
    "COMMISSION_PCT","MANAGER_ID","DEPARTMENT_ID" ) VALUES ( :1   ,:2   ,:3
    ,:4   ,:5   ,:6   ,:7   ,:8   ,:9   ,:10  ,:11  )

Example 2-2 Generated Update

Assume the following update is executed:

    UPDATE hr.employees SET salary=10000 WHERE employee_id=207;

The following is the generated SQL with inline values:

    UPDATE "HR"."EMPLOYEES" SET "SALARY"=10000 WHERE "EMPLOYEE_ID"=207
    AND "SALARY"=9000

The following is the generated SQL with bind variables:

    UPDATE "HR"."EMPLOYEES" SET "SALARY"=:1    WHERE "EMPLOYEE_ID"=:2
    AND "SALARY"=:3

Example 2-3 Generated Delete

Assume the following delete is executed:

    DELETE FROM hr.employees WHERE employee_id=207;

The following is the generated SQL with inline values:

    DELETE  FROM "HR"."EMPLOYEES" WHERE "EMPLOYEE_ID"=207 AND "FIRST_NAME" IS NULL
    AND "LAST_NAME"='Gregory' AND "EMAIL"='pgregory@example.com' AND
    "PHONE_NUMBER" IS NULL  AND "HIRE_DATE"= TO_DATE(' 2009-04-15','syyyy-mm-dd')
    AND "JOB_ID"='PU_CLERK' AND "SALARY"=10000 AND "COMMISSION_PCT" IS NULL
    AND "MANAGER_ID" IS NULL  AND "DEPARTMENT_ID" IS NULL

The following is the generated SQL with bind variables:

    DELETE  FROM "HR"."EMPLOYEES" WHERE "EMPLOYEE_ID"=:1    AND "FIRST_NAME"=:2
    AND "LAST_NAME"=:3    AND "EMAIL"=:4    AND "PHONE_NUMBER"=:5    AND
    "HIRE_DATE"=:6    AND "JOB_ID"=:7    AND "SALARY"=:8    AND
    "COMMISSION_PCT"=:9   AND "MANAGER_ID"=:10   AND "DEPARTMENT_ID"=:11

**Parent topic:** Sample Generated SQL Statements

##### 2.5.5.2 Sample Generated SQL Statements for a Table With LOB Columns

Examples illustrate SQL statements generated by an outbound server for changes made ti a table with LOB columns.

Examples illustrate SQL statements generated by an outbound server for changes made to the following table:

    CREATE TABLE hr.lob_tab(
       n1        number primary key,
       clob_col  CLOB,
       nclob_col NCLOB,
       blob_col  BLOB);

**Note:**

Generated SQL is in a single line and is not formatted.

The `GET_WHERE_CLAUSE` member procedure generates the following `WHERE` clause for this insert:

- Inline:

      WHERE "N1"=2

- Bind variables:

      WHERE "N1"=:1

You can use the `WHERE` clause to identify the row that was inserted when the subsequent chunks arrive for the LOB column change.

Example 2-4 Generated Insert for a Table with LOB Columns

Assume the following insert is executed:

    INSERT INTO hr.lob_tab VALUES (2, 'test insert', NULL, NULL);

The following is the generated SQL with inline values:

    INSERT INTO "HR"."LOB_TAB"("N1","BLOB_COL","CLOB_COL","NCLOB_COL" )
    VALUES ( 2,, EMPTY_CLOB() ,)

The following is the generated SQL with bind variables:

    INSERT INTO "HR"."LOB_TAB"("N1","BLOB_COL","CLOB_COL","NCLOB_COL" )
    VALUES ( :1   ,:2   ,:3   ,:4   )

Example 2-5 Generated Update for a Table with LOB Columns

Assume the following update is executed:

    UPDATE hr.lob_tab SET clob_col='test update' WHERE n1=2;

The following is the generated SQL with inline values:

    UPDATE "HR"."LOB_TAB" SET "CLOB_COL"= EMPTY_CLOB()  WHERE "N1"=2

The following is the generated SQL with bind variables:

    UPDATE "HR"."LOB_TAB" SET "CLOB_COL"=:1    WHERE "N1"=:2

Example 2-6 Generated Delete for a Table with LOB Columns

Assume the following delete is executed:

    DELETE FROM hr.lob_tab WHERE n1=2;

The following is the generated SQL with inline values:

    DELETE  FROM "HR"."LOB_TAB" WHERE "N1"=2

The following is the generated SQL with bind variables:

    DELETE  FROM "HR"."LOB_TAB" WHERE "N1"=:1

**Parent topic:** Sample Generated SQL Statements

#### 2.5.6 SQL Generation Demo

A demo that performs SQL generation is available.

The demo uses the `DBMS_XSTREAM_ADM` PL/SQL package to configure an XStream Out environment, and it uses an OCI client application to perform SQL generation.

The demo uses SQL generation to replicate DML changes from a source database to a destination database. Specifically, the demo creates the `xsdemosg` schema in both the source database and the destination database. It creates various types of tables in the `xsdemosg` schema at each database, including tables with LOB columns. It executes a set of DML statements on the tables in `xsdemosg` schema in the source database. Oracle Replication components, such as a capture process and a queue, send the changes in the form of LCRs to an XStream outbound server that is also running on the source database. The outbound server makes the LCRs available to the demo client application.

The demo client application, when run, uses the OCI API to connect to the outbound server and receive the LCRs. The demo client application uses SQL generation to execute the changes that are encapsulated in the LCRs. Therefore, the client application replicates the changes made to `xsdemosg` schema in the source database to the `xsdemosg` in the destination database.

You can modify the demo to replicate changes to any schema. Both the schema and the replicated tables must exist on both the source database and the destination database. SQL generation is only possible for DML changes. Therefore, this demo cannot be used to replicate DDL changes.

This demo is available in the following location:

    $ORACLE_HOME/rdbms/demo/xstream/sqlgen

**Note:**

The SQL generation demo is not available for the XStream Java API.

**Parent topic:** XStream and SQL Generation
