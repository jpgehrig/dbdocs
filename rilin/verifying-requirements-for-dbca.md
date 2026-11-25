## Verifying Requirements for DBCA

Before using DBCA to create Oracle RAC databases, verify if your system is prepared for configuration changes.

To use Database Configuration Assistant (DBCA) to change the database configuration, run Cluster Verification Utility (CVU) to verify that your system is prepared for configuration changes using the following command syntax:

    /u01/app/19.0.0/grid/bin/cluvfy stage -pre dbcfg -fixup -n node_list -d ORACLE_HOME [-verbose]

In the preceding syntax example, the variable `node_list` is the list of nodes in your cluster, separated by commas, and the variable `ORACLE_HOME` is the path for the Oracle home directory where OUI creates or modifies the database. The `-fixup` flag generates a fixup script that can be run as root to resolve many operating system configuration tasks if they were not completed before you run the check.

For example, to verify that your system is prepared for an Oracle Database with Oracle RAC installation on a two-node cluster with nodes `node1` and `node2`, with the Oracle Grid Infrastructure home path`/u01/app/19.0.0/grid`, and with the Oracle home path `/u01/app/oracle/product/19.0.0/dbhome_1`, enter the following command:

    $ /u01/app/19.0.0/grid/bin/cluvfy stage -pre dbcfg -fixup -n node1,node2 -d\
    /u01/app/oracle/product/19.0.0/dbhome_1

You can select the option `-verbose` to receive progress updates as CVU performs its system checks, and detailed reporting of the test results.

If the CVU summary indicates that the cluster verification check fails, and you cannot resolve these issues by running the fixup script, then review and correct the relevant system configuration steps, and run the test again.

**Parent topic:** [Creating Oracle RAC or Oracle RAC One Node Databases with Oracle DBCA](selecting-dbca-options-to-create-oracle-rac-or-oracle-rac-one-node-databases-with-dbca.md)
