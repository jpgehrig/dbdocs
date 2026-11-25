You can add a node to your two-node cluster by using Fleet Patching and Provisioning to add the node, and then extend an Oracle RAC database to the new node.

### Before You Begin

In this procedure, Oracle Grid Infrastructure 12c release 2 (12.2.0.1) is running on the cluster. Working copy `GI_HOME_12202_WCPY` is the active Grid home on this cluster.

The Oracle RAC database home runs on the working copy `DB_HOME_12202_WCPY`.

Ensure that you have storage, network, and operating system requirements configured for the new node as stated in Oracle Grid Infrastructure Installation Guide.

### Procedure

1.  From the Fleet Patching and Provisioning Server, run the following command to add a node to the existing Oracle Grid Infrastructure working copy:
        rhpctl addnode gihome -workingcopy GI_HOME_12202_WCPY -newnodes n3:n3-vip {authentication_option}

    The command extends the cluster by adding `node3`.
2.  Add instances to the administrator-managed Oracle RAC database on the new node:
        rhpctl addnode database -workingcopy DB_HOME_12202_WCPY -dbname db321 -node n3 {authentication_option}

    The command extends the database home on the `node3` and creates database `db321` on this node.

Watch a video

**Parent topic:** [Fleet Patching and Provisioning Use Cases](fleet-patching-and-provisioning-use-cases.md)
