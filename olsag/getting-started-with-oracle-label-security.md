Before using Oracle Label Security, you must register (configure) it with the database and then you can log in to Oracle Label Security.

- Registering Oracle Label Security with an Oracle Database
  You must register Oracle Label Security with the database in which you plan to use it.
- Security Guideline for Managing the LBACSYS User and the LBAC_DBA Role
  As a good practice, for day-to-day use, grant the `LBAC_DBA` database role to trusted users who will administer Oracle Label Security.
- Logging in to Cloud Control or SQL\*Plus for Oracle Label Security
  After you complete the Oracle Label Security registration and enablement process, you can begin using it.

**Parent topic:** [Using Oracle Label Security Functionality](part2.md)

### 4.1 Registering Oracle Label Security with an Oracle Database

You must register Oracle Label Security with the database in which you plan to use it.

- About Registering Oracle Label Security
  When you install Oracle Database, Oracle Label Security is included in the installation but by default it is not enabled.
- Checking if Oracle Label Security Has Been Registered and Enabled
  You can query the `DBA_OLS_STATUS` data dictionary view to find if Oracle Label Security has already been registered and enabled.
- Registering and Enabling Oracle Label Security from SQL\*Plus
  You can both register and enable Oracle Label Security from SQL\*Plus.
- Registering and Enabling Oracle Label Security Using DBCA
  You can both register and enable Oracle Label Security using Database Configuration Assistant.

**Parent topic:** Registering and Logging in to Oracle Label Security

#### 4.1.1 About Registering Oracle Label Security

When you install Oracle Database, Oracle Label Security is included in the installation but by default it is not enabled.

This applies if you install Oracle Database by using the Typical installation method in Database Configuration Assistant (DBCA). If you install using a custom installation, then you can optionally register Oracle Label Security from DBCA as part of the Oracle Database installation process.

If you installed using the Typical installation method, then you must manually register (enable) Oracle Label Security before you can use it. You have the choice of using either SQL\*Plus or DBCA to perform the registration.

After Oracle Label Security is registered, you must enable the default Oracle Label Security user account, `LBACSYS`. Afterward, you can disable and re-enable Oracle Label Security when necessary.

Only register Oracle Label Security in the pluggable databases (PDBs) in which you plan to create Oracle Label Security policies. Because Oracle Label Security is not designed to protect data dictionary objects, you cannot create policies in the root.

**Parent topic:** Registering Oracle Label Security with an Oracle Database

#### 4.1.2 Checking if Oracle Label Security Has Been Registered and Enabled

You can query the `DBA_OLS_STATUS` data dictionary view to find if Oracle Label Security has already been registered and enabled.

1.  Log into the database instance as user `SYS` with the `SYSDBA` administrative privilege.
        sqlplus sys as sysdba
        Enter password: password
2.  If you are using a multitenant environment, then connect to the appropriate PDB.
    For example, to connect to the PDB `hrpdb`:

        CONNECT SYS@hrpdb AS SYSDBA
        Enter password: password

    To find the available PDBs, query the `DBA_PDBS` data dictionary view. To check the current PDB, run the `show con_name` command.
3.  Execute the following query:
        SELECT * FROM DBA_OLS_STATUS;

        NAME                 STATUS  DESCRIPTION
        -------------------- ------- -------------------------------------
        OLS_CONFIGURE_STATUS TRUE    Determines if OLS is configured
        OLS_DIRECTORY_STATUS FALSE   Determines if OID is enabled with OLS
        OLS_ENABLE_STATUS    TRUE    Determines if OLS is enabled

**Parent topic:** Registering Oracle Label Security with an Oracle Database

#### 4.1.3 Registering and Enabling Oracle Label Security from SQL\*Plus

You can both register and enable Oracle Label Security from SQL\*Plus.

1.  Log into the database instance as user `SYS` with the `SYSDBA` administrative privilege.
    For example:

        sqlplus sys as sysdba
        Enter password: password
2.  If you are using a multitenant environment, then connect to the appropriate PDB.
    For example, to connect to the PDB `hrpdb`:

        CONNECT SYS@hrpdb AS SYSDBA
        Enter password: password

    To find the available PDBs, query the `DBA_PDBS` data dictionary view. To check the current PDB, run the `show con_name` command.
3.  Register and enable Oracle Label Security as follows.
        EXEC LBACSYS.CONFIGURE_OLS; -- This procedure registers Oracle Label Security.
        EXEC LBACSYS.OLS_ENFORCEMENT.ENABLE_OLS; -- This procedure enables it.

    After you invoke `LBACSYS.CONFIGURE_OLS`, all pending transactions are committed and cannot be rolled back, in the event that `LBACSYS.CONFIGURE_OLS` fails.
4.  Connect as user `SYS` with the `SYSOPER` privilege.
        CONNECT SYS AS SYSOPER -- Or, CONNECT SYS@hrpdb AS SYSOPER
        Enter password: password
