### Getting started with ODP.NET, Managed Driver

You can get started with ODP.NET Managed Driver by either using the Windows Installer, Oracle Universal Installer (OUI), XCopy, or NuGet.

If you are using OUI: Follow the Oracle Universal Installer (OUI) steps to install ODP.NET, Managed Driver

If you are using XCopy: Download ODP.NET, Managed Driver `.zip` file to a directory for staging the install. The `.zip` file contains a README file with XCopy installation instructions.

Run the `configure.bat` script in one of the following directories:

- For 32-bit .NET Framework: `OH\odp.net\managed\x86`

- For 64-bit .NET Framework: `OH\odp.net\managed\x64`

Each directory contains an `unconfigure.bat` if ODP.NET, Managed Driver needs to be unconfigured and removed from the machine.

If you are using NuGet: Download the ODP.NET NuGet package(s) and use NuGet Package Manager to install.

The following NuGet packages are available:

- ODP.NET, Managed Driver

- Entity Framework assembly for Code First and Entity Framework 6 or higher use with ODP.NET, Managed Driver

If you are using Windows Installer: Follow the Microsoft Windows Installer (MSI) steps to install ODP.NET, Managed Driver.

### ODP.NET, Managed Driver Files

ODP.NET, Managed Driver consists of the following files:

Table 2-1 ODP.NET, Managed Driver Files with Descriptions

| File                                                       | Description                                                                                                     |
|:-----------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------|
| `Oracle.ManagedDataAccess.dll`                             | Platform-independent (AnyCPU), fully-managed ADO.NET provider                                                   |
| `\Resources\<lang>\Oracle.ManagedDataAccess.resources.dll` | Platform-independent (AnyCPU), fully-managed ADO.NET provider resource DLLs.                                    |
| `OraProvCfg.exe`                                           | Platform-independent (AnyCPU) utility to configure/unconfigure ODP.NET, Managed and Unmanaged Drivers.          |
| `configure.bat`                                            | Batch file to place ODP.NET, Managed Driver into the GAC and add configuration entries into the machine.config. |
| `unconfigure.bat`                                          | Batch file to remove ODP.NET, Managed Driver from the GAC and remove configuration entries from machine.config. |
| `tnsnames.ora`                                             | A sample configuration file that defines data source aliases.                                                   |
| `sqlnet.ora`                                               | A sample configuration file that configures network related settings.                                           |
| `ConfigSchema.xsd`                                         | An XML schema file that defines the configuration section for ODP.NET, Managed Driver.                          |
| `Oracle.ManagedDataAccess.EntityFramework.dll`             | Platform-independent (AnyCPU), fully-managed assembly for Code First and Entity Framework 6 higher              |
| `\x64\Oracle.ManagedDataAccessIOP.dll`                     | Platform-dependent (64-bit .NET Framework), Managed Assembly for Kerberos support                               |
| `\x86\Oracle.ManagedDataAccessIOP.dll`                     | Platform-dependent (32-bit .NET Framework), Managed Assembly for Kerberos support                               |

**See Also:**

[Oracle Database Installation Guide for Microsoft Windows](../ntdbi/index.md) for installation instructions

### Platform-Dependent Assemblies and Their Search Order

ODP.NET, Managed Driver has one set of platform-dependent DLL: `Oracle.ManagedDataAccessIOP.dll`, which has a 32-bit .NET version and a 64-bit .NET version. While they consist of 100% managed code, they call APIs outside of .NET, which is why they are platform dependent.

`Oracle.ManagedDataAccessIOP.dll` supports Kerberos. These assemblies are only needed in your application if you are using Kerberos security.

These assemblies are not intended to be directly referenced by an application. Rather, they will be referenced implicitly. ODP.NET, Managed Driver will reference the assemblies by using the following search order:

1.  Global Assembly Cache

2.  The web application's bin directory or Windows application's `EXE` directory

3.  The `x86` or `x64` subdirectory based on whether the application runs in 32-bit or 64-bit .NET Framework. If the application is built using AnyCPU, then ODP.NET will use the correct DLL bitness as long as the assembly is available. Oracle recommends using this method of finding dependent assemblies if your application is AnyCPU.

For example, use the following steps for your application to use the 64-bit version of `Oracle.ManagedDataAccessIOP.dll`:

1.  Right click Visual Studio project, select Add, and then select New Folder.
2.  Name the folder x64.
3.  Right-click the newly created x64 folder, select Add, and then select Existing Item.
4.  Browse to the folder where the DLL is located, which usually is `ORACLE_HOME``\odp.net\managed\x64`, and then select Oracle.ManagedDataAccessIOP.dll.
5.  Click Add.
6.  Click the newly added Oracle.ManagedDataAccessIOP.dll in the x64 folder.
7.  In the properties window, set Copy To Output Director to Copy Always.

For x86 targeted applications, name the folder x86 and add the assembly from the x86 directory.

To make your application platform independent even if it depends on `Oracle.ManagedDataAccessIOP.dll ` create both x64 and x86 folders with the necessary assemblies added to them.

### File Locations After Installation

In an Oracle Universal Installer based install, the `Oracle.ManagedDataAccess.dll` assembly is installed to the following location:

.NET Framework 4:

`ORACLE_BASE``\``ORACLE_HOME``\``odp.net\managed\common` directory

Documentation and the `readme.txt` file can be accessed through `ORACLE_BASE``\``ORACLE_HOME``\``ODACDoc\DocumentationLibrary\doc\index.htm` in ODAC installations done using Oracle Universal Installer. When Oracle Developer Tools for Visual Studio is installed, Oracle documentation is installed in Visual Studio itself.

Samples are provided in the `ORACLE_BASE``\``ORACLE_HOME``\``ODACsamples` directory for ODAC installations done using Oracle Universal Installer or the Oracle Developer Tools for Visual Studio subdirectory usually located in the `C:\Program Files (x86) `directory for ODAC MSI installs.
