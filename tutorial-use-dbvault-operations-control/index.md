## Before You Begin

This 15-minute tutorial shows you how to use Database Vault Operations Control to automatically restrict common users from accessing pluggable database (PDB) local data in autonomous, regular Cloud, or on-premise environments.

### Background

In Oracle Database 18c, Oracle Database Vault provides command rules and realms to protect sensitive data from users with system privileges and object privileges (mandatory realms). A command rule controls whether a particular SQL command can be executed for a given circumstance. A realm can prevent a user from accessing protected objects if the user is not authorized in the realm. This protection requires the creation and configuration of command rules or realms.

In Oracle Database 19c, Oracle Database Vault provides an extra layer of protection on the database objects. Database Vault Operations Control creates a wall between common users in databases and the customer database data that resides in the associated PDBs. Database Vault Operations Control prevents common users from accessing application local data that resides in PDBs. The capability allows you to store sensitive data for your business applications and manage the database without having to access the sensitive data in PDBs.

### What Do You Need?

- Oracle Database 19c installed
- A CDB and a PDB
- The ` `[`appdata.sh`](files/appdata.sh) shell script that creates the `HR.EMPLOYEES` table in `PDB1`. Download the shell script to the labs directory created on your server `/home/oracle/labs`.
- The ` `[`drop_create_user_sec_admin.sql`](files/drop_create_user_sec_admin.sql) SQL script that creates the Database Vault owner and the Database Vault account manager. Download the SQL script file to the labs directory created on your server `/home/oracle/labs`.

------------------------------------------------------------------------

## Create a Table in the PDB

1.  Execute the ` `[`appdata.sh`](files/appdata.sh) shell script to create the `HR.EMPLOYEES` table in `PDB1`. Update the password in the shell script if necessary.

        /home/oracle/labs/appdata.sh

2.  Check that the user `SYS` can read the `HR.EMPLOYEES` table rows in `PDB1`.

        SHOW CON_NAME

        CON_NAME
        ------------------------------
        PDB1

        SELECT count(*) FROM hr.employees;

        COUNT(*)
        ----------
               107

3.  Verify that neither Oracle Database Vault nor Database Vault Operations Control is configured in `PDB1`.

        SELECT * FROM dba_dv_status;

        NAME                           STATUS
        ------------------------------ --------------
        DV_APP_PROTECTION              NOT CONFIGURED
        DV_CONFIGURE_STATUS            FALSE
        DV_ENABLE_STATUS               FALSE

    `DV_APP_PROTECTION` status of `NOT CONFIGURED` means that Operations Control is not configured.

## Configure and Enable Database Vault in the CDB Root

In this section, you configure Database Vault at the CDB root level, ensuring that the `DV_OWNER` role is granted locally in the CDB root to the common Oracle Database Vault owner, `C##DVO`. Granting `DV_OWNER` locally prevents the CDB common user with `DV_OWNER` from changing containers or logging into PDBs with this role and changing customer DV controls.

1.  Log in to the CDB root as `SYS`.

        CONNECT / AS SYSDBA

2.  Execute the `/home/oracle/labs/drop_create_user_sec_admin.sql` SQL script that creates the Database Vault `C##DVO` owner and the Database Vault `C##DVA` account manager in the CDB root. Update the passwords in the SQL script if necessary.

        @/home/oracle/labs/drop_create_user_sec_admin.sql

3.  Configure Database Vault at the CDB root level ensuring that the `DV_OWNER` role is granted locally in the CDB root to the common Oracle Database Vault owner, `C##DVO`.

        exec DVSYS.CONFIGURE_DV ( dvowner_uname =>'c##dvo',-
                                  dvacctmgr_uname =>'c##dva', -
                                  force_local_dvowner => TRUE)

4.  Observe the Oracle Database Vault status in the CDB root. Oracle Database Vault is configured but Database Vault Operations Control is not configured.

        SELECT * FROM dba_dv_status;

        NAME                     STATUS
        ------------------------ --------------
        DV_APP_PROTECTION        NOT CONFIGURED
        DV_CONFIGURE_STATUS      TRUE
        DV_ENABLE_STATUS         FALSE

