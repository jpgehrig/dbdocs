The following topics outline the steps to configure the Oracle database for a gateway using TCP/IP for IMS Connect on your Microsoft Windows platform. They also provide the steps to verify installation and configuration of the gateway and OLTP components.

- Before You Begin

- Preparing to Configure a Gateway Installation/Upgrade

- Configuring the Oracle Database : First Time Installation

- Upgrading or Migrating the Oracle Database from Previous Gateways

- Optional Configuration Steps to Permit Multiple Users

- Configuring TCP/IP for the Gateway

- Configuring the Gateway

- Loading the PGA_TCP_IMSC Table

- Verifying the Gateway Installation and OLTP Configuration

- Performing Postinstallation Procedures

Configuring the Oracle Database Gateway for APPC using TCP/IP support for IMS Connect involves working with the following components:

- the Oracle database

- your Windows system

- your network

- the OLTP

### Before You Begin

The following topics require you to input parameters unique to your system in order to properly configure the gateway and TCP/IP communications interface.

Refer to [Configuration Worksheet](appc-gateway-configuration-worksheet.md) for a worksheet listing the installation parameters you will need to know before you can complete the configuration process. Ask your network administrator to provide you with these unique parameter names before you begin.

### Preparing to Configure a Gateway Installation/Upgrade

There are three ways to establish the gateway-Oracle database relationship when you are installing or upgrading/migrating the gateway:

- When the Oracle Database and the gateway are installed in the same ORACLE_HOME on the same machine;

- When the Oracle Database and the gateway are installed on separate machine; or

- When the Oracle Database and the gateway are on the same machine but in different directories

Depending on the location of your gateway and your Oracle database , you may need to transfer some of the gateway administrative files to the location where the Oracle database is installed.

Follow the instructions suitable to your combination of the gateway-Oracle database locations listed below.

#### When the Oracle Database and the gateway are installed in the same ORACLE_HOME on the same machine

You do not need to transfer files. Proceed to "Configuring the Oracle Database : First Time Installation ".

#### When the Oracle Database and the gateway are installed on separate machine

1.  Locate the gateway administrative files in the gateway `%ORACLE_HOME%\dg4appc\admin` directory. All files in this directory that have the suffix `.sql`, `.pkh`,and `.pkb` must be copied into a similarly-named directory in the Oracle database 's Oracle home directory.

2.  Now locate the gateway demo files and subdirectories in the gateway `%ORACLE_HOME%\dg4appc\demo` directory. Copy the `pgavsn.sql `and `pgaecho.sql` files into a similarly named directory in the Oracle database .

3.  Copy the `pgaims.sql` file from the gateway Oracle home `%ORACLE_HOME%\dg4appc\demo\IMS` directory to your Oracle database 's Oracle home `%ORACLE_HOME%\dg4appc\demo\IMS `directory.

4.  Optional Steps: If you want to run `IVTNV` and `IVTNO`, then you will need to copy the `ivtno.ctl`, `ivtnod.sql`, `ivtnv.ctl`, and `ivtnvd.sql` files into the Oracle database 's Oracle home `%ORACLE_HOME%\dg4appc\demo\IMS` directory as well. Make sure to generate the required TIPs and transfer them as well.

#### When the Oracle Database and the gateway are on the same machine but in different directories

You must change your gateway's Oracle home to the Oracle database 's Oracle home directory.

1.  For example, if your gateway's Oracle home is set as follows:
        C:\> echo %ORACLE_HOME%
        C:\oracle\pga\12.2

    and your server's Oracle home is located in the '`\oracle\pga\12.2'` directory, then you need to do the following:

        C:\> SET ORACLE_HOME=C:\oracle\pga\12.2
2.  Now, create the directories with the following commands:
        C:\> cd %ORACLE_HOME%
        C:\> mkdir dg4appc
        C:\> mkdir dg4appc\admin
        C:\> mkdir dg4appc\demo
        C:\> mkdir dg4appc\demo\IMS
