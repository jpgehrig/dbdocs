This preface contains:

- Changes in Oracle Data Provider for .NET Release 19c (19.3)

- Changes in Oracle Data Provider for .NET in ODAC Release 18c (18.3)

- Changes in Oracle Data Provider for .NET Release 18c (18.3)

- Changes in Oracle Data Provider for .NET in ODAC 12.2c Release 1

- Changes in Oracle Data Provider for .NET Release 12.2.0.1

- Changes in Oracle Data Provider for .NET in ODAC 12c Release 4

- Changes in Oracle Data Provider for .NET in ODAC 12c Release 3

- Changes in Oracle Data Provider for .NET Release 12.1.0.2

- Changes in Oracle Data Provider for .NET in ODAC 12c Release 2

- Changes in Oracle Data Provider for .NET in ODAC 12c Release 1

- Changes in Oracle Data Provider for .NET Release 12.1

### Changes in Oracle Data Provider for .NET Release 19c (19.3)

The following are the changes in Oracle Data Provider for .NET for Release 19c (19.3).

#### New Features

The following features are new in this release:

- ODP.NET Core -- Lightweight Directory Access Protocol (LDAP)

  ODP.NET Core can use connect identifiers mapped to connect descriptors in an LDAP-compliant directory server, such as Oracle Internet Directory and Microsoft Active Directory. The provider supports the same LDAP features and settings as managed ODP.NET.

  ODP.NET Core LDAP support is available on Windows operating systems only. It requires the `System.DirectoryServices` namespace.

  **See Also:**

  [OracleConfiguration Directories Properties](ConfigurationDirectoriesProperties.md)

- ODP.NET Core -- Performance Counters

  ODP.NET Core can publish key runtime connection counters to Windows Performance Monitor or a file. The provider supports the same counters, setup process, and settings as managed and unmanaged ODP.NET.

  ODP.NET Core performance counters are available on Windows operating systems only. They require `System.Diagnostics` namespace in using performance counters programmatically.

  **See Also:**

  [Connection Performance Counters](featConnecting.md)

- Easy Connect Plus

  Oracle Easy Connect Plus provides a simple way to configure TCP/IP connections to the Oracle Database without having to use parameter files, such as `tnsnames.ora`, nor environment variables. Easy Connect Plus includes support for:

  - TCP/IP with SSL/TLS

  - Any SQL\*Net description level parameter can be used

  - Multiple hosts and ports

  - A straightforward name-value pair format

  Easy Connect Plus supports more configurations and a wider breadth of ODP.NET applications than traditional Easy Connect, including clustered or cloud databases.

  **See Also:**

  [Easy Connect and Easy Connect Plus Naming Methods](featConnecting.md)

- HTTPS Proxy for Cloud Connections

  ODP.NET supports HTTPS proxy configuration. The feature enables tunneling secure connections over forward HTTP proxy using the HTTP CONNECT method.

  HTTPS proxy improves public cloud database service access as it eliminates requiring the client side firewall to open an outbound port.

- More Secure Oracle Notification Service Connections

  ODP.NET now enables Oracle Notification Service (ONS) communications to occur over TCP/IP with SSL/TLS (TCPS), which is more secure than just TCP/IP. As TCPS requires using a wallet for storing keys and certificates, ODP.NET can use one wallet for both ONS and ODP.NET connections or have separate wallets for each.

  TCPS provides more secure ONS communication, gives administrators flexibility in how to configure their wallets, and enables cloud database connections.

### Changes in Oracle Data Provider for .NET in ODAC Release 18c (18.3)

The following are the changes in Oracle Data Provider for .NET for ODAC Release 18c (18.3).

#### New Features

The following features are new in this release:

- .NET Core 2.1 Certification

  ODP.NET Core is certified for .NET Core 2.1 and higher.

  See Also [Installing Oracle Data Provider for .NET Core](InstallODPCore.md)

### Changes in Oracle Data Provider for .NET Release 18c (18.3)

The following are the changes in Oracle Data Provider for .NET for Release 18c (18.3).

#### New Features

The following features are new in this release:

- .NET Framework 4.7.x Certification

  ODP.NET, Managed and Unmanaged Drivers are certified for all versions of .NET Framework 4.7.x, including 4.7.1 and 4.7.2.

