The requirements to enable Oracle Database Vault after upgrades change, depending on your source Oracle Database release.

- Upgrades from Oracle Database 11g release 2 (11.2) or earlier: After the upgrade, Oracle Database Vault is disabled by default.

- Upgrades from Oracle Database 12c release 1 (12.1) or later: After the upgrade, Oracle Database Vault has the same enforcement status that you had in place before the upgrade.

Table 8-1 Common Oracle Database Vault Upgrade Scenarios and Upgrade Preparation Tasks

| Source Database Release     | Target Database Release | Do you need to disable Database Vault Before Upgrade | What is Database Vault Status After Upgrade                                              |
|:----------------------------|:------------------------|:-----------------------------------------------------|:-----------------------------------------------------------------------------------------|
| 11.2 or earlier             | 12.1                    | Yes                                                  | Disabled. You need to enable Database Vault manually after the upgrade.                  |
| 11.2.or earlier             | 12.2, 18.1 and later    | No                                                   | Disabled. You need to enable Database Vault manually after the upgrade.                  |
| 12.1, 12.2, 18.1, and later | 12.2, 18.1 and later    | No                                                   | Database Vault has the same enforcement status that you had in place before the upgrade. |

**Parent topic:** [Enabling Oracle Database Vault After Upgrading Oracle Database](enabling-oracle-db-vault-after-upgrading-oracle-db.md)