3.  Use whatever file transfer mechanism is available on your system to copy all the `.sql`, `.pkh`, and `.pkb` files from the gateway's Oracle home `%ORACLE_HOME%\dg4appc\admin` directory to the Oracle database 's Oracle home `%ORACLE_HOME%\dg4appc\admin` directory.
4.  You may also transfer the demo files from the gateway directory to the Oracle database directory. Copy the pgavsn.sql and `pgaecho.sql` files `and` directory recursively from the gateway Oracle home's `%ORACLE_HOME%\dg4appc\demo` directory to the Oracle database 's `%ORACLE_HOME%\dg4appc\demo` directory.
5.  You may also copy the `pgaims.sql` file from the gateway Oracle home `%ORACLE_HOME%\dg4appc\demo\IMS` directory to the Oracle database Oracle home `%ORACLE_HOME%\dg4appc\demo\IMS `directory.
    Optional Steps: If you want to run `IVTNV` and `IVTNO`, then you will need to copy the` ivtno.ctl`, `ivtnod.sql`, `ivtnv.ctl`, and `ivtnvd.sql` files into the Oracle database 's Oracle home `%ORACLE_HOME%\dg4appc\demo\IMS` directory as well. Make sure to generate the required TIPs and transfer them as well.

Proceed to "Configuring the Oracle Database : First Time Installation ". Following those steps, you may want to perform the Optional Configuration Steps to Permit Multiple Users,Optional Configuration Steps to Permit Multiple Users.

### Configuring the Oracle Database : First Time Installation

Follow these steps to configure the Oracle database after installing the Oracle Database Gateway for APPC.

1.  Ensure that the `UTL_RAW` PL/SQL package has been installed on the Oracle database . All PGAU-generated TIP specifications use `UTL_RAW`, which provides routines for manipulating raw data.

    1.  Use SQL\*Plus to connect to the Oracle database as user `SYS`.

    2.  From SQL\*Plus, enter the following command:

            SQL> DESCRIBE UTL_RAW

        The `DESCRIBE` statement produces output on the screen. If you browse through the output, then you should see some functions, including a compare function. If you do not see this output, then continue the `UTL_RAW` installation by performing Step 1.d.

        If the `DESCRIBE` statement indicates success, then your Oracle database has `UTL_RAW` installed and you can proceed to Step 2.

    3.  Use SQL\*Plus to connect to the Oracle database as `SYS`.

    4.  From SQL\*Plus, run the utlraw.sql and `prvtrawb.plb` scripts in the Oracle database `%ORACLE_HOME%\rdbms\admin` directory, in the following order:

            C:\> cd %ORACLE_HOME%\rdbms\admin
            SQL> @utlraw.sql
            SQL> @prvtrawb.sql

2.  Ensure that the` DBMS_OUTPUT` standard PL/SQL package is enabled on your Oracle database . The sample programs and installation verification programs on the distribution media use this standard package.

    1.  If necessary, then use SQL\*Plus to connect to the Oracle database as user `SYS`.

    2.  Enter the following command:

            SQL> DESCRIBE DBMS_OUTPUT

        The `DESCRIBE` statement produces output on your screen. If you browse through that output, then you should see some functions, including a put_line function.

        If you do not see this output, then you must create the `DBMS_OUTPUT` package. Refer to the [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_OUTPUT.md) for more information about the `DBMS_OUTPUT` package. After successful installation of the `DBMS_OUTPUT` package, issue the `DESCRIBE` statement.

        If the `DESCRIBE` statement indicates success, then your Oracle database has `DBMS_OUTPUT` created, and you can proceed to Step 3.

3.  Install the `UTL_PG` PL/SQL package. All PGAU-generated TIP specifications use `UTL_PG`, which provides routines for performing numeric conversions to and from raw data.

    1.  If necessary, then use SQL\*Plus to connect to the Oracle database as user `SYS`.

    2.  From SQL\*Plus, run the `utlpg.sql `and `prvtpgb.plb` scripts in the Oracle database 's `%ORACLE_HOME%\rdbms\admin` directory, in the following order:

            C:\> cd %ORACLE_HOME%\rdbms\admin
            SQL> @utlpg.sql
            SQL> @prvtpgb.plb

