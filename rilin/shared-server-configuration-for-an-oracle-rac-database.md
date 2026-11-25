## Shared Server Configuration for an Oracle RAC Database

Standalone Oracle databases perform load balancing by distributing connections among the shared server dispatcher processes. By default, DBCA configures your Oracle RAC database with dedicated servers, not shared servers.

However, if you select the shared server option when using DBCA, then DBCA configures shared servers. Oracle RAC uses both dedicated and shared server processing when shared servers are configured.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md) for more information about shared and dedicated server configurations

**Parent topic:** [Performance Features of Oracle Net Services and Oracle RAC](performance-features-of-oracle-net-services-and-oracle-rac.md)
