## File Path and Directory Changes in Read-Only Oracle Homes

Examples of hierarchical file mappings in a read-only Oracle home as compared to a read/write Oracle home.

This example shows an Optimal Flexible Architecture-compliant Oracle Database installation, for the user `oracle`, with the ORACLE_HOME, ORACLE_BASE, ORACLE_BASE_HOME, and ORACLE_BASE_CONFIG logical locations. The database files are under `oraclebase\oradata`.

This example also shows the changes in the Oracle Database software defined paths of configuration files, log files, and other directories in a read-only Oracle home when compared to a read/write Oracle home.

Table D-1 read/write and Read-Only Oracle Home File Path Examples

| Directory          | Read/Write Oracle Home File Path                                                 | Read-Only Oracle Home File Path                                                |
|:-------------------|:---------------------------------------------------------------------------------|:-------------------------------------------------------------------------------|
| ORACLE_HOME        | `C:\app\oracle\product\19.0.0\dbhome_1`                                          | `C:\app\oracle\product\19.0.0\dbhome_1`                                        |
| ORACLE_BASE        | `C:\app\oracle\`                                                                 | `C:\app\oracle\`                                                               |
| ORACLE_BASE_HOME   | ORACLE_HOME<br>(or)<br>`C:\app\oracle\product\19.0.0\dbhome_1`                   | ORACLE_BASE\homes\HOME_NAME.<br>(or)<br>`C:\app\oracle\homes\OraDB19Home1`     |
| ORACLE_BASE_CONFIG | ORACLE_HOME<br>(or)<br>`C:\app\oracle\product\19.0.0\dbhome_1`                   | ORACLE_BASE<br>(or)<br>`C:\app\oracle\`                                        |
| `network`          | ORACLE_HOME\network<br>(or)<br>`C:\app\oracle\product\19.0.0\dbhome_1\network`   | ORACLE_BASE_HOME\network<br>(or)<br>`C:\app\oracle\homes\OraDB19Home1\network` |
| `database`         | ORACLE_HOME\database<br>(or)<br>`C:\app\oracle\product\19.0.0\dbhome_1\database` | ORACLE_BASE\database<br>(or)<br>`C:\app\oracle\database`                       |

**Parent topic:** [Configuring Read-Only Oracle Homes](configuring-read-only-oracle-homes1.md)