- Secure Passwords with `OracleCredential`

  ODP.NET `OracleCredential` class allows application developers to store user names and passwords outside of the connection string without exposure in a memory dump.

  `OracleCredential` can be used with or without connection pooling.

  This feature is available in the terminal releases of ODP.NET 11.2, 12.1, and 12.2 and with the first release of ODP.NET 18c.

  See Also [Connection Pooling with OracleCredential](featConnecting.md)

#### Desupported Features

Some features previously described in this document are desupported in Oracle Database 18`c` (18.3). See [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md) for a complete list of desupported features.

The following feature is no longer supported by Oracle:

- `Oracle.ManagedDataAccessDTC.dll`

### Changes in Oracle Data Provider for .NET in ODAC 12.2c Release 1

The following are the changes in Oracle Data Provider for .NET for ODAC 12.2c Release 1.

#### New Features

The following features are new in this release:

- .NET Framework 4.7 Certification

  ODP.NET, Managed and Unmanaged Drivers are certified for .NET Framework 4.7.

- Entity Framework 6.2 Certification

  ODP.NET, Managed and Unmanaged Drivers are certified for Entity Framework 6.2.

- Database Resident Connection Pooling

  Database Resident Connection Pooling (DRCP) optimizes resource usage by pooling connections at the database server level. With DRCP, server connections can be shared across application that are executed on different client machines, especially in the case when connections are not always in use. DRCP can be used in conjunction with either managed or unmanaged ODP.NET client side pooling to improve scalability and lower resource usage at the database server level.

  See also [Database Resident Connection Pooling](featConnecting.md) for more information.

- Multitenant and Pluggable Databases Connection Pooling

  Oracle Multitenant is a database architecture that enables customers to easily consolidate multiple pluggable databases without changing their application. This architecture delivers all the benefits of managing many databases as one, yet retains the isolation and resource prioritization of separate databases.

  Managed and unmanaged ODP.NET now support hosting connections to multiple pluggable databases from the same connection pool. This feature enhances application performance and scalability, plus makes using multiple pluggable databases from the same application easier.

  See also [Oracle Multitenant and Pluggable Databases](featConnecting.md) for more information.

- Edition-Based Redefinition Connection Pooling

  Edition-based redefinition enables applications to upgrade the database component while it is in use, thereby minimizing or eliminating down time. Managed and unmanaged ODP.NET now support using the same connection pool to connect to multiple Editions. This feature enhances performance and scalability while using different Editions from the same application, and also makes using multiple Editions from the same application easier.

  See also [Edition-Based Redefinition](featConnecting.md) for more information.

- Connection Configuration Upon Open

  Managed and unmanaged ODP.NET introduce the `ConnectionOpen` event handler, which allows developers to provide setup logic and change settings before ODP.NET connections are dispensed from the `Open()` method invocation. This feature is similar in concept to a logon trigger, but is most optimal for client side initialization settings. It works with both pooled and non-pooled connections. The event handler provides a centralized, standardized location for connection initialization.

  See also [ConnectionOpen](ConnectionConnectionOpen.md) for more information.

#### Deprecated Features

The following feature is deprecated in ODAC 12.2c Release 1:

- `Oracle.ManagedDataAccessDTC.dll`

  Oracle provided a native managed distributed transaction support for ODP.NET, Managed Driver using `Oracle.ManagedDataAccessDTC.dll`. In .NET Framework 4.5.2, Microsoft introduced its own native managed distributed transaction implementation, which managed ODP.NET could use. The new .NET Framework made the `Oracle.ManagedDataAccessDTC.dll` unnecessary. Moreover, Microsoft has desupported all .NET Framework 4 versions earlier than 4.5.2. In accordance with Microsoft policy, Oracle is deprecating the `Oracle.ManagedDataAccessDTC.dll` file.

  The deprecation extends to the `UseManagedDTC` .NET configuration file parameter, and `Oracle.ManagedDataAccessDTC.dll`.

**See Also:**

- [Microsoft Distributed Transaction Coordinator Integration](InstallDistributedTransaction.md)

- [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md) for a complete list of deprecated features.

### Changes in Oracle Data Provider for .NET Release 12.2.0.1

