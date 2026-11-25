## Changes in This Release for Oracle Data Guard Broker

This preface lists changes in Oracle Data Guard Broker.

### Changes in Oracle Database Release 19c

These are the changes in Oracle Data Guard Broker User’s Guide for Changes in Oracle Database Release 19c.

#### New Features

- You can dynamically change the fast-start failover target to a specified member in the list without disabling fast-start failover. See [SET FAST_START FAILOVER TARGET](oracle-data-guard-broker-commands.md).

- Without impacting your current environment, you can test how fast-start failover will work by using the observe-only mode of fast-start failover. See [Configuring Fast-Start Failover in Observe-only Mode](using-data-guard-broker-to-manage-switchovers-failovers.md).

- The broker configuration can be exported and stored in a text file, thereby enabling you to create a backup of the current broker configuration. When required, you can recreate the broker configuration using the metadata in the exported file. The new commands [EXPORT CONFIGURATION](oracle-data-guard-broker-commands.md) and [IMPORT CONFIGURATION](oracle-data-guard-broker-commands.md) are used to export and import a broker configuration. See [Scenario 15: Exporting and Importing a Broker Configuration File](examples-using-data-guard-broker-DGMGRL-utility.md).

- New commands are available to set, modify, and display the value of database initialization parameters in a database, far sync instance, or Recovery Appliance. Values set using these commands are directly applied to the database and are not stored in the broker configuration file. The new commands are as follows:

  - [EDIT DATABASE (Parameter)](oracle-data-guard-broker-commands.md)

  - [EDIT DATABASE RESET (Parameter)](oracle-data-guard-broker-commands.md)

  - [EDIT FAR_SYNC RESET (Parameter)](oracle-data-guard-broker-commands.md)

  - [EDIT RECOVERY_APPLIANCE (Parameter)](oracle-data-guard-broker-commands.md)

  - [EDIT RECOVERY_APPLIANCE RESET (Parameter)](oracle-data-guard-broker-commands.md)

  - [SET TRACE_LEVEL](oracle-data-guard-broker-commands.md)

  A new clause, `SET PARAMETER`, is added to the [EDIT FAR_SYNC](oracle-data-guard-broker-commands.md) command.

#### Deprecated Features

- The following properties that are associated with database initialization parameters are deprecated in this release and may be desupported in a future release: `ArchiveLagTarget`, `DataGuardSyncLatency`, `LogArchiveMaxProcesses`, `LogArchiveMinSucceedDest`, `LogArchiveTrace`, `StandbyFileManagement`, `DbFileNameConvert`, `LogArchiveFormat`, `LogFileNameConvert`. These properties will no longer be stored in the Broker configuration file.

  Instead of using the `EDIT DATABASE...SET PROPERTY` command to modify deprecated properties, use the `EDIT DATABASE…SET PARAMATER` command to modify the database initialization parameters that correspond to the deprecated properties.

- The `InconsistentProperties` property is deprecated in this release. This property will always have no value.

- The following properties related to logical standbys are deprecated and may be desupported in a future release: `LsbyMaxEventsRecorded`, `LsbyMaxServers`, `LsbyMaxSga`, `LsbyPreserveCommitOrder`, `LsbyRecordAppliedDdl`, `LsbyRecordSkipDdl`, `LsbyRecordSkipErrors`, and `LsbyParameter`. Use the `DBMS_LOGSTDBY.APPLY_SET` procedure to configure properties related to logical standbys. The deprecated properties will no longer be stored in the Broker configuration file.

#### Desupported Features

- The `MaxConnections` configuration property is desupported.

#### Other Changes

The `OnlineArchiveLocation` property is renamed to `ArchiveLocation` and the `OnlineAlternateLocation` property is renamed to `AlternateLocation`.

There are some changes to the behavior of the `ArchiveLocation`, `AlternateLocation`, `StandbyArchiveLocation`, and `StandbyAlternateLocation` properties. Additionally, these properties are not automatically upgraded from the Oracle Database Release 18c version of the metadata file. You must set the values of these properties after an upgrade to Oracle Database Release 19c.

See [Oracle Data Guard Broker Properties](oracle-data-guard-broker-properties.md) and [Specifying Locations for Archived Redo Log Files](managing-oracle-data-guard-broker-configuration-members.md).

See [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md).

### Changes in Oracle Database Release 18c, Version 18.1

These are the changes in Oracle Data Guard Broker User’s Guide for Changes in Oracle Database Release 18c, Version 18.1.

- This release provides several new commands:

  - `VALIDATE DATABASE SPFILE` performs a comparison of server parameter file (SPFILE) entries between the primary database and a specified standby database. See [VALIDATE DATABASE SPFILE](oracle-data-guard-broker-commands.md).

  - `VALIDATE NETWORK CONFIGURATION` performs network connectivity checks between members of a broker configuration. See [VALIDATE NETWORK CONFIGURATION](oracle-data-guard-broker-commands.md).

  - `VALIDATE STATIC CONNECT IDENTIFIER` validates the static connect identifier of a database. See [VALIDATE STATIC CONNECT IDENTIFIER](oracle-data-guard-broker-commands.md).

  - `SET ECHO` controls whether or not to echo commands that are issued either at the command-line prompt or from a DGMGRL script. See [SET ECHO](oracle-data-guard-broker-commands.md).

  - `SHOW ALL` (DGMGRL CLI properties) shows the values of DGMGRL CLI properties. See [SHOW ALL](oracle-data-guard-broker-commands.md).

- The `AlternateLocation` configurable property is renamed to `StandbyAlternateLocation` and has new valid values. See [StandbyAlternateLocation](oracle-data-guard-broker-properties.md).

- The `StandbyArchiveLocation` configurable property has new valid values. See [StandbyArchiveLocation](oracle-data-guard-broker-properties.md).

- The new  `OnlineArchiveLocation` configurable property specifies the online redo log archive location for primary, logical, and snapshot standby databases. See [ArchiveLocation](oracle-data-guard-broker-properties.md).

- The new `OnlineAlternateLocation` configurable property specifies an alternate online redo log archive location for primary, logical, and snapshot standby databases when the location specified by the `OnlineArchiveLocation` configurable property fails. See [AlternateLocation](oracle-data-guard-broker-properties.md).

- The `V$DATAGUARD_PROCESS` view, introduced in Oracle Database 12c Release 2 (12.2.0.1), now shows broker processes. See [Oracle Data Guard Monitor (DMON) Process](oracle-data-guard-broker-concepts.md).
