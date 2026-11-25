Examples of hierarchical file mappings in a read-only Oracle home as compared to a read/write Oracle home.

This example shows an Optimal Flexible Architecture-compliant Oracle Database installation, for the user `oracle`, with the ORACLE_HOME, ORACLE_BASE, ORACLE_BASE_HOME, and ORACLE_BASE_CONFIG logical locations. The database files are mounted on `/u01` and the HOME_NAME is `OraDB19Home1`.

This example also shows the changes in the Oracle Database software defined paths of configuration files, log files, and other directories in a read-only Oracle home when compared to a read/write Oracle home.

Table D-1 read/write and Read-Only Oracle Home File Path Examples

| Directory          | Read/Write Oracle Home File Path                                                 | Read-Only Oracle Home File Path                                                  |
|:-------------------|:---------------------------------------------------------------------------------|:---------------------------------------------------------------------------------|
| ORACLE_HOME        | `/u01/app/oracle/product/19.0.0/dbhome_1`                                        | `/u01/app/oracle/product/19.0.0/dbhome_1`                                        |
| ORACLE_BASE        | `/u01/app/oracle/`                                                               | `/u01/app/oracle/`                                                               |
| ORACLE_BASE_HOME   | ORACLE_HOME<br>(or)<br>`/u01/app/oracle/product/19.0.0/dbhome_1`                 | ORACLE_BASE/homes/HOME_NAME<br>(or)<br>`/u01/app/oracle/homes/OraDB19Home1`      |
| ORACLE_BASE_CONFIG | ORACLE_HOME<br>(or)<br>`/u01/app/oracle/product/19.0.0/dbhome_1`                 | ORACLE_BASE<br>(or)<br>`/u01/app/oracle/`                                        |
| `network`          | ORACLE_HOME/network<br>(or)<br>`/u01/app/oracle/product/19.0.0/dbhome_1/network` | ORACLE_BASE_HOME/network<br>(or)<br>`/u01/app/oracle/homes/OraDB19Home1/network` |
| `dbs`              | ORACLE_HOME/dbs<br>(or)<br>`/u01/app/oracle/product/19.0.0/dbhome_1/dbs`         | ORACLE_BASE/dbs<br>(or)<br>`/u01/app/oracle/dbs`                                 |

**Parent topic:** [Configuring Read-Only Oracle Homes](configuring-read-only-oracle-homes.md)
