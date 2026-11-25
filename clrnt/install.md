These topics describe the installation of Oracle Database Extensions for .NET, system requirements, and file locations.

- System Requirements

- Requirements for .NET Stored Procedures and Functions

- Installation

- Configuring Extproc Agent Using Windows Service

- File Locations after Installation

- Listener and Tnsnames Files

- Migrating .NET Stored Procedures from Oracle Database 12c Release 1 (12.1) or later

- Migrating .NET Stored Procedures from Oracle Database 11g Release 2 (11.2)

- Mandatory Migration of .NET 1.x Stored Procedures to .NET 2.0 or Later

- Oracle Database Extensions for .NET Registry Options

- extproc.exe.config Configuration File

### System Requirements

Each release of Oracle Database Extensions for .NET has very specific version requirements. The following system requirements only apply to Oracle Database Extensions for .NET version 19.3. If you are using a different version, please see the documentation specific to your version:

- Oracle Database 19.3 on Windows.

  **Note:**

  Oracle Database Extensions for .NET is only supported on the Windows Platform.

- Microsoft .NET Framework

  - Oracle Database Extensions for .NET Framework 2.0 is only supported with Microsoft .NET Framework 3.5 SP 1 and later

  - Oracle Database Extensions for .NET Framework 4 is only supported with Microsoft .NET Framework 4.5.2, 4.6.x, and 4.7.x

  **Note:**

  Microsoft Framework 1.x is no longer supported as of Oracle Database Extensions for .NET version 11.1.0.7.20. If you have stored procedures that require .NET Framework 1.x, you will need to take some special steps to make them work with this release.

- Oracle Data Provider for .NET version 19.3 (if data access in stored procedures is required).

- Oracle Developer Tools for Visual Studio 18.3 or higher is required for .NET stored procedure deployment.

  **Note:**

  Oracle Developer Tools for Visual Studio is not released with Oracle Database. It can be obtained from the Oracle .NET Developer Center at OTN.

**See Also:**

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/operating-system-checklist-oracle-database-installation-microsoft-windows.md)

- Mandatory Migration of .NET 1.x Stored Procedures to .NET 2.0 or Later

### Requirements for .NET Stored Procedures and Functions

A .NET stored procedure or function must meet the following requirements:

- Be declared a public static method.

- Not be a constructor or a destructor.

- Use parameter types that are compatible with the Oracle native database types.

### Installation

This section discusses many of the results of Oracle Database Extensions for .NET installation.

It covers these topics:

- Installation and First Use

- File Locations after Installation

- Oracle CLR Services and the Oracle Home User Account

- Using the OraClrCtl Utility to Create and Run OraClrAgent Services

#### Installation and First Use

In earlier releases of Oracle Database, Oracle Database Extensions for .NET required a custom installation. Beginning in Oracle Database 12c, Oracle Database Extensions for .NET is always installed, however it is not enabled, and Windows services for it are not created.

Before the first use of Oracle Database Extensions for .NET, do the following:

1.  Install Oracle Database 19c and either allow the installer to create the database for you, or install the database software only and use Database Configuration Assistant to create a database afterwards.
2.  Execute the following to create the Oracle Database Extensions for .NET windows service.
        oraclrctl -new

    **See Also:**

    "Using the OraClrCtl Utility to Create and Run OraClrAgent Services"

#### Oracle CLR Services and the Oracle Home User Account

Beginning with Oracle Database 12c, the Oracle CLR services run as the Oracle Home User. Database installations now provide a way for users to specify at installation time a Oracle Home User account under which the various Oracle services are run. This non-privileged account can be a local user or a domain user without administrative privileges.

In earlier versions of Oracle Database, these CLR services were created automatically by the installer. Now, they are created manually, after installation, using the `OraClrCtl.exe` utility.

The database installation does not create the Oracle CLR service but still performs the necessary configuration in the database for Oracle Database Extensions for .NET to function properly. This includes the following:

- Creating the `listener.ora` entries for `extproc`.

