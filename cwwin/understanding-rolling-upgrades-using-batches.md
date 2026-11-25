## Understanding Rolling Upgrades Using Batches

Instead of shutting down all nodes when applying patches, you can shut down some nodes while other nodes remaining running.

When you upgrade Oracle Grid Infrastructure, you upgrade the entire cluster. You cannot select or de-select individual nodes for upgrade. Oracle does not support attempting to add additional nodes to a cluster during a rolling upgrade. Oracle recommends that you leave Oracle RAC instances running when upgrading Oracle Clusterware. When you start the upgrade process on each node, the upgrade scripts shut down the database instances and then start the instances again.

When performing the upgrade, you can divide the nodes into groups, or batches, and start upgrades of these node batches. Between batches, you can move services from nodes running the earlier release to the upgraded nodes, so that services are not affected by the upgrade.

### Restrictions for Selecting Nodes for Batch Upgrades

The following restrictions apply when selecting nodes in batches for upgrade:

- You can pool nodes in batches for upgrade, up to a maximum of three batches.

- The local node, where Oracle Universal Installer (OUI) is running, must be upgraded in batch one.

**Parent topic:** [Upgrading Oracle Grid Infrastructure](upgrading-oracle-grid-infrastructure.md)
