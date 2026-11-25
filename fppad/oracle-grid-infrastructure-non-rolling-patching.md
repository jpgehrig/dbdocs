## Patching Oracle Grid Infrastructure Using the Non-Rolling Method

You can use the `-nonrolling` parameter with the `rhpctl move gihome` command, which restarts the Oracle Grid Infrastructure stack on all nodes in parallel.

As with the rolling method, this is an atomic command which returns after all nodes are online.

**Note:**

The non-rolling patching method is available only if there is just one cluster node. If there are multiple nodes, then there is an error suggesting to use the rolling patching method.

- Use the following command to patch Oracle Grid Infrastructure in an non-rolling fashion:
      $ rhpctl move gihome –sourcewc Grid_home_1 –destwc Grid_home_2 -nonrolling

**Parent topic:** [Patching Oracle Grid Infrastructure](patching-oracle-grid-infrastructure.md)