4.  Install the Heterogeneous Services (HS) catalogs.

    1.  If necessary, then use SQL\*Plus to connect to the Oracle database as user `SYS`.

    2.  Enter the following command:

            SQL> DESCRIBE HS_FDS_CLASS

        The `DESCRIBE `statement produces output on the screen. If the `DESCRIBE` statement indicates success, then Heterogeneous Services catalogs have been created on your Oracle database and you can proceed to Step 5.

        If the `DESCRIBE` statement does not indicate success, then you must create Heterogeneous Services catalogs and you must perform Step 4.c below:

    3.  If it is necessary to create the Heterogeneous Services catalog, then enter the following command:

            C:\> cd %ORACLE_HOME%\rdbms\admin
            SQL> @caths.sql

5.  Create a public database link to access the Oracle Database Gateway for APPC:

    Use SQL\*Plus to connect to the Oracle database as user `SYSTEM`. You can use the following SQL\*Plus sample whether the Oracle database and the gateway are on the same system or on different systems. In the following sample, `pgasrv` is the `tns_name_entry` that will be assigned to the gateway when you modify the `tnsnames.ora` file later.

        SQL> CREATE PUBLIC DATABASE LINK PGA USING 'PGASRV'

6.  Create the gateway administrator user `PGAADMIN` and install the PG DD.

    1.  Use SQL\*Plus to connect to the Oracle database as user `SYSTEM`.

    2.  From SQL\*Plus, run the `pgacr8au.sql` script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script creates the `PGAADMIN` user ID.

        The initial password defined for `PGAADMIN` is `PGAADMIN`. Use the `ALTER USER` command to change the password. For further information about password issues, refer to the [Oracle Database SQL Language Reference](../sqlrf/ALTER-USER.md).

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgacr8au.sql

    3.  Use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`.

    4.  From SQL\*Plus, run the `pgddcr8.sql` script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script installs the PG DD.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgddcr8.sql

    5.  From SQL\*Plus, connect to the Oracle database as user `SYS`.

    6.  Grant execution privileges on `DBMS_PIPE` to `PGAADMIN`:

            SQL> GRANT EXECUTE ON DBMS_PIPE TO PGAADMIN

7.  Ensure that the `pg4tcpmap` package has been installed on your Oracle database . Follow Steps a through c to test for proper installation of `pg4tcpmap`.

    Refer to "[Output for the pg4tcpmap Tool](appc-gateway-initialization-parameters-tcp-ip.md)" in [Gateway Initialization Parameters for TCP/IP Communication Protocol](appc-gateway-initialization-parameters-tcp-ip.md) for a sample of the output from the `pg4tcpmap` tool, and refer to Chapter 6 of the [Oracle Database Gateway for APPC User's Guide ](../appug/pg4tcpmap-commands-tcpip.md)for details about the commands needed to run the tool.

    1.  Use SQL\*Plus to connect to the Oracle database as user `SYSTEM`.

    2.  Enter the following command:

            SQL> select table_name, owner
            from dba_tables
            where table_name = 'PGA_TCP_IMSC',
            and owner = 'PGAADMIN';
            SQL> column owner format a 10
            SQL> column index_name format a 18
            SQL> column table_name format a 14
            SQL> select owner, index_name, table_name, uniqueness
            from dba_indexes
            where index_name = 'PGA_TCP_IMSC_IND';

        Both `SELECT` statements must produce one row each. Following is the result for the first select statement:

            TABLE_NAME                        OWNER
            ------------------------------  ------------------------------
            PGA_TCP_IMSC                      PGAADMIN

        Following is the result of the second select statement:

            OWNER          INDEX_NAME           TABLE_NAME      UNIQUENESS
            ----------     ------------------   --------------  ---------
            PGAADMIN       PGA_TCP_IMSC_IND     PGA_TCP_IMSC    UNIQUE

        If the select statements produce the preceeding output on the screen, then you can skip Step C. If the select statement produces no output or more than one row, then the result is not the same as the output described above, and it is necessary for you to perform Step 7.c.

    3.  From SQL\*Plus, run the `pgaimsc.sql` script in the Oracle database 's `%ORACLE_HOME%\dg4appc\admin` directory:

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgaimsc.sql

8.  Install the TIP trace access PL/SQL routines. These routines require that the `DBMS_PIPE` standard PL/SQL package is installed and that `PGAADMIN` has execute privileges on it. For more information about `DBMS_PIPE`, refer to the [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_PIPE.md).

    1.  If necessary, then use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`.

    2.  From SQL\*Plus, run the `pgatiptr.sql `script in the `%ORACLE_HOME%\dg4appc\admin `directory. This script creates PL/SQL routines that can be called to read and purge trace information created by PGAU-generated TIP specifications. It also creates public synonyms for these routines. The script prompts you for the necessary user IDs and passwords.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgatiptr.sql

