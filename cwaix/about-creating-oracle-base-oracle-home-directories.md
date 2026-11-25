Create Grid home and Oracle base home directories on each cluster node.

Oracle recommends that you create Oracle Grid Infrastructure Grid home and Oracle base homes manually, particularly if you have separate Oracle Grid Infrastructure for a cluster and Oracle Database software owners, so that you can separate log files for the Oracle Grid Infrastructure installation owner in a separate Oracle base, and prevent accidental placement of the Grid home under an Oracle base path. For example:

    # mkdir -p /u01/app/19.0.0/grid
    # mkdir -p /u01/app/grid
    # mkdir -p /u01/app/oracle
    # chown -R grid:oinstall /u01
    # chown oracle:oinstall /u01/app/oracle
    # chmod -R 775 /u01/

**Note:**

Placing Oracle Grid Infrastructure for a cluster binaries on a cluster file system is not supported.

If you plan to install an Oracle RAC home on a shared OCFS2 location, then you must upgrade OCFS2 to at least version 1.4.1, which supports shared writable `maps`.

Oracle recommends that you install Oracle Grid Infrastructure locally, on each cluster member node. Using a shared Grid home prevents rolling upgrades, and creates a single point of failure for the cluster.

Oracle home or Oracle base cannot be `symlinks`, nor can any of their parent directories, all the way to up to the `root` directory.

**Parent topic:** [Creating Groups, Users and Paths for Oracle Grid Infrastructure](creating-users-groups-paths-for-oracle-grid-infrastructure.md)
