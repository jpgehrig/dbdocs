## Configuring the OraClrAgnt Service for Oracle Database Extensions for .NET

Oracle Database Extensions (ODE) for .NET depends on a Windows service to operate properly. This service is called the OraClrAgnt service.

In versions of Oracle Database prior to Oracle Database 12c, this CLR service was created automatically by the installer.

- After installation you use the `OracleClrCtl.exe` utility to create, start, stop, and delete the OraClrAgnt service.
  When you use the `OraClrCtl.exe` utility to create the service, a new service is created named OracleHomenameClrAgent, where Homename represents an Oracle Home name. The OraClrAgnt service is configured by this tool using the Oracle Home User account specified during the Oracle Database installation.

**See Also:**

[Oracle Database Extensions for .NET Developer's Guide for Microsoft Windows](../clrnt/install.md) for more information about using the `OraClrCtl.exe` tool and installing and configuring the OraClrAgnt service

**Parent topic:** [Product-Specific Postinstallation Tasks](configure-oracle-products.md)
