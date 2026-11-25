## Understanding Out-of-Place and Rolling Upgrades

You can use rolling upgrade or out-of-place upgrades to upgrade your Oracle Grid Infrastructure software.

If you have an existing Oracle Grid Infrastructure installation, then you upgrade your existing cluster by performing an out-of-place upgrade. An in-place upgrade of Oracle Grid Infrastructure is not supported. All upgrades are out-of-place upgrades, meaning that the software binaries are placed in a different Grid home from the Grid home used for the prior release. You can also perform the upgrade in a rolling manner, which means there is always at least one cluster node operational during the upgrade.

### Rolling Upgrades

You can upgrade Oracle Grid Infrastructure by upgrading individual nodes without stopping Oracle Grid Infrastructure on other nodes in the cluster, which is called performing a **rolling upgrade**. Rolling upgrades avoid downtime and ensure continuous availability while the software is upgraded to a new release.

**Note:**

In contrast with releases prior to Oracle Clusterware 11g Release 2, Oracle Universal Installer (OUI) always performs rolling upgrades, even if you select all nodes for the upgrade.

### Out-of-Place Upgrades

During an out-of-place upgrade, the installer installs the newer release in a separate Grid home. Both the old and new releases of Oracle Grid Infrastructure exist on each cluster member node, but only one release is active. By contrast, an in-place upgrade overwrites the software in the current Oracle Grid Infrastructure home.

To perform an out-of-place upgrade, you must create new Oracle Grid Infrastructure homes on each node. Then you can perform an out-of-place rolling upgrade, so that some nodes run Oracle Grid Infrastructure from the original Grid home, and other nodes run Oracle Grid Infrastructure from the new Grid home.

**Related Topics**

- [Performing Rolling Upgrades of Oracle Grid Infrastructure](performing-rolling-upgrades-of-oracle-grid-infrastructure.md)

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
