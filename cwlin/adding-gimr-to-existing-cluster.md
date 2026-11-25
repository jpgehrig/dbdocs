## Adding a Local GIMR to an Existing Cluster

You can add a local Grid Infrastructure Management Repository (GIMR) to an existing cluster if you did not create a GIMR as part of the Oracle Grid Infrastructure installation.

1.  As the `grid` user, create GIMR container database on any cluster node using the `mgmtca createGIMRContainer` command from the Grid home directory.
    - For Oracle Database 19c Release Update (19.6) or earlier releases:

          $ $ORACLE_HOME/bin/mgmtca createGIMRContainer [-storageDiskGroup disk_group_name]

    - For Oracle Database 19c Release Update (19.7) or later releases:

          $ $ORACLE_HOME/bin/mgmtca createGIMRContainer [-storageDiskLocation disk_location]

**Related Topics**

- [Using Remote GIMR for Oracle Standalone Cluster](using-remote-gimr-for-oracle-standalone-cluster.md)

**Parent topic:** [Oracle Grid Infrastructure Postinstallation Tasks](oracle-grid-infrastructure-postinstallation-tasks.md)
