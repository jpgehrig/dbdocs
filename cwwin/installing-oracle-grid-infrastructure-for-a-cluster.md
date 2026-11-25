## 9 Installing Oracle Grid Infrastructure for a Cluster

Review this information for installation and deployment options for Oracle Grid Infrastructure.

Oracle Grid Infrastructure consists of Oracle Clusterware and Oracle Automatic Storage Management (Oracle ASM). If you plan afterward to install Oracle Database with Oracle Real Application Clusters (Oracle RAC), then this is phase one of a two-phase installation.

Oracle Database and Oracle Grid Infrastructure installation software is available in multiple media, and can be installed using several options. The Oracle Grid Infrastructure software is available as an image, available for download from the Oracle Technology Network website, or the Oracle Software Delivery Cloud portal. You may use the Graphical User Interface (GUI) mode, or the silent mode to set up Oracle Grid Infrastructure.

- [About Image-Based Oracle Grid Infrastructure Installation](about-image-based-oracle-grid-infrastructure-installation.md)
  Starting with Oracle Grid Infrastructure 12c Release 2 (12.2), installation and configuration of Oracle Grid Infrastructure software is simplified with image-based installation.
- [Setup Wizard Installation Options for Creating Images](setup-wizard-installation-options.md)
  Before you start the setup wizards for your Oracle Database or Oracle Grid Infrastructure installation, decide if you want to use any of the available image-creation options.
- [Understanding Cluster Configuration Options](understanding-cluster-configuration-options.md)
  Review these topics to understand the cluster configuration options available in Oracle Grid Infrastructure 19c.
- [About Default File Permissions Set by Oracle Universal Installer](about-default-file-permissions-set-by-oracle-universal-installer.md)
  Oracle Grid Infrastructure is installed in the `ORACLE_HOME` directory, by default. Oracle Universal Installer sets the permissions for this directory, and for all files and directories under this directory.
- [Installing Oracle Grid Infrastructure for a New Cluster](installing-oracle-grid-infrastructure-for-a-new-cluster.md)
  Complete this procedure to install Oracle Grid Infrastructure (Oracle Clusterware and Oracle ASM) on your cluster.
- [Installing Oracle Grid Infrastructure Using a Cluster Configuration File](intsalling-oracle-grid-infrastructure-using-a-cluster-configuration-file.md)
  During installation of Oracle Grid Infrastructure, you have the option of either providing cluster configuration information manually, or using a cluster configuration file.
- [Installing Software Binaries for Oracle Grid Infrastructure for a Cluster](installing-software-binaries-for-oracle-grid-infrastructure.md)
  If you use the Set Up Software Only option during installation, then Oracle Universal Installer (OUI) installs the software binaries on multiple nodes. You can then perform the additional steps of configuring Oracle Clusterware and Oracle ASM.
- [Configuring the Software Binaries for Oracle Grid Infrastructure for a Cluster](configuring-software-binaries-for-oracle-grid-infrastructure.md)
  Configure the software binaries by starting Oracle Grid Infrastructure configuration wizard in GUI mode.
- [Configuring the Software Binaries Using a Response File](configuring-the-software-binaries-using-a-response-file.md)
  When you install or copy Oracle Grid Infrastructure software on any node, you can defer configuration for a later time using the Grid Setup Wizard utility (`setup.exe`).
- [Setting Ping Targets for Network Checks](setting-ping-targets-for-network-checks.md)
  Receive notification about the status of public networks by setting the `Ping_Targets` parameter during the Oracle Grid Infrastructure installation.
- [Confirming Oracle Clusterware Function](confirming-oracle-clusterware-function.md)
  After installation, use the `crsctl` utility to verify Oracle Clusterware installation is installed and running correctly.
- [Confirming Oracle ASM Function for Oracle Clusterware Files](confirming-oracle-asm-function-for-oracle-clusterware-files.md)
  Confirm Oracle ASM is running after installing Oracle Grid Infrastructure.
- [Understanding Offline Processes in Oracle Grid Infrastructure](understanding-offline-processes-in-oracle-grid-infrastructure.md)
  Oracle Grid Infrastructure provides required resources for various Oracle products and components. Some of those products and components are optional, so you can install and enable them after installing Oracle Grid Infrastructure.
