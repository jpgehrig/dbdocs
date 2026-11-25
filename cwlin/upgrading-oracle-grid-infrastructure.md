## 11 Upgrading Oracle Grid Infrastructure

Oracle Grid Infrastructure upgrade consists of upgrade of Oracle Clusterware and Oracle Automatic Storage Management (Oracle ASM).

Oracle Grid Infrastructure upgrades can be rolling upgrades, in which a subset of nodes are brought down and upgraded while other nodes remain active. Starting with Oracle ASM 11g Release 2 (11.2), Oracle ASM upgrades can be rolling upgrades.

You can also use Oracle Fleet Patching and Provisioning to upgrade Oracle Grid Infrastructure for a cluster.

- [Understanding Out-of-Place Upgrade](understanding-out-of-place-upgrades.md)
  With an out-of-place upgrade, the installer installs the newer version in a separate Oracle Clusterware home.
- [About Oracle Grid Infrastructure Upgrade and Downgrade](about-oracle-grid-infrastructure-upgrade.md)
  You have the ability to upgrade or downgrade Oracle Grid Infrastructure to a supported release.
- [Options for Oracle Grid Infrastructure Upgrades](options-for-oracle-grid-infrastructure-upgrades-and-downgrades.md)
  When you upgrade to Oracle Grid Infrastructure 19c, you upgrade to an Oracle Flex Cluster configuration.
- [Restrictions for Oracle Grid Infrastructure Upgrades](restrictions-for-oracle-grid-infrastructure-upgrades.md)
  Review the following information for restrictions and changes for upgrades to Oracle Grid Infrastructure installations, which consists of Oracle Clusterware and Oracle Automatic Storage Management (Oracle ASM).
- [Preparing to Upgrade an Existing Oracle Clusterware Installation](preparing-to-upgrade-an-existing-oracle-clusterware-installation.md)
  If you have an existing Oracle Clusterware installation, then you upgrade your existing cluster by performing an out-of-place upgrade. You cannot perform an in-place upgrade.
- [Understanding Rolling Upgrades Using Batches](understanding-rolling-upgrades-using-batches.md)
  You can perform rolling upgrades of Oracle Grid Infrastructure in batches.
- [Performing Rolling Upgrade of Oracle Grid Infrastructure](performing-rolling-upgrade-of-oracle-grid-infrastructure.md)
  Review this information to perform rolling upgrade of Oracle Grid Infrastructure.
- [About Upgrading Oracle Grid Infrastructure Using Oracle Fleet Patching and Provisioning](about-upgrading-grid-infrastructure-using-fleet-patching-and-provisioning.md)
  Oracle Fleet Patching and Provisioning (Oracle FPP) is a software lifecycle management method for provisioning and patching Oracle homes.
- [Applying Patches to Oracle Grid Infrastructure](applying-patches-to-oracle-asm.md)
  After you have upgraded Oracle Grid Infrastructure 19c, you can install individual software patches by downloading them from My Oracle Support.
- [Updating Oracle Enterprise Manager Cloud Control Target Parameters](updating-oracle-enterprise-manager-cloud-control-target-parameters.md)
  After upgrading Oracle Grid Infrastructure, upgrade the Enterprise Manager Cloud Control target.
- [Unlocking and Deinstalling the Previous Release Grid Home](unlocking-the-existing-oracle-clusterware-installation.md)
  After upgrading from previous releases, if you want to deinstall the previous release Oracle Grid Infrastructure home, then you must first change the permission and ownership of the previous release Grid home.
- [Checking Cluster Health Monitor Repository Size After Upgrading](checking-cluster-health-monitor-repository-size-after-upgrading.md)
  If you are upgrading Oracle Grid Infrastructure from a prior release using IPD/OS to the current release, then review the Cluster Health Monitor repository size (the CHM repository).
- [Downgrading Oracle Clusterware to an Earlier Release](downgrading-oracle-clusterware-after-an-upgrade.md)
  After a successful or a failed upgrade, you can restore Oracle Clusterware to the previous release.
- [Completing Failed or Interrupted Installations and Upgrades](completing-failed-or-interrupted-installations-and-upgrades.md)
  If Oracle Universal Installer (OUI) exits on the node from which you started the upgrade, or the node reboots before you confirm that the `rootupgrade.sh` script was run on all nodes, then the upgrade remains incomplete.

**Related Topics**

- [About Upgrading Oracle Grid Infrastructure Using Oracle Fleet Patching and Provisioning](about-upgrading-grid-infrastructure-using-fleet-patching-and-provisioning.md)