5.  Observe the Oracle Database Vault status in `PDB1`.

        CONNECT sys@PDB1 AS SYSDBA
        Enter password: password

        SELECT * FROM dba_dv_status;

        NAME                     STATUS
        ------------------------ --------------
        DV_APP_PROTECTION        NOT CONFIGURED
        DV_CONFIGURE_STATUS      FALSE
        DV_ENABLE_STATUS         FALSE

6.  Check that the user `SYS` can still count the `HR.EMPLOYEES` table rows.

        SELECT count(*) FROM hr.employees;

        COUNT(*)
        ----------
               107

------------------------------------------------------------------------

## Enable Database Vault Operations Control

1.  In the CDB root, create a common user granted the `CREATE SESSION` and `SELECT ANY TABLE` privileges.

        CONNECT c##dva
        Enter password: password

        CREATE USER c##common IDENTIFIED BY password CONTAINER=ALL;

2.  Grant the `CREATE SESSION` and `SELECT ANY TABLE` privileges to the common user.

        CONNECT / AS SYSDBA

        GRANT create session, select any table TO c##common CONTAINER=ALL;

3.  Connect to `PDB1` as the common user. Verify that the common user can query the `HR.EMPLOYEES`.

        CONNECT c##common@PDB1
        Enter password: password

        SELECT count(*) FROM hr.employees;

        COUNT(*)
        ----------
               107

4.  Enable Database Vault Operations Control in the CDB root. First, enable Oracle Database Vault in the CDB root.

        CONNECT / AS SYSDBA

        EXEC dvsys.dbms_macadm.enable_app_protection
        BEGIN dvsys.dbms_macadm.enable_app_protection; END;
        *
        ERROR at line 1:
        ORA-47503: Database Vault is not enabled in CDB$ROOT or application root.
        ORA-06512: at "DVSYS.DBMS_MACADM", line 2811
        ORA-06512: at line 1

5.  Log in the CDB root as the Oracle Database Vault owner. Enable Oracle Database Vault in the CDB root.

        CONNECT c##dvo
        Enter password: password

        EXEC dvsys.dbms_macadm.enable_dv

6.  Restart the database instance to enforce DV configuration and enabling.

        CONNECT / AS SYSDBA

        SHUTDOWN IMMEDIATE

        STARTUP

    If the PDB is not automatically opened, open it.

        ALTER PLUGGABLE DATABASE pdb1 OPEN;

7.  Verify the Oracle Database Vault status in the CDB root. Oracle Database Vault is configured and enabled but Database Vault Operations Control is still not configured.

        SELECT * FROM dba_dv_status;

        NAME                     STATUS
        ------------------------ --------------
        DV_APP_PROTECTION        NOT CONFIGURED
        DV_CONFIGURE_STATUS      TRUE
        DV_ENABLE_STATUS         TRUE

8.  Log in to the CDB root as the common account with the `DV_OWNER` role to enable Database Vault Operations Control, even if the `DV_OWNER` role has been granted locally.

        CONNECT c##dvo
        Enter password: password

        EXEC dvsys.dbms_macadm.enable_app_protection

9.  Verify the Oracle Database Vault Operations Control status in the CDB root.

        CONNECT / AS SYSDBA

        SELECT * FROM dba_dv_status;

        NAME                     STATUS
        ------------------------ --------------
        DV_APP_PROTECTION        ENABLED
        DV_CONFIGURE_STATUS      TRUE
        DV_ENABLE_STATUS         TRUE

10. Verify the Oracle Database Vault Operations Control status in `PDB1`.

        CONNECT sys@PDB1 AS SYSDBA
        Enter password: password

        SELECT * FROM dba_dv_status;

        NAME                     STATUS
        ------------------------ --------------
        DV_APP_PROTECTION        ENABLED
        DV_CONFIGURE_STATUS      FALSE
        DV_ENABLE_STATUS         FALSE

    Observe that Oracle Database Vault Operations Control is enabled at the PDB level with its status inherited from the CDB root. Oracle Database Vault is not required to be configured and enabled in PDBs, but must be configured and enabled at the CDB root level.

------------------------------------------------------------------------

## Test Database Vault Operations Control

