## Requirements for the Oracle Grid Infrastructure Home Directory

Review directory path requirements for the Oracle Grid Infrastructure Home directory.

- It is located in a path outside existing Oracle homes, including Oracle Clusterware homes.

- It is not located in a user home directory.

- You create the path before installation, and then the installer for Oracle Grid Infrastructure creates the directories in the path.

Oracle recommends that you install Oracle Grid Infrastructure on local homes, rather than using a shared home on shared storage.

For installations with Oracle Grid Infrastructure only, Oracle recommends that you create a path compliant with Oracle Optimal Flexible Architecture (OFA) guidelines, so that Oracle Universal Installer (OUI) can select that directory during installation.

**Note:**

Oracle Grid Infrastructure homes can be placed in a local directory on servers, even if your existing Oracle Clusterware home from a prior release is in a shared location.

If you are installing Oracle Grid Infrastructure for a Standalone Server (Oracle Restart), then the home directory for Oracle Restart can be under the Oracle base directory for the Oracle Installation user for Oracle Database.

**Related Topics**

- [Optimal Flexible Architecture File Path Examples](optimal-flexible-architecture-file-path-examples.md)
- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/install-configure-oracle-grid-infrastructure-standalone-server.md)

**Parent topic:** [Creating Oracle Software Directories](creating-oracle-software-directories.md)
