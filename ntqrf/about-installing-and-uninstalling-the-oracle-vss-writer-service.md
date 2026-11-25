The Oracle VSS writer runs separately from the Oracle database instance. From the perspective of the database, the VSS writer is simply an OCI client.

Oracle VSS writer instances are created automatically during the setup of an instance. `oradim.exe` utility that sets up an instance, also starts Oracle's VSS writer utility to setup VSS writer instance for managing the given Oracle instance. In addition, the Oracle VSS writer provides command-line options to install and uninstall the writer service. If `/user` option is used but `/password` option not used, then `oravssw` waits for password through `stdin`. During installation, you can specify the Windows account under which the service must be started. The writer uses operating system authentication when connecting to a database instance. Thus, the Windows user must be able to log in as `SYSDBA` to the Oracle database instances managed by the writer service.

Oracle VSS is supported on the same operating systems that are supported by Oracle Database. See [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/oracle-database-software-requirements.md) for the list of supported operating systems.

The command-line syntaxes for the Oracle VSS writer are as follows:

    oravssw {/q [/start | /stop | /status]}|
    oravssw {SID [/tl trace_level] [/tf trace_file]}|
    oravssw {SID [/i {/user:userid /password:password}]}|
    oravssw {SID [/d]}

**Note:**

You can change the user ID and password using the Services snap-in.

Table 9-1 Oracle VSS Writer Options

| Option                                  | Description                                                                                                                                                            |
|:----------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SID`                                   | `SID` of the Oracle instance to which the service connects.                                                                                                            |
| /i {/user:`userid`/password:`password`} | Installs Oracle VSS writer service for a specified `SID`.                                                                                                              |
| `/q`                                    | Queries the Oracle VSS writer services. But when not used with options like `/start` or `/status` or `/stop`, it just displays the list of Oracle VSS writer services. |
| `/``status`                             | Displays the current status of all Oracle writer services and can be used only with the `/q` option.                                                                   |
| `/start`                                | Starts all Oracle VSS writer services and can be used only with the `/q` option.                                                                                       |
| `/stop`                                 | Stops all Oracle VSS writer services and can be used only with the `/q` option.                                                                                        |
| `/tl`                                   | Specifies the trace level for Oracle VSS writer for a specified `SID`.                                                                                                 |
| `/tf`                                   | Specifies the trace file name for Oracle VSS writer for a specified `SID`.                                                                                             |
| `/d`                                    | Uninstalls Oracle VSS writer service for a specified `SID`.                                                                                                            |

In Installing Oracle VSS Writer, you install the service so that it connects to the `prod1` instance.

**Note:**

- Any errors during operation of the Oracle VSS writer are reported by means of Windows System Event logging APIs. You can view these errors with the Windows Event Viewer.

- Oracle Database 10g Release 2 supports Oracle VSS snapshots only when Oracle VSS writer 11g or later is configured to manage the 10.2 database. See My Oracle Support Note 580558.1 at [https://support.oracle.com](https://support.oracle.com/epmos/faces/DocumentDisplay?_afrLoop=563918161999386&id=580558.1&_adf.ctrl-state=1420x8xf0q_77) for more information about installing Oracle VSS writer for use with 9i and 10g databases.

Example 9-1 Installing Oracle VSS Writer

    oravssw prod1 /i

**Parent topic:** [Performing Database Backup and Recovery with VSS](performing-database-backup-and-recovery-with-vss.md)
