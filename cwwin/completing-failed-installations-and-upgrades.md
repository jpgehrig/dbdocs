## Completing Failed Installations and Upgrades

Understand how to join nodes to the cluster after installation or upgrade fails on some nodes.

If installation or upgrade of Oracle Grid Infrastructure on some nodes fails, and you click Ignore to continue the installation, then the installation or upgrade completes on only some nodes in the cluster. Follow this procedure to add the failed nodes to the cluster.

1.  Remove the Oracle Grid Infrastructure software from the failed nodes:
        C:\>cd Grid_home\deinstall\deinstall -local
2.  As the installation user for Oracle Grid Infrastructure, from a node where Oracle Clusterware is installed, delete the failed nodes from the cluster using the `crsctl delete node` command:
        C:\>cd Grid_home\bin\crsctl delete node -n node_name

    where node_name is the node to be deleted.
3.  Run the Oracle Grid Infrastructure installation wizard.
        C:\>cd Grid_home\setup.exe

    After the installation wizard starts, choose the option Add more nodes to the cluster, then follow the steps in the wizard to add the nodes.

    Alternatively, you can also add the nodes by running the `addnode` script and specifying the nodes to add to the cluster:
        C:\>cd Grid_home\addnode\addnode.bat

The failed nodes are added to the cluster.

**Parent topic:** [Completing Failed or Interrupted Installations and Upgrades](completing-failed-or-interrupted-installations-and-upgrades.md)