- Creating a `clr` folder under `ORACLE_BASE\\ORACLE_HOME``\bin`.

- Installing the `OraClrCtl.exe` utility described in Using the OraClrCtl Utility to Create and Run OraClrAgent Services.

**See Also:**

[Oracle Database Platform Guide for Microsoft Windows](../ntqrf/managing-oracle-home-user.md)

#### Using the OraClrCtl Utility to Create and Run OraClrAgent Services

The `OraClrCtl.exe` utility creates the `OraClrAgnt` service in the `ORACLE_BASE\\ORACLE_HOME``\bin` directory and configures it to run using the Oracle Home User account specified during database installation. The service can be accessed through the Service Control Panel, as `Oracle`ORACLE_HOME`ClrAgent`, where `ORACLE_HOME` represents your Oracle home.

`OraClrCtl.exe` can also start, stop, and delete the `OraClrAgnt` service.

Example

    oraclrctl.exe -start -host computer-pc5

`OraClrCtl.exe` accepts these arguments:

`-new`: Create and start new service.

`-delete`: Delete service.

`-start`: Start Service.

`-stop`: Stop service.

`-host` `hostname`: Execute the operation on the specified host. If no host is specified, defaults to local host.

`OraClrCtl.exe` returns `TRUE` (1) or `FALSE` (0), and displays a `SUCCESS` or `FAILURE` message. Upon a failure, the message displays the OS error number and the corresponding message.

### Configuring Extproc Agent Using Windows Service

`OraClrAgnt` is created by `OraClrCtl.exe`. The service can be accessed through the Service Control Panel, as `Oracle``ORACLE_HOME``ClrAgent`, where `ORACLE_HOME` represents your Oracle home.

This service accepts these parameters listed in Table 2-1.

These parameter values can be specified as part of the Start Parameters in the properties window of the Control Panel Service. In this case, the parameter values are not saved and the values must be supplied again if the service is restarted later.

