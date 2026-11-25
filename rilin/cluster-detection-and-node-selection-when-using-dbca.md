## Cluster Detection and Node Selection when Using DBCA

When you start DBCA, it automatically shows Oracle RAC options if it detects from the central Oracle Inventory that the Oracle home is enabled for Oracle RAC.

If DBCA does not automatically display Oracle RAC options, then DBCA was unable to detect if the Oracle home is installed on a cluster. In this case, check that the OUI inventory is correctly located in the directory `/etc/oraInst.loc`, and that the `oraInventory` file is not corrupted. Also, perform clusterware diagnostics by using the following CVU command syntax:

    /u01/app/19.0.0/grid/bin/cluvfy/cluvfy.sh stage -post crsinst -n nodelist

For example, with the mountpoint `/u01/app/19.0.0/grid`, and nodes `node1` and `node2`, run the following command:

    $ /u01/app/19.0.0/grid/bin/cluvfy stage -post crsinst -n node1,node2

Note that when using DBCA, if nodes that are part of your cluster installation do not appear on the Node Selection page, then run the Opatch `lsinventory` command to perform inventory diagnostics. Also use CVU to perform clusterware diagnostics.

On the Management Options page, you are provided options for managing the database, either with Oracle Enterprise Manager Database Express or Oracle Enterprise Manager Cloud Control. For Oracle RAC databases, Oracle Enterprise Manager Database Express is configured to connect to the cluster using the Single Client Access Name (SCAN).

**Parent topic:** [Selecting DBCA Options to Create an Oracle RAC or Oracle RAC One Node Database](creating-an-oracle-rac-or-oracle-rac-one-node-database-with-dbca.md)
