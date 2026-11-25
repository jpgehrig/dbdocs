Review the following information for restrictions and changes for upgrades to Oracle Grid Infrastructure installations, which consists of Oracle Clusterware and Oracle Automatic Storage Management (Oracle ASM).

- Oracle Grid Infrastructure upgrades are always out-of-place upgrades. You cannot perform an in-place upgrade of Oracle Grid Infrastructure to existing homes.

- The same user that owned the earlier release Oracle Grid Infrastructure software must perform the Oracle Grid Infrastructure 19c upgrade.

- Oracle ASM and Oracle Clusterware both run in the Oracle Grid Infrastructure home.

- When you upgrade to Oracle Grid Infrastructure 12c Release 2 (12.2) or later, you upgrade to an Oracle Flex Cluster configuration.

- Do not delete directories in the Grid home. For example, do not delete the directory Grid_home/OPatch. If you delete the directory, then the Grid infrastructure installation owner cannot use OPatch utility to patch the grid home, and OPatch displays the error message "'checkdir' error: cannot create Grid_home/OPatch".

- To upgrade existing Oracle Grid Infrastructure installations to Oracle Grid Infrastructure 19c, you must first verify if you need to apply any mandatory patches for upgrade to succeed.

  Oracle recommends that you use the Cluster Verification Utility tool (CVU) to check if there are any patches required for upgrading your existing Oracle Grid Infrastructure or Oracle RAC database installations. See Using CVU to Validate Readiness for Oracle Clusterware Upgrades for steps to check readiness.

- The software in the 19c Oracle Grid Infrastructure home is not fully functional until the upgrade is completed. Running `srvctl`, `crsctl`, and other commands from the new Grid homes are not supported until the final `rootupgrade.sh` script is run and the upgrade is complete across all nodes.

  To manage databases in existing earlier release database homes during the Oracle Grid Infrastructure upgrade, use the `srvctl` from the existing database homes.

- To upgrade existing Oracle Clusterware installations to Oracle Grid Infrastructure 19c cluster, your release must be greater than or equal to Oracle Grid Infrastructure 11g Release 2 (11.2.0.3).

**See Also:**

[Oracle Database Upgrade Guide](../upgrd/tasks-prepare-upgrade-oracle-database.md) for additional information about preparing for upgrades

### About Storage Restrictions for Upgrade

- If the Oracle Cluster Registry (OCR) and voting file locations for your current installation are on raw or block devices, or shared file systems, then you must migrate them to Oracle ASM disk groups, certified NAS device, or a shared file system before upgrading to Oracle Grid Infrastructure 19c.

- If you want to upgrade Oracle Grid Infrastructure releases before Oracle Grid Infrastructure 11g Release 2 (11.2), where the OCR and voting files are on raw or block devices, then you must upgrade to Oracle Grid Infrastructure 12c Release 1 (12.1), and move the Oracle Cluster Registry (OCR) and voting files to Oracle ASM or a shared file system, before you upgrade to Oracle Grid Infrastructure 19c.

### About Upgrading Shared Grid Homes

- If the existing Oracle Clusterware home is a shared home, then you can use a non-shared home for the Oracle Grid Infrastructure for a cluster home for Oracle Clusterware and Oracle ASM 19c.

- You can perform upgrades on a shared Oracle Clusterware home.

### About Single-Instance Oracle ASM Upgrade

- During Oracle Grid Infrastructure installation or upgrade, if there is a single instance Oracle ASM release on the local node, then it is converted to an Oracle Flex ASM 19c installation, and Oracle ASM runs in the Oracle Grid Infrastructure home on all nodes.

- If a single instance (non-clustered) Oracle ASM installation is on a remote node, which is a node other than the local node (the node on which the Oracle Grid Infrastructure installation or upgrade is being performed), then it remains a single instance Oracle ASM installation. However, during the installation or upgrade, when the OCR and voting files are placed on Oracle ASM, then an Oracle Flex ASM installation is created on all nodes in the cluster. The single instance Oracle ASM installation on the remote node becomes nonfunctional.

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
