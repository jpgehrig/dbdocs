When Oracle Clusterware 12c Release 2 (12.2) or later releases are installed on a cluster with no previous Oracle software version, it configures the cluster nodes dynamically, which is compatible with Oracle Database Release 11.2 and later, but Oracle Database 10g and 11.1 require a persistent configuration.

This process of association of a node name with a node number is called pinning.

**Note:**

During an upgrade, all cluster member nodes are pinned automatically, and no manual pinning is required for existing databases. This procedure is required only if you install earlier database releases after installing Oracle Grid Infrastructure 12c Release 2 (12.2) or later release software.

To pin a node in preparation for installing or using an earlier Oracle Database release, use `Grid_home``/bin/crsctl` with the following command syntax, where `nodes` is a space-delimited list of one or more nodes in the cluster whose configuration you want to pin:

    crsctl pin css -n nodes

For example, to pin nodes `node3` and `node4`, log in as `root` and enter the following command:

    $ crsctl pin css -n node3 node4

To determine if a node is in a pinned or unpinned state, use `Grid_home``/bin/olsnodes` with the following command syntax:

To list all pinned nodes:

    olsnodes -t -n

For example:

    # /u01/app/12.1.0/grid/bin/olsnodes -t -n
    node1 1       Pinned
    node2 2       Pinned
    node3 3       Pinned
    node4 4       Pinned

To list the state of a particular node:

    olsnodes -t -n node3

For example:

    # /u01/app/12.1.0/grid/bin/olsnodes -t -n node3
    node3 3       Pinned

**See Also:**

[Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-control-crsctl-utility-reference.md) for more information about pinning and unpinning nodes

**Parent topic:** [Using Earlier Oracle Database Releases with Oracle Grid Infrastructure](using-earlier-oracle-database-releases-with-oracle-grid-infrastructure.md)
