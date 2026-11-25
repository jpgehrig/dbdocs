## Joining Inaccessible Nodes After Forcing an Upgrade

You can add inaccessible nodes to the cluster after a forced cluster upgrade.

Starting with Oracle Grid Infrastructure 12c release 1 (12.1), after you complete a force cluster upgrade command, you can join inaccessible nodes to the cluster as an alternative to deleting the nodes, which was required in earlier releases.

To use this option, you must already have Oracle Grid Infrastructure 19c software installed on the nodes.

1.  Log in as an Administrator user on the nodes that you want to join to the cluster.
2.  Change directory to the Oracle Grid Infrastructure 19c Grid_home directory.
    For example:

        C:\> cd C:\app\19.0.0\grid
3.  Run the following command, where upgraded_node is one of the cluster nodes that is upgraded successfully:
        C:\..\grid\> rootcrs.bat -join -existingnode upgraded_node

**Parent topic:** [Performing Rolling Upgrades of Oracle Grid Infrastructure](performing-rolling-upgrades-of-oracle-grid-infrastructure.md)