The following are the changes in Oracle Data Provider for .NET for Release 12.2.0.1.

#### New Features

The following features are new in this release:

- .NET Framework 4.6.2 Certification

  ODP.NET, Managed and Unmanaged Drivers are certified for .NET Framework 4.6.2.

  See also [System Requirements](InstallSystemRequirements.md) for more information.

- .NET Cloud Development and Deployment

  ODP.NET, Managed and Unmanaged Drivers can be deployed easily to Oracle Cloud, private clouds, and third-party cloud environments through Web Deploy. All ODP.NET specific settings no longer require any operating system level configuration. These settings can be made in the .NET configuration files. Managed and Unmanaged ODP.NET Drivers now share a unified configuration file format.

- Application Continuity

  Application Continuity recovers incomplete requests from an ODP.NET, Unmanaged Driver perspective and masks many system failures, communication failures, hardware failures, and storage outages from the user.

  See also "[Application Continuity](featAppCont.md)" for more information.

- Sharding and ODP.NET Routing

  Starting from Release 12.2.0.1, ODP.NET, Unmanaged Driver and Oracle Database support sharding. Oracle Sharding provides the ability to horizontally partition the data across multiple independent Oracle databases (shards). Based on a key specified in the connect string, ODP.NET can route the database requests to a particular shard.

  Oracle Sharding is a shared-nothing architecture that allows near-linear scaling of the database across low-cost commodity database servers located in one or more local or global data centers. Other key benefits include global data distribution (store particular data close to consumers) and fault containment (failure of one shard does not affect the availability of other shards). Global Data Services manages the location of data among the shards and allows ODP.NET client requests to be routed to the appropriate shard in this distributed database system.

  See also "[Database Sharding](featDataSharding.md)" for more information.

- Longer Schema Identifiers

  Oracle Data Provider for .NET now supports schema object identifier names, such as tables, columns, views, stored procedures, and functions, up to 128 characters in length. This feature is available in both ODP.NET, Managed and Unmanaged Drivers.

- ODP.NET, Managed Driver – Data Integrity

  ODP.NET, Managed Driver supports cryptographic hash functions to better ensure data integrity between the database server and the client. The algorithms supported include `MD5`, `SHA-1`, and `SHA-2` (`SHA-256`, `SHA-384`, and `SHA-512`).

  See also "[settings section](InstallManagedConfig.md)" and "[Network Data Encryption and Integrity](featConnecting.md)" for more information.

- ODP.NET, Managed Driver -- Transport Layer Security (TLS)

  ODP.NET, Managed Driver has added support for TLS 1.1 and 1.2 in addition to existing support for TLS 1.0 and SSL 3.0.

- ODP.NET, Managed Driver -- Distinguished Name for SSL/TLS

  ODP.NET, Managed Driver connections using SSL/TLS can ensure that the distinguished name (DN) is correct for the database server that it is trying to connect to.

- ODP.NET, Managed Driver - Boolean Data Type

  ODP.NET, Managed Driver now supports the `OracleBoolean` data type when using the database's PL/SQL `Boolean` data type. The managed driver must be connected to Oracle Database 12c Release 2 (12.2) or higher. Booleans store `TRUE` or `FALSE` values.

  The ODP.NET `OracleBoolean` data type eases parameter binding and data type mapping setup with Boolean values.

  See also "[OracleBoolean Structure](OracleBooleanStructure.md)" for more information.

#### Desupported Features

Some features previously described in this document are desupported in Oracle Database 12c Release 2 (12.2). See [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md) for a complete list of desupported features in this release.

The following features are no longer supported by Oracle:

- `OracleLogicalTransactionStatus` class

- `OracleConnection.GetLogicalTransactionStatus` method

- `OracleConnection.LogicalTransactionId` property

- `OracleConnection.OracleLogicalTransaction` property

- `OracleLogicalTransaction.DataSource` property

- `OracleLogicalTransaction.GetOutcome()` method

- `OracleLogicalTransaction.GetOutcome(sting, string, string)` method

- `OracleLogicalTransaction.UserId` property

### Changes in Oracle Data Provider for .NET in ODAC 12c Release 4

The following are the changes in Oracle Data Provider for .NET for ODAC 12c Release 4.

