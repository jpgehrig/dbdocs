## Reviewing Component-Specific Installation Guidelines

Review the following guidelines before starting Oracle Universal Installer:

- Oracle Universal Installer

  Do not use Oracle Universal Installer from an earlier Oracle release to install components from this release.

- Oracle Automatic Storage Management

  In previous releases, Oracle Automatic Storage Management (Oracle ASM) was installed as part of the Oracle Database installation. With Oracle Database 11g Release 2 (11.2), Oracle Automatic Storage Management is part of an Oracle Grid Infrastructure installation, either for a cluster, or for a standalone server.

  If you want to upgrade an existing Oracle Automatic Storage Management installation, then you must upgrade Oracle Automatic Storage Management by running an Oracle Grid Infrastructure upgrade. If you do not have Oracle Automatic Storage Management installed and you want to use Oracle Automatic Storage Management as your storage option, then you must complete an Oracle Grid Infrastructure for a standalone server installation before you start your Oracle Database installation.

- Installations on a cluster

  If Oracle Clusterware or Oracle RAC is installed on the system, then Oracle Universal Installer displays the Grid Installation Options page. You must select Single instance database installation, unless you want to install Oracle RAC. The other options on the page are Oracle Real Application Clusters database installation and Oracle RAC One Node database installation.

  **See Also:**

  [Oracle Real Application Clusters Installation Guide for Linux and UNIX](../rilin/about-character-set-selection-during-installation.md)

**Parent topic:** [Installing Oracle Database](installing-oracle-database.md)
