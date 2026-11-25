## Load Balancing of Connections to Oracle RAC Databases

There are two types of load balancing that you can implement for an Oracle RAC database: client-side and server-side load balancing.

Services coordinate their sessions by registering their workload, or the amount of work they are currently handling, with the local listener and the SCAN listeners. Clients are redirected by the SCAN listener to a local listener on the least-loaded node that is running the instance for a particular service. This feature is called load balancing. The local listener either directs the client to a dispatcher process (if you configured the database to use shared servers), or directs the client to a dedicated server process.

Client-side load balancing balances the connection requests across the listeners. With server-side load balancing, the SCAN listener directs a connection request to the best instance currently providing the service by using the load balancing advisory.

**See Also:**

- [Oracle Grid Infrastructure Installation Guide](../cwwin/about-the-scan.md) for more information about SCAN and its configuration

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/workload-management-with-dynamic-database-services.md) for more information about failover, load balancing, and the load balancing advisory

**Parent topic:** [Performance Features of Oracle Net Services and Oracle RAC](performance-features-of-oracle-net-services-and-oracle-rac.md)
