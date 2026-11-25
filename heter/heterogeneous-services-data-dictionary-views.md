You can use the Heterogeneous Services data dictionary views to access information about Heterogeneous Services.

- Types of Views
  Heterogeneous Services data dictionary views.
- Sources of Data Dictionary Information
  The values used for data dictionary content in any particular connection on a Heterogeneous Services database link can come from a number of sources.
- General Views
  There are common views for all services.
- Transaction Service Views
  When a non-Oracle system is involved in a distributed transaction, the transaction capabilities of the non-Oracle system and the agent control whether it can participate in distributed transactions.
- SQL Service Views
  There are data dictionary views that are specific for the SQL service.

**Parent topic:** [Using Heterogeneous Services Agents](using-heterogeneous-services-agents.md)

### Types of Views

Heterogeneous Services data dictionary views.

The Heterogeneous Services data dictionary views, whose names all begin with the `HS_` prefix, can be divided into the following categories:

- General views

- Views used for the transaction service

- Views used for the SQL service

Most of the data dictionary views are defined for both classes and instances. For most types of data there is a `*_CLASS` view and a `*_INST` view. See Table 4-2 for additional details.

Table 4-2 Data Dictionary Views for Heterogeneous Services

| View            | Type                             | Identifies                                                                                |
|:----------------|:---------------------------------|:------------------------------------------------------------------------------------------|
| `HS_BASE_CAPS`  | SQL service                      | All capabilities supported by Heterogeneous Services                                      |
| `HS_BASE_DD`    | SQL service                      | All data dictionary translation table names supported by Heterogeneous Services           |
| `HS_CLASS_CAPS` | Transaction service, SQL service | Capabilities for each class                                                               |
| `HS_CLASS_DD`   | SQL service                      | Data dictionary translations for each class                                               |
| `HS_CLASS_INIT` | General                          | Initialization parameters for each class                                                  |
| `HS_FDS_CLASS`  | General                          | Classes accessible from the Oracle server                                                 |
| `HS_FDS_INST`   | General                          | Instances accessible from the Oracle server                                               |
| `HS_INST_CAPS`  | Transaction service, SQL service | Capabilities for each instance (if set up by the DBA)                                     |
| `HS_INST_DD`    | SQL service                      | Data dictionary translations for each class (if set up by the DBA)                        |
| `HS_INST_INIT`  | General                          | Initialization parameters for each instance (if set up by the DBA)                        |
| `HS_BULK`       |                                  | Data dictionary view to keep track of internal objects created with bulk load procedures. |

Like all Oracle data dictionary tables, these views are read-only. Do not change the content of any of the underlying tables.

**Parent topic:** Heterogeneous Services Data Dictionary Views

### Sources of Data Dictionary Information

The values used for data dictionary content in any particular connection on a Heterogeneous Services database link can come from a number of sources.

For example, in order of precedence:

- Instance information uploaded by the connected Heterogeneous Services agent at the start of the session. This information overrides corresponding content in the Oracle data dictionary, but is never stored into the Oracle data dictionary.

- Instance information stored in the Oracle data dictionary. This data overrides any corresponding content for the connected class.

- Class information stored in the Oracle data dictionary.

If the Oracle database server runs with the `HS_AUTOREGISTER` server initialization parameter set to `FALSE`, then information is not stored automatically in the Oracle data dictionary. The equivalent data is uploaded by the Heterogeneous Services agent on a connection-specific basis each time a connection is made, with any instance-specific information taking precedence over class information.

**Note:**

It is not possible to determine positively what capabilities and what data dictionary translations are in use for a given session due to the possibility that an agent can upload instance information.

You can determine the values of Heterogeneous Services initialization parameters by querying the `VALUE` column of the `V$HS_PARAMETER` view. Note that the `VALUE` column of `V$HS_PARAMETER` truncates the actual initialization parameter value from a maximum of 255 characters to a maximum of 64 characters. It truncates the parameter name from a maximum of 64 characters to a maximum of 30 characters.

**Parent topic:** Heterogeneous Services Data Dictionary Views

### General Views

There are common views for all services.

The views that are common for all services are:

Table 4-3 Common Views for All Services

| View            | Contains                                                                 |
|:----------------|:-------------------------------------------------------------------------|
| `HS_FDS_CLASS`  | Names of the classes that are uploaded into the Oracle data dictionary   |
| `HS_FDS_INST`   | Names of the instances that are uploaded into the Oracle data dictionary |
| `HS_CLASS_INIT` | Information about the Heterogeneous Services initialization parameters   |

For example, you can access multiple Sybase gateways from an Oracle database server. After accessing the gateways for the first time, the information uploaded into the Oracle database server could appear as follows:

    SQL> SELECT * FROM HS_FDS_CLASS;

    FDS_CLASS_NAME        FDS_CLASS_COMMENTS             FDS_CLASS_ID
    --------------------- ------------------------------ ------------
    Sybase816             Uses Sybase driver, R1.1                 1
    Sybase817             Uses Sybase driver, R1.2                21

Two classes are uploaded: a class that accesses Sybase816 and a class that accesses Sybase817. The data dictionary in the Oracle database server now contains capability information, SQL translations, and data dictionary translations for both Sybase816 and Sybase817.

The Oracle database server data dictionary also contains instance information in the `HS_FDS_INST` view for each non-Oracle system instance that is accessed.

**Parent topic:** Heterogeneous Services Data Dictionary Views

### Transaction Service Views

When a non-Oracle system is involved in a distributed transaction, the transaction capabilities of the non-Oracle system and the agent control whether it can participate in distributed transactions.

