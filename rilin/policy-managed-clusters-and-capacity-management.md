## Policy-Managed Clusters and Capacity Management

Oracle Clusterware uses policy-based management of servers and resources used by Oracle databases or applications.

Oracle Clusterware 11g Release 2 (11.2) introduced server pools, where resources that Oracle Clusterware manages are contained in logical groups of servers called server pools. Resources are hosted on a shared infrastructure and are contained within server pools. Resources are no longer defined as belonging to a specific instance or node. Instead, the priority of resource requirements is defined. In an Oracle Flex Cluster, you can use server pools to run particular types of workloads on cluster member nodes, while providing simplified administration options. You can use a cluster configuration policy set to provide dynamic management of cluster policies across the cluster.

- [Server Pools and Server Categorization](server-pools-and-server-categorization.md)
  You can manage servers dynamically using server pools by identifying servers distinguished by particular attributes, a process called server categorization. In this way, you can manage clusters made up of heterogeneous nodes.
- [Server Pools and Policy-Based Management](server-pools-and-policy-based-management.md)
  With policy-based management, database administrators specify the server pool (excluding Generic or Free) in which the database resource runs.
- [How Server Pools Work](how-server-pools-work.md)
  Server pools divide the cluster into groups of servers hosting singleton and uniform database services and applications.
- [About Server Pools](about-server-pools.md)
  When Oracle Clusterware is installed, two server pools are created automatically: Generic and Free.

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/administering-database-instances-and-cluster-databases.md)

**Parent topic:** [Using Server Pools with Oracle RAC](using-server-pools-with-oracle-rac.md)