To persist the parameter values, you can change the Windows registry entry for this service and provide the parameter values as command line parameters to `OraClrAgnt.exe`. To do this, set the Windows registry key, `ImagePath`, located at

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ Oracle``OracleHome``ClrAgent`

The value should be something similar to the following:

`ORACLE_BASE\\ORACLE_HOME``\bin\OraClrAgnt.exe agent_sid=CLRExtProc ``max_dispatchers=2 tcp_dispatchers=0 max_task_threads=6 max_sessions=25`` ENVS="EXTPROC_DLLS=ONLY:``ORACLE_BASE\\ORACLE_HOME``\bin\oraclr19.dll"`

If the service cannot be started or stopped, the error messages are logged in the Application Log of the Event Viewer, with the service name as the event source name.

**See Also:**

Oracle CLR Services and the Oracle Home User Account for a description of how `OraClrAgnt` is created by `OraClrCtl.exe`.

#### OraClrAgnt Service Parameters

Table 2-1 lists the parameters which can be configured using this service.

Table 2-1 OraClrAgnt Service Parameters

| Parameters         | Descriptions                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `agent_sid`        | This represents the `SID` of the `extproc` process. The default value is `CLRExtProc`. This is a mandatory parameter. If this parameter value is changed, appropriate changes need to be made in `tnsnames.ora` and `listener.ora` files.                                                                                                                                                                       |
| `ENVS`             | Variable that specifies the `EXTPROC_DLLS` environment variable, which restricts the DLLs that `extproc` can load.<br>This is similar to setting environment variables to external procedures using `listener.ora`.<br>Refer to "Table 13–5 External Procedures Settings in listener.ora" in [Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md) for more information. |
| `listener_address` | Address on which the listener is listening. This is an optional parameter. If it is not specified, then this is set to the default value.                                                                                                                                                                                                                                                                       |
| `max_dispatchers`  | Number of maximum dispatchers in the `extproc` process. This is an optional parameter. If it is not specified, then this number is set to a default value.                                                                                                                                                                                                                                                      |
| `max_sessions`     | Number of maximum sessions in the `extproc` process. This is an optional parameter. If it is not specified, then this number is set to a default value.                                                                                                                                                                                                                                                         |
| `max_task_threads` | Number of maximum task threads in the `extproc` process. This is an optional parameter. If it is not specified, then this number is set to a default value.                                                                                                                                                                                                                                                     |
| `shutdown_address` | Address on which the agent should listen for shutdown messages from `agtctl`. This is an optional parameter. If it is not specified, then this is set to the default value.                                                                                                                                                                                                                                     |
| `tcp_dispatchers`  | Number of TCP dispatchers in the `extproc` process. This is an optional parameter. If it is not specified, then this number is set to a default value.                                                                                                                                                                                                                                                          |

**See Also:**

[Oracle Call Interface Programmer's Guide,](../lnoci/multithreaded-extproc-agent.md) Table F-2, Configuration Parameters for `agtctl`

#### Tuning OraClrAgnt for Performance

You should tune the `OraClrAgnt` to match the expected load on your system.

Excessive `extproc.exe` processes being spawned is a sign that you have set the configuration values too low.

Start with the following values and increase as you test your system for performance:

| OraClrAgnt Parameter | Initial Value |
|:---------------------|:--------------|
| `max_sessions`       | `25`          |
| `max_task_threads`   | `6`           |
| `max_dispatchers`    | `2`           |

### File Locations after Installation

`OraClr19.dll` is installed in the `ORACLE_BASE\\ORACLE_HOME`\\`bin` directory.

`Oracle.Database.Extensions.dll` is installed to the following locations:

- .NET Framework 2.0:

  `ORACLE_BASE\\ORACLE_HOME``\ODE.NET``\bin\2.``x`

- .NET Framework 4:

  `ORACLE_BASE\\ORACLE_HOME``\ODE.NET``\bin\4`

The readme file, `readme.html`, is installed in the `ORACLE_BASE\\ORACLE_HOME``\ODE.NET\DOC` directory.

.NET assemblies deployed by developers are copied into the `ORACLE_BASE``\``ORACLE_HOME``\``bin\CLR` directory (or its subdirectory) by the Oracle Deployment Wizard for .NET.

### Listener and Tnsnames Files

The following are typical examples of the `listener.ora` and `tnsnames.ora` files configured for Oracle Database Extensions for .NET. By default, Oracle Database Extensions for .NET uses `CLRExtProc` as the SID, but this can be changed using the Database Configuration Assistant (DBCA).

#### Listener.ora file

    SID_LIST_LISTENER =
      (SID_LIST =
        (SID_DESC =
          (SID_NAME = PLSExtProc)
          (ORACLE_HOME = C:\oracle\database_1)
          (PROGRAM = extproc)
        )
        (SID_DESC =
          (SID_NAME = CLRExtProc)
          (ORACLE_HOME = C:\oracle\database_1)
          (PROGRAM = extproc)
          (ENVS="EXTPROC_DLLS=ONLY:C:\oracle\database_1\bin\oraclr19.dll")
        )
      )

    LISTENER =
      (DESCRIPTION_LIST =
        (DESCRIPTION =
          (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC1))

        )
      )

#### Tnsnames.ora File

    ORACLE =
      (DESCRIPTION =
        (ADDRESS_LIST =
          (ADDRESS = (PROTOCOL = TCP)(HOST = user.us.example.com)(PORT = 1521))
        )
        (CONNECT_DATA =
          (SERVER = DEDICATED)
          (SERVICE_NAME = oracle.us.example.com)
        )
      )

    ORACLR_CONNECTION_DATA =
      (DESCRIPTION =
        (ADDRESS_LIST =
          (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC1))
        )
        (CONNECT_DATA =
          (SID = CLRExtProc)
          (PRESENTATION = RO)
        )
      )

    EXTPROC_CONNECTION_DATA =
      (DESCRIPTION =
        (ADDRESS_LIST =
          (ADDRESS = (PROTOCOL = IPC)(KEY = EXTPROC1))
        )
        (CONNECT_DATA =
          (SID = PLSExtProc)
          (PRESENTATION = RO)
        )
      )

### Migrating .NET Stored Procedures from Oracle Database 12c Release 1 (12.1) or later

You can migrate .NET stored procedures from a source Oracle Database 12c Release 1 (12.1) or later as follows:

1.  Select the libraries that are used by .NET stored procedures from the source database. For example,

    `SELECT ``library_name``, ``file_spec`` FROM ALL_LIBRARIES WHERE OWNER='SYS'` and `FILE_SPEC LIKE '$ORACLE_HOME\bin\clr\%';`

    `library_name` is usually in the format `dll_name_DLL`. For example, the `library_name` for `Project1.dll` would be `PROJECT1_DLL`.

2.  Create a SQL file manually (for example, `DotNetSP_Grant.sql`) with the following SQL statements:

        CREATE LIBRARY "SYS"."library_name" AS 'file_spec'
        GRANT EXECUTE ON "SYS"."library_name" TO "schema_name"
        GRANT EXECUTE ON "SYS"."DBMS_CLR" TO "schema_name"
        GRANT EXECUTE ON "SYS"."DBMS_CLRTYPE" TO "schema_name"
        GRANT EXECUTE ON "SYS"."DBMS_CLRPARAMTABLE" TO "schema_name"

3.  Run Oracle Data Pump Export utility for the source database.

    For non-pluggable databases, execute the following command:

        Expdp system schemas="schema_name" directory=ORACLECLRDIR dumpfile=DotNetSP.dmp include=PROCEDURE,FUNCTION

    For pluggable databases, execute the following commands:

    1.  Create directory `name` as the path to `DotNetSP.dmp` on the server.

            create directory name as 'path to DotNetSP.dmp on the server';

    2.  Run Oracle Data Pump Export utility for the source database.

            expdp system@TNS alias for pluggable database schemas="schema_name"
            directory=name dumpfile=DotNetSP.dmp include=PROCEDURE,FUNCTION

        where `name` is the directory name provided in step 3.a.

    3.  Drop the directory name provided in step 3.a.

            drop directory name

        where `name` is the directory name provided in step 3.a.

4.  Copy .NET stored procedure assemblies from the source database `ORACLE_BASE\\ORACLE_HOME``\bin\clr` folder and its subfolders to the same directory structure in the target database.

5.  Run `DotNetSP_Grant.sql` as `SYSDBA` against the target database.

6.  If you are migrating to a target that is a pluggable database:

    1.  Create directory `name` as the path to `DotNetSP.dmp` on the server.

            create directory name as 'path to DotNetSP.dmp on the server';

    2.  Run Oracle Data Pump Import utility for the target database.

            impdp system@TNS alias for pluggable database schemas="schema_name" directory=name dumpfile=DotNetSP.dmp

        where `name` is the directory name provided in step 6.a.

    3.  Drop the directory `name` provided in step 6.a.

            drop directory name

        where `name` is the directory name provided in step 6.a.

7.  If you are not migrating to a target that is a pluggable database:

    Run Oracle Data Pump Import utility for the target database.

        impdp system schemas="schema_name" directory=ORACLECLRDIR
        dumpfile=DotNetSP.dmp

    **Note:**

    Do not drop directory `ORACLECLRDIR`.

### Migrating .NET Stored Procedures from Oracle Database 11g Release 2 (11.2)

You can migrate .NET stored procedures from Oracle Database 11g Release 2 (11.2) as follows:

1.  Select the libraries that are used by .NET stored procedures from the Oracle Database 11g Release 2 (11.2). For example,

    `SELECT ``library_name``, ``file_spec`` FROM ALL_LIBRARIES WHERE OWNER='SYS'` and `FILE_SPEC LIKE '$ORACLE_HOME\bin\clr\%';`

    `library_name` is usually in the format `dll_name_DLL`. For example, the `library_name` for `Project1.dll` would be `PROJECT1_DLL`.

2.  Create a SQL file manually (for example, `DotNetSP_Grant.sql`) with the following SQL statements:

        CREATE LIBRARY "SYS"."library_name" AS 'file_spec'
        GRANT EXECUTE ON "SYS"."library_name" TO "schema_name"
        GRANT EXECUTE ON "SYS"."DBMS_CLR" TO "schema_name"
        GRANT EXECUTE ON "SYS"."DBMS_CLRTYPE" TO "schema_name"
        GRANT EXECUTE ON "SYS"."DBMS_CLRPARAMTABLE" TO "schema_name"

3.  Run Oracle Data Pump Export utility for the Oracle Database 11g Release 2 (11.2).

        Expdp system schemas="schema_name" directory=ORACLECLRDIR dumpfile=DotNetSP.dmp include=PROCEDURE,FUNCTION

4.  Copy .NET stored procedure assemblies from Oracle Database 11g Release 2 (11.2) `ORACLE_BASE\\ORACLE_HOME``\bin\clr` folder and its subfolders to the same directory structure in the target database.

5.  Run `DotNetSP_Grant.sql` as `SYSDBA` against the target database.

6.  If you are migrating to a target that is a pluggable database:

    1.  Create directory `name` as the path to `DotNetSP.dmp` on the server.

            create directory name as 'path to DotNetSP.dmp on the server';

    2.  Run Oracle Data Pump Import utility for the target database.

            impdp system@TNS alias for pluggable database schemas="schema_name"
            directory=name
            dumpfile=DotNetSP.dmp

        where name is the directory name created in step 6.a.

    3.  Drop the directory `name` provided in step 6.a.

            drop directory name

        where name is the directory name created in step 6.a.

7.  If you are not migrating to a target that is a pluggable database:

    Run Oracle Data Pump Import utility for the target database.

        impdp system schemas="schema_name" directory=ORACLECLRDIR
        dumpfile=DotNetSP.dmp

    **Note:**

    Do not drop directory `ORACLECLRDIR`.

### Mandatory Migration of .NET 1.x Stored Procedures to .NET 2.0 or Later

Beginning with Oracle Database Extensions for .NET version 11.1.0.7.20, .NET 1.x stored procedures are no longer supported. Specifically, Oracle Database Extensions for .NET 1.x and Oracle Data Provider for .NET 1.x are no longer included in this release. If you have existing .NET 1.x stored procedures from an earlier release, you will need to take special migration steps to ensure that they work in this release.

**WARNING:**

In some cases, this migration will require code changes. You should not install this release in a production environment if you have .NET 1.x stored procedures until you have verified in a test environment that your stored procedures have been successfully migrated. If you have already installed this release and are encountering errors in your .NET 1.x stored procedures, you should downgrade to an earlier version of Oracle Database Extensions for .NET until you are able to make any required code changes to your stored procedures.

#### Determining if Code Changes are Needed

You will need to analyze your .NET 1.x stored procedures to determine if code changes are required to migrate to this release. Specifically you should investigate:

- Code incompatibilities between ODP.NET for .NET 1.x and ODP.NET for .NET 2.0 (or later).

- Code incompatibilities between Oracle Database Extensions for .NET 1.x and Oracle Database Extensions for .NET 2.0 (or later).

- ADO.NET 1.x and ADO.NET 2.0 migration issues.

**See Also:**

- Addressing Code Incompatibilities Between ODP.NET for .NET 1.x and ODP.NET for .NET 2.0 or Later

- Addressing Code Incompatibilities Between Oracle Database Extensions for .NET Versions 1.x and 2.0 or Later

- [`https://msdn.microsoft.com/en-us/default.aspx`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/clrnt&id=msdn_microsoft)