1.  Connect to `PDB1` as the common user. Verify that the common user cannot query the `HR.EMPLOYEES`.

        CONNECT c##common@PDB1
        Enter password: password

        SELECT * FROM hr.employees;
        SELECT * FROM hr.employees
                         *
        ERROR at line 1:
        ORA-01031: insufficient privileges

------------------------------------------------------------------------

## Complete Administrative Tasks in PDBs

In this section, you back up the PDB although Oracle Database Vault Operations Control is enabled. Because database patching, backing up, restoring, and upgrading do not touch customer schemas, DBAs and privileged common users can still run tools as `SYSDBA` to patch the database (with `DV_PATCH_ADMIN` granted commonly in the CDB root), backup, restore, and upgrade the database although Oracle Database Vault Operations Control is enabled.

1.  Grant the `SYSDBA` privilege to the common user in `PDB1`.

        CONNECT sys@PDB1 AS SYSDBA
        Enter password: password

        GRANT sysdba TO c##common;

2.  Quit the session.

        EXIT

3.  Use RMAN to back up `PDB1`. Connect as the common user to `PDB1`.

        rman target c##common@PDB1
        target database Password: password

        BACKUP DATABASE;

    Although common users cannot query application data in PDBs, they can still complete administrative tasks for which they are granted privileges.

4.  Quit the RMAN session.

        exit

------------------------------------------------------------------------

## Add Users in an Exception List to Allow Them Operations in PDBs

In this section, you will maintain the exception list of common users and packages so that the tasks that need to be completed by common users can be completed despite the Database Vault Operations Control enabled. These common users are automation accounts, not used by humans.

`HR` application data in `PDB1` is very sensitive and should be protected against common users in the CDB. Nevertheless, the `C##REPORT` common user should be able to access some of the `HR` application information in `PDB1` to generate statistics for Human Resources.

1.  Log in as the common user who has been granted the `DV_ACCTMGR` role to create the common user `C##REPORT`.

        sqlplus c##dva
        Enter password: password

        CREATE USER c##report IDENTIFIED BY password CONTAINER=ALL;

2.  Grant the `CREATE SESSION` and `SELECT ANY TABLE` privileges to `C##REPORT`.

        CONNECT / AS SYSDBA

        GRANT create session, select any table TO c##report CONTAINER=ALL;

3.  Connect as the common user in `PDB1` and check if the common user can query the application data in `PDB1`.

        CONNECT c##report@PDB1
        Enter password: password

        SELECT count(*) FROM hr.employees;
        SELECT count(*) FROM hr.employees
        *
        ERROR at line 1:
        ORA-01031: insufficient privileges

    The behavior is expected because Oracle Database Vault Operations Control is enabled.

4.  Add the user to the exception list of users and packages allowed to access local data in `PDB1`. This operation can only be completed in the CDB root.

        CONNECT c##dvo
        Enter password: password

5.  Query the exception list.

        SELECT * FROM DVSYS.DBA_DV_APP_EXCEPTION;

        OWNER          PACKAGE
        -------------- --------------
        C##REPORT      %

    Automation accounts frequently have procedure or functions that need to access local data. In this case, include the package name so that only the package name can access local data and not someone who has stolen the credentials and runs SQL statements.

6.  Re-connect as the common user in `PDB1` and check that the common user can query the application data in `PDB1`.

        CONNECT c##report@PDB1
        Enter password: password

        SELECT count(*) FROM hr.employees;

        COUNT(*)
        ----------
               107

------------------------------------------------------------------------

## Clean Up the Environment

1.  Disable Database Vault Operations Control.

        CONNECT c##dvo
        Enter password: password

        EXEC dvsys.dbms_macadm.disable_app_protection

2.  Drop the `HR` schema in `PDB1`.

        CONNECT c##dva@PDB1
        Enter password: password

        DROP USER hr CASCADE;

3.  Revoke the `SYSDBA` privilege from the common user in `PDB1`.

        CONNECT sys@PDB1 AS SYSDBA
        Enter password: password

        REVOKE sysdba FROM c##common;

4.  Drop the `C##COMMON` user in the CDB.

        CONNECT c##dva
        Enter password: password

        DROP USER c##common CASCADE;

5.  Drop the `C##REPORT` user in the CDB.

        DROP USER c##report CASCADE;

6.  Quit the session.

        EXIT

------------------------------------------------------------------------
