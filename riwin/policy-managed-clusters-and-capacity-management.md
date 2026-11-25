## Policy-Managed Clusters and Capacity Management

Starting with Oracle Clusterware 11g release 2, resources that Oracle Clusterware manages are contained in logical groups of servers called server pools.

Resources are hosted on a shared infrastructure and are contained within server pools. Resources are no longer defined as belonging to a specific instance or node. Instead, the priority of resource requirements is defined. You can use a cluster configuration policy set to provide dynamic management of cluster policies across the cluster.

- [Server Pools and Server Categorization](server-pools-and-server-categorization.md)
  You can manage servers dynamically using server pools by identifying servers distinguished by particular attributes, a process called server categorization.
- [Server Pools and Policy-Based Management](server-pools-and-policy-based-management.md)
  With policy-based management, database administrators specify the server pool (excluding Generic or Free) in which the database resource runs.
- [How Server Pools Work](how-server-pools-work.md)
  Server pools divide the cluster into groups of servers hosting singleton and uniform database services and applications.
- [Default Server Pools](default-server-pools.md)
  When Oracle Clusterware is installed, two server pools are created automatically: Generic and Free.

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/administering-database-instances-and-cluster-databases.md)

**Parent topic:** [Using Server Pools with Oracle RAC](using-server-pools-with-oracle-rac.md)
