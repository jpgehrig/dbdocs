If your Oracle database interacts with non-Oracle software through a gateway, then you must add the gateway executable to the Windows Firewall exception list.

Table 5-1  Oracle Executables Requiring Windows Firewall Exceptions

| File Name      | Executable Name                                  |
|:---------------|:-------------------------------------------------|
| `omtsreco.exe` | Oracle Services for Microsoft Transaction Server |
| `dg4sybs.exe`  | Oracle Database Gateway for Sybase               |
| `dg4tera.exe`  | Oracle Database Gateway for Teradata             |
| `dg4msql.exe`  | Oracle Database Gateway for SQL Server           |
| `dg4db2.exe`   | Oracle Database Gateway for DRDA                 |
| `pg4arv.exe`   | Oracle Database Gateway for APPC                 |
| `pg4t4ic.exe`  | Oracle Database Gateway for APPC                 |
| `dg4mqs.exe`   | Oracle Database Gateway for WebSphere MQ         |
| `dg4mqc.exe`   | Oracle Database Gateway for WebSphere MQ         |
| `dg4odbc.exe`  | Oracle Database Gateway for ODBC                 |

**Parent topic:** [Overview of Different Executables Added to the Windows Firewall Exception List](overview-of-different-executables.md)
