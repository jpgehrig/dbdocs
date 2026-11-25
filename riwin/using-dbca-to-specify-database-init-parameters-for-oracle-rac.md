## Using DBCA to Specify Database Initialization Parameters for Oracle RAC

Set the `CLUSTER_DATABASE_INSTANCES` parameter to the expected number of instances.

1.  On the Initialization Parameters page, if you intend to add more nodes in your cluster than you have during the current Oracle Database Configuration Assistant session, then click All Initialization Parameters, and change the parameter `CLUSTER_DATABASE_INSTANCES` to the total number of nodes that you plan to add to the cluster.
2.  In addition, if you click All Initialization Parameters, note that if your global database name is longer than 8 characters, then the database name value (in the `DB_NAME` parameter) is truncated to the first 8 characters, and the `DB_UNIQUE_NAME` parameter value is set to the global name.

**See Also:**

[Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md) for information about initialization parameters

**Parent topic:** [Selecting DBCA Options to Create an Oracle RAC or Oracle RAC One Node Database](creating-an-oracle-rac-or-oracle-rac-one-node-database-with-dbca.md)
