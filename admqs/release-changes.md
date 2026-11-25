This preface lists changes in Oracle Database 2 Day DBA.

- Changes in Oracle Database Release 19c, Version 19.1

- Changes in Oracle Database Release 18c, Version 18.1

- Changes in Oracle Database 12c Release 2 (12.2.0.1)

- Changes in Oracle Database 12c Release 1 (12.1.0.2)

- Changes in Oracle Database 12c Release 1 (12.1.0.1)

### Changes in Oracle Database Release 19c, Version 19.1

The following section describes changes in Oracle Database 2 Day DBA for Oracle Database release 19c, version 19.1.

See [Oracle Database New Features Guide](../newft/index.md) for a complete list of new features in this release.

#### New Features

This section lists new Oracle Database release 19c, version 19.1 features described in this manual.

For Linux and UNIX operating systems, you can run root scripts automatically during Oracle Database software installation.

**See Also:**

[Installing Oracle Database Software](installing-oracle-database-creating-database.md)

Easy connect adaptor accepts name-value pairs, multiple hosts or ports, and protocol in the connect identifier.

**See Also:**

[Connecting to an Oracle Database from a Client Computer](configuring-the-network-environment.md)

#### Deprecated Features

This section lists the deprecated features in this manual.

Flash-based Enterprise Manager Express is deprecated in Oracle Database 19c. Starting with Oracle Database 19c, Enterprise Manager Express uses Java JET technology for the user interface.

#### Desupported Features

This section lists the desupported features in this manual.

Starting with Oracle Database Release 19c, Oracle Streams is desupported. Oracle GoldenGate is the replication solution for Oracle Database.

### Changes in Oracle Database Release 18c, Version 18.1

The following section describes changes in Oracle Database 2 Day DBA for Oracle Database release 18c, version 18.1.

See [Oracle Database New Features Guide](../newft/index.md) for a complete list of new features in this release.

#### New Features

This section lists new Oracle Database release 18c, version 18.1 features described in this manual.

You can create new pluggable databases (PDBs) in a multitenant container database (CDB) using Database Configuration Assistant (DBCA).

See "[Using DBCA to Manage PDBs](installing-oracle-database-creating-database.md)" for more information about creating PDBs using DBCA..

### Changes in Oracle Database 12c Release 2 (12.2.0.1)

The following are changes in Oracle Database 2 Day DBA for Oracle Database 12c Release 2 (12.2.0.1).

#### New Features

There are several new features in Oracle Enterprise Manager Database Express (EM Express).

EM Express has the following new features:

- Resource Manager support for multitenant container databases (CDBs), pluggable databases (PDBs), and non-CDBs. You can create, edit, delete, activate, and deactivate resource plans to help you manage resources effectively in these databases.

  See "[Managing Database Resources](managing-database-resources.md)" for information about Resource Manager features in EM Express.

- SQL Performance Analyzer (SPA) and SQL Performance Analyzer Quick Check (SPA Quick Check) support, which enables you to assess the effects of database changes on SQL performance

  See "[Analyzing the Impact of Database Changes on SQL Performance](analyzing-database-changes-sql-performance.md)" for information about the SPA and SPA Quick Check features in EM Express.

- In the root of a CDB, you can configure a single port (known as the global port), which enables you to use EM Express to connect to all of the PDBs in the CDB using the HTTPS port for the CDB

  See "[Starting EM Express for a PDB](getting-started-with-database-administration.md)" for information about configuring the global port.

- Additional Performance Hub support for CDBs and PDBs

  See the table in "[Monitoring Performance Using the Performance Hub](monitoring-and-tuning-the-database.md)" for a list of the tabs that are available for different databases (CDBs, PDBs, and non-CDBs).

- Support for managing new types of PDBs

  You can use EM Express to manage refreshable PDBs, proxy PDBs, application roots, and application PDBs. See "[About PDBs That Can be Managed in EM Express](managing-pdbs-with-em-express.md)" and "[Accessing the Containers Page for an Application Root](managing-pdbs-with-em-express.md)".

  EM Express supports management of proxy PDBs. A proxy PDB provides a context to execute SQL statements and perform operations in a remote PDB from the proxy PDB.

  All statements (except the `ALTER DATABASE`, `CREATE PLUGGABLE DATABASE`, `ALTER PLUGGABLE DATABASE`, and `DROP PLUGGABLE DATABASE` statements) that are executed in the proxy PDB will be executed in the remote PDB.

