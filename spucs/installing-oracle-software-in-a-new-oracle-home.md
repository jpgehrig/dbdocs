Choose a new location for the target Oracle home, and then install the new Oracle Database release software for single-instance.

- [Choose a New Location for Oracle Home when Upgrading or Patching](https://docs.oracle.com/en/database/oracle/oracle-database/19/spucs/unresolvable-reference.html)
  When you upgrade or patch the database, you install the new Oracle home in a new location (an out-of-place upgrade or patch).
- [Installing the New Oracle Database Software for Single Instance](https://docs.oracle.com/en/database/oracle/oracle-database/19/spucs/unresolvable-reference.html)
  Use this procedure overview to assist you to install the software for the new Oracle Database release for a single instance deployment.

**Parent topic:** [Preparing to Upgrade Oracle Database](preparing-to-upgrade.md)

### Choose a New Location for Oracle Home when Upgrading or Patching

When you upgrade or patch the database, you install the new Oracle home in a new location (an out-of-place upgrade or patch).

AutoUpgrade performs out-of-place upgrades and patches. This means that the upgrade or the patched Oracle home is in a new Oracle home. Using separate installation locations enables you to keep your existing Oracle software installed along with the new Oracle software. By using separate installation locations, you can test the upgrade or patch process in the out-of-place Oracle home database before replacing your production environment entirely.

If you are upgrading a PDB by using an unplug/plug upgrade, then the target CDB into which you plug the PDB is the location for the PDB. Because the CDB is the target release, it is already in a new Oracle home for that release. There is no need to choose a new location for installing the target Oracle homes for the PDBs, because the target CDB already has its Oracle home.

**Related Topics**

- [How to Speed Up Your Database and GI Patching](https://mikedietrichde.com/2022/05/09/how-to-speed-up-your-database-and-gi-patching/)

### Installing the New Oracle Database Software for Single Instance

Use this procedure overview to assist you to install the software for the new Oracle Database release for a single instance deployment.

To install the new Oracle Database software for this release:

1.  Follow the instructions in your Oracle operating system-specific documentation to prepare for installation of Oracle Database software.

2.  Start Oracle Universal Installer, and select a software-only installation.

    When installation of Oracle Database software has completed successfully, click Exit to close Oracle Universal Installer.

3.  If you use Oracle Label Security, Oracle Database Vault, or both, then select Enterprise Edition on the Select Database Edition page, click Select Options, and enable one or both components from the components list.
