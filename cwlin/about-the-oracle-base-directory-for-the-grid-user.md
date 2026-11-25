## About the Oracle Base Directory for the grid User

Review this information about creating the Oracle base directory on each cluster node.

The Oracle base directory for the Oracle Grid Infrastructure installation is the location where diagnostic and administrative logs, and other logs associated with Oracle ASM and Oracle Clusterware are stored. For Oracle installations other than Oracle Grid Infrastructure for a cluster, it is also the location under which an Oracle home is placed.

However, in the case of an Oracle Grid Infrastructure installation, you must create a different path, so that the path for Oracle bases remains available for other Oracle installations.

For OUI to recognize the Oracle base path, it must be in the form` u[``00-99``][00-99]/app`, and it must be writable by any member of the oraInventory (`oinstall`) group. The OFA path for the Oracle base is `u[00-99][00-99]/app/``user`, where user is the name of the software installation owner. For example:

    /u01/app/grid

**Note:**

Oracle home or Oracle base cannot be `symlinks`, nor can any of their parent directories, all the way to up to the `root` directory.

**Parent topic:** [Creating Groups, Users and Paths for Oracle Grid Infrastructure](creating-users-groups-paths-for-grid-infrastructure.md)
