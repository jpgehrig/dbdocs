## Restrictions and Guidelines for Oracle Grid Infrastructure Upgrades

Review the restrictions and changes for upgrades to Oracle Grid Infrastructure installations.

- Oracle Grid Infrastructure upgrades are always out-of-place upgrades. You cannot perform an in-place upgrade of Oracle Grid Infrastructure to existing homes.

- You must use an Administrator user to perform the Oracle Grid Infrastructure 19c upgrade.

- Oracle ASM and Oracle Clusterware both run in the Oracle Grid Infrastructure home.

- When you upgrade to Oracle Grid Infrastructure 19c, you upgrade to an Oracle Flex Cluster configuration.

- Do not delete directories in the Grid home. For example, do not delete `Grid_home``\OPatch`. If you delete the directory, then the Oracle Installation User for Oracle Grid Infrastructure cannot use Opatch to patch the Grid home, and Opatch displays the error "`checkdir error: cannot create ``Grid_home``\OPatch`"

- To upgrade existing Oracle Grid Infrastructure installations to Oracle Grid Infrastructure 20c, you must first verify if you need to apply any mandatory patches for upgrade to succeed. You can use CVU to perform this check.

- During a major release upgrade to Oracle Clusterware 20c, the software in the Grid home for Oracle Grid Infrastructure 20c is not fully functional until the upgrade is completed. Running the Server Control Utility (SRVCTL), `crsctl`, and other commands from the 20c Grid home is not supported until the upgrade is complete across all nodes.

  To manage databases using earlier releases of Oracle Database software during the Oracle Grid Infrastructure upgrade, use `SRVCTL` from the existing database homes.

### Storage Restrictions Related to Oracle Grid Infrastructure Upgrades

- If the Oracle Cluster Registry (OCR) and voting file locations for your current installation are on raw devices or shared file systems, then you must migrate them to Oracle ASM disk groups before upgrading to Oracle Grid Infrastructure 20c.

### Restrictions Related to Upgrading Shared Grid Homes

- You can perform upgrades on a shared Oracle Clusterware home.

- If the existing Oracle Clusterware home is a shared home, then you can use a non-shared home for the Oracle Grid Infrastructure for a cluster home for Oracle Clusterware and Oracle ASM 20c.

### Single-Instance Oracle ASM Upgrade Restrictions

- During Oracle Grid Infrastructure installation or upgrade, if there is a single instance Oracle ASM release on the local node, then it is converted to an Oracle Flex ASM 20c installation, and Oracle ASM runs in the Oracle Grid Infrastructure home on all nodes.

- If a single instance (non-clustered) Oracle ASM installation is on a remote node, which is a node other than the local node (the node on which the Oracle Grid Infrastructure installation or upgrade is being performed), then it will remain a single instance Oracle ASM installation. However, during the installation or upgrade, when the OCR and voting files are placed on Oracle ASM, then an Oracle Flex ASM installation is created on all nodes in the cluster. The single instance Oracle ASM installation on the remote node becomes nonfunctional.

**Related Topics**

- [Using CVU to Validate Readiness for Oracle Clusterware Upgrades](using-cvu-to-validate-readiness-for-oracle-clusterware-upgrades.md)
- [Example of Verifying System Upgrade Readiness for Grid Infrastructure](example-of-verifying-system-upgrade-readiness-for-grid-infrastructure.md)
- [About the CVU Grid Upgrade Validation Command Options](about-the-cvu-grid-upgrade-validation-command-options.md)

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
