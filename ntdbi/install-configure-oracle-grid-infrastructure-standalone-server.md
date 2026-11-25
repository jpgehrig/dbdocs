## 6 Installing and Configuring Oracle Grid Infrastructure for a Standalone Server

If you intend to use Oracle Automatic Storage Management (Oracle ASM), then you must install Oracle Restart before installing your database.

Oracle Grid Infrastructure for a standalone server is a version of Oracle Grid Infrastructure that supports single instance databases. This support includes volume management, file system, and automatic restart capabilities. Oracle Grid Infrastructure for a standalone server includes Oracle Restart and Oracle Automatic Storage Management. Oracle combined the two infrastructure products into a single set of binaries that is installed into an Oracle Restart home.

Oracle Restart is a feature provided as part of Oracle Grid Infrastructure. Oracle Restart monitors and can restart Oracle Database instances, Oracle Net Listeners, and Oracle ASM instances. Oracle Restart is currently restricted to manage single instance Oracle Databases and Oracle ASM instances only, and is subject to desupport in future releases. Oracle continues to provide Oracle ASM as part of the Oracle Grid Infrastructure installation for a standalone server and Cluster deployments.

Oracle Automatic Storage Management is a volume manager and a file system for Oracle Database files that supports single-instance Oracle Database and Oracle Real Application Clusters (Oracle RAC) configurations. Oracle Automatic Storage Management also supports a general purpose file system for your application needs, including Oracle Database binaries. Oracle Automatic Storage Management is Oracle's recommended storage management solution that provides an alternative to conventional volume managers and file systems.

Oracle Restart improves the availability of your Oracle database because of the following:

- When there is a hardware or a software failure, Oracle Restart automatically starts all Oracle components, including the Oracle database instance, Oracle Net Listener, database services, and Oracle ASM.

- Oracle Restart starts components in the proper order when the database host is restarted.

- Oracle Restart runs periodic checks to monitor the status of Oracle components. If a check operation fails for a component, then the component is shut down and restarted.

**Note:**

- You can neither install Oracle Restart on an Oracle Grid Infrastructure cluster member node, nor add an Oracle Restart server to an Oracle Grid Infrastructure cluster member node. Oracle Restart supports single-instance databases on one server, while Oracle Grid Infrastructure for a Cluster supports single-instance or Oracle RAC databases on a cluster.

- If you install Oracle Grid Infrastructure for a standalone server on a host computer on which a database already exists, then you must manually add the database, the listener, the Oracle ASM instance, and other components to the Oracle Restart configuration before you are able to configure automatic database restarts.

- You can use the Oracle Restart implementation of Oracle Grid Infrastructure only in single-instance (nonclustered) environments. Use Oracle Grid Infrastructure with Oracle Clusterware for clustered environments.

- Oracle Grid Infrastructure for a standalone server can support multiple single-instance databases on a single host computer.

<!-- -->

- [Requirements for an Oracle Restart Installation](requirements-for-an-oracle-grid-infrastructure-for-a-standalone-server-oracle-restart-installation.md)
  Before you install Oracle Restart, ensure that your system meets the following requirements:
- [Oracle ACFS and Oracle ADVM](oracle-acfs-and-oracle-advm.md)
  Oracle Automatic Storage Management Cluster File System (Oracle ACFS) extends Oracle ASM technology to support of all of your application data in both single instance and cluster configurations.
- [Oracle Automatic Storage Management Storage Configuration](oracle-automatic-storage-management-storage-configuration.md)
  Review the following sections for information on Oracle Automatic Storage Management (Oracle ASM) storage configuration:
- [About Upgrading Existing Oracle Automatic Storage Management Instances](upgrading-existing-oracle-asm-instances.md)
  Oracle Automatic Storage Management (Oracle ASM) upgrades are carried out during an Oracle Grid Infrastructure upgrade.
- [Configuring Oracle Automatic Storage Management Disk Groups Manually Using Oracle ASMCA](configuring-oracle-automatic-storage-management-disk-groups-manually-using-oracle-asmca.md)
  The Oracle Automatic Storage Management Configuration Assistant utility creates a new Oracle Automatic Storage Management instance if there is no Oracle Automatic Storage Management instance currently configured on this computer.
- [About Image-Based Oracle Grid Infrastructure Installation](about-image-based-oracle-grid-infrastructure-installation.md)
  Starting with Oracle Grid Infrastructure 12c Release 2 (12.2), installation and configuration of Oracle Grid Infrastructure software is simplified with image-based installation.
- [Setup Wizard Installation Options for Creating Images](setup-wizard-installation-options.md)
  Before you start the setup wizards for your Oracle Database or Oracle Grid Infrastructure installation, decide if you want to use any of the available image-creation options.
- [Installing Oracle Grid Infrastructure for a Standalone Server with a New Database Installation](installing-oracle-restart-with-a-new-database-installation.md)
  Complete these steps to install Oracle Restart and then create a database that is managed by Oracle Restart.
- [Installing Oracle Grid Infrastructure for a Standalone Server for an Existing Database](installing-oracle-restart-for-an-existing-database.md)
  Follow the high-level instructions in this section to install Oracle Grid Infrastructure and configure it for an existing Oracle database.
- [Installing Oracle Grid Infrastructure for a Standalone Server Using a Software-Only Installation](installing-oracle-grid-infrastructure-for-a-standalone-server-using-a-software-only-installation.md)
  A software-only installation only installs the Oracle Restart binaries at the specified location. You must complete a few manual configuration steps to enable Oracle Grid Infrastructure after you install the software.
- [Testing the Oracle Automatic Storage Management Installation](testing-the-oracle-automatic-storage-management-installation.md)
  After installing Oracle Grid Infrastructure for a single instance, use the ASMCMD command-line utility to test the Oracle ASM installation.
- [Modifying Oracle Grid Infrastructure for a Standalone Server Binaries After Installation](modifying-oracle-grid-infrastructure-for-a-standalone-server-binaries-after-installation.md)
  After installation, you must first stop the Oracle Restart stack to modify the software installed in your Grid home.

**See Also:**

[https://support.oracle.com/rs?type=doc&id=1584742.1](https://support.oracle.com/epmos/faces/DocumentDisplay?_afrLoop=258113192006335&id=1584742.1&displayIndex=1&_afrWindowMode=0&_adf.ctrl-state=kphwf35ym_4)
