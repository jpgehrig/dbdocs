Oracle Data Provider for .NET (ODP.NET) is an implementation of a .NET data provider for Oracle Database, using and inheriting from classes and interfaces available in the [Microsoft .NET Framework Class Library](glossary.md).

Following the .NET Framework, ODP.NET uses the ADO.NET model, which allows native providers to expose provider-specific features and data types. This is similar to Oracle Provider for OLE DB, where ADO (ActiveX Data Objects) provides an automation layer that exposes an easy programming model. ADO.NET provides a similar programming model, but without the automation layer, for better performance.

Oracle Data Provider for .NET uses Oracle native APIs to offer fast and reliable access to Oracle data and features from any .NET application. ODP.NET consists of three drivers: ODP.NET, Managed Driver, ODP.NET, Unmanaged Driver, and ODP.NET Core. ODP.NET, Managed Driver is a fully managed ADO.NET provider, consisting of fewer DLLs and smaller install size than ODP.NET, Unmanaged Driver. The managed driver has the same exact application programming interfaces (APIs) as ODP.NET, Unmanaged Driver. However, the managed driver's APIs are a subset of the Unmanaged Driver's APIs.

ODP.NET Core employs the same namespaces and application programming interfaces (APIs) as ODP.NET, Managed Driver. This parallel eases migration and developer learning curve from managed ODP.NET to ODP.NET Core. It does not support all managed ODP.NET functionality. ODP.NET Core supports a subset of managed ODP.NET APIs. These differences are listed later on in this documentation.

The ODP.NET classes described in this guide are contained in the `Oracle.DataAccess.dll` and `Oracle.ManagedDataAccess.dll` assembly.

- Client Applications: All ODP.NET classes are available for use in client applications.

  As ODP.NET, Managed Driver does not support all classes and members in the ODP.NET, Unmanaged Driver, the unsupported managed driver classes and members will be labeled Not Supported in ODP.NET, Managed Driver.

  ODP.NET Core does not support all classes and members in the ODP.NET, Managed Driver. The unsupported managed driver classes and members will be labeled Not Supported in ODP.NET Core.

- .NET Stored Procedures: Most ODP.NET classes can be used from within .NET stored procedures and functions. Those classes which cannot, are labeled Not Supported in a .NET Stored Procedure. Additionally, some classes contain members which may not be supported, and this is so indicated in the member tables that follow the class descriptions, and listed in Chapter 4 of this guide.

**See Also:**

- [Table 5-1](extenPorting.md)

- "[Oracle Data Provider for .NET Assemblies](intro003.md)" for class lists

- [Oracle Data Provider for .NET Stored Procedures](extensions.md)

- [Oracle Database Extensions for .NET Developer's Guide for Microsoft Windows](../clrnt/intro.md) for more information about .NET stored procedures and functions
