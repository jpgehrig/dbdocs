Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TimeToLiveConnectionTimeoutCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](NoAvailableConnectionsException.md)
- [Next Class](UniversalConnectionPool.md)

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

## Interface TimeToLiveConnectionTimeoutCallback

-

  ------------------------------------------------------------------------



      public interface TimeToLiveConnectionTimeoutCallback

  The callback interface for the time-to-live (TTL) connection timeout feature. This allows applications to provide customized handling for TTL timed-out connections. Also, see the related properties on `UniversalConnectionPool` and `PoolDataSource`.
  The callback object is optionally registered with each pooled connection or using any of its logical connection proxies, allowing applications to perform customized handling when this particular connection has TTL timed-out.

  The `handleTimedOutConnection(...)` method is invoked when a borrowed connection is found to be TTL timed-out by the Universal Connection Pool. Applications can choose to completely override the pool's handling, invoke additional handling actions, or simply assume the pool's default handling. For example, JDBC applications can invoke `cancel()`, `close()`, and `rollback()` methods on the TTL timed-out connection within this method.

  It is an error to register more than one `TimeToLiveConnectionTimeoutCallbacks` on the same connection. Any such attempt will result in a `UniversalConnectionPoolException` at the pool layer, or an exception specific to the type of a Universal Connection Pool Adapter (e.g., JDBC, JCA, and so forth) like `java.sql.SQLException`.

  See Also:
  [`UniversalConnectionPool`](UniversalConnectionPool.md), [`UniversalPooledConnection`](UniversalPooledConnection.md), [`PoolDataSource`](jdbc/PoolDataSource.md), [`ConnectionWithTimeToLiveTimeout`](jdbc/ConnectionWithTimeToLiveTimeout.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                    |
    |-------------------|-----------------------------------------------------------------------------------------------------------|
    | `boolean`         | `handleTimedOutConnection``()`<br>Returns whether or not and application handles TTL timeout connections. |

<!-- -->

- - ### Method Detail

    - #### handleTimedOutConnection

          boolean handleTimedOutConnection()

      Returns whether or not and application handles TTL timeout connections.
      This method is called by the connection pool on the connection that has TTL timed-out to allow applications to customize the TTL timed-out connection handling.

      The method implementation must return `true` if the application handles the `timeToLiveConnectionTimeout` in place of the pool and must return `false` if the application wants the pool to take over the TTL-timeout connection handling. In the former case, applications have the option of simply holding on to the borrowed connection or performing some actions and returning the timed-out connection to the pool. For the pool layer, this means calling `returnConnection()`; while, for the pool adapter layer, this means calling `close()` on the connection proxy.

      Returns:
      If the application's customized handling overrides the pool's actions, return `true`; otherwise, return `false`.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/TimeToLiveConnectionTimeoutCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](NoAvailableConnectionsException.md)
- [Next Class](UniversalConnectionPool.md)

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
