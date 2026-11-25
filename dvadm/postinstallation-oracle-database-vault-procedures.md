After you configure and enable Oracle Database Vault, you can perform specialized tasks, such as adding languages or uninstalling and reinstalling Oracle Database Vault.

- Adding Languages to Oracle Database Vault
  By default, Oracle Database Vault loads only the English language tables.
- Deinstalling Oracle Database Vault
  You can remove Oracle Database Vault from an Oracle Database installation, for both to both single-instance and Oracle RAC installations.
- Reinstalling Oracle Database Vault
  You can reinstall Oracle Database Vault by using Database Configuration Assistant and afterward, configure and enable Database Vault.

**Related Topics**

- [Converting a Standalone Oracle Database to a PDB and Plugging It into a CDB](dba-operations-in-an-oracle-database-vault-environment.md)

### C.1 Adding Languages to Oracle Database Vault

By default, Oracle Database Vault loads only the English language tables.

You can add more languages by running the `DBMS_MACADM.ADD_NLS_DATA` procedure for each new language that you want to add. You can add more than one language to Database Vault.

1.  Log into the database instance as a user who has been granted the `DV_OWNER` or `DV_ADMIN` role.
2.  Run the following procedure:
        EXEC DBMS_MACADM.ADD_NLS_DATA('language');

    You can specify the `language` setting using any case. For example:

        EXEC DBMS_MACADM.ADD_NLS_DATA('french');

        EXEC DBMS_MACADM.ADD_NLS_DATA('JAPANESE');

    Replace `language` with one of the following supported languages:

    - `ENGLISH`

    - `GERMAN`

    - `SPANISH`

    - `FRENCH`

    - `ITALIAN`

    - `JAPANESE`

    - `KOREAN`

    - `BRAZILIAN PORTUGUESE`

    - `SIMPLIFIED CHINESE`

    - `TRADITIONAL CHINESE`

**Parent topic:** Postinstallation Oracle Database Vault Procedures

### C.2 Deinstalling Oracle Database Vault

You can remove Oracle Database Vault from an Oracle Database installation, for both to both single-instance and Oracle RAC installations.

However, you cannot deinstall Database Vault from databases in a multitenant environment. This procedure only applies to legacy, non-CDB Oracle Database environments.

The deinstallation process does not affect the initialization parameter settings, even those settings that were modified during the installation process, nor does it affect Oracle Label Security.

1.  Log into the database instance as user `SYS` with the `SYSDBA` administrative privilege, or as user who has the `ALTER SYSTEM` system privilege.
    For example:

        sqlplus psmith -- Or, sqlplus psmith@hrpdb for a pluggable database (PDB)
        Enter password: password
2.  Ensure that the recycle bin is disabled.
        SHOW PARAMETER RECYCLEBIN
3.  If the recycle bin is on, then disable it using one of the following statements:
        ALTER SYSTEM SET RECYCLEBIN = OFF;

        ALTER SESSION SET recyclebin = OFF SCOPE = SPFILE;
4.  Connect as a user who has been granted the `DV_OWNER` or `DV_ADMIN` role.
    For example:

        CONNECT sec_admin_owen -- Or, CONNECT sec_admin_owen@hrpdb
        Enter password: password
5.  Run the following procedure to disable Oracle Database Vault:
        EXEC DBMS_MACADM.DISABLE_DV;
6.  Connect as `SYS` with the `SYSOPER` privilege and then restart the database.
    For example:

        CONNECT SYS AS SYSOPER -- Or, CONNECT SYS@hrpdb AS SYSOPER
        Enter password: password

        SHUTDOWN IMMEDIATE
        STARTUP

    For Oracle RAC installations, shut down and then restart each database instance as follows:

        srvctl stop database -db db_name
        srvctl start database -db db_name
7.  Run the `dvremov.sql` script to remove Oracle Database Vault.
    For example:

        $ORACLE_HOME/rdbms/admin/dvremov.sql
8.  If necessary, in SQL\*Plus, as user `SYS` with the `SYSDBA` administrative privilege, manually revoke the `EXECUTE` privilege on the `DBMS_RLS` PL/SQL package from any users who have been granted the `DV_OWNER` role.
    When you configure Oracle Database Vault, one of the privileges that `DV_OWNER`users are granted is this privilege. However, when you remove Oracle Database Vault, `DV_OWNER` users still have this privilege. Optionally, you can revoke it.
        REVOKE EXECUTE ON DBMS_RLS FROM dbv_owner_backup;

Afterward, you can double-check that Oracle Database Vault is truly deinstalled by logging in to SQL\*Plus and entering the following statement:

    SELECT * FROM V$OPTION WHERE PARAMETER = 'Oracle Database Vault';

If Oracle Database Vault is deinstalled, the following output appears:

    PARAMETER                     VALUE
    ----------------------------- -----------------------
    Oracle Database Vault         FALSE

**Parent topic:** Postinstallation Oracle Database Vault Procedures

### C.3 Reinstalling Oracle Database Vault

You can reinstall Oracle Database Vault by using Database Configuration Assistant and afterward, configure and enable Database Vault.

1.  Log into the database instance as user `SYS` with the `SYSDBA` administrative privilege.
        sqlplus sys as sysdba -- Or, sqlplus sys@hrpdb as sysdba
        Enter password: password
2.  Start Database Configuration Assistant (DBCA).
    - UNIX: Enter the following command in a shell window:

          dbca

    - Windows: Use one of the following methods to start DBCA on Windows:

      - Click Start, select Programs (or All Programs), then Oracle - HOME_NAME, then Configuration and Migration Tools, and then Database Configuration Assistant.

      - Enter the following command at a command prompt:

            dbca
3.  Use DBCA to configure Database Vault for either a new or an existing database.
4.  Configure and enable Oracle Database Vault.

**Related Topics**

- [Registering Database Vault Users](getting-started-with-oracle-database-vault.md)
- [Configuring and Enabling Oracle Database Vault with an Oracle Database in a Multitenant Environment](getting-started-with-oracle-database-vault.md)

**Parent topic:** Postinstallation Oracle Database Vault Procedures
