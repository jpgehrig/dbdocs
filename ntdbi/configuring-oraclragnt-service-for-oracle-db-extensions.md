## Configuring the OraClrAgnt Service for Oracle Database Extensions for .NET

Oracle Database Extensions for .NET depends on a Windows service to operate properly. This service is called the OraClrAgnt service, which can be accessed through the Service Control Panel, as `Oracle``ORACLE_HOME``ClrAgent`, where `ORACLE_HOME` represents an Oracle home name.

In earlier versions of Oracle Database, the OraClrAgnt service was automatically created by the installer. Starting with Oracle Database 12c Release 2 (12.2), after installation you use the `OraClrCtl.exe` utility to create, start, stop, and delete the OraClrAgnt service. The OraClrAgnt service is configured by this tool using the Oracle Home User account specified during the Oracle Database installation.

**See Also:**

[Oracle Database Extensions for .NET Developer's Guide for Microsoft Windows](../clrnt/install.md)

**Parent topic:** [Configuring Oracle Components](configuring-oracle-components.md)
