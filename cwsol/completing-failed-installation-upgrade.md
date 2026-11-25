Understand how to join nodes to the cluster after installation or upgrade fails on some nodes.

If installation or upgrade of Oracle Grid Infrastructure on some nodes fails, and the installation or upgrade completes with only successful nodes in the cluster, then follow this procedure to add the failed nodes to the cluster.

1.  Remove the Oracle Grid Infrastructure software from the failed nodes:
        Grid_home/deinstall/deinstall -local
2.  As the `root` user, from a node where Oracle Clusterware is installed, delete the failed nodes using the `delete node` command:
        Grid_home/bin/crsctl delete node -n node_name

    node_name is the node to be deleted.
3.  Run the Oracle Grid Infrastructure installation wizard and follow the steps in the wizard to add the nodes:
        Grid_home/gridSetup.sh

The nodes are added to the cluster.

**Parent topic:** [Completing Failed or Interrupted Installations and Upgrades](completing-failed-or-interrupted-installations-and-upgrades.md)
