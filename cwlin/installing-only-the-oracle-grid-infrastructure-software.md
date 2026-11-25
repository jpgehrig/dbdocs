## Installing Only the Oracle Grid Infrastructure Software

This installation option requires manual postinstallation steps to enable the Oracle Grid Infrastructure software.

If you use the Set Up Software Only option during installation, then Oracle Universal Installer (OUI) installs the software binaries on multiple nodes. You can then perform the additional steps of configuring Oracle Clusterware and Oracle ASM.

- [Installing Software Binaries for Oracle Grid Infrastructure for a Cluster](installing-software-binaries-for-oracle-grid-infrastructure-for-a-cluster.md)
  You can install Oracle Grid Infrastructure software binaries for a cluster software on multiple nodes at a time.
- [Configuring Software Binaries for Oracle Grid Infrastructure for a Cluster](configuring-software-binaries-for-oracle-grid-infrastructure-for-a-cluster.md)
  Configure the software binaries by starting Oracle Grid Infrastructure configuration wizard in GUI mode.
- [Configuring the Software Binaries Using a Response File](configuring-the-software-binaries-using-a-response-file.md)
  When you install or copy Oracle Grid Infrastructure software on any node, you can defer configuration for a later time. Review this procedure for completing configuration after the software is installed or copied on nodes, using the configuration wizard (`gridSetup.sh`).
- [Setting Ping Targets for Network Checks](setting-ping-targets-for-network-checks.md)
  Receive notification about network status by setting the `Ping_Targets` parameter during the Oracle Grid Infrastructure installation.

**See Also:**

[Oracle Clusterware Administration and Deployment Guide](../fppad/patching-and-upgrading-oracle-grid-infrastructure.md) for information about cloning an Oracle Grid Infrastructure installation to other nodes that were not included in the initial installation of Oracle Grid Infrastructure, and then adding them to the cluster

**Parent topic:** [Installing Oracle Grid Infrastructure](installing-oracle-grid-infrastructure.md)
