## About Standard Edition High Availability

Starting with Oracle Database 19c Release Update (19.7), you can install Oracle Database Standard Edition 2 in high availability mode.

Standard Edition High Availability provides cluster-based failover for single-instance Standard Edition Oracle Databases using Oracle Clusterware.

Oracle Standard Edition High Availability benefits from the cluster capabilities and storage solutions that are already part of Oracle Grid Infrastructure, such as Oracle Clusterware, Oracle Automatic Storage Management (Oracle ASM) and Oracle ASM Cluster File System (Oracle ACFS).

Using integrated, shared, and concurrently mounted storage, such as Oracle ASM and Oracle ACFS for database files as well as for unstructured data, enables Oracle Grid Infrastructure to restart an Oracle Database on a failover node much faster than any cluster solution that relies on failing over and remounting volumes and file systems.

Standard Edition High Availability is supported on Linux x86-64, Oracle Solaris on SPARC (64-bit), and Microsoft Windows.

Starting with Oracle Database 19c Release Update (19.13), Standard Edition High Availability is supported on IBM AIX on POWER Systems (64-bit).

**Note:**

This section is specific to Standard Edition High Availability, which provides cluster-based database failover for Standard Edition Oracle Databases 19c. For more information about high availability options for Oracle Database, see [Oracle Clusterware Administration and Deployment Guide](../cwadd/introduction-to-oracle-clusterware.md).

**Parent topic:** [Installing Standard Edition High Availability](configuring-standard-edition-high-availability.md)
