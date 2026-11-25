This section provides instructions for setting connection pool properties in order to optimize pooling behavior. Upon creation, UCP JDBC connection pools are pre-configured with a default setup. The default setup provides a general, all-purpose connection pool. However, different applications may have different database connection requirements and may want to modify the default behavior of the connection pool. Behaviors, such as pool size and connection timeouts can be configured and can improve overall connection pool performance as well as connection availability. In many cases, the best way to tune a connection pool for a specific application is to try different property combinations using different values until optimal performance and throughput is achieved.

### Setting Connection Pool Properties

Connection pool properties are set either when getting a connection through a pool-enabled data source or when creating a connection pool using the connection pool manager.

The following example demonstrates setting connection pool properties though a pool-enabled data source:

    PoolDataSource  pds = PoolDataSourceFactory.getPoolDataSource();

    pds.setConnectionPoolName("JDBC_UCP");
    pds.setMinPoolSize(4);pds.setMaxPoolSize(20);
    ...

The following example demonstrates setting connection pool properties when creating a connection pool using the connection pool manager:

    UniversalConnectionPoolManager mgr = UniversalConnectionPoolManagerImpl.
    getUniversalConnectionPoolManager();

    pds.setConnectionPoolName("JDBC_UCP");
    pds.setMinPoolSize(4);pds.setMaxPoolSize(20);
    ...

    mgr.createConnectionPool(pds);
