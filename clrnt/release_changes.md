This preface contains:

- Changes in Oracle Database 12c Release 2 (12.2)

- Changes in Oracle Database 12c Release 1 (12.1)

### Changes in Oracle Database 12c Release 2 (12.2)

The following are changes in Oracle Database Extensions for .NET Developer's Guide for Oracle Database 12c Release 2 (12.2).

#### New Features

The following features are new in this release:

- Unhandled exceptions are no longer automatically handled.

  Beginning with this release of Oracle Database Extensions for .NET, unhandled exceptions in .NET stored procedures or functions will terminate the process to make it easier to detect issues as soon as it happens. This behavior can be modified through the `extproc.exe.config` configuration file.

  **See Also:**

  [extproc.exe.config Configuration File](install.md)

- Oracle assemblies are no longer placed in Global Assembly Cache

  The Oracle Database Extensions for .NET no longer places its assemblies in the Global Assembly Cache (GAC). The `extproc.exe.config` configuration file is configured properly by the installer with the location of these assemblies so that they can be located and loaded at runtime.

  **See Also:**

  [extproc.exe.config Configuration File](install.md)

- New `TraceFileLocation` registry key

  The `TraceFileLocation` registry key allows you to choose the directory in which the trace files will be generated.

  **See Also:**

  [TraceFileLocation](install.md)

### Changes in Oracle Database 12c Release 1 (12.1)

The following are changes in Oracle Database Extensions for .NET Developer's Guide for Oracle Database 12c Release 1 (12.1).

#### New Features

The following features are new in this release:

- The Oracle CLR services now runs as the Oracle Home User, a potentially lower privileged user that is defined during database installation. These services are no longer automatically created by the installer. Instead, a new utility, `OraClrCtl.exe`, is used to create them.

  **See Also:**

  "[Oracle CLR Services and the Oracle Home User Account](install.md)."