#### New Features

The following features are new in this release:

- .NET Framework 4.6 and 4.6.1 Certification

  ODP.NET, Managed and Unmanaged Drivers are certified for .NET Framework 4.6 and 4.6.1.

  See also "[System Requirements](InstallSystemRequirements.md)" for more information.

- ODP.NET, Managed Driver - Windows Installer

  ODP.NET, Managed Driver is now available as part of an ODAC Microsoft Windows Installer package.

- ODP.NET, Managed Driver - Network Data Encryption

  ODP.NET, Managed Driver supports database security network data encryption using Advanced Encryption Standard (AES), RC4, or Triple-DES to enable more secure database communication over intranet and cloud access.

  See also "[settings section](InstallManagedConfig.md)" and "[Network Data Encryption and Integrity](featConnecting.md)" for more information.

- ODP.NET, Managed Driver - Secure External Password Store

  ODP.NET, Managed Driver supports connection establishment by retrieving password credentials from a client-side Oracle wallet.

  See also "[Using Secure External Password Store](featConnecting.md)" for more information.

- ODP.NET, Managed Driver - Microsoft Local Security Authority (MSLSA)

  ODP.NET, Managed Driver now supports the Kerberos credential cache type, MSLSA. MSLSA is used to access the Microsoft Kerberos Logon Session credentials cache.

  See also "[Using Kerberos](featConnecting.md)" for more information.

- ODP.NET, Managed Driver - SSL/TLS Connections Use a Single Port

  An ODP.NET, Managed Driver SSL/TLS connection will now continue on the original connection to the database listener instead of the previous SSL/TLS client redirection to a database server created new listening endpoint on a dynamic (ephemeral) port. Hence, firewalls will only need to allow access to the TNS listener's port. For example, 1521.

  See also "[Using Transport Layer Security and Secure Sockets Layer](featConnecting.md)" for more information.

- Service Relocation Connection Timeout

  Whenever a database service becomes unavailable, an application can encounter numerous connectivity errors. To avoid connection attempts to an unavailable service, ODP.NET, Managed and Unmanaged Drivers block any connection attempts until the service is up or until the configured time limit expires from the time when the service DOWN event was received. This feature is useful for planned outages and service relocations. It works with Oracle RAC and Oracle Data Guard.

  See also "[`ServiceRelocationConnectionTimeout`](InstallManagedConfig.md)" for more information.

- ODP.NET, Unmanaged Driver - Transaction Guard

  Transaction Guard allows ODP.NET applications to use at-most-once execution in case of planned and unplanned outages and repeated submissions. This feature's architecture has been modified to simplify the application code needed for transaction recovery. Developers will find it easier to utilize Transaction Guard in their applications.

  See also "[Using Transaction Guard to Prevent Logical Corruption](featTG.md)" for more information.

- ODP.NET, Managed Driver - Transaction Guard

  ODP.NET, Managed Driver now supports Transaction Guard. Its API and architecture are the same as ODP.NET, Unmanaged Driver's in ODAC 12c Release 4 to provide improved developer productivity.

  See also "[Using Transaction Guard to Prevent Logical Corruption](featTG.md)" for more information.

- ODP.NET, Unmanaged Driver - Managed Code for Distributed Transactions

  In .NET Framework 4.5.2 or higher, ODP.NET, Unmanaged Driver includes managed code for distributed transaction enlistment and commitment services using Microsoft Distributed Transaction Coordinator. Previously, applications had to use Oracle Services for Microsoft Transaction Server for these services. This new feature simplifies setup and deployment of ODP.NET, Unmanaged Driver applications that use distributed transactions.

  See also "[Distributed Transactions](InstallDistributedTransaction.md)" for more information.

- ODP.NET, Unmanaged Driver - SQL Translation Framework

  Introduced in Oracle Database 12c, SQL Translation Framework helps migrate .NET client applications that use SQL statements with vendor-proprietary syntax to semantically-equivalent Oracle syntax.

  The framework automatically translates non-Oracle SQL to Oracle SQL, thereby enabling existing client-side application code to run largely unchanged against an Oracle Database. This reduces the cost of migration to Oracle Database significantly.

  See also "[Database Application Migration: SQL Translation Framework](featSqlTranslationFW.md)" and "[SQL Translation Framework Configuration](InstallUnmanagedConfig.md)" for more information.

