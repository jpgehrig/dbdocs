### Getting started with ODP.NET Core

You can get started with ODP.NET Core on Windows by using the Windows Installer, Oracle Universal Installer (OUI), or NuGet. Only NuGet can be used to install ODP.NET Core on Linux.

If you are using Windows Installer: Follow the Oracle Developer Tools for Visual Studio Microsoft Windows Installer (MSI) steps. MSI will copy the ODP.NET Core NuGet package to the machine.

If you are using OUI: Follow the ODAC OUI steps to install ODP.NET Core. OUI will copy the ODP.NET Core NuGet package to the machine.

If you are using NuGet: Download the ODP.NET Core NuGet package and use NuGet Package Manager to install.

### ODP.NET Core Files

ODP.NET Core consists of the following files:

Table 2-2 ODP.NET, Core Files with Descriptions

| File                           | Description                                                                                 |
|:-------------------------------|:--------------------------------------------------------------------------------------------|
| `Oracle.ManagedDataAccess.dll` | Platform-independent (AnyCPU), operating system independent, fully-managed ADO.NET provider |

### File Locations After Installation

In an Oracle Universal Installer based install, the ODP.NET Core package is installed to the following directory:

    ORACLE_BASE\ORACLE_HOME\odp.net\Core2

Documentation and the `readme.txt `file can be accessed through `ORACLE_BASE\ORACLE_HOME\ODACDoc\DocumentationLibrary\doc\index.htm` in ODAC installations done using Oracle Universal Installer. When Oracle Developer Tools for Visual Studio is installed, Oracle documentation is installed in Visual Studio itself.

Samples are provided in the `ORACLE_BASE``\ORACLE_HOME\ODACsamples` directory for ODAC installations done using Oracle Universal Installer or the Oracle Developer Tools for Visual Studio subdirectory usually located in the `C:\Program Files (x86)` directory for ODAC MSI installs.
