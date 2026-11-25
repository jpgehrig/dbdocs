Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionWithTimeToLiveTimeout.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionWithAbandonedTimeout.md)
- [Next Class](HarvestableConnection.md)

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

## Interface ConnectionWithTimeToLiveTimeout

-

  ------------------------------------------------------------------------



      public interface ConnectionWithTimeToLiveTimeout

  Interface supporting time-to-live connection timeout handling for JDBC `java.sql.Connections`.
  A time-to-live connection allows a borrowed connection to remain borrowed only for a pre-determined period of time. When this period passes, this connection is reclaimed and put back into the connection pool.

  The Universal Connection Pool supports the `timeToLiveConnectionTimeout` pool property and provides `TimeToLiveConnectionTimeoutCallback` to allow customized handling of TTL timed-out connections.

  Applications use this interface along with the `timeToLiveConnectionTimeout` properties for complete TTL-connection handling.

  See Also:
  [`PoolDataSource`](PoolDataSource.md), [`TimeToLiveConnectionTimeoutCallback`](../TimeToLiveConnectionTimeoutCallback.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                  |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `registerTimeToLiveConnectionTimeoutCallback``(`[`TimeToLiveConnectionTimeoutCallback`](../TimeToLiveConnectionTimeoutCallback.md)` cbk)`<br>Registers a time-to-live connection timeout callback with this connection. |
    | `void`            | `removeTimeToLiveConnectionTimeoutCallback``()`<br>Removes the `TimeToLiveConnectionTimeoutCallback` object registered with this connection, if any.                                                                    |

<!-- -->

- - ### Method Detail

    - #### registerTimeToLiveConnectionTimeoutCallback

          void registerTimeToLiveConnectionTimeoutCallback(TimeToLiveConnectionTimeoutCallback cbk)
                                                    throws java.sql.SQLException

      Registers a time-to-live connection timeout callback with this connection.
      Parameters:
      `cbk` - The `TimeToLiveConnectionTimeoutCallback` object to be registered.

      Throws:
      `java.sql.SQLException` - If there is a callback already registered with the connection.

    <!-- -->

    - #### removeTimeToLiveConnectionTimeoutCallback

          void removeTimeToLiveConnectionTimeoutCallback()
                                                  throws java.sql.SQLException

      Removes the `TimeToLiveConnectionTimeoutCallback` object registered with this connection, if any.
      Throws:
      `java.sql.SQLException` - If callback removal fails.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionWithTimeToLiveTimeout.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionWithAbandonedTimeout.md)
- [Next Class](HarvestableConnection.md)

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
