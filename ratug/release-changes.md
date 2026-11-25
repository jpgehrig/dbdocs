This preface lists changes in Oracle Database Testing Guide.

### Changes in Oracle Database Release 19c, Version 19.1

The following are changes in Oracle Database Testing Guide for Oracle Database release 19c, version 19.1.

#### New Features

This section describes the new SQL Performance Analyzer and DB Replay features in Oracle Database release 19c, version 19.1.

- You can enable a workload capture and start a workload replay for the current pluggable database (PDB).

  **See Also:**

  [Workload Capture and Replay in a PDB](introduction-to-database-replay.md)

- You can diagnose a slow workload replay by using the workload replay report.

  **See Also:**

  [Reviewing Workload Replay Reports](analyzing-captured-and-replayed-workloads.md)

- You can query the `DBA_RAT_CAPTURE_SCHEMA_INFO` view to obtain `login_schema` and `current_schema` that were in effect when SQL statements were recorded in a workload capture.

  **See Also:**

  [Starting a Workload Replay](replaying-a-database-workload.md)

### Changes in Oracle Database Release 18c, Version 18.1

The following are changes in Oracle Database Testing Guide for Oracle Database release 18c, version 18.1.

#### New Features

This section describes the new SQL Performance Analyzer and DB Replay features in Oracle Database release 18c, version 18.1.

- You can enable encryption for a workload capture using the new `ENCRYPTION` parameter.

  **See Also:**

  - [Starting a Workload Capture](capturing-a-database-workload.md)

  - [Starting Replay Clients](replaying-a-database-workload.md)

- You can encrypt and decrypt an existing workload capture.

  **See Also:**

  [Encrypting and Decrypting an Existing Workload Capture Using APIs](capturing-a-database-workload.md)

- You can enable concurrent SQL execution with SQL Performance Analyzer using the new `TEST_EXECUTE_DOP` parameter.

  **See Also:**

  [Configuring the Degree of Parallelism for an Analysis Task](creating-an-analysis-task.md)

- You can validate SQL result sets using the new `COMPARE_RESULTSET` parameter.

  **See Also:**

  [Validating SQL Result Sets Using SQL Performance Analyzer](creating-an-analysis-task.md)

- You can perform Database Replay operations in a Database Vault environment if you have the necessary Database Vault authorizations.

  **See Also:**

  [Oracle Database Vault Administrator’s Guide](../dvadm/dba-operations-in-an-oracle-database-vault-environment.md) for information about using Database Replay in a Database Vault environment

### Changes in Oracle Database 12c Release 2 (12.2.0.1)

The following are changes in Oracle Database Testing Guide for Oracle Database 12c Release 2 (12.2.0.1).

#### New Features in Oracle Database 12c Release 2 (12.2.0.1)

This section describes the new SQL Performance Analyzer and DB Replay features in Oracle Database 12c Release 2 (12.2.0.1).

- You can enable or disable the execution of triggers in a SQL Performance Analyzer analysis task.

  See [Configuring Trigger Execution in an Analysis Task](creating-an-analysis-task.md).

- You can configure the date to be returned by calls in a SQL Performance Analyzer analysis task.

  See [Configuring a Date to be Returned by Calls in an Analysis Task](creating-an-analysis-task.md).

- You can configure the number of rows to fetch in a SQL Performance Analyzer analysis task.

  See [Configuring the Number of Rows to Fetch for an Analysis Task](creating-an-analysis-task.md)

- You can specify how user PL/SQL calls are handled during workload capture and workload replay with DB Replay.

  See the following sections for more information:
  - [Starting a Workload Capture](capturing-a-database-workload.md)

  - [Preprocessing a Database Workload Using APIs](preprocessing-a-database-workload.md)

  - [Initializing Replay Data](replaying-a-database-workload.md)

  The `plsql_mode` parameter can also be used with the `INITIALIZE_CONSOLIDATED_REPLAY` procedure, which is described in [Initializing Consolidated Database Replay Using APIs](using-consolidated-database-replay.md).

#### Other Changes in Oracle Database 12c Release 2 (12.2.0.1)

This topic describes additional changes in Oracle Database Testing Guide for Oracle Database 12c Release 2 (12.2.0.1).

The following change was also made in Oracle Database Testing Guide for Oracle Database 12c Release 2 (12.2.0.1).:

- The Test Data Management features that were documented in Part III of this manual in Oracle Database 12c Release 1 have been removed. These features are now documented in a separate manual: [Oracle Data Masking and Subsetting Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/ratug&id=DMKSB).

### Changes in Oracle Database 12c Release 1 (12.1)

The following are changes in Oracle Database Testing Guide for Oracle Database 12c Release 1 (12.1).

#### New Features

The following features are new in this release:

- SQL Performance Analyzer Quick Check (SPA Quick Check)

  On some Oracle Enterprise Manager Cloud Control database management pages, SPA Quick Check can validate the impact of a system change to the database workload before you make the change.

  See [Using SPA Quick Check](using-spa-quick-check.md).

- SQL Performance Analyzer support for the multitenant architecture

  You can use a SQL tuning set that was transported from a non-CDB to a multitenant container database (CDB) as the input source to SQL Performance Analyzer by remapping its CDB identifiers.

  See [Remapping Multitenant Container Database Identifiers in an Analysis Task Using APIs](creating-an-analysis-task.md).

- Workload Intelligence

  Workload Intelligence comprises a suite of Java programs that enable you to analyze the data stored in a captured workload.

  See [Using Workload Intelligence](using-workload-intelligence.md).

- Consolidated Database Replay

  Consolidated Database Replay enables you to consolidate multiple workloads captured from one or multiple systems and replay them concurrently on a single test system, such as a single Oracle Exadata Machine.

  See [Using Consolidated Database Replay](using-consolidated-database-replay.md).

- Workload Scale-up

  Database Replay enables you to perform scale-up testing and stress testing in various use cases and scenarios.

  See [Using Workload Scale-Up](using-workload-scale-up.md).

#### Other Changes

The following are additional changes in the release:

- New book

  Oracle Database Real Application Testing User's Guide is now part of Oracle Database Testing Guide.

- New part

  Part III “Test Data Management” was added to Oracle Database Testing Guide to describe the test data management features of Oracle Database.
