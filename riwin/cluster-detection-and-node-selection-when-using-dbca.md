## Cluster Detection and Node Selection when Using DBCA

When you start Oracle Database Configuration Assistant (DBCA), it automatically shows options for Oracle RAC if it detects from the central Oracle Inventory that the Oracle Home is enabled for Oracle RAC.

If DBCA does not detect the Oracle home as an Oracle RAC home, check that the Oracle Universal Installer (OUI) inventory is correctly located in the directory `C:\Program Files\Oracle\Inventory`, and that the `oraInventory` file is not corrupted. Also, perform clusterware diagnostics by using the following CVU command syntax:

    Grid_home\bin\cluvfy\cluvfy.bat stage -post crsinst -n nodelist

When using DBCA, if nodes that are part of your cluster installation do not appear on the Node Selection page, then run the Opatch `lsinventory` command to perform inventory diagnostics. Also use CVU to perform clusterware diagnostics.

Example 3-4 Performing Clusterware Diagnostics If DCBA Fails To Detect A Two-Node Cluster

If the Grid Home is `D:\app\19.0.0\grid`, and the nodes are named `node1` and `node2`, then run the following command to perform clusterware diagnostics:

    D:\app\19.0.0\grid\bin> cluvfy stage -post crsinst -n node1,node2

**Parent topic:** [Selecting DBCA Options to Create an Oracle RAC or Oracle RAC One Node Database](creating-an-oracle-rac-or-oracle-rac-one-node-database-with-dbca.md)