- Tracing Enhancements

  ODP.NET improves and unifies tracing features between managed and unmanaged ODP.NET. Key features include traces now output to a Windows temporary files directory and both providers use the same tracing parameters.

  See also "[Debug Tracing](featDebug.md)" for more information.

### Changes in Oracle Data Provider for .NET in ODAC 12c Release 3

The following are the changes in Oracle Data Provider for .NET for ODAC 12c Release 3.

#### New Features

The following features are new in this release:

- Entity Framework Code First and Code First Migrations

  In Entity Framework 6 and higher, managed and unmanaged ODP.NET support Code First and Code First Migrations.

  See also "[ADO.NET Entity Framework and LINQ to Entities](entity_framework.md)" for more information.

- Entity Framework 6

  ODP.NET, Managed and Unmanaged Drivers are certified and supported natively for Entity Framework version 6.

  See also "[Entity Framework Requirements](InstallEntityReq.md)" for more information.

- NuGet

  ODP.NET, Managed Driver is available in a NuGet package. This feature simplifies distributing customized ODP.NET, Managed Driver to developers.

  The Entity Framework assembly for Code First and Entity Framework 6 is available as a separate NuGet package.

  NuGet is the package manager for Microsoft .NET. NuGet can install software by copying library files to a .NET solution and automatically updating the project accordingly by adding references and updating config files.

  See also "[Installing Oracle Data Provider for .NET, Managed Driver](installODPmd.md)" for more information.

- ODP.NET, Managed Driver - XML DB APIs

  ODP.NET, Managed Driver now supports all ODP.NET XML classes supported by ODP.NET, Unmanaged Driver.

- Distributed Transactions without `Oracle.ManagedDataAccessDTC.dll`

  The `Oracle.ManagedDataAccessDTC.dll` assembly is no longer required for distributed transaction applications running in .NET Framework 4.5.2 or higher and ODP.NET, Managed Driver. Upon ODP.NET installation, `Oracle.ManagedDataAccessDTC.dll `is no longer placed into the Global Assembly Cache (GAC). For applications that use .NET Framework 4.5.1 or earlier, `Oracle.ManagedDataAccessDTC.dll` needs to either be placed in the application directory or in the GAC.

- ODP.NET, Managed Driver - Kerberos

  Kerberos is a network authentication service for security in distributed environments. ODP.NET, Managed Driver can now use Kerberos for single sign-on and centralized user authentication.

  See also "[Using Kerberos](featConnecting.md)" for more information.

- ODP.NET, Managed Driver - Implicit Ref Cursor

  ODP.NET, Managed Driver introduces support for the new Oracle Database 12c Implicit Ref Cursor. Configuration occurs using the \<implicitrefcursor\> .NET configuration section. When using database implicit ref cursors, the bindInfo element should be specified with a mode of "Implicit":

      <bindinfo mode="Implicit" />

  See also "[implicitRefCursor section](InstallManagedConfig.md)" for more information.

- Configuration Files: Unified Managed and Unmanaged ODP.NET Format

  ODP.NET, Unmanaged Driver now has the option of using the same configuration file format as ODP.NET, Managed Driver. The format simplifies configuration by using a single unified scheme. To utilize this format, the existing unmanaged ODP.NET configuration section should be renamed from \<oracle.dataaccess.client\> to \<oracle.unmanageddataaccess.client\>. The existing unmanaged ODP.NET elements and values are supported within the new section using the same format as with ODP.NET, Managed Driver.

  The traditional ODP.NET, Unmanaged Driver configuration file format will continue to be supported.

  See Also "[Configuration File Support](InstallUnmanagedConfig.md)" for more information.

### Changes in Oracle Data Provider for .NET Release 12.1.0.2

The following are the changes in Oracle Data Provider for .NET for Release 12.1.0.2.

#### New Features

The following features are new in this release:

- .NET Framework 4.5.2 Certification

  ODP.NET, Managed and Unmanaged Drivers are certified for .NET Framework 4.5.2.

  See also "[System Requirements](InstallSystemRequirements.md)" for more information.