#### Migration Approaches

There are two possible approaches to allow your .NET 1.x stored procedures to work with this release:

- Recompile and redeploy your .NET 1.x stored procedures using ODP.NET for .NET 2.0 (or later). Oracle strongly recommends this approach and it is required if there are incompatibilities that require code changes.

- Configure your .NET 1.x stored procedures to run using ODP.NET for .NET 2.0 (or later). This does not require recompilation but introduces the possibility of run-time errors if there are unaddressed incompatibilities.

**See Also:**

Configure .NET 1.x Stored Procedures Using ODP.NET for .NET 2.0 or Later

#### Addressing Code Incompatibilities Between ODP.NET for .NET 1.x and ODP.NET for .NET 2.0 or Later

You may need to address the following code incompatibilities related to ODP.NET in your .NET 1.x stored procedures:

- In ODP.NET for .NET 2.0 (or later), `OracleParameter.Value` returns `OracleDecimal` instead of .NET native types when `OracleParameter.OracleDbType` is set to a number type, such as `Int32`, `Double`. This behavior change is summarized in the following table:

  | OracleParameter.OracleDbType | OracleParameter.Value Returned in .NET 1.x | OracleParameter.Value Returned in .NET 2.x |
  |:-----------------------------|:-------------------------------------------|:-------------------------------------------|
  | `OracleDbType.Byte`          | `System.Byte`                              | `OracleDecimal`                            |
  | `OracleDbType.Double`        | `System.Double`                            | `OracleDecimal`                            |
  | `OracleDbType.BinaryDouble`  | `System.Double`                            | `OracleDecimal`                            |
  | `OracleDbType.Int16`         | `System.Int16`                             | `OracleDecimal`                            |
  | `OracleDbType.Int32`         | `System.Int32`                             | `OracleDecimal`                            |
  | `OracleDbType.Int64`         | `System.Int64`                             | `OracleDecimal`                            |
  | `OracleDbType.Single`        | `System.Single`                            | `OracleDecimal`                            |
  | `OracleDbType.BinaryFloat`   | `System.Single`                            | `OracleDecimal`                            |

  If any of the preceding `OracleDbType` enumeration values are used by your .NET 1.x stored procedure for an `out` or `in/out` `OracleParameter`, then it may need to be modified.

