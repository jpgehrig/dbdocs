### Atomicity, Consistency, Isolation, and Durability (ACID)

ACID consists of the four primary attributes provided to any transaction by a transaction manager (also called a transaction manager).

### component object model (COM)

A binary standard that enables objects to interact with other objects, regardless of the programming language in which each object was written.

### distributed component object model (DCOM)

An extension of COM that enables objects to interact with other objects across a network.

### data manipulation language

The category of SQL statements that query and update database data. Common DML statements are `SELECT`, `INSERT`, `UPDATE`, and `DELETE`.

### JOB_QUEUE_PROCESSES

This initialization parameter specifies the maximum number of `DBMS_JOB` jobs and Oracle Scheduler (`DBMS_SCHEDULER`) jobs running concurrently on an instance. This parameter must be set to at least 1 to run Oracle Scheduler or `DBMS_JOB` jobs and to use database features that depend on these jobs

### listener.ora

A listener configuration file that identifies the following for a listener:

- Unique name

- Protocol addresses on which it accepts connection requests

- Services for which it is listening

### Microsoft .NET

Microsoft .NET is a set of Microsoft software technologies used to connect information, people, systems, and devices through web services to each other and to larger applications over the Internet.

### Microsoft application demo

An Oracle Call Interface (OCI) implementation of the Visual C++ Sample Bank package that ships with Microsoft Transaction Server on Windows.

### Microsoft Distributed Transaction Coordinator (MS DTC)

The focal point of the transaction process is a component of Microsoft Transaction Server called Microsoft Distributed Transaction Coordinator (MS DTC).

### Microsoft Transaction Server

A COM-based transaction processing system that runs on an Internet or network server.

### mtssys

The default Microsoft Transaction Server administrator username. In releases prior to Oracle9i Database release 1 (9.0.1), this was the username for the OraMTS.

### net service name

The name used by clients to identify an Oracle Net server and the specific system identifier (SID) or database for the Oracle Net connection. A net service name is mapped to a port number and protocol. A net service name is also known as a connect string, database alias, host string, or service name.

This also identifies the specific SID or database to which the connection is attaching, and not just the Oracle Net server.

### OraMTS

Abbreviation for "Oracle Services for Microsoft Transaction Server".

### Oracle Call Interface (OCI)

An application programming interface that enables you to manipulate data and schemas in a database. You compile and link an OCI program in the same way that you compile and link a nondatabase application. There is no requirement for a separate preprocessing or precompilation step.

### Oracle Data Provider for .NET (ODP.NET)

Oracle Data Provider for .NET (ODP.NET) features optimized data access to the Oracle Database from a .NET environment. ODP.NET includes support for connection pooling, PL/SQL, LOBs, RefCursors, globalization/localization, proxy user authentication/ parameter array binding, named parameters, and safe type mapping between Oracle types and .NET types.

### Oracle Fail Safe

Ensures that if a failure occurs on one cluster node, then the databases and applications running on that node fail over (move) automatically and quickly to a surviving node.

### Oracle MTS Recovery Service

The Oracle MTS Recovery Service resolves in-doubt transactions on the computer that started the failed transaction. A scheduled recovery job for each Microsoft Transaction Server-enabled database lets the Oracle MTS Recovery Service resolve in-doubt transactions.

### Oracle Open Database Connectivity (ODBC) Driver

Oracle ODBC Driver provides a standard interface that allows one application to access many different data sources. The application's source code does not have to be recompiled for each data source. A database driver links the application to a specific data source. A database driver is a dynamic link library that an application can invoke on demand to gain access to a particular data source. Therefore, the application can access any data source for which a database driver exists.

### Oracle Provider for OLE DB

Interfaces that offer high performance and efficient access to Oracle data by applications, compilers, and other database components.

### Oracle Services for Microsoft Transaction Server (OraMTS)

A component that provides full integration of the Oracle Database with Microsoft Transaction Server. This component enables you to develop and deploy COM-based applications using Microsoft Transaction Server.

### Optimal Flexible Architecture (OFA)

A set of file naming and placement guidelines for Oracle software and databases.

### resource manager (RM)

Microsoft Transaction Server enlists the database to act as a resource manager (RM) in the transaction process.

### SYSDBA

A special database administration role that contains all system privileges with the `ADMIN` `OPTION` and the `SYSOPER` system privilege. `SYSDBA` also permits `CREATE DATABASE` actions and time-based recovery.

### SYSOPER

A special database administration role that permits a database administrator to perform `STARTUP`, `SHUTDOWN`, `ALTER` `DATABASE` `OPEN/MOUNT`, `ALTER` `DATABASE` `BACKUP`, `ARCHIVE` `LOG`, and `RECOVER`, and includes the `RESTRICTED` `SESSION` privilege.

### tnsnames.ora

A file that contains connect descriptors mapped to net service names. The file can be maintained centrally or locally for use by all or individual clients.

### transaction identifiers (XIDs)

Identifies the client computer from which a transaction originated.
