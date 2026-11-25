This section discusses Oracle Data Provider for .NET and Oracle Database components that use Oracle Data Provider for .NET for data access. It briefly describes what each component does and where to find additional documentation.

These Oracle products provide .NET integration on the Windows operating system:

### Oracle Data Provider for .NET (ODP.NET)

Oracle Data Provider for .NET provides fast data access from .NET clients to Oracle databases. ODP.NET enables .NET applications to take advantage of Oracle advanced features, such as Oracle Real Application Clusters (Oracle RAC) and XML DB. It is accessible through any .NET language, including C#, Visual Basic .NET, and C++ .NET.

ODP.NET consists of three drivers: ODP.NET, Managed Driver, ODP.NET, Unmanaged and ODP.NET Core. ODP.NET, Managed Driver is a fully managed ADO.NET provider, consisting of fewer DLLs and smaller install size than ODP.NET, Unmanaged Driver. The managed driver has the same exact application programming interfaces (APIs) as ODP.NET, Unmanaged Driver. However, the managed driver's APIs are a subset of the Unmanaged Driver's APIs.

ODP.NET Core is a multi-platform provider for Microsoft .NET Core. In functionality, it is very similar to ODP.NET, Managed Driver. However, ODP.NET Core has a subset of managed ODP.NET's APIs.

This guide describes Oracle Data Provider for .NET features, their use, installation, requirements, and classes. The guide distinguishes which classes and APIs are supported for the managed driver, unmanaged driver, .NET stored procedures, and .NET clients.

Additionally, Oracle Data Provider for .NET Dynamic Help, which is context-sensitive online help, contains the same reference sections available in Oracle Data Provider for .NET Developer's Guide for Microsoft Windows, this guide.

Oracle Data Provider for .NET Dynamic Help is integrated with Visual Studio Dynamic Help. With Dynamic Help, you can access Oracle Data Provider for .NET documentation within Visual Studio by placing the cursor on an Oracle Data Provider for .NET keyword and pressing the F1 function key.

### Oracle Developer Tools for Visual Studio

Oracle Developer Tools is an add-in to Visual Studio that provides graphical user interface (GUI) access to Oracle functionality. It provides improved developer productivity and ease of use. Oracle Developer Tools provide the ability to build .NET stored procedures using Visual Basic .NET, C#, and other .NET languages.

Oracle Developer Tools for Visual Studio Help describes Oracle Developer Tools. This help is in the form of dynamic help, which installs as part of the product.

Additionally, the Oracle Developer Tools for Visual Studio Help includes the following documentation:

- [Oracle Database PL/SQL Language Reference](../lnpls/overview.md)

- [Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md)

- [Oracle Database Extensions for .NET Developer's Guide for Microsoft Windows](../clrnt/intro.md)

- [Oracle Database Error Messages Reference](../errmg/index.md)

- Access to Oracle Data Provider for .NET Dynamic Help

- Access to Oracle Providers for ASP.NET Dynamic Help

### Oracle Database Extensions for .NET

Oracle Database Extensions for .NET provides the following:

- Hosting of Microsoft Common Language Runtime (CLR) in an external process on the server side, to execute .NET stored procedures.

- ODP.NET data access on the server side, from within the .NET stored procedure.

Oracle Data Provider for .NET Developer's Guide for Microsoft Windows describes all ODP.NET classes. Classes that are not supported by Oracle Database Extensions for .NET are described as Not Supported in a .NET Stored Procedure.

**See Also:**

- Oracle Developer Tools for Visual Studio Help

- [Oracle Database Extensions for .NET Developer's Guide for Microsoft Windows](../clrnt/intro.md) for more information about Oracle Database Extensions for .NET features, their use, installation, and requirements.

- "[Oracle Data Provider for .NET Assemblies](intro003.md)" for class listings

- [Oracle Data Provider for .NET Stored Procedures](extensions.md)

### Oracle Providers for ASP.NET

Oracle Providers for ASP.NET offer ASP.NET developers an easy to use method to store state common to web applications within an Oracle database. These providers are modeled on existing Microsoft ASP.NET providers, sharing similar schema and programming interfaces to provide .NET developers a familiar interface. Oracle supports the following providers:

- Cache Dependency Provider

- Membership Provider

- Profile Provider

- Role Provider

- Session State Provider

- Site Map Provider

- Web Events Provider

- Web Parts Personalization Provider

Oracle Providers for ASP.NET classes, their use, installation, and requirements are described in Oracle Providers for ASP.NET Developer's Guide for Microsoft Windows, which is also provided as dynamic help.

### Oracle Services for Microsoft Transaction Server

Oracle Services for Microsoft Transaction Server (OraMTS) permit Oracle databases to be used as resource managers in Microsoft application coordinated transactions. OraMTS acts as a proxy for the Oracle database to the Microsoft Distributed Transaction Coordinator (MSDTC). As a result, OraMTS provides client-side connection pooling and allows client components that leverage Oracle to participate in promotable and distributed transactions. In addition, OraMTS can operate with Oracle databases running on any operating system, given that the services themselves are run on Windows.

**See Also:**

[Oracle Services for Microsoft Transaction Server Developer's Guide for Microsoft Windows](../ntmts/using-mts-with-oracledb.md) for description about OraMTS, which allows Oracle databases to be used as resource managers in distributed transactions.

### Oracle TimesTen In-Memory Database

ODP.NET support for Oracle TimesTen In-Memory Database (TimesTen) provides fast and efficient ADO.NET data access for applications that require the highest performance.

You can use ODP.NET with any of the following TimesTen installations:

- TimesTen Data Manager only (for direct connections)

- TimesTen Client only (for client/server connections, assuming a TimesTen Data Manager instance and TimesTen Server instance are accessible elsewhere)

- TimesTen Data Manager with TimesTen Server

For more information on ODP.NET features specific to a TimesTen environment, refer to the Oracle Data Provider for .NET Oracle TimesTen In-Memory Database Support User's Guide.

**Note:**

TimesTen does not support ODP.NET, Managed Driver and ODP.NET Core.