Transaction capabilities are stored in the `HS_CLASS_CAPS` tables.

The ability of the non-Oracle system and agent to support two-phase commit protocols is specified by the 2PC type capability, which can specify one of the types shown in the following table:

Table 4-4 Transaction Service Views

| Type                            | Capability                                                                                                                                                                                                                                                                                                                               |
|:--------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Read-Only (RO)                  | The non-Oracle system can be queried only with SQL `SELECT` statements. Procedure calls are not allowed because procedure calls are assumed to write data.                                                                                                                                                                               |
| Single-Site (SS)                | The non-Oracle system can handle remote transactions but not distributed transactions. That is, it cannot participate in the two-phase commit protocol.                                                                                                                                                                                  |
| Commit Confirm (CC)             | The non-Oracle system can participate in distributed transactions. It can participate in the server's two-phase commit protocol but only as the commit point site. That is, it cannot prepare data, but it can remember the outcome of a particular transaction if asked by the global coordinator.                                      |
| Two-Phase Commit (2PC)          | The non-Oracle system can participate in distributed transactions. It can participate in the server's two-phase commit protocol, as a regular two-phase commit node, but not as a commit point site. That is, it can prepare data, but it cannot remember the outcome of a particular transaction if asked to by the global coordinator. |
| Two-Phase Commit Confirm (2PCC) | The non-Oracle system can participate in distributed transactions. It can participate in the server's two-phase commit protocol as a regular two-phase commit node or as the commit point site. That is, it can prepare data and it can remember the outcome of a particular transaction if asked by the global coordinator.             |

The transaction model supported by the driver and non-Oracle system can be queried from the `HS_CLASS_CAPS` Heterogeneous Services data dictionary view.

The following example shows one of the capabilities is of the 2PC type:

    SELECT cap_description, translation
    FROM   hs_class_caps
    WHERE  cap_description LIKE '2PC%'
    AND    fds_class_name LIKE 'SYBASE%';

    CAP_DESCRIPTION                          TRANSLATION
    ---------------------------------------- -----------
    2PC type (RO-SS-CC-PREP/2P-2PCC)                  CC

When the non-Oracle system and agent support distributed transactions, the non-Oracle system is treated like any other Oracle server. When a failure occurs during the two-phase commit protocol, the transaction is recovered automatically. If the failure persists, the in-doubt transaction may need to be manually overridden by the database administrator.

**Parent topic:** Heterogeneous Services Data Dictionary Views

### SQL Service Views

There are data dictionary views that are specific for the SQL service.

Data dictionary views that are specific for the SQL service contain information about:

- SQL capabilities and SQL translations of the non-Oracle data source

- Data dictionary translations to map Oracle data dictionary views to the data dictionary of the non-Oracle system

  **Note:**

  This section describes only a portion of the SQL Service-related capabilities. Because you should never need to alter these settings for administrative purposes, these capabilities are not discussed here.

<!-- -->

- Views for Capabilities and Translations
  The `HS_*_CAPS` data dictionary tables contain information about the SQL capabilities of the non-Oracle data source and required SQL translations.
- Views for Data Dictionary Translations
  In order to make the non-Oracle system appear similar to an Oracle database server, Heterogeneous Services connections map a limited set of Oracle data dictionary views onto the non-Oracle system's data dictionary.

**Parent topic:** Heterogeneous Services Data Dictionary Views

#### Views for Capabilities and Translations

The `HS_*_CAPS` data dictionary tables contain information about the SQL capabilities of the non-Oracle data source and required SQL translations.

These views specify whether the non-Oracle data store or the Oracle database server implements certain SQL language features. If a capability is turned off, then Oracle does not send any SQL statements to the non-Oracle data source that require this particular capability, but it still performs postprocessing.

**Parent topic:** SQL Service Views

#### Views for Data Dictionary Translations

In order to make the non-Oracle system appear similar to an Oracle database server, Heterogeneous Services connections map a limited set of Oracle data dictionary views onto the non-Oracle system's data dictionary.

This mapping permits applications to issue queries as if these views belonged to an Oracle data dictionary. Data dictionary translations make this access possible. These translations are stored in Heterogeneous Services views whose names have the `_DD` suffix.

For example, the following `SELECT` statement transforms into a Sybase query that retrieves information about `emp` tables from the Sybase data dictionary table:

    SELECT * FROM USER_TABLES@remote_db
    WHERE UPPER(TABLE_NAME)='EMP';

Data dictionary tables can be mimicked instead of translated. If a data dictionary translation is not possible because the non-Oracle data source does not have the required information in its data dictionary, then Heterogeneous Services causes it to appear as if the data dictionary table is available, but the table contains no information.

To retrieve information about which Oracle data dictionary views or tables are translated or mimicked for the non-Oracle system, connect as user `SYS` and issue the following query on the `HS_CLASS_DD` view:

    SELECT DD_TABLE_NAME, TRANSLATION_TYPE
    FROM   HS_CLASS_DD
    WHERE  FDS_CLASS_NAME LIKE 'SYBASE%';

    DD_TABLE_NAME                  T
    -----------------------------  -
    ALL_ARGUMENTS                  M
    ALL_CATALOG                    T
    ALL_CLUSTERS                   T
    ALL_CLUSTER_HASH_EXPRESSIONS   M
    ALL_COLL_TYPES                 M
    ALL_COL_COMMENTS               T
    ALL_COL_PRIVS                  M
    ALL_COL_PRIVS_MADE             M
    ALL_COL_PRIVS_RECD             M
    ...

The `T` translation type specifies that a translation exists. When the translation type is `M`, the data dictionary table is mimicked.

**Parent topic:** SQL Service Views
