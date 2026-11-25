## About Oracle Grid Infrastructure Upgrade and Downgrade

There are different methods you can use to upgrade the Oracle Grid Infrastructure software.

You can upgrade Oracle Grid Infrastructure in any of the following ways:

- Rolling Upgrade: Involves upgrading individual nodes without stopping Oracle Grid Infrastructure on other nodes in the cluster

- Non-Rolling Upgrade: Involves bringing down all the nodes except one. A complete cluster outage occurs while the root script stops the old Oracle Clusterware stack and starts the new Oracle Clusterware stack on the node where you initiate the upgrade. After upgrade is completed, the new Oracle Clusterware is started on all the nodes.

Note that some services are disabled when one or more nodes are in the process of being upgraded. All upgrades are **out-of-place upgrades**, meaning that the software binaries are placed in a different Grid home from the Grid home used for the prior release.

You can downgrade from Oracle Grid Infrastructure 19c to Oracle Grid Infrastructure 18c, Oracle Grid Infrastructure 12c Release 2 (12.2), and Oracle Grid Infrastructure 12c Release 1 (12.1). Be aware that if you downgrade to a prior release, then your cluster must conform with the configuration requirements for that prior release, and the features available for the cluster consist only of the features available for that prior release of Oracle Clusterware and Oracle ASM.

You can perform out-of-place upgrades to an Oracle ASM instance using ASMCA. In addition to running ASMCA using the graphical user interface, you can run ASMCA in non-interactive (silent) mode.

**Note:**

- If you are currently using OCFS for Windows as your shared storage, then you must migrate to using Oracle ASM during the upgrade of Oracle Database and Oracle Grid Infrastructure.

- You must complete an upgrade before attempting to use cluster backup files. You cannot use backups for a cluster that has not completed the upgrade.

**See Also:**

[Oracle Automatic Storage Management Administrator's Guide](../ostmg/upgrade-patch-asm.md) for additional information about upgrading existing Oracle ASM installations

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
