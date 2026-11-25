The following topics outline the steps needed to configure the Oracle database for a gateway using the SNA protocol on the Microsoft Windows platform. They show you how to configure commit-confirm, should you choose to implement it. The topics also provide the steps to verify installation and configuration of the gateway components, including optional commit-confirm.

- Before You Begin

- Preparing to Configure a Gateway Installation/Upgrade

- Integrating Server Configuration: First-Time Gateway Installations

- Upgrading or Migrating the Oracle Database from Previous Gateways

- Configuring the Oracle Database for Gateways to Coexist

- Optional Configuration Steps to Permit Multiple Users

- Configuring the Gateway

- Configuring Commit-Confirm

- Verifying the Gateway Installation and OLTP Configuration

- Performing Postinstallation Procedures

Configuring the Oracle Database Gateway for APPC using SNA involves working with the following components:

- the Oracle database

- your Microsoft Windows system

- your network

- the OLTP

### Before You Begin

The following topics require you to input parameters unique to your system in order to properly configure the gateway and SNA communications interface.

Refer to [Configuration Worksheet](appc-gateway-configuration-worksheet.md) for a worksheet listing the installation parameters you will need to know before you can complete the configuration process. Ask your network administrator to provide you with these unique parameter names before you begin.

### Preparing to Configure a Gateway Installation/Upgrade

There are three ways to establish the gateway-Oracle database relationship when you are installing or upgrading/migrating the gateway:

- When the Oracle Database and the gateway are installed in the same ORACLE_HOME on the same machine

- When the Oracle Database and the gateway are installed on separate machine

- When the Oracle Database and the gateway are on the same machine but in different directories

Depending on the location of your gateway and your Oracle database, you may need to transfer some of the gateway administrative files to the location where your Oracle database is installed.

Follow the instructions suitable to your combination of the gateway-Oracle database locations listed below.

#### When the Oracle Database and the gateway are installed in the same ORACLE_HOME on the same machine

You do not need to transfer files. Proceed to "Integrating Server Configuration: First-Time Gateway Installations".

#### When the Oracle Database and the gateway are installed on separate machine

1.  Locate the gateway administrative files in the gateway `%ORACLE_HOME%\dg4appc\admin` directory. All files in this directory that have the suffix `.sql`, `.pkh`, and `.pkb` must be copied into a similarly-named directory in the Oracle database's Oracle home directory.

2.  Now, locate the gateway demo files and subdirectories in the gateway's `%ORACLE_HOME%\dg4appc\demo` directory. Copy the `pgavsn.sql` and `pgaecho.sql` files into a similarly named directory in the Oracle database .

