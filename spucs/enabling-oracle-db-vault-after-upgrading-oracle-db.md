Depending on your target database release, you can be required to disable Oracle Database Vault to complete an Oracle Database upgrade.

- [Upgrading Oracle Database Without Disabling Oracle Database Vault](https://docs.oracle.com/en/database/oracle/oracle-database/19/spucs/unresolvable-reference.html)
  To upgrade to Oracle Database 12c Release 2 (12.2.0.1) or later releases, either grant the `DV_PATCH_ADMIN` role to `SYS` commonly in the root container, and revoke after the upgrade, or disable Oracle Database Vault and reenable it after upgrade.
- [Common Upgrade Scenarios with Oracle Database Vault](https://docs.oracle.com/en/database/oracle/oracle-database/19/spucs/unresolvable-reference.html)
  The requirements to enable Oracle Database Vault after upgrades change, depending on your source Oracle Database release.

**Parent topic:** [Preparing to Upgrade Oracle Database](preparing-to-upgrade.md)

### Upgrading Oracle Database Without Disabling Oracle Database Vault

To upgrade to Oracle Database 12c Release 2 (12.2.0.1) or later releases, either grant the `DV_PATCH_ADMIN` role to `SYS` commonly in the root container, and revoke after the upgrade, or disable Oracle Database Vault and reenable it after upgrade.

If Oracle Database Vault is enabled and you are upgrading an entire CDB, then use one of the following methods:

- CDB upgrade method 1: Temporarily grant the `DV_PATCH_ADMIN` to user `SYS` commonly by logging into the root container as a common user with the `DV_OWNER` role, and then issuing the `GRANT DV_PATCH_ADMIN TO SYS CONTAINER=ALL` statement. Oracle Database Vault controls will be in the same state as it was before the upgrade. When the upgrade is complete, log into the root container as the `DV_OWNER` user, and revoke the `DV_PATCH_ADMIN` role from `SYS` by issuing the `REVOKE DV_PATCH_ADMIN FROM SYS CONTAINER=ALL` statement.
- CDB upgrade method 2: Log into each container as a user who has the `DV_OWNER` role, and then run the `DBMS_MACADM.DISABLE_DV` procedure. You must first disable Oracle Database Vault on the PDBs, and then after that, disable Oracle Database Vault on the root container last. If you are upgrading only one PDB, then you can disable Oracle Database Vault in that PDB only. After you have completed the upgrade, you can enable Oracle Database Vault by logging into each container as the `DV_OWNER` user and then executing the `DVSYS.DBMS_MACADM.ENABLE_DV` procedure. The order of enabling Oracle Database Vault must be the root container first and PDBs afterward. You can enable the PDBs in any order, but the root container must be enabled first.

If you manually disable Oracle Database Vault before the upgrade, then you must enable Oracle Database Vault manually after the upgrade.

If you did not have Oracle Database Vault enabled before the upgrade, then you can enable it manually after the upgrade.

**Note:**

This procedure applies to non-CDB upgrades as well

**Related Topics**

- [Oracle Database - Overview of Database Patch Delivery Methods for 12.2.0.1 and greater (Doc ID 2337415.1)](https://support.oracle.com/rs?type=doc&id=2337415.1)
- [Disabling and Enabling Oracle Database Vault Oracle Database Vault Administrator’s Guide](../dvadm/disabling-and-enabling-oracle-database-vault.md)

### Common Upgrade Scenarios with Oracle Database Vault

The requirements to enable Oracle Database Vault after upgrades change, depending on your source Oracle Database release.

- Upgrades from Oracle Database 11g release 2 (11.2) or earlier: After the upgrade, Oracle Database Vault is disabled by default.

- Upgrades from Oracle Database 12c release 1 (12.1) or later: After the upgrade, Oracle Database Vault has the same enforcement status that you had in place before the upgrade.

Table 2-1 Common Oracle Database Vault Upgrade Scenarios and Upgrade Preparation Tasks

| Source Database Release     | Target Database Release | Do you need to disable Database Vault Before Upgrade | What is Database Vault Status After Upgrade                                              |
|:----------------------------|:------------------------|:-----------------------------------------------------|:-----------------------------------------------------------------------------------------|
| 11.2 or earlier             | 12.1                    | Yes                                                  | Disabled. You need to enable Database Vault manually after the upgrade.                  |
| 11.2.or earlier             | 12.2, 18.1 and later    | No                                                   | Disabled. You need to enable Database Vault manually after the upgrade.                  |
| 12.1, 12.2, 18.1, and later | 12.2, 18.1 and later    | No                                                   | Database Vault has the same enforcement status that you had in place before the upgrade. |
