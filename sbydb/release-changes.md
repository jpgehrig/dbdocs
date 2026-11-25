This preface lists changes in Oracle Data Guard Concepts and Administration.

### Changes in Oracle Database Release 19c

These are the changes in Oracle Data Guard Concepts and Administration for Oracle Database Release 19c.

#### New Features

- The process of flashing back a physical standby to a point in time that was captured on the primary is simplified by automatically replicating restore points from primary to the standby. See [Replicating Restore Points from Primary to Standby](managing-oracle-data-guard-physical-standby-databases.md).

- When flashback or point-in-time recovery is performed on the primary database, a standby that is in mounted mode can automatically follow the same recovery procedure performed on the primary. See [Automatic Flashback of a Mounted Standby After a Primary RESETLOGS Operation](managing-oracle-data-guard-physical-standby-databases.md).

- You can enable the Oracle Database In-Memory Column Store and Data Guard Multi-Instance Redo Apply at the same time on an Active Data Guard standby database.

- DML operations can be performed on Active Data Guard standby instances. When an invalid PL/SQL object is run on an ADG standby database, the object is automatically recompiled. See [Performing DML Operations on Active Data Guard Standby Databases](managing-oracle-data-guard-physical-standby-databases.md) and [Running Top-level PL/SQL Operations on Active Data Guard Standby Databases](managing-oracle-data-guard-physical-standby-databases.md).

#### Desupported Features

- The `MAX_CONNECTIONS` attribute for the `LOG_ARCHIVE_DEST_``n` initialization parameter is desupported.

- Extended Datatype Support (EDS) is desupported. All EDS-supported Oracle data types are now supported natively by logical standbys or Oracle GoldenGate.

### Changes in Oracle Database Release 18c, Version 18.1

These are the changes in Oracle Data Guard Concepts and Administration for Changes in Oracle Database Release 18c, Version 18.1.

- The database buffer cache state is now maintained on an Oracle Active Data Guard standby during a role change. See [Role Transitions Involving Physical Standby Databases](managing-oracle-data-guard-role-transitions.md).

- Global temporary tables can now be dynamically created on an Oracle Active Data Guard standby database. See [Global Temporary Tables on Active Data Guard Instances](managing-oracle-data-guard-physical-standby-databases.md).

- A new initialization parameter, `ADG_ACCOUNT_INFO_TRACKING`, extends control of user account security against login attacks across a production database and all Oracle Active Data Guard standby databases. See [Oracle Database Reference](../refrn/ADG_ACCOUNT_INFO_TRACKING.md).

- A new view `V$DATAGUARD_PROCESS` (which replaces `V$MANAGED_STANDBY`) provides information that can be queried to verify that redo is being transmitted from the primary database and applied to the standby database. See [Creating a Physical Standby Task 7: Verify the Physical Standby Database Is Performing Properly](creating-oracle-data-guard-physical-standby.md).

- Metadata for private temporary tables (also known as local temporary tables) can be stored in memory. This allows private temporary tables to be enabled on read-only databases, hence allowing reporting applications to run on Oracle Active Data Guard standby databases. See [Private Temporary Tables on Active Data Guard Instances](managing-oracle-data-guard-physical-standby-databases.md).

- Database nologging has been extended with two new modes: `Standby Nologging for Load Performance` and `Standby Nologging for Data Availability`. These modes provide better support for use in an Oracle Active Data Guard environment without significantly increasing the amount of redo generated. See [Enable an Appropriate Logging Mode](creating-oracle-data-guard-physical-standby.md).

- A standby database can now be refreshed over the network using one RMAN command, `RECOVER STANDBY DATABASE`. See [Rolling Forward a Standby With One Command](using-RMAN-in-oracle-data-guard-configurations.md).

- Enhancements have been made to Data Guard broker support for upgrades performed using the `DBMS_ROLLING` PL/SQL package. See [Data Guard Broker Support for DBMS_ROLLING Upgrades](using-DBMS_ROLLING-to-perform-rolling-upgrade.md).

- Block Change Tracking is now supported with multi-instance redo apply. See [Setting Up Multi-Instance Redo Apply](configuring-data-guard-standby-databases-in-oracle-RAC.md).