- Character Data Types Extended to 32 KB

  ODP.NET, Managed Driver supports the `VARCHAR2`, `NVARCHAR2`, and `RAW` data types up to 32 KB in size. No code changes are required to use the larger data types.

  By being able to store more data, developers can use these data types more frequently, providing programming flexibility. In addition, SQL Server to Oracle Database application migration is easier with these new data type sizes.

- Return Number of Rows Affected from Each Input in Array Binding Operations

  When using array binding to execute multiple DML statements, ODP.NET, Managed Driver provides an array that lists the number of rows affected for each input value from the bound array, rather than just the total number of rows affected. This information provides more detailed feedback for the application developer. To retrieve the row count, ODP.NET can call the `OracleCommand.ArrayBindRowsAffected` property.

  With more detailed feedback on the array bound DML execution, the developer can better evaluate the query's efficiency and whether the data changes were correctly applied.

  See Also "[ArrayBindRowsAffected](CommandArrayBindRowsAffected.md)" for more information.

### Changes in Oracle Data Provider for .NET in ODAC 12c Release 2

The following are the changes in Oracle Data Provider for .NET for ODAC 12c Release 2.

#### New Features

The following features are new in this release:

- .NET Framework 4.5.1 Certification

  Oracle Data Provider for .NET is now certified for .NET Framework 4.5.1.

  See also "[System Requirements](InstallSystemRequirements.md)" for more information.

- .NET Framework 4.6 Certification

  Oracle Data Provider for .NET is now certified for .NET Framework 4.6.

  See also "[System Requirements](InstallSystemRequirements.md)" for more information.

- Improvements to ODP.NET, Managed Driver Versioning

  This feature allows unique identification of ODP.NET, Managed Driver assemblies which have the same assembly version number.

  See also "[Oracle Data Provider for .NET Versioning Scheme](InstallVersioningScheme.md)" for more information.

### Changes in Oracle Data Provider for .NET in ODAC 12c Release 1

The following are the changes in Oracle Data Provider for .NET for ODAC 12c Release 1.

#### New Features

The following feature is new in this release:

- LDAP Connections to Active Directory and Oracle Internet Directory

  ODP.NET, Managed Driver supports TNS alias resolution through a LDAP server/service, specifically Microsoft Active Directory and Oracle Internet Directory.

  This feature allows ODP.NET, Managed Driver to connect to a database using a directory server/service.

  See also "[Lightweight Directory Access Protocol](InstallManagedConfig.md)".

### Changes in Oracle Data Provider for .NET Release 12.1

The following are the changes in Oracle Data Provider for .NET for Release 12.1.

#### New Features

The following features are new in this release:

- ODP.NET, Managed Driver

  ODP.NET now includes a fully managed provider version, which is 100% native .NET code. ODP.NET, Managed Driver includes nearly all the features of ODP.NET, Unmanaged Driver and uses the same application programming interface. This makes migrating existing ODP.NET applications to ODP.NET, Managed Driver easier.

  With ODP.NET, Managed Driver, it is easier and faster to deploy ODP.NET. There are fewer assemblies, as few as one to deploy, which also makes patching straightforward, and the install size is smaller at less than 10 MB. Only one ODP.NET, Managed Driver assembly is necessary whether you are using 32-bit or 64-bit .NET Framework. Side-by-side deployment with other ODP.NET versions is simple since there are no unmanaged assemblies to account for. As a fully managed provider, ODP.NET can better integrate with Code Access Security and ClickOnce deployment.

  See also "[Installing Oracle Data Provider for .NET, Managed Driver](installODPmd.md)" .

- Support for Pluggable Database

  Pluggable Databases (PDBs) enable an Oracle database to contain a portable collection of schemas, schema objects, and nonschema objects that appears to ODP.NET as a separate database. ODP.NET can seamlessly use PDBs.

  PDBs allow fast database provisioning, fast database redeployment by unplugging and plugging in existing databases, and quick patching or upgrading many databases at the cost of doing it once or by unplugging a PDB and plugging it into a different container database. A machine can run more database instances in the form of PDBs than as individual, monolithic databases. It is also easier to separate application administrator duties from the Oracle system administrator duties.

  **See Also:**

  - "[Oracle Multitenant and Pluggable Databases](featConnecting.md)"

