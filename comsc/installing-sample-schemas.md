Starting with Oracle Database 12c Release 2, the latest version of the sample schema scripts are available on GitHub at <https://github.com/oracle/db-sample-schemas/releases/latest>.

During a complete installation of Oracle Database, the HR schema can be installed either manually or automatically when creating a database using the `dbca` option. All the other sample schemas must be installed manually via the scripts available on GitHub.

This chapter contains the following topics:

- Installing HR Schema Only

- Installing Sample Schemas from GitHub

**Note:**

By installing any of the Oracle Database sample schemas, you will drop any previously installed schemas that use the following user names: `HR`, `OE`, `PM`, `SH`, `IX`, `BI`.

Data contained in any of these schemas will be lost if you run any of the installation scripts described in this section. You should not use the sample schemas for your personal or business data and applications. They are meant to be used for demonstration purposes only.

### 2.1 Installing HR Schema Only

This section contains the following topics:

- Installing HR Schema Using Database Configuration Assistant

- Manually Installing the HR Schema

- Uninstalling HR Schema

#### 2.1.1 Installing HR Schema Using Database Configuration Assistant

Select the `sample schemas` option to install `HR` schema in the database.

At the end of the installation process, a dialog box displays the accounts that have been created and their lock status. By default, sample schemas are locked and their passwords are expired. Before you can use a locked account, you must unlock it and reset its password. You can unlock the accounts at this point in the installation process. Alternatively, after the installation completes, you can unlock the schemas and reset their passwords by using the `ALTER USER ... ACCOUNT UNLOCK` statement. For example:

    ALTER USER hr ACCOUNT UNLOCK IDENTIFIED BY Password;

**See Also:**

"[Guidelines for Securing Passwords](../dbseg/keeping-your-oracle-database-secure.md)" in Oracle Database Security Guide for guidelines related to creating secure passwords

#### 2.1.2 Manually Installing the HR Schema

All scripts necessary to create the Human Resource (`HR`) schema reside in `$ORACLE_HOME``/demo/schema/human_resources`.

You need to call only one script, `hr_main.sql`, to create all the objects and load the data. The following steps provide a summary of the installation process:

1.  Log on to SQL\*Plus as `SYS` and `connect` using the `AS SYSDBA` privilege.

        sqlplus connect sys as sysdba
        Enter password: password

2.  To run the `hr_main.sql` script, use the following command:

        SQL> @?/demo/schema/human_resources/hr_main.sql

3.  Enter a secure password for `HR`

        specify password for HR as parameter 1:
        Enter value for 1:

    Enter an appropriate tablespace, for example, `users` as the default tablespace for `HR`

        specify default tablespace for HR as parameter 2:
        Enter value for 2:

4.  Enter `temp` as the temporary tablespace for `HR`

        specify temporary tablespace for HR as parameter 3:
        Enter value for 3:

5.  Enter your `SYS` password

        specify password for SYS as parameter 4:
        Enter value for 4:

6.  Enter the directory path, for example, `$ORACLE_HOME``/demo/schema/log/`, for your log directory

        specify log path as parameter 5:
        Enter value for 5:

After script `hr_main.sql` runs successfully and schema `HR` is installed, you are connected as user `HR.` To verify that the schema was created, use the following command:

    SQL> SELECT table_name FROM user_tables;

Running `hr_main.sql` accomplishes the following tasks:

1.  Removes any previously installed `HR` schema
2.  Creates user `HR` and grants the necessary privileges
3.  Connects as `HR`
4.  Calls the scripts that create and populate the schema objects

For a complete listing of the scripts and their functions, refer to [HR Sample Schema Scripts and Objects](HR-sample-schema-scripts-and-objects.md).

A pair of optional scripts, `hr_dn_c.sql` and `hr_dn_d.sql`, is provided as a schema extension. To prepare schema `HR` for use with the directory capabilities of Oracle Internet Directory, run the `hr_dn_c.sql` script. If you want to return to the initial setup of schema `HR`, use script `hr_dn_d.sql` to undo the effects of script `hr_dn_c.sql`.

You can use script `hr_drop.sql` to drop schema `HR`.

**See Also:**

Oracle Database Security Guide for the minimum password requirements

#### 2.1.3 Uninstalling HR Schema

