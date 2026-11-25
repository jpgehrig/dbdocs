Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/JDBCConnectionPoolStatistics.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](HarvestableConnection.md)
- [Next Class](LabelableConnection.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.ucp.jdbc

## Interface JDBCConnectionPoolStatistics

- All Superinterfaces:
  [UniversalConnectionPoolStatistics](../UniversalConnectionPoolStatistics.md)

  <!-- -->

  All Known Subinterfaces:
  [OracleJDBCConnectionPoolStatistics](oracle/OracleJDBCConnectionPoolStatistics.md)

  ------------------------------------------------------------------------



      public interface JDBCConnectionPoolStatistics
      extends UniversalConnectionPoolStatistics

  Various runtime statistics for the Universal Connection Pool that are specific to JDBC resources. This interface provides query-only operations on all available pool statistics.

<!-- -->

- - ### Method Summary

    - ### Methods inherited from interface oracle.ucp.[UniversalConnectionPoolStatistics](../UniversalConnectionPoolStatistics.md)

      [`getAbandonedConnectionsCount`](../UniversalConnectionPoolStatistics.md)`, `[`getAvailableConnectionsCount`](../UniversalConnectionPoolStatistics.md)`, `[`getAverageBorrowedConnectionsCount`](../UniversalConnectionPoolStatistics.md)`, `[`getAverageConnectionWaitTime`](../UniversalConnectionPoolStatistics.md)`, `[`getBorrowedConnectionsCount`](../UniversalConnectionPoolStatistics.md)`, `[`getConnectionsClosedCount`](../UniversalConnectionPoolStatistics.md)`, `[`getConnectionsCreatedCount`](../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeConnectionBorrowedCount`](../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeConnectionReturnedCount`](../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeConnectionUseTime`](../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeConnectionWaitTime`](../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeFailedConnectionWaitCount`](../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeFailedConnectionWaitTime`](../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeSuccessfulConnectionWaitCount`](../UniversalConnectionPoolStatistics.md)`, `[`getCumulativeSuccessfulConnectionWaitTime`](../UniversalConnectionPoolStatistics.md)`, `[`getLabeledConnectionsCount`](../UniversalConnectionPoolStatistics.md)`, `[`getPeakConnectionsCount`](../UniversalConnectionPoolStatistics.md)`, `[`getPeakConnectionWaitTime`](../UniversalConnectionPoolStatistics.md)`, `[`getPendingRequestsCount`](../UniversalConnectionPoolStatistics.md)`, `[`getRemainingPoolCapacityCount`](../UniversalConnectionPoolStatistics.md)`, `[`getTotalConnectionsCount`](../UniversalConnectionPoolStatistics.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/JDBCConnectionPoolStatistics.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](HarvestableConnection.md)
- [Next Class](LabelableConnection.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
