UCP provides a set of Oracle RAC run-time statistics that are used to determine how well a connection pool is utilizing Oracle RAC features and are also used to help determine whether the connection pool has been configured properly to use the Oracle RAC features. The statistics report FCF processing information, run-time connection load balance success/failure rate, and affinity context success/failure rate.

The `OracleJDBCConnectionPoolStatistics` interface that is located in the `oracle.ucp.jdbc.oracle` package provides methods that are used to query the connection pool for Oracle RAC statistics. The methods of this interface can be called from a pool-enabled and pool-enabled XA data source using the data source's `getStatistics` method. For example:

    PoolDataSource  pds = PoolDataSourceFactory.getPoolDataSource();
    ...

    Long rclbS = ((OracleJDBCConnectionPoolStatistics)pds.getStatistics()).
       getSuccessfulRCLBBasedBorrowCount();
    System.out.println("The RCLB success rate is "+rclbS+".");

The data source's `getStatistics` method can also be called by itself and returns all connection pool statistics as a `String` and includes the Oracle RAC statistics.

### 12.3.1 Fast Connection Failover Statistics

The `getFCFProcessingInfo` method provides information on recent Fast Connection Failover (FCF) attempts in the form of a `String`. The FCF information is typically used to help diagnose FCF problems. The information includes the outcome of each FCF attempt (successful or failed), the relevant Oracle RAC instances, the number of connections that were cleaned up, the exception that triggered the FCF attempt failure, and more. The following example demonstrates using the `getFCFProcessingInfo` method:

    Sting fcfInfo = ((OracleJDBCConnectionPoolStatistics)pds.getStatistics()).
       getFCFProcessingInfo();
    System.out.println("The FCF information: "+fcfInfo+".");

Following is a sample output string from the `getFCFProcessingInfo()` method:

        Oct 28, 2008 12:34:02 SUCCESS <Reason:planned> <Type:SERVICE_UP> \
          <Service:"svvc1"> <Instance:"inst1"> <Db:"db1"> \
          Connections:(Available=6 Affected=2 FailedToProcess=0 MarkedDown=2 Closed=2) \
          (Borrowed=6 Affected=2 FailedToProcess=0 MarkedDown=2 MarkedDeferredClose=0 Closed=2) \
          TornDown=2 MarkedToClose=2 Cardinality=2
        ...
        Oct 28, 2008 12:09:52 SUCCESS <Reason:unplanned> <Type:SERVICE_DOWN> \
          <Service:"svc1"> <Instance:"inst1"> <Db:"db1"> \
          Connections:(Available=6 Affected=2 FailedToProcess=0 MarkedDown=2 Closed=2) \
          (Borrowed=6 Affected=2 FailedToProcess=0 MarkedDown=2 MarkedDeferredClose=0 Closed=2)
        ...
        Oct 28, 2008 11:14:53 FAILURE <Type:HOST_DOWN> <Host:"host1"> \
          Connections:(Available=6 Affected=4 FailedToProcess=0 MarkedDown=4 Closed=4) \
          (Borrowed=6 Affected=4 FailedToProcess=0 MarkedDown=4 MarkedDeferredClose=0 Closed=4)

If you enable logging, then the preceding information will also be available in the UCP logs and you will be able to verify the FCF outcome.

### 12.3.2 Run-Time Connection Load Balance Statistics

The run-time connection load balance statistics are used to determine if a connection pool is effectively utilizing the run-time connection load balancing feature of Oracle RAC. The statistics report how many requests successfully used the run-time connection load balancing algorithms and how many requests failed to use the algorithms. The `getSuccessfulRCLBBasedBorrowCount` method and the `getFailedRCLBBasedBorrowCount` method, respectively, are used to get the statistics. The following example demonstrates using the `getFailedRCLBBasedBorrowCount` method:

    Long rclbF = ((OracleJDBCConnectionPoolStatistics)pds.getStatistics()).
       getFailedRCLBBasedBorrowCount();
    System.out.println("The RCLB failure rate is: "+rclbF+".");

A high failure rate may indicate that the Oracle RAC Load Balancing Advisory or connection pool is not configured properly.

### 12.3.3 Connection Affinity Statistics

The connection affinity statistics are used to determine if a connection pools is effectively utilizing connection affinity. The statistics report the number of borrow requests that succeeded in matching the affinity context and how many requests failed to match the affinity context. The `getSuccessfulAffinityBasedBorrowCount` method and the `getFailedAffinityBasedBorrowCount` method, respectively, are used to get the statistics. The following example demonstrates using the `getFailedAffinityBasedBorrowCount` method:

    Long affF = ((OracleJDBCConnectionPoolStatistics)pds.getStatistics()).
       getFailedAffinityBasedBorrowCount();
    System.out.println("The connection affinity failure rate is: "+affF+".");