5.  Restart the database.
    For example:

        SHUTDOWN IMMEDIATE
        STARTUP

**Parent topic:** Registering Oracle Label Security with an Oracle Database

#### 4.1.4 Registering and Enabling Oracle Label Security Using DBCA

You can both register and enable Oracle Label Security using Database Configuration Assistant.

1.  Start Database Configuration Assistant (DBCA).
    - UNIX: Run the following command:

          $ORACLE_HOME/bin/dbca

    - Windows: From the Start menu, click All Programs. Then click Oracle - ORACLE_HOME, then Configuration and Migration Tools, and then Database Configuration Assistant.

    The Welcome screen appears.
2.  Click Next.
    The Operations screen appears.
3.  Select Configure Database Options. Click Next.
    The Database screen appears.
4.  From the list, select the database where you need to configure and enable OLS. Click Next.
    The Database Content screen appears.
5.  Select Oracle Label Security. Click Next.
    The Connection Mode screen appears.
6.  Select either Dedicated Server Mode or Shared Server Mode. Click Finish.
    A dialog box is displayed informing you that the operation will require the database to be restarted.
7.  Click OK.
    A confirmation dialog box is displayed.
8.  Click OK.
    The DBCA progress screen is displayed.
9.  After the operation is complete, you are prompted to perform another operation. Click No to exit DBCA.

**Parent topic:** Registering Oracle Label Security with an Oracle Database

### 4.2 Security Guideline for Managing the LBACSYS User and the LBAC_DBA Role

As a good practice, for day-to-day use, grant the `LBAC_DBA` database role to trusted users who will administer Oracle Label Security.

If you plan to use Enterprise Manager Cloud Control to administer Oracle Label Security, then ensure that any users to whom you have granted the `LBAC_DBA` role also have the `SELECT ANY DICTIONARY` privilege.

Oracle strongly recommends that you maintain two accounts for users who have been granted the `LBAC_DBA` role. One account, the primary user account, will be used on a day-to-day basis and the other account will be used as a backup account in case the password of the primary account is lost and must be reset.

**Parent topic:** Registering and Logging in to Oracle Label Security

### 4.3 Logging in to Cloud Control or SQL\*Plus for Oracle Label Security

After you complete the Oracle Label Security registration and enablement process, you can begin using it.

- Logging in to Oracle Label Security from Enterprise Manager Cloud Control
  From Enterprise Manager Cloud Control, you use the Oracle Label Security pages to create and manage Oracle Label Security policies.
- Logging in to Oracle Label Security from SQL\*Plus
  You can log in to Oracle Label Security from SQL\*Plus if you have been granted the `LBAC_DBA` database role.

**Parent topic:** Registering and Logging in to Oracle Label Security

#### 4.3.1 Logging in to Oracle Label Security from Enterprise Manager Cloud Control

From Enterprise Manager Cloud Control, you use the Oracle Label Security pages to create and manage Oracle Label Security policies.

1.  Ensure that you have configured the Cloud Control target databases that you plan to use with Oracle Label Security.
    See the Oracle Enterprise Manager online help for more information about configuring target databases.
2.  Point your browser to the Cloud Control login page.
    For example:

        https://myserver.example.com:7799/em
3.  Log into Cloud Control as user `SYSMAN`.
4.  In the Cloud Control home page, from the Targets menu, select Databases.
5.  In the Databases page, select the link for the database to which you want to connect.
    The Database home page appears.
6.  From the Security menu, select Label Security.
    The Database Login page appears.
7.  Enter the following information:
    - Username: Enter the user name of a user who has been granted the `LBAC_DBA` database role, or enter `LBACSYS`.

    - Password: Enter the password.

    - Role: Select NORMAL from the list.

    - Save As: Select this check box if you want these credentials to be automatically filled in for you the next time that this page appears. The credentials are stored in Enterprise Manager in a secured manner. Access to these credentials depends on the user who is currently logged in.

**Parent topic:** Logging in to Cloud Control or SQL\*Plus for Oracle Label Security

#### 4.3.2 Logging in to Oracle Label Security from SQL\*Plus

You can log in to Oracle Label Security from SQL\*Plus if you have been granted the `LBAC_DBA` database role.

- To use Oracle Label Security from SQL\*Plus, connect as user `LBACSYS` or as a user who has been granted the `LBAC_DBA` database role. To find if a user has been granted this role, query the `GRANTEE` and `GRANTED_ROLE` columns of the `DBA_ROLE_PRIVS` data dictionary view.

For example:

    sqlplus psmith_ols -- Or, sqlplus psmith_ols@hrpdb for a PDB named hrpdb
    Enter password: password

To find the available PDBs, query the `DBA_PDBS` data dictionary view. To check the current PDB, run the `show con_name` command.

**Parent topic:** Logging in to Cloud Control or SQL\*Plus for Oracle Label Security