9.  Install the `GPGLOCAL` package. This package is required for compilation and execution of all PGAU-generated TIP specifications. TIP developers should be granted execute privileges on `GPGLOCAL` (refer to "Optional Configuration Steps to Permit Multiple Users").

    1.  Use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`.

    2.  From SQL\*Plus, run the` gpglocal.pkh `script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script compiles the `GPGLOCAL` package specification.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @gpglocal.pkh

    3.  From SQL\*Plus, run the `gpglocal.pkb` script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script compiles the `GPGLOCAL` package body.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @gpglocal.pkb

        **Note:**

        Recompile TIPs when changing communication protocol from SNA to TCP/IP:

        If you have existing TIPs that were generated previously on a gateway using the SNA protocol and you want to use the new TCP/IP feature, then the TIPs will have to be regenerated by PGAU with mandatory `NLS_LANGUAGE` and Side Profile Settings. Specify the suitable ASCII character set in the `DEFINE` `TRANSACTION` command.

        This is due to the fact that the gateway assumes that the appropriate user exit in IMS Connect is being used, which would translate between the suitable ASCII and EBCDIC character sets.

### Upgrading or Migrating the Oracle Database from Previous Gateways

Follow these instructions only if you have a previous version of the Oracle Database Gateway for APPC installed on your system and need to configure it for 12c Release 21 (12.2) of the gateway.

1.  Upgrade your Oracle Database Gateway for APPC to current version levels as follows:

    1.  Use SQL\*Plus to connect to the Oracle database as user `SYS`.

    2.  Install the `UTL_RAW` package body. From SQL\*Plus, run the` prvtrawb.plb` script from the `%ORACLE_HOME%\rdbms\admin` directory. This script upgrades the `UTL_RAW` package body.

            C:\> cd %ORACLE_HOME%\rdbms\admin
            SQL> @prvtrawb.plb

    3.  Install the `UTL_PG` package body. From SQL\*Plus, run the `prvtpgb.plb` script from the `%ORACLE_HOME%\rdbms\admin `directory. This script upgrades the `UTL_PG` package body.

            C:\> cd %ORACLE_HOME%\rdbms\admin
            SQL> @prvtpgb.plb

    The `prvtrawb.plb` and `prvtpgb.plb` scripts should complete successfully. If they fail because specifications do not exist or were invalidated, then consider reinstalling the package specifications as directed in If You Must Reinstall Package Specifications .

#### If You Must Reinstall Package Specifications

If the `UTL_RAW` or `UTL_PG` package has been invalidated or removed, then the `prvtrawb.plb` and `prvtpgb.plb` scripts may not complete successfully, then, you might have to reinstall the package specifications.

If you do reinstall the package specifications, then any dependent objects (such as existing user TIPs and client applications) are invalidated and will subsequently need to be recompiled. The impact of this is a one-time performance delay while recompilation of the TIPs and dependent client applications proceeds.

**Note:**

Before proceeding with reinstallation of the package scripts, make sure that you are in the` %ORACLE_HOME%\dg4appc\admin` directory

TIPs were split into separate specification and body files in release 3.3 to avoid cascaded recompilations in later releases.

- Step 1: Run the following scripts before proceeding with the PGAU upgrade:

  1.  If necessary, then use SQL\*Plus to connect to the Oracle database as user `SYS`.

  2.  From SQL\*Plus, run the `utlraw.sql` and `utlpg.sql` scripts in the Oracle database `%ORACLE_HOME%\rdbms\admin `directory, in the following order, to upgrade their respective package specifications:

          C:\> cd %ORACLE_HOME%\rdbms\admin
          SQL> @utlraw.sql
          SQL> @utlpg.sql

- Step 2: Repeat installation of `UTL_RAW` and `UTL_PG` package body

After the scripts have run, repeat Steps 1a and 1b in Upgrading or Migrating the Oracle Database from Previous Gateways and then, proceed to Upgrading PGAU from Previous Gateway Releases.

**Note:**

TIPs and dependent client applications must be recompiled after reinstallation of the package specifications. Refer to [Oracle Database Gateway for APPC User's Guide](../appug/creating-tip-oracle-database-gateway-appc.md) for more information about compiling TIPs

#### Upgrading PGAU from Previous Gateway Releases

Upgrade the PG DD as follows before execution the new PGAU:

1.  If necessary, then use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`.
2.  From SQL\*Plus, run the` pgddupgr.sql` script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script upgrades the PG DD.
        C:\> cd %ORACLE_HOME%\dg4appc\admin
        SQL> @pgddupgr.sql