3.  Copy the other subdirectories and files related to your installed OLTP on your remote host. For example, if you have CICS as your only OLTP, then copy the gateway `%ORACLE_HOME%\dg4appc\demo\CICS `files into a similarly named directory in the Oracle database .

    **Note:**

    Before transferring the files from the `%ORACLE_HOME%\dg4appc\demo` directory, make sure that you have generated your required TIPs. You need to transfer the TIPs as well.

    Refer to the [Oracle Database Gateway for APPC User's Guide](../appug/pga-utility-oracle-database-gateway-appc.md) for information about generating TIPs using PGAU.

#### When the Oracle Database and the gateway are on the same machine but in different directories

You must change your gateway's Oracle home to the Oracle database 's Oracle home directory.

1.  For example, if your gateway's Oracle home is set as follows:
        C:\> echo %ORACLE_HOME%
        C:\oracle\pga\12.2

    and your server's Oracle home is located in the `\oracle\pga\12.2` directory, then you need to do the following:

        C:\> SET ORACLE_HOME=C:\oracle\pga\12.2
2.  Now create the directories with the following commands:
        C:\> cd %ORACLE_HOME%
        C:\> mkdir dg4appc
        C:\> mkdir dg4appc\admin
3.  Use whatever file transfer mechanism is available on your system to copy all the `.sql`, `.pkh`, and `.pkb` files from the gateway Oracle home `%ORACLE_HOME%\dg4appc\admin` directory to the Oracle database 's Oracle home `%ORACLE_HOME%\dg4appc\admin` directory.
4.  You may also transfer the demo files from the gateway directory to the Oracle database directory. Copy the files and the directory recursively from the gateway Oracle home `%ORACLE_HOME%\dg4appc\demo` directory to the Oracle database `%ORACLE_HOME%\dg4appc\demo` directory.
    For example:

        C:\> cd %ORACLE_HOME%\dg4appc
        C:\> mkdir\demo
        C:\> cd demo
        C:\> xcopy C:\oracle\pga\12.2\demo /E /I /Q

    **Note:**

    Before transferring the files from the `%ORACLE_HOME%\dg4appc\demo` directory, make sure that you have generated the required TIPs. You need to transfer the TIPs as well.

    Refer to the [Oracle Database Gateway for APPC User's Guide](../appug/pga-utility-oracle-database-gateway-appc.md) for information about generating TIPs using PGAU.

If this is a first-time installation, then proceed with "Integrating Server Configuration: First-Time Gateway Installations".

If this is an upgrade, then proceed with "Upgrading or Migrating the Oracle Database from Previous Gateways".

Following those steps, you may want to perform the Optional Configuration Steps to Permit Multiple Users,Optional Configuration Steps to Permit Multiple Users.

### Integrating Server Configuration: First-Time Gateway Installations

Follow these steps to configure your Oracle database if you have installed Oracle Database Gateway for APPC for the first time:

1.  Ensure that the `UTL_RAW` PL/SQL package has been installed on your Oracle database . All PGAU-generated TIP specifications use `UTL_RAW`, which provides routines for manipulating raw data.

    1.  Use SQL\*Plus to connect to the Oracle database as user `SYS`.

    2.  From SQL\*Plus, enter the following command:

            SQL> DESCRIBE UTL_RAW

        The `DESCRIBE` statement produces output on your screen. If you browse through the output, then you should see some functions, including a compare function. If you do not see this output, then continue the `UTL_RAW` installation by performing Step 1.d. below.

        If the `DESCRIBE` statement indicates success, then your Oracle database has `UTL_RAW` installed and you can proceed to Step 2.

    3.  Use SQL\*Plus to connect to the Oracle database as user `SYS`.

    4.  From SQL\*Plus, run the utlraw.sql and prvtrawb.plb scripts in the Oracle database 's `%ORACLE_HOME%\rdbms\admin` directory, in the following order:

            C:\> cd %ORACLE_HOME%\rdbms\admin
            SQL> @utlraw.sql
            SQL> @prvtrawb.plb

2.  Ensure that the `DBMS_OUTPUT` standard PL/SQL package is enabled on your Oracle database . The sample programs and installation verification programs on the distribution media use this standard package.

    1.  If necessary, then use SQL\*Plus to connect to the Oracle database as user `SYS`.

    2.  From SQL\*Plus, enter the following command:

            SQL> DESCRIBE DBMS_OUTPUT

    The `DESCRIBE` statement produces output on your screen. If you browse through that output, you should see some functions, including a put_line function.

    If you do not see this output, then you must create the `DBMS_OUTPUT` package. Refer to the [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_OUTPUT.md) for more information about creating the `DBMS_OUTPUT` package. After successful installation of the `DBMS_OUTPUT` package, issue the `DESCRIBE` statement.

    If the `DESCRIBE` statement indicates success, then your Oracle database has `DBMS_OUTPUT` created, and you can proceed to Step 3.

3.  Install the `UTL_PG` PL/SQL package. All PGAU-generated TIP specifications use `UTL_PG`, which provides routines for performing numeric conversions to and from raw data.

    1.  If necessary, then use SQL\*Plus to connect to the Oracle database as user `SYS`.

    2.  From SQL\*Plus, run the `utlpg.sql `and `prvtpgb.plb` scripts in the Oracle database 's `%ORACLE_HOME%\rdbms\admin` directory, in the following order:

            C:\> cd %ORACLE_HOME%\rdbms\admin
            SQL> @utlpg.sql
            SQL> @prvtpgb.plb

4.  Install the Heterogeneous Services (HS) catalogs.

    1.  If necessary, use SQL\*Plus to connect to the Oracle database as user `SYS`.

    2.  Enter the following command:

            SQL> DESCRIBE HS_FDS_CLASS

        The `DESCRIBE` statement produces output on your screen. If the `DESCRIBE` statement indicates success, then heterogeneous services catalogs have been created on your Oracle database and you can proceed to Step 5. otherwise follow the next step only if the `DESCRIBE` statement does not indicate success. The next step will create the Heterogeneous Services catalog.

    3.  If it is necessary to create the Heterogeneous Services catalog, then enter the following command:

            C:\> cd %ORACLE_HOME%\rdbms\admin
            SQL> @caths.sql

5.  Create a public database link to access Oracle Database Gateway for APPC:

    Use SQL\*Plus to connect to the Oracle database as user `SYSTEM`. You can use the following SQL\*Plus sample whether the Oracle database and the gateway are on the same system or on different systems. In the following sample, `pgasrv` is the `tns_name_entry` that will be assigned to the gateway when you modify the tnsnames.ora file later.

        SQL> CREATE PUBLIC DATABASE LINK PGA USING 'PGASRV'

6.  Create the gateway administrator user `PGAADMIN` and install the PG DD.

    1.  Use SQL\*Plus to connect to the Oracle database as user `SYSTEM`.

    2.  From SQL\*Plus, run the pgacr8au.sql script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script creates the `PGAADMIN` user ID.

        The initial password defined for `PGAADMIN` is `PGAADMIN`. Use the `ALTER USER` command to change the password. For further information about password issues, refer to the [Oracle Database SQL Language Reference](../sqlrf/ALTER-USER.md).

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgacr8au.sql

    3.  Use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`.

    4.  From SQL\*Plus, run the `pgddcr8.sql `script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script installs the PG DD.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgddcr8.sql

    5.  From SQL\*Plus, connect to the Oracle database as user `SYS`.

    6.  Grant execution privileges on `DBMS_PIPE` to `PGAADMIN`:

            SQL> GRANT EXECUTE ON DBMS_PIPE TO PGAADMIN

7.  Install the TIP trace access PL/SQL routines. These routines require that the `DBMS_PIPE` standard PL/SQL package is installed and that `PGAADMIN` has execute privileges on it. For more information on `DBMS_PIPE`, refer to the [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_PIPE.md).

    1.  If necessary, then use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`.

    2.  From SQL\*Plus, run the` pgatiptr.sql` script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script creates PL/SQL routines that can be called to read and purge trace information created by PGAU-generated TIP specifications. It also creates public synonyms for these routines. The script prompts you for the necessary user IDs and passwords.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgatiptr.sql

8.  Install the `GPGLOCAL` package. This package is required for compilation and execution of all PGAU-generated TIP specifications. TIP developers should be granted execute privileges on `GPGLOCAL` (refer to Step 3 of "Optional Configuration Steps to Permit Multiple Users").

    1.  Use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`.

    2.  From SQL\*Plus, run the` gpglocal.pkh` script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script compiles the `GPGLOCAL` package specification.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @gpglocal.pkh

    3.  From SQL\*Plus, run the` gpglocal.pkb` script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script compiles the `GPGLOCAL` package body.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @gpglocal.pkb

### Upgrading or Migrating the Oracle Database from Previous Gateways

Follow these instructions only if you have a previous version of the Oracle Database Gateway for APPC installed on your system and need to configure it for 12c Release 2 (12.2) of the gateway.

1.  Upgrade your Oracle Database Gateway for APPC to current version levels as follows:

    1.  Use SQL\*Plus to connect to the Oracle database as user `SYS`.

    2.  Install the `UTL_RAW` package body. From SQL\*Plus, run the `prvtrawb.plb` script from the `%ORACLE_HOME%\rdbms\admin` directory. This script upgrades the `UTL_RAW` package body.

            C:\> cd %ORACLE_HOME%\rdbms\admin
            SQL> @prvtrawb.plb

    3.  Install the `UTL_PG` package body. From SQL\*Plus, run the `prvtpgb.plb` script from the `%ORACLE_HOME%\rdbms\admin` directory. This script upgrades the `UTL_PG` package body.

            C:\> cd %ORACLE_HOME%\rdbms\admin
            SQL> @prvtpgb.plb

        The `prvtrawb.plb` and` prvtpgb.plb` scripts should complete successfully. If they fail because specifications do not exist or were invalidated, then consider reinstalling the package specifications as directed in If You Must Reinstall Package Specifications.

#### If You Must Reinstall Package Specifications

If the `UTL_RAW` or `UTL_PG` package has been invalidated or removed, then the `prvtrawb.plb` and `prvtpgb.plb` scripts may not complete successfully, then, you might have to reinstall the package specifications.

If you do reinstall the package specifications, then any dependent objects (such as existing user TIPs and client applications) are invalidated and will subsequently need to be recompiled. The impact of this is a one-time performance delay while recompilation of the TIPs and dependent client applications proceeds.

**Note:**

Before proceeding with reinstallation of the package scripts, make sure that you are in the `%ORACLE_HOME%\dg4appc\admin` directory.

TIPs were split into separate specification and body files in release 3.3 to avoid cascaded recompilations in later releases.

Step 1   Run the following scripts before proceeding with the PGAU upgrade
1.  If necessary, then use SQL\*Plus to connect to the Oracle database as user `SYS`.

2.  From SQL\*Plus, run the `utlraw.sql` and `utlpg.sql` scripts in the Oracle database `%ORACLE_HOME%\rdbms\admin` directory, in the following order, to upgrade their respective package specifications:

        C:\> cd %ORACLE_HOME%\rdbms\admin
        SQL> @utlraw.sql
        SQL> @utlpg.sql

Step 2   Repeat installation of UTL_RAW and UTL_PG package body
After the scripts have run, repeat Steps 1b. and c. in Upgrading or Migrating the Oracle Database from Previous GatewaysUpgrading or Migrating the Oracle Database from Previous Gateways. Then, proceed to the section titled "Upgrading PGAU from Previous Gateway Releases".

**Note:**

TIPs and dependent client applications must be recompiled after reinstallation of the package specifications. Refer to the "Compiling a TIP" section in Chapter 3 of the [Oracle Database Gateway for APPC User's Guide](../appug/creating-tip-oracle-database-gateway-appc.md) for information about compiling TIPs.

#### Upgrading PGAU from Previous Gateway Releases

1.  Upgrade the PG DD as follows before executing the new PGAU:

    1.  If necessary, then use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`.

    2.  From SQL\*Plus, run the `pgddupgr.sql `script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script upgrades the PG DD.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgddupgr.sql

### Configuring the Oracle Database for Gateways to Coexist

You may have an older version of the gateway already installed. Be aware that although a version 10 gateway can communicate with a version 9 data dictionary (PG DD), a version 9 gateway cannot communicate with a version 10 data dictionary. So, if you upgrade your data dictionary to version 10, no gateways which were configured with a version 9 data dictionary will be able to communicate with it.

### Optional Configuration Steps to Permit Multiple Users

The following configuration steps are optional. Perform these steps if you want to permit users other than `PGAADMIN` to perform PG DD operations using PGAU.

1.  Create public synonyms for the PG DD to allow other users to access the tables:

    1.  Use SQL\*Plus to connect to the Oracle database as user `SYSTEM`.

    2.  From SQL\*Plus, run the` pgddcr8s.sql` script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script creates public synonyms for the PG DD.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgddcr8s.sql

2.  Create roles for accessing the PG DD, performing definitions of transactions, and generating TIP specifications. The `PGAADMIN` user can grant these roles to other users as necessary.

    1.  Use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`.

    2.  From SQL\*Plus, run the `pgddcr8r.sql `script in the `%ORACLE_HOME%\dg4appc\admin` directory. This script creates two roles, `PGDDDEF` and `PGDDGEN`. The `PGDDDEF` role provides `SELECT`, `INSERT`, `UPDATE`, and `DELETE` privileges against some of the PG DD tables, and select privileges against others, and allows execution of the `PGAU` `DEFINE`, `GENERATE`, `REDEFINE`, `REPORT`, and `UNDEFINE` statements. The `PGDDGEN` role provides select privileges against the PG DD tables, and allows execution of the `PGAU` `GENERATE` and `REPORT` statements only.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgddcr8r.sql

3.  Grant access to PGA required packages.

    TIP developers require access to the following PL/SQL packages, which are shipped with the Oracle database :

    - `DBMS_PIPE` in the `%ORACLE_HOME%\rdbms\admin `directory

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

    You can use either private or public grants. Both grants are sufficient for using PGA. Public grants are easier and can be performed now. If you use private grants, then they must be issued each time a new TIP developer user ID is created.

    SQL scripts for performing these grants are provided in the `%ORACLE_HOME%\dg4appc\admin` directory. The `pgddapub.sql` script performs these grants for public access to the packages. The `pgddadev.sql` script performs the grants for private access to the packages by a single TIP developer. If you are going to use private grants, then you must run the `pgddadev.sql `script once for each TIP developer's user ID:

    1.  Use SQL\*Plus to connect to the Oracle database as user `PGAADMIN`.

    2.  From SQL\*Plus, run the suitable script (`pgddapub.sql` or `pgddadev.sql`) from the `%ORACLE_HOME%\dg4appc\admin` directory. The script performs the necessary grants as described earlier. You are prompted for the required user IDs, passwords, and database specification strings.

        If you are using private grants, then repeat this step for each user ID requiring access to the packages.

            C:\> cd %ORACLE_HOME%\dg4appc\admin
            SQL> @pgddapub.sql

        or

            SQL> @pgddadev.sql

4.  If you are upgrading from a previous release of the gateway and if you want to upgrade your existing TIPs with new function and maintenance, then regenerate existing TIP specifications using the PGAU `GENERATE` statement.

    **Note:**

    The Procedural Gateway Administrative Utility (PGAU) has been enhanced to automatically upgrade existing PG DD entries with a new attribute when a PGAU `GENERATE` command is executed. To support this enhancement, add a new privilege to the `PGDDGEN` role. To do this, as the `PGAADMIN` user, use SQL\*Plus to connect to the Oracle database where the PG DD is stored. Then issue the following SQL command:

        SQL> GRANT INSERT ON PGA_DATA_VALUES TO PGDDGEN

    1.  Call PGAU in the directory path where the PGAU control files are generated and where TIPs are stored:

            C:\> pgau
            PGAU> CONNECT PGAADMIN\pgaadmin@database_specification_string
            PGAU> GENERATE tranname
            PGAU> EXIT

    For more information about the `GENERATE` command, refer to the PGAU `GENERATE` command section in Chapter 2 of the [Oracle Database Gateway for APPC User's Guide](../appug/pga-utility-oracle-database-gateway-appc.md).

    Note that it is not necessary to define the PG DD entries again.

5.  Call SQL\*Plus in the same directory path where the newly-generated TIP specifications are stored.

        C:\> sqlplus tip_owner\pw@database_specification_string
        SQL> @tipname.pkh
        SQL> @tipname.pkb
        SQL> exit

    `PGAU` `GENERATE` produces the TIP in two output file, a specification and a body. You must compile both, first the specification and then the body.

    For more information about the `GENERATE` command, refer to the PGAU `GENERATE` command section in Chapter 2 of the [Oracle Database Gateway for APPC User's Guide](../appug/pga-utility-oracle-database-gateway-appc.md).

### Configuring the Gateway

To configure the gateway, perform the following steps:

1.  Customize the Oracle Database Gateway for APPC parameters.
    Parameters specific to the gateway are supplied in the gateway parameter file, `init``sid``.ora`, which is in the `%ORACLE_HOME%\dg4appc\admin `directory. A sample gateway parameter file, `initPGA.ora`, is provided in this subdirectory.

    **Note:**

    In the `init``sid``.ora` file, substitute your `dg4appc` SID name for "`sid` " in this file name.

    The `init``sid``.ora` file contains both APPC and TCP/IP parameters, separated by a description. You must modify the `init``sid``.ora` file by deleting the TCP/IP parameters. Refer to [Gateway Initialization Parameters for SNA Protocol](appc-gateway-initialization-parameters-sna.md) for the valid APPC parameters.

    The parameters fall into two categories:

    - gateway initialization parameters

      These parameters control the general operation of the gateway in the Oracle environment.

      **Note:**

      Before performing the following step, refer to [Gateway Initialization Parameters for SNA Protocol](appc-gateway-initialization-parameters-sna.md) for information about tailoring gateway initialization and PGA parameters. Pay special attention to the information about using the `PGA_CAPABILITY` parameter.

    - PGA parameters

      PGA parameters control the APPC interface portion of the gateway. Use the `SET` gateway initialization parameter to specify PGA parameters. Oracle recommends that you group all `SET` commands for PGA parameters at the end of the `init``sid``.ora` file.

      **Note:**

      Misspelled parameters are ignored. However, if the `%ORACLE_HOME%\dg4appc\admin\initsid.ora` file is missing, then all calls to the gateway fail and return a `PGA-20928` error.

      If you do not plan to configure commit-confirm, then proceed to"Verifying the Gateway Installation and OLTP Configuration".

### Configuring Commit-Confirm

**Note:**

If you are planning to implement commit-confirm, then read the detailed explanation of commit-confirm capabilities in Chapter 5 of the [Oracle Database Gateway for APPC User's Guide](../appug/implement-appc-commit-confirm-sna-only.md), "Implementing Commit-Confirm (SNA Only) before proceeding.

Follow these steps to configure the commit-confirm components.

The steps for configuring commit-confirm include:

- configuring the Oracle database where the gateway server will store its transaction log information

- configuring the gateway initialization parameters, and

- configuring the OLTP.

All these steps must be performed before attempting to use any application that uses commit-confirm.

#### Configuring the Oracle Database for Commit-Confirm

The Oracle database where the gateway server will store its transaction log information should ideally be on the same system where the gateway runs. The configuration of the server consists of creating the gateway DBA user, creating the commit-confirm log tables and creating the PL/SQL stored procedure used by the gateway server for logging transactions.

The `pgaccau.sql` script from the `%ORACLE_HOME%\dg4appc\admin` directory creates the gateway DBA user ID. The default user ID is `PGADBA` with the initial password set to `PGADBA`. If you want to change the user ID or initial password, you must modify the script.

1.  Use SQL\*Plus to connect to the Oracle database as user `SYSTEM`.
2.  From SQL\*Plus, run the `pgaccau.sql` script from the `%ORACLE_HOME%\dg4appc\admin` directory. This script creates the gateway DBA user ID. If you want to change the password at any time after running this script, then you can use the `ALTER USER` command to change the password. For further information, refer to the [Oracle Database SQL Language Reference](../sqlrf/ALTER-USER.md).
3.  Use SQL\*Plus to connect to the Oracle database as user `PGADBA`.
4.  From SQL\*Plus, run the `pgaccpnd.sql` script from the `%ORACLE_HOME%\dg4appc\admin `directory. This script creates the `PGA_CC_PENDING` table used by the gateway server for its commit-confirm transaction log.
5.  From SQL\*Plus, run the `pgacclog.sql` script from the `%ORACLE_HOME%\dg4appc\admin` directory. This script creates the `PGA_CC_LOG` PL/SQL stored procedure used by the gateway server for updating the `PGA_CC_PENDING` table.
6.  Disconnect from the Oracle database .

#### Configuring Gateway Initialization Parameters for Commit-Confirm

The gateway initialization parameters are described in [Gateway Initialization Parameters for SNA Protocol](appc-gateway-initialization-parameters-sna.md). The parameters necessary for commit-confirm support in the gateway are:

- `PGA_CAPABILITY`

- `PGA_LOG_DB`

- `PGA_LOG_USER`

- `PGA_LOG_PASS`

- `PGA_RECOVERY_USER`

- `PGA_RECOVERY_PASS`

- `PGA_RECOVERY_TPNAME`

These parameters should be added to your `init``sid``.ora` file, where `sid` is the gateway SID for the commit-confirm gateway.

Refer to [Gateway Initialization Parameters for SNA Protocol](appc-gateway-initialization-parameters-sna.md) for full information about the gateway initialization parameters supported by the Oracle Database Gateway for APPC.

#### Configuring the OLTP for Commit-Confirm

Configuration of the OLTP includes the following:

- defining and installing the commit-confirm transaction log database

- defining and installing the commit-confirm forget/recovery transaction

- defining and installing the sample commit-confirm applications provided with the gateway.

  **Note:**

  A restart of the OLTP may be necessary to implement the changes required for commit-confirm support. You should plan for this with your OLTP system administrator.

Detailed instructions for configuring the Transaction Server for z/OS and IMS/TM are provided in the `%ORACLE_HOME%\dg4appc\demo\CICS\README.doc` and `%ORACLE_HOME%\dg4appc\demo\IMS\README.doc` files, respectively.

Refer to Chapter 5, "Implementing Commit-Confirm (SNA Only)" in the [Oracle Database Gateway for APPC User's Guide](../appug/implement-appc-commit-confirm-sna-only.md) for detailed information about commit-confirm.

- You will take steps to verify configuration of commit-confirm later, in Verifying OLTP Configuration for Commit-ConfirmVerifying OLTP Configuration for Commit-Confirm.

However, first proceed to Verifying the Gateway Installation and OLTP Configuration to verify the gateway installation.

### Verifying the Gateway Installation and OLTP Configuration

To verify the gateway installation and the OLTP configuration, perform the following procedures after installing Oracle Database Gateway for APPC. In addition, if you chose to configure commit-confirm, then follow the steps to verify the OLTP configuration for commit-confirm.

**Note:**

If your database link name is not PGA, then modify the demonstration .sql files to give them the particular database link name that you created in Step 5 of "Integrating Server Configuration: First-Time Gateway Installations". You must modify the following .sql files:

- `pgavsn.sql `

- `pgaecho.sql `

- `pgacics.sql`

- `pgaidms.sql`

- `pgaims.sql `

- `pgamvs.sql `

#### Verifying the Gateway Installation

To verify the gateway software installation using the database link PGA previously created, perform the following steps:

1.  Using SQL\*Plus, connect to the Oracle database as user `PGAADMIN`.
2.  Run `%ORACLE_HOME%\dg4appc\demo\pgavsn.sql`.
        C:\> cd %ORACLE_HOME%\dg4appc\demo
        SQL> @pgavsn.sql

    The server version number banner appears at your terminal. You will receive the following output:

        Oracle Database Gateway for APPC.
        Version 11.2.0.0.2 Thu Jun 11 14:39:15
        2009

        Copyright (c) Oracle Corporation 1979, 2009.  All rights reserved.


        PL/SQL procedure successfully completed.
3.  Run `%ORACLE_HOME%\dg4appc\demo\pgaecho.sql`.
        C:\> cd %ORACLE_HOME%\dg4appc\demo
        SQL> @pgaecho.sql

    You will receive the following output:

        ==> Congratulations, your installation was successful. <==

#### Verifying the OLTP Configuration

The procedure for verifying the OLTP configuration varies, depending on which OLTP you are using and depending on the platform the OLTP is running on. CICS Transaction Server for z/OS, IMS/TM, APPC/MVS and z/OS are the currently supported OLTPs. Follow the instructions for verifying the installation.

**Note:**

If you have not completed the file transfers detailed in "Preparing to Configure a Gateway Installation/Upgrade", then complete them now, before proceeding to the next step.

##### CICS Verification

If your OLTP is CICS Transaction Server for z/OS, then perform the following steps to verify the CICS configuration.

1.  To verify that the `FLIP` transaction is installed correctly, log on to your CICS Transaction Server for z/OS and enter the following transaction, replacing `FLIP` with the transaction ID you chose for `FLIP` when you configured your CICS Transaction Server for z/OS for the gateway:
        FLIPTHIS MESSAGE

    The following output appears at your terminal:

        EGASSEM SIHT PILF
2.  From the Windows platform, modify the pgacics.sql file which resides at `%ORACLE_HOME%\dg4appc\demo\CICS\pgacics.sql`.
    Customize the following three items used for accessing the gateway and the CICS Transaction Server for z/OS, as described in the comments at the beginning of the file:

    - the CICS transaction ID

    - the side profile name

    - the logmode entry name
3.  Ensure that the SNA Server on the system has been started.
4.  Log on to the CICS Transaction Server for z/OS and enter this transaction, where `name` is the name of the `CONNECTION` definition installed by the `DFHCSDUP` job you ran in the CICS configuration steps:
        CEMT SET CONNECTION(name) ACQUIRED

    This transaction activates the CICS connection to Windows.
5.  Use SQL\*Plus to connect to the Oracle database as `PGAADMIN`.
6.  Run `pgacics.sql`.
        C:\> cd %ORACLE_HOME%\dg4appc\demo\CICS
        SQL> @pgacics.sql

    The following message appears:

        ==> Congratulations, your gateway is communicating with CICS <==

The CICS Transaction Server for z/OS installation verification is complete.

##### IMS/TM Verification

If the OLTP is IMS/TM, then perform the following steps to verify the IMS/TM configuration:

1.  To verify that the `FLIP` transaction is installed correctly, log on to the IMS/TM system and enter the following transaction, replacing `FLIP` with the transaction ID you chose for `FLIP` when you configured the IMS/TM system for the gateway:
        FLIP THIS MESSAGE

    The following output appears on the terminal:

        EGASSEM SIHT PILF
2.  From a Windows platform, modify the `pgaims.sql` file, which resides at
    `%ORACLE_HOME%\dg4appc\demo\IMS\pgaims.sql`. Customize the following three items used for accessing the gateway and the IMS/TM system, as described in the comments at the beginning of the file:

    - the IMS/TM transaction ID

    - the side profile name

    - the logmode entry name
3.  Ensure that the SNA Server on the system has been started.
4.   Use SQL\*Plus to connect to the Oracle database as `PGAADMIN`.
5.  Run `pgaims.sql`.
        C:\> cd %ORACLE_HOME%\dg4appc\demo\IMS
        SQL> @pgaims.sql

The following message appears:

    ==> Congratulations, your gateway is communicating with IMS/TM <==

The IMS/TM installation verification is now complete.

##### APPC/MVS Verification

If the OLTP is APPC/MVS, then perform the following steps to verify the APPC/MVS configuration:

1.  Verify that the APPC/MVS subsystem is active.
2.  From the Windows platform, modify the `pgamvs.sql` file, which resides at `%ORACLE_HOME%\dg4appc\demo\MVS\pgamvs.sql`. Customize the following three items used for accessing the gateway and the APPC/MVS system, as described in the comments at the beginning of the file:
    - the APPC/MVS transaction ID

    - the side profile name

    - the logmode entry name
3.  Ensure that the SNA Server on the system has been started.
4.  Use SQL\*Plus to connect to the Oracle database as `PGAADMIN`.
5.  Run `pgamvs.sql`.
        C:\> cd %ORACLE_HOME%\dg4appc\demo\MVS
        SQL> @pgamvs.sql

    The following message appears:

        => Congratulations, your gateway is communicating with APPC/MVS <=

<!-- -->

The APPC/MVS installation verification is now complete.

#### Verifying OLTP Configuration for Commit-Confirm

If you chose to configure commit-confirm in Configuring Commit-Confirm, then the following section will assist you in verifying the configuration.

**Note:**

Refer to Chapter 5, "Implementing Commit-Confirm" in the [Oracle Database Gateway for APPC User's Guide](../appug/implement-appc-commit-confirm-sna-only.md) for background information about the components and capabilities of commit-confirm.

Samples are provided with the gateway for Transaction Server for z/OS and IMS/TM for implementing commit-confirm support. They are in the following directories, respectively: `%ORACLE_HOME%\dg4appc\demo\CICS` and `%ORACLE_HOME%\dg4appc\demo\IMS. A README.doc` file in each directory provides detailed information about installing and using the samples. JCL files for compiling and linking the sample programs are provided as well. The samples included with the gateway assist you with the following:

- Creating and initializing the commit-confirm transaction log databases and defining those databases to the OLTP. For Transaction Server for z/OS, the sample uses a VSAM file for the log database. For IMS/TM, a SHISAM/VSAM database is used.

- Using subroutines for receiving the Oracle Global Transaction ID from the gateway and logging it into the commit-confirm transaction log database. These subroutines are provided in the `pgacclg.asm `files. They can be used in the applications to reduce the complexity of the code changes to the programs.

  For Transaction Server for z/OS, the subroutine provided is called using the EXEC CICS LINK interface. For IMS/TM, the subroutine provided is called using the standard `CALL` statement or its equivalent in the application's programming language. Both these subroutines are written in 370 assembler to eliminate any interlanguage interface complexities and compiler dependencies.

- Installing forget/recovery transactions in the OLTP. These are provided in the `pgareco.asm `files. Forget/recovery transactions must be accessible through APPC so that the gateway can call them to forget a transaction once it has been successfully committed, and to query a transaction's state during recovery processing. These transactions delete the entry for a particular Oracle Global Transaction ID from the OLTP commit-confirm transaction log database during forget processing, and query the entry for a particular Oracle Global Transaction ID from the OLTP commit-confirm transaction log database during recovery processing. For both Transaction Server for z/OS and IMS/TM, these transactions are written in 370 assembler.

- Using the sample commit-confirm transaction log databases and subroutines. For Transaction Server for z/OS, a sample DB2 update transaction, `DB2C`, is provided in the` pgadb2c.cob file`. This is a COBOL example that updates the DB2 sample `EMP` table. For IMS/TM, a sample DLI update transaction, `PGAIMSU`, is provided in the `pgaimsu.cob` file. This is a COBOL example that updates the DLI sample `PARTS` database.

### Performing Postinstallation Procedures

The following are optional steps that you can perform as necessary. Installation of the sample applications for your OLTP is recommended to help you to fully understand how the gateway works and how it interfaces with the OLTP.

#### Installing Sample Applications

The Oracle Database Gateway for APPC package contains sample PL/SQL procedures and OLTP transaction programs that demonstrate the capabilities of the gateway. Samples are provided for the following:

APPC/MVS

- z/OS dataset information

CICS Transaction Server for z/OS

- DB2 inquiry

- DB2 multirow inquiry

- DB2 update

- VSAM inquiry

- VSAM update

- DLI inquiry

- FEPI DB2 inquiry

- FEPI VSAM inquiry

IMS/TM

- IMS inquiry using IVTNO and IVTNV sample transactions

- IMS PARTS inquiry (CPI-C)

- IMS PARTS update (CPI-C)

Additional samples are added to the distribution media in later releases of the product. Wherever possible, the sample applications use the sample databases provided with the database products.

For this release, full documentation on installing and using the sample applications is available in the `README.doc `files in the following directories:

- `%ORACLE_HOME%\dg4appc\CICS\sample_CICS_applications.txt`

- `%ORACLE_HOME%\dg4appc\IMS\sample_IMS_applications.txt`

- `%ORACLE_HOME%\dg4appc\MVS\sample_MVS_applications.txt`
