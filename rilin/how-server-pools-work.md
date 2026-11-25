## How Server Pools Work

Server pools divide the cluster into groups of servers hosting singleton and uniform database services and applications.

Server pools distribute a uniform workload (a set of Oracle Clusterware resources) over several servers in the cluster. For example, you can restrict Oracle databases to run only in certain server pools. When you enable role-separated management, you can grant permission to operating system users to use server pools.

You manage server pools that contain Oracle RAC databases with the Server Control (SRVCTL) utility. Use the Oracle Clusterware Control (CRSCTL) utility to manage all other server pools. Only cluster administrators have permission to create top-level server pools.

Top-level server pools:

- Logically divide the cluster

- Are always exclusive, meaning that one server can only reside in one particular server pool at a certain point in time

**Parent topic:** [Policy-Managed Clusters and Capacity Management](policy-managed-clusters-and-capacity-management.md)