If you need to remove the HR schema, run the following script on the SQL\* Plus command line.

    sqlplus system/systempw@connect_string
    @drop_hr.sql

### 2.2 Installing Sample Schemas from GitHub

Starting with Oracle Database 12c Release 2, only the `HR` sample schema SQL scripts are available in the  `$ORACLE_HOME/demo/schema/human_resources` directory. If you want to use sample schemas other than` HR`, such as` OE, OC, PM`, and `SH` schemas, you must download them from the GitHub repository.

The procedure to install sample schemas from GitHub is as follows:

1.  To find the latest version of the sample schemas installation scripts, go to the following GitHub web site : <https://github.com/oracle/db-sample-schemas/releases/latest>

    For example, If you want a 12.2.0.1 version of the scripts, then go to <https://github.com/oracle/db-sample-schemas/releases/tag/v12.2.0.1>

2.  Clone the GitHub repository, or download the ZIP bundle from GitHub and extract the files.

3.  Unzip the file.

4.  Follow the instructions to create the schemas in the README contained in the zip file.

This section includes the following topics:

- Resetting Sample Schemas

- Uninstalling Sample Schemas

#### 2.2.1 Resetting Sample Schemas

To reset sample schemas to their initial state, use the following syntax from the SQL\*Plus command-line interface:

    sqlplus system/systempw@connect_string
    @mksample systempw syspw hrpw oepw pmpw ixpw shpw bipw users temp /your/path/to/log/ connect_string

The `mksample` script expects 11 parameters. Provide the password for `SYSTEM` and `SYS`, and for schemas `HR`, `OE`, `PM`, `IX`, and `SH`. Specify a temporary and a default tablespace, and make sure to end the name of the log file directory with a trailing slash.

The `mksample` script produces several log files:

- `mkverify.log` is the Sample Schema creation log file.

- `hr_main.log` is the `HR` schema creation log file.

- `oe_oc_main.log` is the `OE` schema creation log file.

- `pm_main.log` is the `PM` schema creation log file.

- `pm_p_lob.log` is the SQL\*Loader log file for `PM.PRINT_MEDIA`.

- `ix_main.log` is the `IX` schema creation log file.

- `sh_main.log` is the `SH` schema creation log file.

- `cust.log` is the SQL\*Loader log file for `SH.CUSTOMERS`.

- `prod.log` is the SQL\*Loader log file for `SH.PRODUCTS`.

- `promo.log` is the SQL\*Loader log file for `SH.PROMOTIONS`.

- `sales.log` is the SQL\*Loader log file for `SH.SALES`.

- `sales_ext.log` is the external table log file for `SH.COSTS`.

In most situations, there is no difference between installing a Sample Schema for the first time or reinstalling it over a previously installed version. The `*_main.sql` scripts drop the schema users and all of their objects.

#### 2.2.2 Uninstalling Sample Schemas

If you need to remove the sample schemas from the installation, run script `drop_sch.sql` on the SQL\*Plus command line. This script ships with Oracle Database.

This script uses the following parameters:

- `systempwd`

- `SYSTEM`

- `connect_string`

The `systempwd` is the password for `SYSTEM` user and `connect_string` is the connection string of the database.

Example 2-1 How to Uninstall Sample Schemas

    sqlplus system/systempw@connect_string
    @drop_sch.sql

### 2.3 Installing CO schema

Currently, CO schema cannot be installed along with the other schema using the mksample script. Install the CO schema independently from GitHub.

The steps to install CO schema from GitHub is as follows:

1.  Go to the GitHub web site: <https://github.com/oracle/db-sample-schemas/releases/tag/v19.2>
2.  Clone the GitHub repository, or download the ZIP bundle from GitHub and extract the files.
3.  Unzip the file.
4.  Follow the instructions to create the schema in `README.txt` contained in the zip file.
5.  Review `co_install.log` in the extracted zip folder for errors.
6.  To verify that the schema was created, use the following command:
        SQL> SELECT table_name FROM user_tables;
7.  To remove the CO schema, run the following script to drop the CO user:
        SQL> @co_drop_user.sql

**Note:**

- The Customer Orders(CO) schema is available from Oracle Database 12c onwards.
- The master script `@mksample` currently does not include the CO schema.
