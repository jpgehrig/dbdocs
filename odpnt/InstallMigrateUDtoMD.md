To ease migration, the APIs of ODP.NET, Managed Driver are a complete subset of the APIs of ODP.NET, Unmanaged Driver. As long as the existing unmanaged ODP.NET applications use currently available managed ODP.NET APIs, migration is straightforward and simple.

In future versions, the managed driver will support more APIs of ODP.NET, Unmanaged Driver. Both drivers will continue to be enhanced to support the latest Oracle Database and .NET Framework features.

To migrate from unmanaged to managed ODP.NET, perform the following steps:

1.  Add a Reference to `Oracle.ManagedDataAccess.dll` in the .NET project.
2.  Change the existing ODP.NET, Unmanaged Driver namespace references to ODP.NET, Managed Driver references.
        // C#
        using Oracle.ManagedDataAccess.Client;
        using Oracle.ManagedDataAccess.Types;

        // VB
        Imports Oracle.ManagedDataAccess.Client
        Imports Oracle.ManagedDataAccess.Types
3.  Some provider configuration settings may need to be migrated because ODP.NET, Managed Driver supports very few Windows Registry settings and a different .NET configuration setting format.

**See Also:**

[Configuring Oracle Data Provider for .NET](InstallConfig.md) for more information.
