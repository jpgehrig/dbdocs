Oracle Data Provider for .NET, Unmanaged Driver requires the following:

- Windows operating system

  - 64-bit: Windows 8.1 (Pro and Enterprise Editions), Windows Server 2012 R2 x64 (Standard, Datacenter, Essentials, and Foundation Editions), Windows 10 x64 (Pro, Enterprise, and Education Editions), Windows Server 2016 x64 (Standard, Datacenter, and Essentials Editions), or Windows Server 2019 (Standard, Datacenter, and Essentials Editions).

    Oracle supports 32-bit ODP.NET and 64-bit ODP.NET for Windows x64 on these operating systems.

  **Note:**

  ODP.NET does not support Itanium systems.

- Microsoft .NET Framework

  - ODP.NET for .NET Framework 2.0 is only supported with Microsoft .NET Framework 3.5 SP 1 and later.

  - ODP.NET for .NET Framework 4 is only supported with Microsoft .NET Framework 4.5.2, 4.6.x, and 4.7.x.

- Access to Oracle Database 11g Release 2 or later

- Oracle Client release 19c

  This is automatically installed as part of the ODP.NET installation.

Promotable and distributed transactions may require Oracle Services for Microsoft Transaction Server in whole or in part. Refer to the [Distributed Transactions](InstallDistributedTransaction.md) section for more information.

Oracle Data Provider for .NET, Managed Driver requires the following:

- Same Windows operating system support as ODP.NET, Unmanaged Driver.

  ODP.NET, Managed Driver is built with AnyCPU. It runs on either 32-bit or 64-bit (x64) Windows and on either 32-bit or 64-bit (x64) .NET Framework.

- Microsoft .NET Framework 4.5.2, 4.6.x, or 4.7.x.

- Access to Oracle Database 11g Release 2 or later

ODP.NET Core requires the following:

- Operating systems:

  - Same Windows operating system support as managed and unmanaged ODP.NET

  - Oracle Linux 7

  - Red Hat Enterprise Linux 7

- Microsoft .NET Framework

  - Microsoft .NET Core 2.1 or later

  - Microsoft .NET Framework 4.6.1 and later

  **Note:**

  .NET Core 3.x is not currently supported.

- Access to Oracle Database 11g Release 2 or later

ODP.NET Core is compatible with ASP.NET Core 2.x and ASP.NET.

ODP.NET Core is built with AnyCPU. It supports 64-bit .NET and 32-bit .NET.

**See Also:**

- Document 726240.1 on My Oracle Support (formerly OracleMetaLink) for details on supported configuration for different ODP.NET versions. You can access My Oracle Support from:

  [`https://support.oracle.com`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=myoracle_support)

- [`https://msdn.microsoft.com/en-us/default.aspx`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=msdn_microsoft)