### Optional Configuration Steps to Permit Multiple Users

The following configuration steps are optional. Perform these steps if you want to allow users other than `PGAADMIN` to perform PG DD operations using PGAU.

1.  Create public synonyms for the PG DD to allow other users to access the tables:

    1.  Use SQL\*Plus to connect to the Oracle database as user `SYSTEM`.

    2.  From SQL\*Plus, run the `pgddcr8s.sql` script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script creates public synonyms for the PG DD.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgddcr8.sql

2.  Create roles for accessing the PG DD, performing definitions of transactions, and generating TIP specifications. The `PGAADMIN` user can grant these roles to other users as necessary.

    1.  Use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`.

    2.  From SQL\*Plus, run the` pgddcr8r.sql` script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script creates two roles, `PGDDDEF` and `PGDDGEN`. The `PGDDDEF` role provides `SELECT`, `INSERT`, `UPDATE`, and `DELETE` privileges against some of the PG DD tables, and select privileges against others, and allows execution of the `PGAU` `DEFINE`, `GENERATE`, `REDEFINE`, `REPORT`, and `UNDEFINE` statements. The `PGDDGEN` role provides select privileges against the PG DD tables, and allows execution of the `PGAU` `GENERATE` and `REPORT` statements only.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgddcr8r.sql

3.  Grant access to PGA required packages.

    TIP developers require access to the following PL/SQL packages, which are shipped with the Oracle database :

    - `DBMS_PIPE` in the `%ORACLE_HOME%\rdbms\admin` directory

    - `UTL_RAW` in the `%ORACLE_HOME%\rdbms\admin` directory

    - `UTL_PG` in the `%ORACLE_HOME%\rdbms\admin` directory

    Explicit grants to execute these packages must be made to TIP developers.

    These grants can be private, as in the following example:

        C:\> sqlplus SYS\pw@database_specification_string
        SQL> GRANT EXECUTE ON UTL_RAW TO tip_developer;
        SQL> GRANT EXECUTE ON UTL_PG TO tip_developer;
        SQL> GRANT EXECUTE ON DBMS_PIPE TO tip_developer;
        SQL> CONNECT PGAADMIN\pw@database_specification_string
        SQL> GRANT EXECUTE ON PGAADMIN.PURGE_TRACE TO tip_developer;
        SQL> GRANT EXECUTE ON PGAADMIN.READ_TRACE TO tip_developer;
        SQL> GRANT EXECUTE ON PGAADMIN.GPGLOCAL TO tip_developer;
        SQL> exit

    Alternatively, these grants can be public, as in the following example:

        C:\> sqlplus SYS\pw@database_specification_string
        SQL> GRANT EXECUTE ON UTL_RAW TO PUBLIC;
        SQL> GRANT EXECUTE ON UTL_PG TO PUBLIC;
        SQL> GRANT EXECUTE ON DBMS_PIPE to PUBLIC;
        SQL> CONNECT PGAADMIN\pw@database_specification_string
        SQL> GRANT EXECUTE ON PGAADMIN.PURGE_TRACE TO PUBLIC;
        SQL> GRANT EXECUTE ON PGAADMIN.READ_TRACE TO PUBLIC;
        SQL> GRANT EXECUTE ON PGAADMIN.GPGLOCAL TO PUBLIC;
        SQL> EXIT

    You can use either private or public grants. Both are sufficient for using PGA. Public grants are easier and can be performed now. If you use private grants, then they must be issued each time a new TIP developer user ID is created.

    SQL scripts for performing these grants are provided in the `%ORACLE_HOME%\dg4appc\admin` directory. The `pgddapub.sql `script performs these grants for public access to the packages. The `pgddadev.sql `script performs the grants for private access to the packages by a single TIP developer. If you are going to use private grants, then you must run the `pgddadev.sql` script once for each TIP developer's user ID:

    1.  Use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`.

    2.  From SQL\*Plus, run the suitable script (`pgddapub.sql` or `pgddadev.sql`) from the `%ORACLE_HOME%\dg4appc\admin` directory. The script performs the necessary grants as described earlier. You are prompted for the required user IDs, passwords, and database specification strings. If you are using private grants, then repeat this step for each user ID requiring access to the packages.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgddapub.sql

        or

            SQL> @pgddadev.sql

