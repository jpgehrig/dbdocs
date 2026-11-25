## About Upgrading Existing Oracle Automatic Storage Management Instances

Oracle Automatic Storage Management (Oracle ASM) upgrades are carried out during an Oracle Grid Infrastructure upgrade.

If you are upgrading from Oracle ASM 11g Release 2 (11.2.0.4) or later, then Oracle ASM is always upgraded with Oracle Grid Infrastructure as part of the upgrade, and Oracle Automatic Storage Management Configuration Assistant (Oracle ASMCA) is started by the root scripts during upgrade. Subsequently, you can use Oracle ASMCA (located in `Grid_home/bin`) to configure failure groups, Oracle ASM volumes, and Oracle Automatic Storage Management Cluster File System (Oracle ACFS).

Oracle ASMCA cannot perform a separate upgrade of Oracle ASM from a prior release to the current release.

Upgrades of Oracle ASM from releases prior to 11g Release 2 (11.2) are not supported.

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/upgrade-patch-asm.md)
- [Oracle Database Upgrade Guide](../upgrd/recommended-and-best-practices-complete-upgrading-oracle-database.md)

**Parent topic:** [Supported Storage Options for Oracle Database and Oracle Grid Infrastructure](supported-storage-options-for-oracle-database-and-oracle-grid-infrastructure.md)