- Hot cloning a PDB in a remote CDB to another CDB

  See "[Creating a PDB by Cloning a PDB from a Remote CDB Using EM Express](managing-pdbs-with-em-express.md)" for information about cloning a PDB from a remote CDB to another CDB.

- Relocating a PDB from a remote CDB to another CDB with minimal downtime

  See "[Relocating a Remote PDB](managing-pdbs-with-em-express.md)" for information about relocating a PDB from a remote CDB to another CDB.

- Creating a refreshable PDB

  See "[Creating a PDB by Cloning a PDB from a Remote CDB Using EM Express](managing-pdbs-with-em-express.md)" for information about creating a refreshable PDB by using the Refresh Option field when you create a new PDB by cloning an existing PDB from a remote CDB.

- Refreshing a refreshable PDB on demand

  See "[Refreshing a PDB on Demand](managing-pdbs-with-em-express.md)" for information about refreshing a refreshable PDB.

- New EM Express features for managing Oracle Data Guard standby databases

  You can use EM Express to:

  - View real-time performance statistics for a standby database in the Performance Hub

    See "[About Viewing Performance Statistics on a Standby Database](monitoring-and-tuning-the-database.md)" for information about viewing standby database performance statistics.

  - Tune SQL queries for a standby database with SQL Tuning Advisor

    See "[About Tuning SQL Statements on a Standby Database](monitoring-and-tuning-the-database.md)" and "[Tuning SQL Statements on a Standby Database](monitoring-and-tuning-the-database.md)" for information about tuning SQL statements for a standby database.

### Changes in Oracle Database 12c Release 1 (12.1.0.2)

The following are changes in Oracle Database 2 Day DBA for Oracle Database 12c Release 1 (12.1.0.2).

#### New Features

You can use Oracle Enterprise Manager Database Express (EM Express) to manage multitenant container databases (CDBs) and pluggable databases (PDBs), in addition to managing non-CDBs.

- See "[Starting EM Express for a CDB](getting-started-with-database-administration.md)" for information about starting EM Express to manage a CDB.

- See "[Starting EM Express for a PDB](getting-started-with-database-administration.md)" for information about starting EM Express to manage a PDB.

- See "[Managing PDBs with EM Express](managing-pdbs-with-em-express.md)" for information on the features provided in EM Express for managing PDBs. Many of those features are available on the Containers page for a CDB.

EM Express provides support for in-memory database features introduced in Oracle Database 12c Release 1 (12.1.0.2):

- The Allocation Breakdown and Allocation History charts on the Memory Management page show In-Memory Area information.

- The amount of CPU consumed is broken out into regular CPU usage (CPU usage not related to in-memory operations) and in-memory CPU usage (CPU usage for in-memory operations), when applicable. This CPU breakdown is shown in several places:

  - On the Monitored SQL Execution Details page, wherever CPU activity is shown.

  - On the SQL Details page, in the Activity % column.

  - On the Activity tab in the Performance Hub, when Resource Consumption by Wait Class is selected.

### Changes in Oracle Database 12c Release 1 (12.1.0.1)

The following are changes in Oracle Database 2 Day DBA for Oracle Database 12c Release 1 (12.1.0.1).

#### New Features

This section describes new features described in this manual for Oracle Database 12c Release 1 (12.1.0.1).

- Oracle Enterprise Manager Database Express (EM Express) is the next-generation management tool for administration and management of individual databases that comes with Oracle Database 12c Release 1 (12.1).

  In previous Oracle Database releases, Oracle Enterprise Manager Database Control (DB Control) was the primary database management tool. DB Control is not included in this release.

  See "[Introduction to Oracle Enterprise Manager Database Express](getting-started-with-database-administration.md)" for more information about EM Express.

- SQL Developer is used to manage schema objects.

  Previous versions of this book described how to manage schema objects using DB Control. This version describes how to manage schema objects using SQL Developer.

  See "[Managing Schema Objects](managing-schema-objects.md)" for more information about using SQL Developer.

- Oracle Recovery Manager (RMAN) is used to perform database backup and recovery operations.

  Previous versions of this book described how to perform database backup and recovery operations using DB Control. This version describes how to perform database backup and recovery operations using RMAN.

  See "[Performing Backup and Recovery](performing-backup-and-recovery.md)" for more information about using RMAN to perform database backup and recovery.
