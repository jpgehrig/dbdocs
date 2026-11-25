Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ReplayableConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXADataSourceImpl.md)
- [Next Class](ReplayableConnection.StatisticsReportType.md)

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

oracle.jdbc.replay

## Interface ReplayableConnection

-

  ------------------------------------------------------------------------



      public interface ReplayableConnection

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                                                              |
    |-------------------|------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`ReplayableConnection.StatisticsReportType`](ReplayableConnection.StatisticsReportType.md)<br>Statistics report type. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                              |
    |-------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                    | `beginRequest``()`<br>Declares that a request to the server is starting on this connection.                                                                                         |
    | `void`                                    | `clearReplayStatistics``(`[`ReplayableConnection.StatisticsReportType`](ReplayableConnection.StatisticsReportType.md)` reportType)`<br>Clears replay statistics accumulated so far. |
    | `void`                                    | `disableReplay``()`<br>Allows disabling replay at runtime on a per-connection basis.                                                                                                |
    | `void`                                    | `endRequest``()`<br>Declares that the request that was in progress on this connection has completed.                                                                                |
    | [`ReplayStatistics`](ReplayStatistics.md) | `getReplayStatistics``(`[`ReplayableConnection.StatisticsReportType`](ReplayableConnection.StatisticsReportType.md)` reportType)`<br>Obtains replay statistics accumulated so far.  |

<!-- -->

- - ### Method Detail

    - #### beginRequest

          void beginRequest()
                     throws SQLException

      Declares that a request to the server is starting on this connection. When called after another beginRequest() but before an endRequest(), this call is a no-op and does not throw any exception. Therefore, application is allowed to call beginRequest after a connection pool checkout, which implicitly calls beginRequest.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - When called with an open transaction on this connection.

    <!-- -->

    - #### endRequest

          void endRequest()
                   throws SQLException

      Declares that the request that was in progress on this connection has completed. Existing connection labels and state on the connection are not affected by this call. Calling endRequest() multiple times without beginRequest() in-between is allowed.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - When called with an open transaction on this connection.

    <!-- -->

    - #### disableReplay

          void disableReplay()
                      throws SQLException

      Allows disabling replay at runtime on a per-connection basis. This does not affect replay that is already in-progress.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getReplayStatistics

          ReplayStatistics getReplayStatistics(ReplayableConnection.StatisticsReportType reportType)

      Obtains replay statistics accumulated so far. These reflect either replay actions on the current connection, or across all the connections created by the underlying data source. When the argument value is false, it is recommended that the call be made when there are few new connections opened.
      Parameters:
      `reportType` - The type of statistics report.

      Returns:
      A replay statistics object containing all the metrics.

      See Also:
      `ReplayStatistics#StatisticsReportType`, [`OracleDataSource.getReplayStatistics()`](OracleDataSource.md)

    <!-- -->

    - #### clearReplayStatistics

          void clearReplayStatistics(ReplayableConnection.StatisticsReportType reportType)

      Clears replay statistics accumulated so far. This can be done on a per-connection basis, or applied to all connections. Future statistics reporting only reflects statistics updates accumulated after the latest clearing.
      Parameters:
      `reportType` - The type of statistics report.

      See Also:
      `ReplayStatistics#StatisticsReportType`, `ReplayStatistics#getReplayStatistics()`

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ReplayableConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXADataSourceImpl.md)
- [Next Class](ReplayableConnection.StatisticsReportType.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
