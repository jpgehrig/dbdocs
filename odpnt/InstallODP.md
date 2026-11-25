Oracle Data Provider for .NET is part of Oracle Data Access Components (ODAC), which can be downloaded from OTN. Oracle Data Provider for .NET, Unmanaged Driver can be installed through XCopy or Oracle Universal Installer.

- XCopy

  Administrators use XCopy to deploy Oracle Data Provider for .NET to large numbers of computers for production deployments. The XCopy has a smaller installation size and fine-grain control during installation and configuration than Oracle Universal Installer.

- Oracle Universal Installer (OUI)

  Developers and administrators use Oracle Universal Installer for automated ODP.NET installations. It includes documentation and code samples that are not part of the XCopy.

**Note:**

This section describes installation using the Oracle Universal Installer. For installation and configuration using the XCopy install, refer to the README.TXT file that is part of the XCopy installation.

Additionally, Oracle Data Provider for .NET Dynamic Help is registered with Visual Studio, providing context-sensitive online help that is seamlessly integrated with Visual Studio Dynamic Help. With Dynamic Help, the user can access ODP.NET documentation within the Visual Studio IDE by placing the cursor on an ODP.NET keyword and pressing the F1 function key.

Oracle Data Provider for .NET creates an entry in the `machine.config` file of the computer on which it is installed, for applications using the `OracleClientFactory` class. This enables the `DbProviderFactories` class to recognize ODP.NET.

ODP.NET, Unmanaged Driver Entity Framework 6 and Code First functionality are available through a NuGet package. OUI and Xcopy installations include this package as well, but require post-install configuration steps. The NuGet package for ODP.NET, Unmanaged Driver Entity Framework automates these post-install steps, except for the application-specific connection string settings.

**See Also:**

[Configuring for Entity Framework Code First](InstallEntityConfig.md)

### File Locations After Installation

The `Oracle.DataAccess.dll` assembly is installed to the following locations

.NET Framework 2.0:

`ORACLE_BASE``\``ORACLE_HOME``\``odp.net\bin\2.x` directory

.NET Framework 4:

`ORACLE_BASE``\``ORACLE_HOME``\``odp.net\bin\4` directory

**Note:**

If the machine has the corresponding .NET Framework installed, then the `Oracle.DataAccess.dll` assembly is added to the Global Assembly Cache (GAC) if machine-wide configuration is set. This is to ensure that existing applications can start using the newly installed ODP.NET version immediately. If this is not desired, then be sure to remove the policy DLLs from the GAC or choose non-machine-wide configuration.

Documentation and the `readme.txt` file can be accessed through `ORACLE_BASE``\``ORACLE_HOME``\``ODACDoc\DocumentationLibrary\doc\index.htm` in ODAC installations done using Oracle Universal Installer. When Oracle Developer Tools for Visual Studio is installed, Oracle documentation is installed in Visual Studio itself.

Samples are provided in the `ORACLE_BASE``\``ORACLE_HOME``\``ODACsamples` directory for ODAC installations done using Oracle Universal Installer.

### Search Order for Unmanaged DLLs

ODP.NET consists of managed and unmanaged binaries. Through the use of the `DllPath` configuration parameter, each application can specify the `ORACLE_BASE\\ORACLE_HOME``\bin` location that the dependent unmanaged Oracle Client binaries are loaded from. However, the `ORACLE_BASE\\ORACLE_HOME` must have the same ODP.NET version installed as the version that the application uses. Otherwise, a version mismatch exception is thrown.

The `Oracle.DataAccess.dll` searches for dependent unmanaged DLLs (such as Oracle Client) based on the following order:

1.  Directory of the application or executable.

2.  `DllPath` setting specified by application config or `web.config`.

3.  `DllPath` setting specified by `machine.config`.

4.  `DllPath` setting specified by the Windows Registry.

    `HKEY_LOCAL_MACHINE\Software\Oracle\``ODP.NET\``version``\DllPath`

5.  Directories specified by the Windows `PATH` environment variable.

Upon installation of ODP.NET, Oracle Universal Installer sets the `DllPath` Windows Registry value to the `ORACLE_BASE\\ORACLE_HOME``\bin` directory where the corresponding dependent DLLs are installed. Developers must provide this configuration information on an application-by-application basis.

When a new ODP.NET version is installed, default values are set in the Windows Registry for the new version. Because the policy DLLs redirect all ODP.NET references to this new ODP.NET version, applications use the default values. Developers can provide a config or `web.config` file specific to the application to prevent this redirection. The configuration file settings always apply to the application, regardless of whether or not patches or new versions are installed later.

**Note:**

Both `Oracle.DataAccess.dll` for .NET Framework 2.0 and `Oracle.DataAccess.dll` for .NET Framework 4 use the same unmanaged DLL, `OraOps12.dll`.

#### ODP.NET and Dependent Unmanaged DLL Mismatch

To enforce the usage of `Oracle.DataAccess.dll` assembly with the correct version of its unmanaged DLLs, an exception is raised if `Oracle.DataAccess.dll` notices it has loaded a mismatched version of a dependent unmanaged DLL.
