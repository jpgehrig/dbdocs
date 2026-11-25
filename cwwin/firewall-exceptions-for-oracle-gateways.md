## Firewall Exceptions for Oracle Gateways

If your Oracle database interacts with non-Oracle software through a gateway, then you must add the gateway executable file to the Windows Firewall exception list.

The following table lists the gateway executable files used to access non-Oracle software.

Table 10-1 Oracle Executables Used to Access Non-Oracle Software

| Executable Name | Description                                                                     |
|:----------------|:--------------------------------------------------------------------------------|
| `omtsreco.exe`  | Oracle Services for Microsoft Transaction Server                                |
| `dg4sybs.exe`   | Oracle Database Gateway for Sybase                                              |
| `dg4tera.exe`   | Oracle Database Gateway for Teradata                                            |
| `dg4msql.exe`   | Oracle Database Gateway for SQL Server                                          |
| `dg4db2.exe`    | Oracle Database Gateway for Distributed Relational Database Architecture (DRDA) |
| `pg4arv.exe`    | Oracle Database Gateway for Advanced Program to Program Communication (APPC)    |
| `pg4t4ic.exe`   | Oracle Database Gateway for APPC                                                |
| `dg4mqs.exe`    | Oracle Database Gateway for WebSphere MQ                                        |
| `dg4mqc.exe`    | Oracle Database Gateway for WebSphere MQ                                        |
| `dg4odbc.exe`   | Oracle Database Gateway for ODBC                                                |

**Parent topic:** [Configuring Exceptions for the Windows Firewall](configuring-exceptions-for-the-windows-firewall.md)