- In ODP.NET for .NET 2.0 (or later), `OracleParameter.Value `returns provider-type specific `null` value (`OracleClob.Null`) instead of `DBNull.Value` when `OracleParameter.OracleDbType` is set for connected types. For example, if `OracleParameter.OracleDbType` is set to `OracleDbType.Clob`, then `OracleParameter.Value` represents a `null` value by returning `OracleClob.Null` instead of `DBNull.Value`, which is the case in ODP.NET for .NET 1.x.

#### Addressing Code Incompatibilities Between Oracle Database Extensions for .NET Versions 1.x and 2.0 or Later

If any of the connected types are passed as parameters to your .NET 1.x stored procedure, and if the procedure checks for `null` values, then you may need to modify the procedure. Oracle Database Extensions for .NET 1.x uses a .NET `null` to represent a `null` value when the parameter happens to be a connected type. Oracle Database Extensions for .NET 2.0 (or later) uses provider-type specific `null` value, such as `OracleBFile.Null`, in these cases.

You can configure Oracle Database Extensions for .NET 2.0 (or later) to use .NET `null` values for connected type `null` values in place of provider-specific type `null` values. To do this, create and set the following registry value to 0:

`HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_ORACLE_HOME\ODE\ProviderNull`

You can find the documentation about this registry value in the section "Backward Compatibility for Nullable ODP.NET Connected Types" in Oracle Data Provider for .NET Developer's Guide for Microsoft Windows.

