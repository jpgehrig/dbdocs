## Requirements for Upgrading Databases That Use Oracle Label Security and Oracle Database Vault

You must complete these tasks before starting an upgrade with a database using Oracle Label Security or Oracle Database Vault.

- Audit Table Preupgrade and Archive Requirements
  For Oracle Database releases earlier than 12.1 using Oracle Label Security and Oracle Database Vault, you must run the OLS preprocess script before you upgrade.
- Preparing for Upgrades of Databases with Oracle Database Vault
  If the Oracle Database you plan to upgrade uses Oracle Database Vault, then you must disable Oracle Database Vault before starting the upgrade.
- Oracle Database Vault and Upgrades of Oracle Database Release 11.2
  If Oracle Label Security is installed in the earlier release that you are upgrading, then grant the DV_PATCH_ADMIN role to SYS.

**Parent topic:** [Preparing to Upgrade Oracle Database](tasks-prepare-upgrade-oracle-database.md)

### Audit Table Preupgrade and Archive Requirements

For Oracle Database releases earlier than 12.1 using Oracle Label Security and Oracle Database Vault, you must run the OLS preprocess script before you upgrade.

If you are upgrading from a database earlier than Oracle Database release 12.1 that uses Oracle Label Security (OLS) and Oracle Database Vault, then you must first run the OLS preprocess script, `olspreupgrade.sql`, to process the `aud$` table contents. The OLS upgrade moves the `aud$` table from the `SYSTEM` schema to the `SYS` schema. The `olspreupgrade.sql` script is a preprocessing script required for this move.

**Caution:**

Running the `olspreupgrade.sql` script before upgrading is mandatory for upgrading databases earlier than Oracle Database release 12.1 that use Oracle Label Security and Oracle Database Vault. Once you have upgraded to Oracle Database release 12.1, you do not have to perform the OLS preprocessing procedure going forward to patch or upgrade the database.

The `olspreupgrade.sql` script creates a temporary table `PREUPG_AUD$` in the `SYS` schema and moves the `SYSTEM.aud$` records to `SYS.PREUPG_AUD$`. As a safety measure, Oracle recommends that you archive your audit trail before running the `olspreupgrade.sql` script. If Oracle Label Security is installed on your database, and you are upgrading from an earlier release, then you must run the OLS preprocess script before upgrading.

**See Also:**

[Oracle Database Security Guide](../dbseg/administering-the-audit-trail.md) for information about archiving audit trails

[Oracle Label Security Administrator's Guide](../olsag/performing-dba-functions-under-oracle-label-security.md) for information about the OLS preprocess script

**Parent topic:** Requirements for Upgrading Databases That Use Oracle Label Security and Oracle Database Vault

### Preparing for Upgrades of Databases with Oracle Database Vault

If the Oracle Database you plan to upgrade uses Oracle Database Vault, then you must disable Oracle Database Vault before starting the upgrade.

During the upgrade process, if your source Oracle Database uses Oracle Database Vault, then you must first disable Oracle Database Vault before you start the upgrade.

You have two options you can use:

1.  Use a manual procedure: Log on as the common Database Vault (DV) administrator in the `CDB$ROOT `and grant the `DV_PATCH_ADMIN` role to `SYS`, or log in and disable Oracle Database Vault on every container. Procedures vary slightly, depending on your upgrade scenario. This procedure is described in My Oracle Support, "Requirement for Upgrading Database with Database Vault (Doc ID 2757126.1)".
2.  Download the latest AutoUpgrade Jar file, and perform the procedure described here.

With either option, when you run AutoUpgrade in Analyze mode, it detects that Oracle Database Vault is enabled, and indicates in its report that you must ensure the prerequisites for Oracle Database Vault and upgrade are met.

Example 2-7 AutoUpgrade Procedure for Databases Using Oracle Database Vault

When you use AutoUpgrade, and your database is configured with Oracle Database Vault, the upgrade procedure is as follows:

1.  Disable Oracle Database Vault.
2.  Install the new Oracle Database release.
3.  Download the latest AutoUpgrade JAR file from My Oracle Support note 2485457.1, and replace the AutoUpgrade JAR file in the new Oracle Database release, in the path `Oracle_home``/rdbms/admin`
4.  Run the AutoUpgrade utility (or Database Upgrade Assistant), and complete the upgrade.
5.  Enable Oracle Database Vault in the upgraded Oracle Database.

**Related Topics**

- [Disabling and Enabling Oracle Database Vault](../dvadm/disabling-and-enabling-oracle-database-vault.md)
- [Requirement for Upgrading Database with Database Vault (Doc ID 2757126.1)](https://support.oracle.com/rs?type=doc&amp;id=2757126.1)
- [AutoUpgrade Tool (Doc ID 2485457.1)](https://support.oracle.com/rs?type=doc&id=2485457.1)

**Parent topic:** Requirements for Upgrading Databases That Use Oracle Label Security and Oracle Database Vault

### Oracle Database Vault and Upgrades of Oracle Database Release 11.2

If Oracle Label Security is installed in the earlier release that you are upgrading, then grant the DV_PATCH_ADMIN role to SYS.

If Oracle Database Vault is not installed with your release 11.2 database, then you can skip steps 2, 3, 6, and 7 in this section.

To run the OLS preprocess script on a release 11.2 database before upgrading:

1.  Copy the following scripts script from the newly installed Oracle home to the Oracle home of the database that y0u want to upgrade:

    - `ORACLE_HOME``/rdbms/admin/olspreupgrade.sql`

    - `ORACLE_HOME``/rdbms/admin/emremove.sql`

    - `ORACLE_HOME``/rdbms/admin/catnoamd.sql`

2.  Start SQL\*Plus and connect as `DVOWNER` to the database that you want to upgrade.

3.  Run the following statement:

        SQL> GRANT DV_PATCH_ADMIN to SYS;

4.  At the system prompt, connect SYS as SYSDBA:

        CONNECT SYS AS SYSDBA

5.  Run the preprocess scripts for Data Vault

        ORACLE_HOME/rdbms/admin/olspreupgrade.sql
        ORACLE_HOME/rdbms/admin/emremove.sql
        ORACLE_HOME/rdbms/admin/catnoamd.sql

    You may continue to run your applications on the database while the preprocess scripts are running.

6.  After the `olspreupgrade.sql` completes its run successfully, start SQL\*Plus and connect to the database as `DVOWNER`.

7.  Run the following SQL statement:

        SQL> REVOKE DV_PATCH_ADMIN from SYS;

**Parent topic:** Requirements for Upgrading Databases That Use Oracle Label Security and Oracle Database Vault