4.  If you are upgrading from a previous release of the gateway when the communication protocol was SNA, to the current gateway using TCP/IP, and if you want to upgrade your existing TIPs with new function and maintenance, then regenerate existing TIP specifications using the PGAU `GENERATE` statement.

    **Note:**

    The Procedural Gateway Administrative Utility (PGAU) has been enhanced to automatically upgrade existing PG DD entries with a new attribute when a PGAU `GENERATE` command is executed. To support this enhancement, add a new privilege to the `PGDDGEN` role. To do this, as the `PGAADMIN` user, use SQL\*Plus to connect to the Oracle database where the PG DD is stored. Then, issue the following SQL command:

        SQL> GRANT INSERT ON PGA_DATA_VALUES TO PGDDGEN

    1.  Call PGAU in the directory path where the PGAU control files are generated and where TIPs are stored:

            C:\> pgau
            PGAU> CONNECT PGAADMIN\pgaadmin@database_specification_string
            PGAU> GENERATE tranname
            PGAU> EXIT

    For more information about the `GENERATE` command, refer to the [PGAU GENERATE](../appug/pga-utility-oracle-database-gateway-appc.md) section in Chapter 2 of the [Oracle Database Gateway for APPC User's Guide](../appug/pga-utility-oracle-database-gateway-appc.md).

    Note that it is not necessary to define the PG DD entries again.

5.  Call SQL\*Plus in the same directory path where the newly-generated TIP specifications are stored.

        C:\> sqlplus tip_owner\pw@database_specification_string
        SQL> @tipname.pkh
        SQL> @tipname.pkb
        SQL> exit

    PGAU `GENERATE` produces the TIP in two output files, a specification and a body. You must compile both, first the specification and then the body.

    For more information about the `GENERATE` command, refer to the [PGAU GENERATE](../appug/pga-utility-oracle-database-gateway-appc.md) command section in Chapter 2 of the [Oracle Database Gateway for APPC User's Guide](../appug/pga-utility-oracle-database-gateway-appc.md).

### Configuring TCP/IP for the Gateway

You must now configure the TCP/IP for IMS Connect communication package profiles for TCP/IP connections.

Configure the profiles to define the TCP/IP conversations with the OLTP.

When you have finished configuring your communications package, return to the following section, Configuring the Gateway.

### Configuring the Gateway

Use the following steps to configure the gateway.

1.  Customize the gateway parameters.
    There are a number of parameters specific to the Oracle Database Gateway for APPC when it is using TCP/IP for IMS Connect. These are supplied in the gateway parameter file, `init``sid``.ora`, which is in the `%ORACLE_HOME%\dg4appc\admin` directory. A sample gateway parameter file, `initPGA.ora`, is provided in this subdirectory.

    **Note:**

    In the `init``sid``.ora` file, substitute your gatewaySID name for "`sid` " in this file name.

    The initsid.ora file contains both APPC and TCP/IP parameters, separated by a description. You must modify the `init``sid``.ora` file by deleting the APPC parameters. Refer to [Gateway Initialization Parameters for TCP/IP Communication Protocol](appc-gateway-initialization-parameters-tcp-ip.md) for the valid TCP/IP parameters.

    The parameters fall into two categories:

    - gateway initialization parameters

      These parameters control the general operation of the gateway in the Oracle environment.

      **Note:**

      Before performing the following step, refer to [Gateway Initialization Parameters for TCP/IP Communication Protocol](appc-gateway-initialization-parameters-tcp-ip.md) for information about tailoring gateway initialization and PGA parameters. Pay special attention to the information about using the `PGA_CAPABILITY` parameter.

    - PGA parameters

      PGA parameters control the TCP/IP interface portion of the gateway. Use the `SET` gateway initialization parameter to specify PGA parameters. Oracle recommends that you group all `SET` commands for PGA parameters at the end of the initsid.ora file.

      **Note:**

      Misspelled parameters are ignored. However, if the `%ORACLE_HOME%\dg4appc\admin\initsid.ora` file is missing, then all calls to the gateway fail and return a `PGA-20928` error.

### Loading the PGA_TCP_IMSC Table

Gateway users who wish to employ the TCP/IP protocol do so by using the `pg4tcpmap` tool.

The `pg4tcpmap` tool resides on the gateway. Its function is to map the side profile name to TCP/IP and IMS Connect attributes. You must run this tool before executing the PL/SQL gateway statements (such as `%ORACLE_HOME%\dg4appc\demo\IMS\pgaims.sql`).

In PGAINIT TIP, for example, the user must specify a side profile name. The SNA protocol recognizes and uses the parameter. In this release of the gateway, the `pg4tcpmap` tool uses the original PGAINIT TIP format to map the relevant SNA parameters to TCP/IP. The `pg4tcpmap` tool inserts the values of these parameters into a table called `PGA_TCP_IMSC`.

Before executing `pg4tcpmap`, you must specify the `ORACLE_HOME`, Oracle SID and modify `init``sid``.ora`. Refer to [Gateway Initialization Parameters for TCP/IP Communication Protocol](appc-gateway-initialization-parameters-tcp-ip.md) in this guide and Chapter 6 in the [Oracle Database Gateway for APPC User's Guide](../appug/pg4tcpmap-commands-tcpip.md) for complete information about the `pg4tcpmap` commands.

Chapter 6 of the [ Oracle Database Gateway for APPC User's Guide ](../appug/pg4tcpmap-commands-tcpip.md)contains a list of `pg4tcpmap` commands and instructions for using them, as well as an example of the table. Refer to "Troubleshooting" in the [Oracle Database Gateway for APPC User's Guide ](../appug/troubleshooting-oracle-database-gateway-appc.md) for information about the trace file for the executed `pg4tcpmap` tool.

To operate this tool, execute the following command:

    C:\> cd %ORACLE_HOME%\bin
    C:\> pg4tcpmap

Refer to "[Output for the pg4tcpmap Tool](appc-gateway-initialization-parameters-tcp-ip.md)" for a sample of the `pg4tcpmap` output.

### Verifying the Gateway Installation and OLTP Configuration

To verify the gateway installation and the OLTP configuration, perform the following procedures after installing the gateway.

**Note:**

If your database link name is not "PGA," modify the demonstration `.sql` files to give them the particular database link name that you created in Step configure-appc-gateway-using-tcp-ip.html#GUID-C1D6A15C-21DD-480A-A45D-EE4D3554B54C\_\_i1008586 of "Configuring the Oracle Database : First Time Installation ". You must modify the following .sql files:

- `pgavsn.sql `

- `pgaecho.sql`

- `pgaims.sql `

#### Verifying the Gateway Installation

To verify the gateway software installation using the database link PGA previously created, perform the following steps:

1.  Using SQL\*Plus, connect to your Oracle database as user `PGAADMIN`.
2.  Run `%ORACLE_HOME%\dg4appc\demo\pgavsn.sql`.
        C:\> cd %ORACLE_HOME%\dg4appc\demo
        SQL> @pgavsn.sql

    The server version number banner appears at your terminal. You will receive the following output:

        Oracle Database Gateway for APPC (extension TCP/IP for IMS connect).
        Version
        11.2.0.0.2 Thu Jun 11 14:52:36 2009

        Copyright (c) Oracle Corporation 1979,
        2009.  All rights reserved.


        PL/SQL procedure successfully completed.
3.  Run `%ORACLE_HOME%\dg4appc\demo\pgaecho.sql`.
        C:\> cd %ORACLE_HOME%\dg4appc\demo
        SQL> @pgaecho.sql

    You will receive the following output:

        ==> Congratulations, your installation was successful. <==

#### Verifying the OLTP Configuration

Use the following procedure to verify the OLTP configuration.

**Note:**

If you have not completed the file transfers detailed in "Preparing to Configure a Gateway Installation/Upgrade ",then complete them now, before proceeding to the next step.

##### IMS/TM Verification

Perform the following steps to verify the IMS/TM configuration. Be certain that you have installed and configured the IMS Connect and that it is up and running before you begin this procedure. Refer to the IBM IMS Connect Guide and Reference for information about how to perform the installation and configuration tasks.

**Note:**

TIPs must be recompiled when changing the communication protocol to TCP/IP.

TCP/IP only: If you have existing TIPs that were generated previously on a gateway using the SNA protocol and you want to use the new TCP/IP feature, then the TIPs will have to be regenerated by PGAU with mandatory `NLS_LANGUAGE` and Side Profile Settings. Specify the suitable ASCII character set in the `DEFINE TRANSACTION `command.

This is because the gateway assumes that the appropriate user exit in IMS Connect is being used, which would translate between the suitable ASCII and EBCDIC character sets.

1.  To verify that the `FLIP` transaction is installed correctly, log on to your IMS/TM system and enter the following transaction (replacing `FLIP` with the transaction ID you chose for `FLIP` when you configured the IMS/TM system for the gateway):
        FLIP THIS MESSAGE

    The following output appears on your terminal:

        EGASSEM SIHT PILF

    **Note:**

    If you have not completed the file transfers detailed in Preparing to Configure a Gateway Installation/Upgrade "Preparing to Configure a Gateway Installation/Upgrade ", then complete them now, before proceeding to the next step.
2.  From your Windows platform, modify the `pgaims.sql` file, which resides at `%ORACLE_HOME%\dg4appc\demo\IMS\pgaims.sql. `Customize the following three items used for accessing the gateway and the IMS/TM system, as described in the comments at the beginning of the file:
    - the IMS/TM transaction ID

    - the side profile name

    - the logmode entry name
3.  Ensure that the TCP/IP communication protocol on your system has been started.
4.  Using SQL\*Plus, connect to your Oracle database from `PGAADMIN`.
5.  Run `pgaims.sql`.
        C:\> cd %ORACLE_HOME%\dg4appc\demo\IMS
        SQL> @pgaims.sql

    The following message appears:

<!-- -->

    ==> Congratulations, your gateway is communicating with IMS/TM <==

Your IMS/TM installation verification is now complete.

### Performing Postinstallation Procedures

The following are optional steps that you can perform as necessary. Installation of the sample applications for the OLTP is recommended to help you to fully understand how the gateway works and how it interfaces with the OLTP.

#### Installing Sample Applications

Your Oracle Database Gateway for APPC featuring TCP/IP for IMS Connect contains sample PL/SQL procedures and OLTP transaction programs that demonstrate the gateway's capabilities.

**Note:**

When you are calling a gateway that is using TCP/IP as the communication protocol, and you are using EBCDIC as the language in the control files, you must change the language from EBCDIC to ASCII. Some examples of control files that may be in EBCDIC language are `ivtno.ctl` and` ivtnv.ctl`.

For more information, refer to the `%ORACLE_HOME%\dg4appc\demo\IMS\ivtno.ctl` and

`%ORACLE_HOME%\dg4appc\demo\IMS\ivtnv.ctl` files.

Samples are provided for IMS/TM:

- IMS inquiry using` IVTNO` and `IVTNV` sample transactions

Additional samples are added to the distribution media in later releases of the product. Wherever possible, the sample applications use the sample databases provided with the database products.

For this release, full documentation on installing and using the sample applications is available in the `README.doc `files in the following directory:

`%ORACLE_HOME%\pg4appc\demo\IMS\sample_IMS_applications.txt`