#### Recompile and Redeploy .NET 1.x Stored Procedures Using ODP.NET for .NET 2.0 or Later

If you find code incompatibilities, you will need to recompile your .NET 1.x stored procedures using ODP.NET for .NET 2.0 (or later).

Even if you do not find code incompatibilities, Oracle recommends that you recompile and redeploy your .NET 1.x stored procedures. Recompiling ensures that you do not get run-time errors, if there are any unaddressed compatibility issues. Redeploy the stored procedures after successful recompilation.

#### Configure .NET 1.x Stored Procedures Using ODP.NET for .NET 2.0 or Later

Alternatively, if there are no code incompatibilities, you can configure the .NET 1.x stored procedures to run with ODP.NET for .NET 2.0 (or later). This approach does not require you to recompile and redeploy the .NET stored procedures. However, you might get run-time errors, if there are any unaddressed incompatibilities between versions 1.x and 2.0 of Oracle Database Extensions for .NET, ODP.NET, and ADO.NET. Use the following steps to configure the .NET 1.x stored procedures to run with ODP.NET for .NET 2.0 (or later) without recompiling and redeploying them:

1.  Follow steps similar to those given in Migrating .NET Stored Procedures from Oracle Database 11g Release 2 (11.2) to migrate your stored procedures to Oracle Database 19c.
2.  Modify or create the `extproc.exe.config` file in the `NewOracleHome``\bin` folder to redirect ODP.NET (`Oracle.DataAccess.dll`) 1.x references to the installed version of ODP.NET for .NET 2.0 (or later). For example, to redirect ODP.NET 1.111.6.20 references to ODP.NET 2.111.7.20, the `extproc.exe.config` file should include the following configuration section:
        <configuration>
          <runtime>
            <legacyUnhandledExceptionPolicy enabled="1"/>
            <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
              <dependentAssembly>
                <assemblyIdentity name="Oracle.DataAccess"
                                  publicKeyToken="89b483f429c47342"
                                  culture="neutral" />
                <bindingRedirect oldVersion="1.111.6.20"
                                 newVersion="2.111.7.20"/>
              </dependentAssembly>
            </assemblyBinding>
          </runtime>
        </configuration>

