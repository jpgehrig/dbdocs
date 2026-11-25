UCP JDBC connection pools are configured using connection pool properties. The properties have `get` and `set` methods that are available through a pool-enabled data source instance. The methods are a convenient way to programmatically configure a pool. If no pool properties are set, then a connection pool uses default property values.

The following example demonstrates configuring connection pool properties. The example sets the connection pool name and the maximum/minimum number of connections allowed in the pool.

    PoolDataSource  pds = PoolDataSourceFactory.getPoolDataSource();

    pds.setConnectionPoolName("JDBC_UCP");
    pds.setMinPoolSize(4);pds.setMaxPoolSize(20);

UCP JDBC connection pool properties may be set in any order and can be dynamically changed at run time. For example, `setMaxPoolSize` could be changed at any time and the pool recognizes the new value and adapts accordingly.

**Related Topics**

- [Optimizing Universal Connection Pool Behavior](optimizing-ucp-behavior.md)