- Support for Auto Increment Identity Column

  Oracle Database 12c Release 1 (12.1) introduces an auto increment identity column. ODP.NET, Unmanaged Driver 12.1 and higher releases support interacting with this column data. Identity columns are generally used to uniquely identify rows in a table when there is no other natural primary key constraint.

  An identity column simplifies .NET development for applications with no natural primary key and eases application migration from databases that have an identity column.

  **See Also:**

  - "[IdentityInsert](DataAdapterIdentityInsert.md)"

  - "[IdentityUpdate](DataAdapterIdentityUpdate.md)"

  - "[OracleIdentityType Enumeration](OracleIdentityTypeEnumeration.md)"

- Support for Character Data Types Extended to 32 KB

  Starting with Oracle Database 12c Release 1 (12.1), ODP.NET, Unmanaged Driver now supports the `VARCHAR2`, `NVARCHAR2`, and `RAW` data types up to 32 KB in size. No code changes are required to use the larger data types.

  By being able to store more data, developers can use these data types more frequently, providing programming flexibility. In addition, SQL Server to Oracle Database application migration is easier with these new data type sizes.

- Boolean Data Type

  Oracle Database 12c Release 1 (12.1) introduces a new PL/SQL Boolean data type, which ODP.NET, Unmanaged Driver can store as an `OracleBoolean` data type. Booleans store `TRUE` or `FALSE` values.

  The ODP.NET `OracleBoolean` data type eases parameter binding and data type mapping setup with Boolean values.

  **See Also:**

  - "[OracleBoolean Structure](OracleBooleanStructure.md)"

- Enhanced Implicit REF Cursor Binding

  In Oracle Database 12c Release 1 (12.1), ODP.NET 12c can retrieve the results of a SELECT statement run in PL/SQL without an explicit target nor REF CURSOR data type. ODP.NET retrieves result sets from stored procedures implicitly without declaring a return type. It is no longer necessary to declare REF CURSOR metadata in a .NET configuration file, except when using Entity Framework, REF Cursors that can be updated, or constraint metadata is required to be passed to the client side.

  This capability simplifies using implicit Oracle result sets. In addition, it eases migration to the Oracle database from other vendor databases that use a similar feature.

  **See Also:**

  - "[ImplicitRefCursors](CommandImplicitRefCursors.md)"

  - "[Implicit REF CURSOR Binding](featImplRefCursor.md)"

- Return Number of Rows Affected from Each Input in Array Binding Operations

  When using array binding to execute multiple DML statements, Oracle Data Provider for .NET, Unmanaged Driver, now provides an array that lists the number of rows affected for each input value from the bound array, rather than just the total number of rows affected. This information provides more detailed feedback for the application developer. To retrieve the row count, ODP.NET can call the `OracleCommand.ArrayBindRowsAffected` property.

  With more detailed feedback on the array bound DML execution, the developer can better evaluate the query's efficiency and whether the data changes were correctly applied.

  **See Also:**

  - "[ArrayBindRowsAffected](CommandArrayBindRowsAffected.md)"

- Support for `APPLY` Keyword

  Language Integrated Query (LINQ) is a .NET querying language. At runtime, LINQ is translated into native database SQL before it can query the database. In some circumstances, LINQ uses the non-standard APPLY keyword in its SQL translation for retrieving lateral views. Oracle Database and ODP.NET support the APPLY keyword in Oracle Database 12c Release 1 (12.1) to more fully support LINQ.

  This feature allows the occasional LINQ query that uses SQL APPLY to work seamlessly with ODP.NET and Oracle Database for lateral views.

  **See Also:**

  - [ADO.NET Entity Framework and LINQ to Entities](entity_framework.md)

- Transaction Guard Support

  Transaction Guard in Oracle Database 12c Release 1 (12.1) preserves transaction commit outcomes for ODP.NET, Unmanaged Driver, 12c applications during planned and unplanned outages, preventing applications from repeatedly submitting the same transaction. Applications use a new logical transaction identifier to determine the last open transaction's outcome in a database session following an outage. With the known outcome, the application can confidently determine whether to resubmit the transaction or not. Without Transaction Guard, applications that retry operations following outages by committing duplicate transactions can cause logical corruptions.

  Transaction Guard preserves the commit outcome for every transaction and makes it available to ODP.NET applications. It allows ODP.NET developers to maintain at-most-once transaction execution.

  **See Also:**

  - "[Using Transaction Guard to Prevent Logical Corruption](featTG.md)"

