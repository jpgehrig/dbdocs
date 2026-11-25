Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleJDBCConnectionPoolStatistics.md)
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-files/index-1.md)
- [Help](../../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev Class
- Next Class

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.ucp.jdbc.oracle

## Interface OracleJDBCConnectionPoolStatistics

- All Superinterfaces:
  [JDBCConnectionPoolStatistics](../JDBCConnectionPoolStatistics.md), [UniversalConnectionPoolStatistics](../../UniversalConnectionPoolStatistics.md)

  ------------------------------------------------------------------------



      public interface OracleJDBCConnectionPoolStatistics
      extends JDBCConnectionPoolStatistics

  Various runtime statistics for the Universal Connection Pool that are specific to Oracle JDBC resources. This interface provides query-only operations on all available pool statistics.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                  |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `long`             | `getConnectionRepurposeCount``()`<br>Returns the number of connection repurposed in a shared pool for a mutitenant database, where connections can be reused across PDB's by switching their container and PDB service. |
    | `long`             | `getFailedAffinityBasedBorrowCount``()`<br>Gets the number of borrow requests that returned connections not matching the affinity contexts.                                                                             |
    | `long`             | `getFailedRCLBBasedBorrowCount``()`<br>Gets the number of borrow requests that failed to use Runtime Connection Load-Balancing (RCLB) algorithms.                                                                       |
    | `java.lang.String` | `getFCFProcessingInfo``()`<br>Gets the information of recent Fast Connection Failover (FCF) attempts, in the form of a String.                                                                                          |
    | `java.lang.String` | `getFCFProcessingInfoProcessedOnly``()`                                                                                                                                                                                 |
    | `long`             | `getSuccessfulAffinityBasedBorrowCount``()`<br>Gets the number of borrow requests that succeeded in matching affinity contexts.                                                                                         |
    | `long`             | `getSuccessfulRCLBBasedBorrowCount``()`<br>Gets the number of borrow requests that succeeded in using the Runtime Connection Load-Balancing (RCLB) algorithms.                                                          |

    - ### Methods inherited from interface oracle.ucp.[UniversalConnectionPoolStatistics](../../UniversalConnectionPoolStatistics.md)

      [`getAbandonedConnectionsCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getAvailableConnectionsCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getAverageBorrowedConnectionsCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getAverageConnectionWaitTime`](../../UniversalConnectionPoolStatistics.md)`, `[`getBorrowedConnectionsCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getConnectionsClosedCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getConnectionsCreatedCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeConnectionBorrowedCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeConnectionReturnedCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeConnectionUseTime`](../../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeConnectionWaitTime`](../../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeFailedConnectionWaitCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeFailedConnectionWaitTime`](../../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeSuccessfulConnectionWaitCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeSuccessfulConnectionWaitTime`](../../UniversalConnectionPoolStatistics.md)`, `[`getLabeledConnectionsCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getPeakConnectionsCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getPeakConnectionWaitTime`](../../UniversalConnectionPoolStatistics.md)`, `[`getPendingRequestsCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getRemainingPoolCapacityCount`](../../UniversalConnectionPoolStatistics.md)`, `[`getTotalConnectionsCount`](../../UniversalConnectionPoolStatistics.md)

<!-- -->

- - ### Method Detail

    - #### getSuccessfulAffinityBasedBorrowCount

          long getSuccessfulAffinityBasedBorrowCount()

      Gets the number of borrow requests that succeeded in matching affinity contexts.
      Returns:
      The number of borrow requests that succeeded in matching affinity contexts.

    <!-- -->

    - #### getFailedAffinityBasedBorrowCount

          long getFailedAffinityBasedBorrowCount()

      Gets the number of borrow requests that returned connections not matching the affinity contexts.
      Returns:
      The number of borrow requests that returned connections not matching the affinity contexts.

    <!-- -->

    - #### getSuccessfulRCLBBasedBorrowCount

          long getSuccessfulRCLBBasedBorrowCount()

      Gets the number of borrow requests that succeeded in using the Runtime Connection Load-Balancing (RCLB) algorithms.
      Returns:
      The number of borrow requests that succeeded in using Runtime Connection Load-Balancing (RCLB) algorithms.

    <!-- -->

    - #### getFailedRCLBBasedBorrowCount

          long getFailedRCLBBasedBorrowCount()

      Gets the number of borrow requests that failed to use Runtime Connection Load-Balancing (RCLB) algorithms.
      Returns:
      The number of borrow requests that failed to use Runtime Connection Load-Balancing (RCLB) algorithms.

    <!-- -->

    - #### getFCFProcessingInfo

          java.lang.String getFCFProcessingInfo()

      Gets the information of recent Fast Connection Failover (FCF) attempts, in the form of a String. The information returned is to help diagnosing FCF problems, and includes the outcome of each FCF attempt (successful or failed), the relevant Oracle RAC instances, the number of connections cleaned up, the exception that triggered the FCF attempt failure, and so forth.
      Returns:
      The information string for recent FCF attempts.

    <!-- -->

    - #### getFCFProcessingInfoProcessedOnly

          java.lang.String getFCFProcessingInfoProcessedOnly()

    <!-- -->

    - #### getConnectionRepurposeCount

          long getConnectionRepurposeCount()

      Returns the number of connection repurposed in a shared pool for a mutitenant database, where connections can be reused across PDB's by switching their container and PDB service.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleJDBCConnectionPoolStatistics.md)
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-files/index-1.md)
- [Help](../../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev Class
- Next Class

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2022, Oracle and/or its affiliates.
