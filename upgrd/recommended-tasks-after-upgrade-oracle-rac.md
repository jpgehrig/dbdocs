## Recommended Tasks After Upgrading an Oracle RAC Database

Decide if you want to configure clients to use SCAN or node listeners for connections.

Oracle Real Application Clusters 12c uses the Single Client Access Name (SCAN). The SCAN is a single name that resolves to three IP addresses in the public network. When you upgrade a release of an Oracle RAC database earlier than release 11.2, the Oracle RAC database is registered with SCAN listeners as remote listeners. The Oracle RAC database also continues to register with all node listeners. SCAN listeners offer a variety of benefits. These benefits include enabling you to configure clients one time, and adding or removing nodes from the cluster without needing to change client connection configurations.

You can configure clients to use SCANs, or you can continue to use listeners configured on cluster member nodes. If you migrate all of your client connections to use SCANs, then you can remove the node listeners from the REMOTE_LISTENERS parameter. However, you cannot remove the node listeners themselves, because only node listeners can create dedicated servers for the database.

**See Also:**

[Oracle Clusterware Administration and Deployment Guide](../cwadd/introduction-to-oracle-clusterware.md) for more information about Single Client Access Names (SCAN)

**Parent topic:** [Post-Upgrade Tasks for Oracle Database](post-upgrade-tasks-oracle-database.md)
