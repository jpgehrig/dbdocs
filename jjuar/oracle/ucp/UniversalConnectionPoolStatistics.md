Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolStatistics.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolLifeCycleState.md)
- [Next Class](UniversalPooledConnection.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.ucp

## Interface UniversalConnectionPoolStatistics

- All Known Subinterfaces:
  [JDBCConnectionPoolStatistics](jdbc/JDBCConnectionPoolStatistics.md), [OracleJDBCConnectionPoolStatistics](jdbc/oracle/OracleJDBCConnectionPoolStatistics.md)

  ------------------------------------------------------------------------



      public interface UniversalConnectionPoolStatistics

  Various runtime statistics for the Universal Connection Pool. This interface provides query-only operations on all available pool statistics.
  The *cumulative* statistics are collected across multiple pool start/stop cycles, while the others only apply to the current running connection pool instance.

  See Also:
  [`UniversalConnectionPool`](UniversalConnectionPool.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                      |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`             | `getAbandonedConnectionsCount``()`<br>Gets the number of abandoned connections that have been reclaimed.                                                                                    |
    | `int`             | `getAvailableConnectionsCount``()`<br>Gets the number of connections that are available in the connection pool (that is, connections in the pool that are not currently in use by clients). |
    | `int`             | `getAverageBorrowedConnectionsCount``()`<br>Gets the average number of connections that are borrowed and actively in use by clients.                                                        |
    | `long`            | `getAverageConnectionWaitTime``()`<br>Gets the average time (in milliseconds) a user thread has to wait before it could obtain a connection from the connection pool.                       |
    | `int`             | `getBorrowedConnectionsCount``()`<br>Gets the number of connections that are actively in use by clients.                                                                                    |
    | `int`             | `getConnectionsClosedCount``()`<br>Gets the number of connections closed by this connection pool.                                                                                           |
    | `int`             | `getConnectionsCreatedCount``()`<br>Gets the number of connections created for this connection pool.                                                                                        |
    | `long`            | `getCumulativeConnectionBorrowedCount``()`<br>Gets the number of connections borrowed from the connection pool over the life of the pool.                                                   |
    | `long`            | `getCumulativeConnectionReturnedCount``()`<br>Gets the number of connections returned to the connection pool over the life of the pool.                                                     |
    | `long`            | `getCumulativeConnectionUseTime``()`<br>Gets the cumulative time (in milliseconds) of connections that were borrowed from the pool and remained in use.                                     |
    | `long`            | `getCumulativeConnectionWaitTime``()`<br>Gets the cumulative time (in milliseconds) that connection requests have waited for connections over the life of the connection pool.              |
    | `long`            | `getCumulativeFailedConnectionWaitCount``()`<br>Gets the number of connection requests that waited unsuccessfully to borrow a connection from the pool.                                     |
    | `long`            | `getCumulativeFailedConnectionWaitTime``()`<br>Gets the cumulative time (in milliseconds) that connection requests waited but failed to borrow a connection from the pool.                  |
    | `long`            | `getCumulativeSuccessfulConnectionWaitCount``()`<br>Gets the number of connection requests that waited successfully and borrowed a connection from the pool.                                |
    | `long`            | `getCumulativeSuccessfulConnectionWaitTime``()`<br>Gets the cumulative time (in milliseconds) that connection requests waited successfully and borrowed a connection from the pool.         |
    | `int`             | `getLabeledConnectionsCount``()`<br>Gets the number of labeled connections in the connection pool.                                                                                          |
    | `int`             | `getPeakConnectionsCount``()`<br>Gets the maximum number of connections that the connection pool has reached during the life of the pool.                                                   |
    | `long`            | `getPeakConnectionWaitTime``()`<br>Gets the longest wait (in milliseconds) a user request has to incur before obtaining a connection from the connection pool.                              |
    | `int`             | `getPendingRequestsCount``()`<br>Gets the number of clients that are currently waiting to obtain a connection from the pool.                                                                |
    | `int`             | `getRemainingPoolCapacityCount``()`<br>Gets the number of connections that may be added to the pool before it reaches `maxPoolSize`.                                                        |
    | `int`             | `getTotalConnectionsCount``()`<br>Gets the total number of connections (both available and borrowed) in the connection pool.                                                                |

<!-- -->

- - ### Method Detail

    - #### getTotalConnectionsCount

          int getTotalConnectionsCount()

      Gets the total number of connections (both available and borrowed) in the connection pool.
      Returns:
      The total number of connections (both available and borrowed) in the connection pool.

    <!-- -->

    - #### getAvailableConnectionsCount

          int getAvailableConnectionsCount()

      Gets the number of connections that are available in the connection pool (that is, connections in the pool that are not currently in use by clients).
      Returns:
      The number of connections that are available in the connection pool.

    <!-- -->

    - #### getBorrowedConnectionsCount

          int getBorrowedConnectionsCount()

      Gets the number of connections that are actively in use by clients.
      Returns:
      The number of connections that are actively in use by clients.

    <!-- -->

    - #### getAverageBorrowedConnectionsCount

          int getAverageBorrowedConnectionsCount()

      Gets the average number of connections that are borrowed and actively in use by clients.
      Returns:
      The number of connections that are borrowed and actively in use by clients.

    <!-- -->

    - #### getPeakConnectionsCount

          int getPeakConnectionsCount()

      Gets the maximum number of connections that the connection pool has reached during the life of the pool.
      Returns:
      The maximum number of connections that the connection pool has reached during the life of the pool.

    <!-- -->

    - #### getRemainingPoolCapacityCount

          int getRemainingPoolCapacityCount()

      Gets the number of connections that may be added to the pool before it reaches `maxPoolSize`.
      Returns:
      The number of connections that may be added to the pool before it reaches `maxPoolSize`.

    <!-- -->

    - #### getLabeledConnectionsCount

          int getLabeledConnectionsCount()

      Gets the number of labeled connections in the connection pool.
      Returns:
      The number of labeled connections in the connection pool.

    <!-- -->

    - #### getConnectionsCreatedCount

          int getConnectionsCreatedCount()

      Gets the number of connections created for this connection pool.
      Returns:
      The number of connections created for this connection pool.

    <!-- -->

    - #### getConnectionsClosedCount

          int getConnectionsClosedCount()

      Gets the number of connections closed by this connection pool.
      Returns:
      The number of connections closed by this connection pool.

    <!-- -->

    - #### getAverageConnectionWaitTime

          long getAverageConnectionWaitTime()

      Gets the average time (in milliseconds) a user thread has to wait before it could obtain a connection from the connection pool.
      Returns:
      The average time (in milliseconds) a user thread has to wait before it could obtain a connection from the connection pool.

    <!-- -->

    - #### getPeakConnectionWaitTime

          long getPeakConnectionWaitTime()

      Gets the longest wait (in milliseconds) a user request has to incur before obtaining a connection from the connection pool. This includes threads that waited unsuccessfully for a connection.
      Returns:
      The longest wait (in milliseconds) a user request has to incur before obtaining a connection from the connection pool.

    <!-- -->

    - #### getAbandonedConnectionsCount

          int getAbandonedConnectionsCount()

      Gets the number of abandoned connections that have been reclaimed.
      Returns:
      The number of abandoned connections that have been reclaimed.

    <!-- -->

    - #### getPendingRequestsCount

          int getPendingRequestsCount()

      Gets the number of clients that are currently waiting to obtain a connection from the pool.
      Returns:
      The number of clients that are currently waiting to obtain a connection from the pool.

    <!-- -->

    - #### getCumulativeConnectionWaitTime

          long getCumulativeConnectionWaitTime()

      Gets the cumulative time (in milliseconds) that connection requests have waited for connections over the life of the connection pool. This includes the time connections waited successfully and obtained a connection from the pool and those that failed waiting for a connection.
      Returns:
      The cumulative time (in milliseconds) that connection requests have waited for connections over the life of the connection pool.

    <!-- -->

    - #### getCumulativeConnectionBorrowedCount

          long getCumulativeConnectionBorrowedCount()

      Gets the number of connections borrowed from the connection pool over the life of the pool. This count is incremented each time a connection is borrowed.
      Returns:
      The number of connections borrowed from the connection pool over the life of the pool.

    <!-- -->

    - #### getCumulativeConnectionUseTime

          long getCumulativeConnectionUseTime()

      Gets the cumulative time (in milliseconds) of connections that were borrowed from the pool and remained in use.
      Returns:
      The cumulative time (in milliseconds) of connections that were borrowed from the pool and remained in use.

    <!-- -->

    - #### getCumulativeConnectionReturnedCount

          long getCumulativeConnectionReturnedCount()

      Gets the number of connections returned to the connection pool over the life of the pool.
      Returns:
      The number of connections returned to the connection pool over the life of the pool.

    <!-- -->

    - #### getCumulativeSuccessfulConnectionWaitTime

          long getCumulativeSuccessfulConnectionWaitTime()

      Gets the cumulative time (in milliseconds) that connection requests waited successfully and borrowed a connection from the pool.
      Returns:
      The cumulative time (in milliseconds) that connection requests waited successfully and borrowed a connection from the pool.

    <!-- -->

    - #### getCumulativeSuccessfulConnectionWaitCount

          long getCumulativeSuccessfulConnectionWaitCount()

      Gets the number of connection requests that waited successfully and borrowed a connection from the pool.
      Returns:
      The number of connection requests that waited successfully and borrowed a connection from the pool.

    <!-- -->

    - #### getCumulativeFailedConnectionWaitTime

          long getCumulativeFailedConnectionWaitTime()

      Gets the cumulative time (in milliseconds) that connection requests waited but failed to borrow a connection from the pool.
      Returns:
      The cumulative time (in milliseconds) that connection requests waited but failed to borrow a connection from the pool.

    <!-- -->

    - #### getCumulativeFailedConnectionWaitCount

          long getCumulativeFailedConnectionWaitCount()

      Gets the number of connection requests that waited unsuccessfully to borrow a connection from the pool.
      Returns:
      The number of connection requests that waited unsuccessfully to borrow a connection from the pool.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolStatistics.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolLifeCycleState.md)
- [Next Class](UniversalPooledConnection.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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