### Oracle Database Extensions for .NET Registry Options

You can add functionality to Oracle Database Extensions for .NET using Windows registry entries that are located at

`HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_``ORACLE_HOME``\ODE`

Table 2-2 lists registry keys that add functionality to Oracle Database Extensions for .NET and the sections where the keys are discussed.

Table 2-2 Registry Options

| Registry Key        | Section                                                       |
|:--------------------|:--------------------------------------------------------------|
| .`NETFramework`     | "Selecting a .NET Run Time Version"                           |
| `ProviderNull`      | "Backward Compatibility for Nullable ODP.NET Connected Types" |
| `RecreateAppDomain` | "Unloading .NET Assemblies for Easy Redeployment"             |
| `TraceFileLocation` | "TraceFileLocation"                                           |
| `TraceOption`       | "TraceOption"                                                 |
| `TraceLevel`        | "TraceLevel"                                                  |

#### Unloading .NET Assemblies for Easy Redeployment

From release 11.1.0.6.20, you can unload .NET assemblies when .NET stored procedure execution completes. This makes it easier to repeatedly test your code during development. If this registry key is not enabled, the `exproc.exe` process must be stopped and started with each redeployment.

This feature should not be used during performance testing or for production, as it has a negative effect on performance.

To define assembly loading behavior, set the registry value `RecreateAppDomain` of type `REG_SZ` under this registry key:

`HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_``ORACLE_HOME``\ODE`

The valid values for `RecreateAppDomain` are:

`0` = .NET Assembly remains loaded when the .NET stored procedure execution completes.

`1` = .NET Assembly is unloaded when the .NET stored procedure execution completes.

#### Backward Compatibility for Nullable ODP.NET Connected Types

ODP.NET for .NET 2.0 (or later) supports a static `Null` property in ODP.NET Connected Types, in addition to the existing support for disconnected types such as `OracleDecimal`. It also supports a public property, `IsNull`, for each of these types to check whether or not objects of these types have been assigned a value.

This enables `Null` objects of ODP.NET Connected Types to be propagated to and from a .NET stored procedure. The list of these connected types follows:

- `OracleBlob`

- `OracleClob`

- `OracleBFile`

- `OracleXmlType`

