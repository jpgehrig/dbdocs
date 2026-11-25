## Using DBCA to Specify Database Initialization Parameters for Oracle RAC

Specify initialization parameters if you intend to add more nodes in your cluster.

On the Initialization Parameters page, if you intend to add more nodes in your cluster than you have during the current DBCA session, then click All Initialization Parameters, and change the parameter `CLUSTER_DATABASE_INSTANCES` to the total number of nodes that you plan to add to the cluster.

If you click All Initialization Parameters, note that if your global database name is longer than 8 characters, then the database name value (in the `DB_NAME` parameter) is truncated to the first 8 characters, and the `DB_UNIQUE_NAME` parameter value is set to the global name.

If you are installing on a Linux system, note that Memory Size (SGA and PGA), which sets the initialization parameter `MEMORY_TARGET` or `MEMORY_MAX_TARGET`, cannot be greater than the shared memory file system on your operating system.

For example, if the shared memory file system allocation on your system is 1 GB, but you set Memory Size (`MEMORY_TARGET`) to 2 GB, then you receive the following error during database startup:

    ORA-00845: MEMORY_TARGET not supported on this system
    ORA-01078: Failure in processing system parameters

This issue is not relevant for other platforms.

**See Also:**

[Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md) for information about initialization parameters

**Parent topic:** [Selecting DBCA Options to Create an Oracle RAC or Oracle RAC One Node Database](creating-an-oracle-rac-or-oracle-rac-one-node-database-with-dbca.md)
