There are changes in this document for recent releases of Oracle Database.

- Changes in Oracle Database Release 19c, Version 19.1
- Changes in Oracle Database Release 18c, Version 18.1
- Changes in Oracle Database 12c Release 2 (12.2.0.1)

### Changes in Oracle Database Release 19c, Version 19.1

The following are changes in Oracle Database XStream Guide for Oracle Database release 19c, version 19.1.

- New Features
- Desupported Features

**Parent topic:** Changes in This Release for Oracle Database XStream Guide

#### New Features

The following feature is new in this release:

- Support of Tables with BFILE Columns

  XStream now supports replication of changes to BFILE columns.

  **See Also:**

  - [Data Types Captured by a Capture Process](xstream-out-concepts.md)

  - [Data Types Applied by Inbound Servers](xstream-in-concepts.md)

**Parent topic:** Changes in Oracle Database Release 19c, Version 19.1

#### Desupported Features

The following feature is desupported in this release:

- Oracle Streams

  Starting in Oracle Database Release 19c, Oracle Streams is desupported. Oracle GoldenGate is the replication solution for Oracle Database.

**Parent topic:** Changes in Oracle Database Release 19c, Version 19.1

### Changes in Oracle Database Release 18c, Version 18.1

The following are changes in Oracle Database XStream Guide for Oracle Database release 18c, version 18.1.

- New Features

**Parent topic:** Changes in This Release for Oracle Database XStream Guide

#### New Features

The following feature is new in this release:

- Support of Tables with UROWID Columns

  XStream now supports replication of changes to UROWID columns.

  **See Also:**

  - [Data Types Captured by a Capture Process](xstream-out-concepts.md)

  - [Data Types Applied by Inbound Servers](xstream-in-concepts.md)

**Parent topic:** Changes in Oracle Database Release 18c, Version 18.1

### Changes in Oracle Database 12c Release 2 (12.2.0.1)

The following are changes in Oracle Database XStream Guide for Oracle Database 12c Release 2 (12.2.0.1).

- New Features

**Parent topic:** Changes in This Release for Oracle Database XStream Guide

#### New Features

The following features are new in this release:

- DML conflict handlers

  XStream provides prebuilt DML conflict handlers.

  See "[Managing XStream In Conflict Detection and Resolution](managing-xstream-in.md)".

- Support for application containers and application common objects in a multitenant environment

  XStream can replicate changes made to application roots and application PDBs.

  See "[XStream Out and a Multitenant Environment](xstream-out-concepts.md)" and "[XStream In and a Multitenant Environment](xstream-in-concepts.md)".

- Improved support for user-defined types

  XStream now supports object types, REFs, and varrays.

  See "[Data Types Captured by a Capture Process](xstream-out-concepts.md)" and "[Data Types Applied by Inbound Servers](xstream-in-concepts.md)".

- LCRID versions

  An LCRID is the raw value used to specify the position of an LCR for XStream Out. Starting with Oracle Database 12c Release 2 (12.2.0.1), the LCRID is versioned.

  See "[LCRIDs and the Position of LCRs](general-xstream-concepts.md)".

- XStream support for different character sets in a multitenant container database (CDB)

  When the character set of the root of a CDB is AL32UTF8, any pluggable database (PDB) in the CDB can use a character set that is different from the root and other PDBs.

- XStream supports long identifiers for database objects

  In this release, identifiers for some database objects can be up to 128 bytes in length. XStream outbound servers can capture changes made to database objects with long identifiers, and XStream inbound servers can apply changes to database objects with long identifiers.

- LCR tracking

  You can track an LCR through a stream using the `message_tracking_frequency` apply parameter or the `SET_MESSAGE_TRACKING` procedure in the `DBMS_XSTREAM_ADM` package.

  See "[Changes Are Failing to Reach the Client Application in XStream In](troubleshooting-xstream-in.md)".

- New capture process parameters

  The following new capture process parameter is added for XStream Out configurations:

  - `annotateddlsize`

  See [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_CAPTURE_ADM.md) for information about these apply parameters.

- New apply parameters

  The following new apply parameters are added for XStream inbound servers:

  - `batchsql_mode`

  - `cdgranularity`

  - `message_tracking_frequency`

  See [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_APPLY_ADM.md) for information about these apply parameters.

- View the history of events for XStream components

  The `DBA_REPLICATION_PROCESS_EVENTS` view displays the history of events for XStream components.

  See "[Monitoring the History of Events for XStream Out Components](monitoring-xstream-out.md)" and "[Monitoring the History of Events for XStream In Components](monitoring-xstream-in.md)".

**Parent topic:** Changes in Oracle Database 12c Release 2 (12.2.0.1)
