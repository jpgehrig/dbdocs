You can perform rolling upgrades of Oracle Grid Infrastructure in batches.

You can use `root` user automation to automate running the `rootupgrade.sh` script during the upgrade. When you use `root` user automation, you can divide the nodes into groups, or batches, and start upgrades of these batches. Between batches, you can move services from nodes running the previous release to the upgraded nodes, so that services are not affected by the upgrade. Oracle recommends that you use `root` automation, and allow the `rootupgrade.sh` script to stop and start instances automatically. You can also continue to run `root` scripts manually.

When you upgrade Oracle Grid Infrastructure without using `root` user automation, you upgrade the entire cluster. You cannot select or de-select individual nodes for upgrade. Oracle does not support attempting to add additional nodes to a cluster during a rolling upgrade. Oracle recommends that you leave Oracle RAC instances running when upgrading Oracle Clusterware. When you start the `root` script on each node, the database instances on that node are shut down and then the `rootupgrade.sh` script starts the instances again.

### Restrictions for Selecting Nodes for Batch Upgrades

The following restrictions apply when selecting nodes in batches for upgrade:

- You can pool nodes in batches for upgrade, up to a maximum of three batches.

- The local node, where Oracle Universal Installer (OUI) is running, must be upgraded in batch one.

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