Previous versions of .NET stored procedures expected ODP.NET connected type parameters to be passed as `NULL` rather than a `Type.Null` object. In order to support backward compatibility, the registry string `ProviderNull` can be used to retain the old behavior.

To determine how Oracle Database Extensions for .NET handles passing a `NULL` value to an ODP.NET connected type parameter in a .NET stored procedure, set the registry string `ProviderNull` under this registry key:

`HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_``ORACLE_HOME``\ODE`

The valid values for `ProviderNull` are:

`0` = ODP.NET connected-type parameters are passed as `NULL` rather than `Type.Null` object.

`1` = Oracle Database Extensions for .NET passes a `Type.Null` object to the .NET stored procedure in the case of a null value.

**See Also:**

[Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/featUDTs.md) for more information on nullable types

#### Selecting a .NET Run Time Version

If multiple .NET run time versions are installed on the database computer, then Oracle Database Extensions for .NET defaults to the latest .NET run time available. However, you can configure Oracle Database Extensions for .NET to load a particular .NET run time by setting a registry value.

To specify .NET run time version, set the registry value, `.NETFramework` under this registry key:

`HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_``ORACLE_HOME``\ODE`

Set the registry value to the appropriate .NET run time version, for example, v2.0.50727.

Note: .NET framework 1.x is not supported in this release.

**See Also:**

Mandatory Migration of .NET 1.x Stored Procedures to .NET 2.0 or Later

#### Debug Tracing

Oracle Database Extensions for .NET provides debug tracing support, which allows logging of all the Oracle Database Extensions for .NET activities into one or more trace files. A Windows event log entry will be created each time a trace is generated.

Beginning in this release, if the `TraceFileLocation` option (below) is not set, by default trace files will be created in the Windows user temporary folder:

`<``Windows user temporary folder``>\ODE\trace>`.

The Windows user temporary folder is determined by your local Windows settings, such as your Windows `TMP` or `TEMP` environment variable. Typically, it can be `C:\temp` or `C:\Users\<``user name``>\AppData\Local\Temp`.

**Note:**

You can use Oracle Data Provider for .NET tracing mechanisms to troubleshoot ODP.NET specific issues.

The following registry settings should be configured under

`HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_``ORACLE_HOME``\ODE`

##### TraceOption

`TraceOption` specifies whether to log trace information in single or multiple files for different threads. If the multiple trace files option is requested, a Thread ID is appended to the file name to create a trace file for each thread.

The valid values for `TraceOption` are:

`0` = Single trace file

`1` = Multiple trace files

##### TraceFileLocation

`TraceFileLocation` specifies the trace file destination directory, for example, `D:\traces`. The default `TraceFileLocation` is `<``Windows user temporary folder``>\ODE\trace>`.

##### TraceLevel

`TraceLevel` specifies the level of tracing in Oracle Database Extensions for .NET.

The valid values for `TraceLevel` are:

`0` = None

`1` = Entry and exit information

**See Also:**

Debug Tracing section in [Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/features.md)

### extproc.exe.config Configuration File

Oracle Database Extensions for .NET will read a `extproc.exe.config` configuration file in the `ORACLE_BASE``\\``ORACLE_HOME``\Bin` directory to look up configuration values such as Oracle Database Extensions for .NET and Oracle Data Provider for .NET assembly locations.

Beginning with Oracle Database Extensions for .NET 12.2, the `legacyUnhandledExceptionPolicy` will not be enabled. Thus, by default, if any unhandled exceptions occur within the process that executes the .NET stored procedure, then the process will terminate. However, the `extproc.exe.config` file can be configured to have the same pre-12.2 behavior by enabling `legacyUnhandledExceptionPolicy` so that the process does not terminate for unhandled exceptions.

The following is an example of the `extproc.exe.config` configuration file with `legacyUnhandledExceptionPolicy` enabled:

    <configuration>
      <runtime>
        <legacyUnhandledExceptionPolicy enabled="1"/>
      </runtime>
    </configuration>
