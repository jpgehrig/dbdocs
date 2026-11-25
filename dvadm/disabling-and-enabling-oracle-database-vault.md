Periodically you must disable and then re-enable Oracle Database Vault, for activities such as installing Oracle Database optional products or features.

- When You Must Disable Oracle Database Vault
  You may need to disable Oracle Database Vault to perform upgrade tasks or correct erroneous configurations.
- Step 1: Disable Oracle Database Vault
  Be aware that after you disable Oracle Database Vault, Oracle Label Security, which is required to run Database Vault, is still enabled.
- Step 2: Perform the Required Tasks
  At this stage, Oracle Database Vault is disabled and you can perform the required tasks.
- Step 3: Enable Oracle Database Vault
  You can enable Oracle Database Vault and Oracle Label Security from SQL\*Plus.

### B.1 When You Must Disable Oracle Database Vault

You may need to disable Oracle Database Vault to perform upgrade tasks or correct erroneous configurations.

You can reenable Oracle Database Vault after you complete the corrective tasks.

To find the enablement and configuration status of Oracle Database Vault, see [Verifying That Database Vault Is Configured and Enabled](getting-started-with-oracle-database-vault.md).

The following situations require you to disable Oracle Database Vault:

- You must install any of the Oracle Database optional products or features, such as Oracle Spatial, by using Database Configuration Assistant (DBCA).

- If you did not configure backup `DV_OWNER` and `DV_ACCTMGR` accounts when you configured and enabled Oracle Database Vault, and these accounts are inadvertently locked or their passwords forgotten. Note that if your site only has one `DV_OWNER` user and this user has lost his or her password, you will be unable to disable Oracle Database Vault. However, if your site's only `DV_ACCTMGR` user has lost the password, you can disable Database Vault. As a best practice, you should grant the `DV_OWNER` and `DV_ACCTMGR` roles to new or existing user accounts, and use the Database Vault Owner and Account Manager accounts that you created when you configured and enabled Database Vault as back-up accounts. (See [Backup Oracle Database Vault Accounts](oracle-database-vault-schemas-roles-and-accounts.md) for a guideline for avoiding this problem in the future.)

- If you want to configure Oracle Internet Directory (OID) using Oracle Database Configuration Assistant (DBCA).

**Note:**

- Be aware that if you disable Oracle Database Vault, the privileges that were revoked from existing users and roles during configuration remain in effect. See [Privileges That Are Revoked from Existing Users and Roles](what-to-expect-after-you-enable-oracle-database-vault.md) for a listing of the revoked privileges.

- When Oracle Database Vault is disabled, there are some Database Vault features that you can still use.

- Oracle does not support the deinstallation of Oracle Database Vault.

**Parent topic:** Disabling and Enabling Oracle Database Vault

### B.2 Step 1: Disable Oracle Database Vault

Be aware that after you disable Oracle Database Vault, Oracle Label Security, which is required to run Database Vault, is still enabled.

1.  In SQL\*Plus, log in as the Oracle Database Owner (`DV_OWNER`) account, and then disable Oracle Database Vault.
        sqlplus psmith
        Enter password: password

        EXEC DBMS_MACADM.DISABLE_DV;
2.  In a multitenant environment, connect to the appropriate pluggable database (PDB).
    For example:

        CONNECT psmith@hrpdb
        Enter password: password

    To find the available PDBs, query the `DBA_PDBS` data dictionary view. To check the current PDB, run the `show con_name` command.
3.  Restart the database.
        CONNECT SYS AS SYSOPER -- Or, CONNECT SYS@hrpdb AS SYSOPER
        Enter password: password

        SHUTDOWN IMMEDIATE
        STARTUP
4.  For Oracle RAC installations, repeat these steps for each node on which the database is installed.

**Parent topic:** Disabling and Enabling Oracle Database Vault

### B.3 Step 2: Perform the Required Tasks

At this stage, Oracle Database Vault is disabled and you can perform the required tasks.

You can perform the following types of activities:

- Use the Oracle Database Vault PL/SQL packages and functions. For example, to correct a login or `CONNECT` rule set error, use the `DBMS_MACADM` PL/SQL package or the Oracle Database Vault pages in Enterprise Manager Cloud Control. Note that a CONNECT command rule cannot prevent a user who has the `DV_OWNER` or `DV_ADMIN` role from connecting to the database. This enables a Database Vault administrator to correct a misconfigured protection without having to disable Database Vault.

- Use the SYSTEM or SYS accounts to perform tasks such as creating or changing passwords, or locking and unlocking accounts. In addition to modifying standard database and administrative user accounts, you can modify passwords and the lock status of any of the Oracle Database Vault-specific accounts, such as users who have been granted the `DV_ADMIN` or `DV_ACCTMGR` roles. (See the tip under [Oracle Database Vault Accounts Created During Registration](oracle-database-vault-schemas-roles-and-accounts.md) for a guideline for avoiding this problem in the future.)

- Perform the installation or other tasks that require security protections to be disabled.

**Parent topic:** Disabling and Enabling Oracle Database Vault

### B.4 Step 3: Enable Oracle Database Vault

You can enable Oracle Database Vault and Oracle Label Security from SQL\*Plus.

1.  In SQL\*Plus, connect as the Oracle Database Owner (`DV_OWNER`) account, and then enable Database Vault.
    If you are enabling Database Vault from a non-multitenant environment or from a PDB:

        CONNECT psmith -- Or, CONNECT psmith@hrpdb for a PDB
        Enter password: password

        EXEC DBMS_MACADM.ENABLE_DV;

    If you are enabling Database Vault from the CDB root, for example:

        CONNECT c##sec_admin_owen
        Enter password: password

    Select from one of the following settings:

        EXEC DBMS_MACADM.ENABLE_DV (strict_mode => 'n');
         -- For regular mode
        EXEC DBMS_MACADM.ENABLE_DV (strict_mode => 'y');
         -- For strict mode
2.  Check if Oracle Label Security is enabled.
        SELECT VALUE FROM V$OPTION WHERE PARAMETER = 'Oracle Label Security';

    Oracle Label security must be enabled before you can use Database Vault. If it is not enabled, then this query returns `FALSE`.
3.  If Oracle Label Security is not enabled, then enable it.
        CONNECT SYS AS SYSDBA -- Or, CONNECT SYS@hrpdb AS SYSDBA
        Enter password: password

        EXEC LBACSYS.CONFIGURE_OLS;
        EXEC LBACSYS.OLS_ENFORCEMENT.ENABLE_OLS;
4.  Restart the database.
        CONNECT SYS AS SYSOPER -- Or, CONNECT SYS@hrpdb AS SYSOPER
        Enter password: password

        SHUTDOWN IMMEDIATE
        STARTUP
5.  For Oracle RAC installations, repeat these steps for each node on which the database is installed.

**Parent topic:** Disabling and Enabling Oracle Database Vault
