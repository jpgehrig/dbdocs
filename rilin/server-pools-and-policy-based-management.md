## Server Pools and Policy-Based Management

With policy-based management, database administrators specify the server pool (excluding Generic or Free) in which the database resource runs.

Policy-based management:

- Enables dynamic capacity assignment when needed to provide server capacity in accordance with the priorities you set with policies

- Enables allocation of resources by importance, so that applications obtain the required minimum resources, whenever possible, and so that lower priority applications do not take resources from more important applications

- Ensures isolation where necessary, so that you can provide dedicated servers in a cluster for applications and databases

- Enables policies to be configured to change pools in accordance with business needs or application demand, so that pools provide the right service at the right time

Applications and databases running in server pools do not share resources. Because server pools do not share resources, they isolate resources where necessary, but enable dynamic capacity assignments as required. Together with role-separated management, this capability addresses the needs of organizations that have standardized cluster environments, but allow multiple administrator groups to share the common cluster infrastructure.

Oracle Clusterware efficiently allocates different resources in the cluster. You need only to provide the minimum and maximum number of nodes on which a resource can run, combined with a level of importance for each resource that is running on these nodes.

**See Also:**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-resource-reference.md) for more information about resource attributes

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/policy-based-cluster-and-capacity-management.md) for details about managing server pools to respond to business or application demand

**Parent topic:** [Policy-Managed Clusters and Capacity Management](policy-managed-clusters-and-capacity-management.md)
