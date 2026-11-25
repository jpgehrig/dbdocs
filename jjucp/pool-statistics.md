Universal Connection Pool (UCP) provides a set of run-time statistics for the connection pool. These statistics can be divided into the following two categories:

- Noncumulative

  These statistics apply only to the current running connection pool instance.

- Cumulative

  These statistics are collected across multiple pool start/stop cycles.

The `oracle.ucp.UniversalConnectionPoolStatistics` interface provides methods that are used to query the connection pool statistics. The methods of this interface can be called from a pool-enabled data source and pool-enabled XA data source, using the `oracle.ucp.jdbc.PoolDataSource.getStatistics` method. For example:

    PoolDataSource pds = PoolDataSourceFactory.getPoolDataSource();
    ...
    ...
    int totalConnsCount = pds.getStatistics().getTotalConnectionsCount();
    System.out.println("The total connetion count in the pool is "+ totalConnsCount +".");

The `oracle.ucp.jdbc.PoolDataSource.getStatistics` method can also be called by itself to return all connection pool statistics as a `String`.
