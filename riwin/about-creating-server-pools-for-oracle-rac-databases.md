## About Creating Server Pools for Oracle RAC Databases

You can create a server pool with Oracle Database Configuration Assistant while creating an Oracle RAC database, but Oracle recommends that you create server pools before you deploy database software and databases.

Oracle also recommends that you perform the following steps:

- Enable role separation before you create the first server pool in the cluster.

- Create and manage server pools using configuration policies and a respective policy set.

You can implement role-separated management in one of two ways: Vertical or Horizontal.

### Vertical Implementation (Between Layers)

Vertical implementation describes a role separation approach based on different operating system users and groups used for various layers in the technology stack. Permissions on server pools and resources are granted to different users (and groups) for each layer in the stack using access control lists. Oracle Automatic Storage Management (Oracle ASM) offers setting up role separation as part of the Oracle Grid Infrastructure installation based on a granular assignment of operating system groups for specific roles.

### Horizontal Implementation (Within One Layer)

Horizontal implementation describes a role separation approach that restricts resource access within one layer using access permissions for resources that are granted using access control lists assigned to server pools and policy-managed databases or applications.

For example, consider an operating system user called `grid`, that installs Oracle Grid Infrastructure and creates two database server pools. The operating system users `ouser1` and `ouser2` must be able to operate within a server pool, but must not be able to modify those server pools and withdraw hardware resources from other server pools either accidentally or intentionally.

**See Also:**

- "[Overview of Cluster Configuration Policies and the Policy Set](../cwadd/policy-based-cluster-and-capacity-management.md)" in Oracle Clusterware Administration and Deployment Guide

- "[Role-Separated Management](../cwadd/oracle-clusterware-administration.md)" in Oracle Clusterware Administration and Deployment Guide

**Parent topic:** [Using Server Pools with Oracle RAC](using-server-pools-with-oracle-rac.md)
