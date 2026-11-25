## Performance Features of Oracle Net Services and Oracle RAC

Oracle RAC databases provide the important benefits of connection load balancing and failover.

- [Load Balancing of Connections to Oracle RAC Databases](load-balancing-of-connections-to-oracle-rac-databases.md)
  Services coordinate their sessions by registering their workload, or the amount of work they are currently handling, with the local listener and the SCAN listeners.
- [Connection Failover for Oracle RAC Databases](connection-failover-for-oracle-rac-databases.md)
  Oracle RAC provides failover with the node VIP addresses by configuring multiple listeners on multiple nodes to manage client connection requests for the same database service.
- [Shared Server Configuration for an Oracle RAC Database](shared-server-configuration-for-an-oracle-rac-database.md)
  Standalone Oracle databases perform load balancing by distributing connections among the shared server dispatcher processes. By default, DBCA configures your Oracle RAC database with dedicated servers, not shared servers.

**Parent topic:** [Understanding the Oracle RAC Installed Configuration](understanding-the-oracle-rac-installed-configuration.md)