- Recoverable Error Detection and Recovery

  After an Oracle Database 12c Release 1 (12.1) failure, ODP.NET, Unmanaged Driver, 12c can determine if a failed transaction is recoverable or not. ODP.NET returns the OracleException `IsRecoverable` property indicating whether the transaction is recoverable. If true, the application can retry the transaction.

  This feature makes determining whether failed transactions are recoverable easier, allowing applications to proceed quickly to the next step in the recovery process.

  **See Also:**

  - "[Using Transaction Guard to Prevent Logical Corruption](featTG.md)"

- Support for Faster and Planned Database Outage

  In Oracle Database 12c Release 1 (12.1), a database being brought offline automatically alerts ODP.NET applications of the impending downtime. ODP.NET will then stop allocating new connections and close connections returned to the pool from that particular instance.

  This feature enables databases to be brought offline more quickly and minimizes potential end user disruptions by disallowing new ODP.NET connections to databases being brought offline.

  **See Also:**

  - "[Using FCF Planned Outage to Minimize Service Disruption](featRAC.md)"

- Support for Oracle Notification Service

  Oracle Notification Service (ONS) is a publish and subscribe service for communicating Fast Application Notification (FAN) events. ODP.NET receives fast connection failover and load balancing messages from the database server through ONS. Previously, ODP.NET used Oracle Advanced Queuing (AQ) as its FAN publish and subscribe service.

  Because ONS is a memory-based service, it delivers messages faster than AQ. Using ONS, Oracle consolidates the publish and subscribe service that all Oracle data access drivers use.

  **See Also:**

  - "[Fast Application Notification](featRAC.md)"

- Support for Global Data Services

  Global Data Services (GDS) is a capability of Oracle Database 12c that extends the concept of services, which previously only was available in Oracle RAC, to a globally distributed configuration that can include a combination of Oracle RAC, Oracle Data Guard, and Oracle GoldenGate. This allows services to be deployed anywhere within this globally distributed configuration, supporting load balancing, high availability, database affinity, and so on with ODP.NET.

  ODP.NET applications can now more efficiently use database resources on a global basis to improve performance and availability. Applications that utilize the Oracle RAC concept of services can now extend the same benefits of automatic workload management to their Oracle Data Guard and Oracle GoldenGate configurations. Similarly, Oracle Data Guard and Oracle GoldenGate customers can now fully utilize the benefits of services and automatic workload management for their replicated configurations.

  **See Also:**

  - "[Runtime Connection Load Balancing](featRAC.md)"

  - "[Fast Connection Failover (FCF)](featRAC.md)"

- Transaction and Connection Association

  Connections associate with `System.Transactions` transactions when they enlist either implicitly through `enlist=true` connection string attribute, or explicitly through `OracleConnection.EnlistTransaction()` method. A connection in ODP.NET now, by default, detaches from a transaction only when the connection object is closed or when the transaction object is disposed.

  In earlier ODP.NET releases, the connection would get detached from a transaction under the conditions mentioned earlier and when the transaction was complete (committed, aborted, or timed out). When the transaction timeout elapses before the transaction completes, the connection unbinds itself from the transaction and all subsequent operations on this connection execute in `AutoCommit` mode. Any operations prior to the timeout roll back, but operations performed after the timeout commit. The new transaction unbinding default behavior also alerts users with an exception if transactions time out and subsequent operations execute on this connection before the transaction is disposed. This new behavior provides a consistent transactional experience for the end user, even when a timeout occurs.

  See also "[LegacyTransactionBindingBehavior](InstallUnmanagedConfig.md)" for more information.

- Greater Granular Connection Pool Monitoring

  Performance counters can now monitor at the application domain, pool, or database instance level.

  It is now easier to distinguish which application domains, pools, and instances are healthy and which ones are having problems.

  **See Also:**

  "[Connection Performance Counters](featConnecting.md)"
