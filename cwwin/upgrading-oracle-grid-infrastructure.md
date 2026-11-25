## 11 Upgrading Oracle Grid Infrastructure

Oracle Grid Infrastructure upgrade consists of upgrade of Oracle Clusterware and Oracle Automatic Storage Management (Oracle ASM).

Oracle Grid Infrastructure upgrades can be rolling upgrades, in which a subset of nodes are brought down and upgraded while other nodes remain active. Starting with Oracle ASM 11g Release 2 (11.2), Oracle ASM upgrades can be rolling upgrades.

You can also use Oracle Fleet Patching and Provisioning to upgrade Oracle Grid Infrastructure for a cluster.

- [Understanding Out-of-Place and Rolling Upgrades](understanding-out-of-place-and-rolling-upgrades.md)
  You can use rolling upgrade or out-of-place upgrades to upgrade your Oracle Grid Infrastructure software.
- [About Oracle Grid Infrastructure Upgrade and Downgrade](about-oracle-grid-infrastructure-and-oracle-asm-upgrade-and-downgrade.md)
  There are different methods you can use to upgrade the Oracle Grid Infrastructure software.
- [Options for Oracle Grid Infrastructure Upgrades](options-for-oracle-grid-infrastructure-upgrades-and-downgrades.md)
  When you upgrade to Oracle Grid Infrastructure 19c, you upgrade to an Oracle Flex Cluster configuration.
- [Restrictions and Guidelines for Oracle Grid Infrastructure Upgrades](restrictions-and-guidelines-for-oracle-grid-infrastructure-upgrades.md)
  Review the restrictions and changes for upgrades to Oracle Grid Infrastructure installations.
- [Preparing to Upgrade an Existing Oracle Clusterware Installation](preparing-to-upgrade-an-existing-oracle-clusterware-installation.md)
  If you have an existing Oracle Clusterware installation, then you upgrade your existing cluster by performing an out-of-place upgrade. You cannot perform an in-place upgrade.
- [Understanding Rolling Upgrades Using Batches](understanding-rolling-upgrades-using-batches.md)
  Instead of shutting down all nodes when applying patches, you can shut down some nodes while other nodes remaining running.
- [Performing Rolling Upgrades of Oracle Grid Infrastructure](performing-rolling-upgrades-of-oracle-grid-infrastructure.md)
  Review this information to perform rolling upgrade of Oracle Grid Infrastructure.
- [Applying Patches to Oracle Grid Infrastructure](applying-patches-to-oracle-grid-infrastructure.md)
  After you have upgraded Oracle Grid Infrastructure 19c, you can install individual software patches by downloading them from My Oracle Support.
- [Updating Oracle Enterprise Manager Cloud Control Target Parameters](updating-oracle-enterprise-manager-cloud-control-target-parameters.md)
  After upgrading Oracle Grid Infrastructure, upgrade the Enterprise Manager Cloud Control target.
- [Checking Cluster Health Monitor Repository Size After Upgrading](checking-cluster-health-monitor-repository-size-after-upgrading.md)
  If you are upgrading Oracle Grid Infrastructure from a prior release using IPD/OS to the current release, then review the Cluster Health Monitor repository size (the CHM repository).
- [Downgrading Oracle Clusterware to an Earlier Release](downgrading-oracle-clusterware-after-an-upgrade.md)
  After a successful or a failed upgrade, you can restore Oracle Clusterware to the previous release.
- [Completing Failed or Interrupted Installations and Upgrades](completing-failed-or-interrupted-installations-and-upgrades.md)
  If Oracle Universal Installer (OUI) exits on the node from which you started the installation or upgrade (the first node), or the node reboots before you confirm that the `gridconfig.bat` script was run on all cluster nodes, then the upgrade or installation remains incomplete.

**Related Topics**

- [General Upgrade Best Practices](general-upgrade-best-practices.md)
