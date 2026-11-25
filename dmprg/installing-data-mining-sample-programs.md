Learn how to install Data Mining sample programs.

The data mining sample programs require:

- Oracle Database Enterprise Edition with the Advanced Analytics option

- Oracle Database sample schemas

- Oracle Database Examples

- A data mining user account

- Execution of `dmshgrants.sql` by a system administrator

- Execution of `dmsh.sql` by the data mining user

Follow these steps to install the data mining sample programs:

1.  Install or obtain access to Oracle Database 19c Enterprise Edition or Oracle Standard Edition 2 (SE2). To install the Database, see the installation instructions for your platform at [`Oracle Database 19c Release`](../index.md).

2.  Ensure that the sample schemas are installed in the database. The sample schemas are installed by default with Oracle Database. See Oracle Database Sample Schemasfor details about the sample schemas.

3.  Verify that Oracle Database Examples has been installed with the database, or install it locally. Oracle Database Examples loads the Database sample programs into the `rdbms/demo` directory under Oracle home. See Oracle Database Examples Installation Guide for installation instructions.

4.  Verify that a data mining user account has been created, or create it yourself if you have administrative privileges. See "Creating a Data Mining User".

5.  Ask your system administrator to run `dmshgrants.sql`, or run it yourself if you have administrative privileges. `dmshgrants` grants the privileges that are required for running the sample programs. These include `SELECT` access to tables in the `SH` schema as described in "The Data Mining Sample Data" and the system privileges listed in the following table.

    Pass the name of the data mining user to `dmshgrants`.

        SQL> CONNECT sys / as sysdba
        Enter password: sys_password
        Connected.
        SQL> @ $ORACLE_HOME/rdbms/demo/dmshgrants dmuser

    Table A-1 System Privileges Granted by dmshgrants.sql to the Data Mining User

    | Privilege                   | Allows the data mining user to                                                      |
    |:----------------------------|:------------------------------------------------------------------------------------|
    | `CREATE SESSION`            | log in to a database session                                                        |
    | `CREATE TABLE`              | create tables, such as the settings tables for `CREATE_MODEL`                       |
    | `CREATE VIEW`               | create views, such as the views of tables in the `SH` schema                        |
    | `CREATE MINING MODEL`       | create data mining models                                                           |
    | `EXECUTE ON ctxsys.ctx_ddl` | execute procedures in the `ctxsys.ctx_ddl `PL/SQL package; required for text mining |

6.  Connect to the database as the data mining user and run `dmsh.sql`. This script creates views of the sample data in the schema of the data mining user.

        SQL> CONNECT dmuser
        Enter password: dmuser_password
        Connected.
        SQL> @ $ORACLE_HOME/rdbms/demo/dmsh

**Related Topics**

- [Oracle Database Sample Schemas](../comsc/installing-sample-schemas.md)
- [Oracle Database Examples Installation Guide](../exmpl/index.md)
- [Creating a Data Mining User](controlling-access-mining-models-data.md)
