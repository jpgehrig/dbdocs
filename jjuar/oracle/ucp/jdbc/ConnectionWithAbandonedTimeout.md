Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionWithAbandonedTimeout.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionLabelingCallback.md)
- [Next Class](ConnectionWithTimeToLiveTimeout.md)

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

## Interface ConnectionWithAbandonedTimeout

-

  ------------------------------------------------------------------------



      public interface ConnectionWithAbandonedTimeout

  Interface supporting abandoned connection timeout handling for JDBC `java.sql.Connections`.
  A connection is considered abandoned when there is no activity from the connection to the backend resource for an extended period. By default, the connection pool reclaims the physical connection when a connection is determined to be abandoned.

  The Universal Connection Pool supports the `abandonedConnectionTimeout` pool property and provides `AbandonedConnectionTimeoutCallback` to allow customized handling of abandoned connections.

  Applications use this interface along with the `abandonedConnectionTimeout` properties for complete abandoned-connection handling.

  See Also:
  [`PoolDataSource`](PoolDataSource.md), [`AbandonedConnectionTimeoutCallback`](../AbandonedConnectionTimeoutCallback.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                         |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `registerAbandonedConnectionTimeoutCallback``(`[`AbandonedConnectionTimeoutCallback`](../AbandonedConnectionTimeoutCallback.md)` cbk)`<br>Registers `AbandonedConnectionTimeoutCallback` with this connection. |
    | `void`            | `removeAbandonedConnectionTimeoutCallback``()`<br>Removes the `AbandonedConnectionTimeoutCallback` object registered with this connection, if any.                                                             |

<!-- -->

- - ### Method Detail

    - #### registerAbandonedConnectionTimeoutCallback

          void registerAbandonedConnectionTimeoutCallback(AbandonedConnectionTimeoutCallback cbk)
                                                   throws java.sql.SQLException

      Registers `AbandonedConnectionTimeoutCallback` with this connection.
      Parameters:
      `cbk` - The `AbandonedConnectionTimeoutCallback` object to be registered.

      Throws:
      `java.sql.SQLException` - If there is a callback already registered with the connection.

    <!-- -->

    - #### removeAbandonedConnectionTimeoutCallback

          void removeAbandonedConnectionTimeoutCallback()
                                                 throws java.sql.SQLException

      Removes the `AbandonedConnectionTimeoutCallback` object registered with this connection, if any.
      Throws:
      `java.sql.SQLException` - If callback removal fails.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionWithAbandonedTimeout.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionLabelingCallback.md)
- [Next Class](ConnectionWithTimeToLiveTimeout.md)

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
