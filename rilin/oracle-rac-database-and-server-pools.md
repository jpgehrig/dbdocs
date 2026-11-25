## Oracle RAC Database and Server Pools

Oracle RAC databases support two types of server pool management styles and deployment models.

- Policy-managed: Deployment is based on server pools, where database services run within a server pool as singleton or uniform across all of the servers in the server pool. Databases are deployed in one or more server pools and the size of the server pools determine the number of database instances in the deployment. Policy management allows clusters and databases to expand or shrink as requirements change.

  A policy-managed database is defined by cardinality, which is the number of database instances you want running during normal operations. A policy-managed database runs in one or more database server pools that the cluster administrator creates in the cluster, and it can run on different servers at different times. A database instance starts on all servers that are in the server pools defined for the database.

  Clients can connect to a policy-managed database using the same SCAN-based connect string no matter which servers they happen to be running on at the time.

- Administrator-managed: Deployment is based on the Oracle RAC deployment types that existed before Oracle Database 11g Release 2 (11.2) and requires that you statically configure each database instance to run on a specific node in the cluster, and that you configure database services to run on specific instances belonging to a certain database using the preferred and available designation.

  When you review the database resource for an administrator-managed database, you see a server pool defined with the same name as the Oracle database. This server pool is part of a special Oracle-defined server pool called Generic. Oracle RAC manages the Generic server pool to support administrator-managed databases. When you add or remove an administrator-managed database using either SRVCTL or DBCA, Oracle RAC creates or removes the server pools that are members of Generic.

**See Also:**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/policy-based-cluster-and-capacity-management.md) for detailed information about server pools

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/policy-based-cluster-and-capacity-management.md) for information about policy sets

**Parent topic:** [Using Server Pools with Oracle RAC](using-server-pools-with-oracle-rac.md)
