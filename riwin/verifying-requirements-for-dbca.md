## Verifying Requirements for Oracle DBCA

Use Cluster Verification Utility (CVU) to verify that your system is prepared for configuration changes.

- Prior to using Oracle Database Configuration Assistant (Oracle DBCA) to change the database configuration, run Cluster Verification Utility (CVU) to verify that your system is prepared for configuration changes using the following command syntax:
      Grid_home\bin\cluvfy stage -pre dbcfg -n node_list -d Oracle_home [-verbose]

  In the preceding syntax example, the variable Grid_home is the Oracle Grid Infrastructure home, the variable node_list is the list of nodes in your cluster, separated by commas, and the variable Oracle_home is the path for the Oracle home directory where Oracle Universal Installer (OUI) creates or modifies the database.
  You can select the option `-verbose` to receive progress updates as CVU performs its system checks, and detailed reporting of the test results.

If the CVU summary indicates that the cluster verification check fails, then review and correct the relevant system configuration steps, and run the test again.

Example 3-3 Using CVU Prior to Verify Your System is Prepared for an Oracle RAC Installation

To verify that your system is prepared for an Oracle Database with Oracle RAC installation on a two-node cluster with nodes `node1` and `node2`, with the Grid home `C:\app\19.0.0\grid`, and with the Oracle home path `C:\app\oracle\product\19.0.0\dbhome_1`, enter the following command:

    C:\app\19.0.0\grid\bin> cluvfy stage -pre dbcfg -n node1,node2 \
    -d C:\app\oracle\product\19.0.0\dbhome_1

**Parent topic:** [Creating Oracle RAC or Oracle RAC One Node Databases with Oracle DBCA](creating-oracle-rac-or-oracle-rac-one-node-databases-with-dbca.md)
