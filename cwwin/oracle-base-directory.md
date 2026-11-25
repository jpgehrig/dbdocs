## Oracle Base Directory for the Grid User

During installation, you are prompted to specify an Oracle base location, which is owned by the user performing the installation.

The Oracle base directory for the Oracle Grid Infrastructure installation is the location where diagnostic and administrative logs, and other logs associated with Oracle ASM and Oracle Clusterware are stored. For Oracle installations other than Oracle Grid Infrastructure for a cluster, it is also the location under which an Oracle home is placed. However, for an Oracle Grid Infrastructure installation, you must create a different path for the Grid home, so that the path for Oracle base remains available for other Oracle installations.

Multiple Oracle Database installations can use the same Oracle base directory. The Oracle Grid Infrastructure installation uses a different directory path, one outside of Oracle base. If you use different operating system users to perform the Oracle software installations, then each user will have a different default Oracle base location.

**Caution:**

After installing Oracle Database 12c release 1 (12.1) (or later) release with a Windows User Account as Oracle Home User, do not install older releases of Oracle Database that share the same Oracle Base Directory. During installation of the software for older releases, the ACLs are reset and Oracle Database 12c release 1 (12.1) (or later) services may not be able to access the Oracle Base directory and files.

In a default Windows installation, the Oracle base directory appears as follows, where X represents a disk drive and username is the name of the installation owner, which is also the name of the software installation owner:

    X:\app\username

Because you can have only one Oracle Grid Infrastructure installation on a cluster, and because all upgrades are out-of-place upgrades, Oracle recommends that you have an Oracle base for the Oracle Installation user for Oracle Grid Infrastructure (for example, `C:\app\grid`). You should also use a Grid home for the Oracle Grid Infrastructure binaries using the release number of that installation (for example, `C:\app\12.2.0\grid`).

During installation, ownership of the path to the Grid home is changed to the LocalSystem or Oracle Home user, if specified. Using separate paths for the Oracle base directory for the `grid` user and the Grid home directory means the path for Oracle base remains available for other Oracle software installations by the `grid` user. If you do not create a unique path to the Grid home, then after the Oracle Grid Infrastructure installation, you might encounter permission errors for other installations, including any existing installations under the same path.

**Caution:**

For Oracle Grid Infrastructure (for a cluster) installations, note the following restriction for the Oracle Grid Infrastructure home (the Grid home directory for Oracle Grid Infrastructure):

It must not be placed in the home directory of an installation owner.

These requirements are specific to Oracle Grid Infrastructure for a cluster installations. Oracle Grid Infrastructure for a standalone server (Oracle Restart) can be installed under the Oracle base for the Oracle Database installation.

**Note:**

Placing Oracle Grid Infrastructure for a cluster binaries on a cluster file system is not supported.

Oracle recommends that you install Oracle Grid Infrastructure locally, on each cluster member node. Using a shared Grid home prevents rolling upgrades, and creates a single point of failure for the cluster.

**Parent topic:** [About the Directories Used During Installation of Oracle Grid Infrastructure](about-the-directories-used-during-installation-of-oracle-grid-infrastructure.md)
