## Connection Failover for Oracle RAC Databases

Oracle RAC provides failover with the node VIP addresses by configuring multiple listeners on multiple nodes to manage client connection requests for the same database service.

When a client issues a connection request using SCAN, the three SCAN addresses are returned to the client. If the first address fails, then the connection request to the SCAN fails over to the next address. Using multiple addresses allows a client to connect to an instance of the database even if the initial instance has failed.

If a node fails, then the service connecting to the VIP is relocated transparently to a remaining node, enabling fast notification of the failure to the clients connecting through the VIP. If the application and client are configured with transparent application failover options, then the client is reconnected to the remaining node.

**Parent topic:** [Performance Features of Oracle Net Services and Oracle RAC](performance-features-of-oracle-net-services-and-oracle-rac.md)
