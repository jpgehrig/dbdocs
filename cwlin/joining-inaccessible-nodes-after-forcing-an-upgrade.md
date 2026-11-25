## Joining Inaccessible Nodes After Forcing an Upgrade

Use this procedure to join inaccessible nodes after a force cluster upgrade.

Starting with Oracle Grid Infrastructure 12c, after you complete a force cluster upgrade, you can use the procedure described here to join inaccessible nodes to the cluster as an alternative to deleting the nodes, which was required in earlier releases. To use this option, you must already have Oracle Grid Infrastructure 19c software installed on the nodes.

1.  Log in as the `root` user on the node that you want to join to the cluster.

2.  Change directory to the Oracle Grid Infrastructure 19c `Grid_home` directory. For example:

        $ cd /u01/app/19.0.0/grid/

3.  Run the following command, where upgraded_node is one of the cluster nodes that is upgraded successfully:

        $ rootupgrade.sh -join -existingnode upgraded_node

**Parent topic:** [Performing Rolling Upgrade of Oracle Grid Infrastructure](performing-rolling-upgrade-of-oracle-grid-infrastructure.md)
