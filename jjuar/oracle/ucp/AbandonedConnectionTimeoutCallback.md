Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AbandonedConnectionTimeoutCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev Class
- [Next Class](ConnectionAffinityCallback.md)

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

## Interface AbandonedConnectionTimeoutCallback

-

  ------------------------------------------------------------------------



      public interface AbandonedConnectionTimeoutCallback

  The callback interface for the abandoned connection timeout feature. This allows applications to provide customized handling for abandoned connections. Also see the related properties on `UniversalConnectionPool` and `PoolDataSource`.
  The callback object is optionally registered with each pooled connection or using any of its logical connection proxies, allowing applications to perform customized handling when this particular connection is deemed abandoned by the pool.

  The `handleTimedOutConnection(...)` method is invoked when a borrowed connection is deemed abandoned by the Universal Connection Pool. Applications can choose to completely override the pool's handling, invoke additional handling actions, or simply assume the pool's default handling. For example, JDBC applications can invoke `cancel()`, `close()` and `rollback()` methods on the abandoned connection within this method.

  It is an error to register more than one `AbandonedConnectionTimeoutCallback` on the same connection. Any such attempt will result in a `UniversalConnectionPoolException` at the pool layer, or an exception specific to the type of a Universal Connection Pool Adapter (for example, JDBC, JCA, and so forth) like `java.sql.SQLException.`

  See Also:
  [`UniversalConnectionPool`](UniversalConnectionPool.md), [`UniversalPooledConnection`](UniversalPooledConnection.md), [`PoolDataSource`](jdbc/PoolDataSource.md), [`ConnectionWithAbandonedTimeout`](jdbc/ConnectionWithAbandonedTimeout.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                       |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `handleTimedOutConnection``()`<br>Sets whether or not the connection pool is responsible for handling abandoned connections. |

<!-- -->

- - ### Method Detail

    - #### handleTimedOutConnection

          boolean handleTimedOutConnection()

      Sets whether or not the connection pool is responsible for handling abandoned connections. This method is called by the connection pool on the connection that is deemed abandoned to allow applications to customize abandoned connection handling.
      The method implementation must return `true` if the application handles the `abandonedConnectionTimeout` in place of the pool, and must return `false` if the application wants the pool to take over the abandoned connection handling. In the former case, applications have the option of simply holding on to the borrowed connection or performing some actions and returning the abandoned connection to the pool. For the pool layer, this means calling `returnConnection()`; while, for the pool adapter layer, this means calling `close()` on the connection proxy.

      Returns:
      If the application's customized handling overrides the pool's actions, return `true`; otherwise, return `false`.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/AbandonedConnectionTimeoutCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev Class
- [Next Class](ConnectionAffinityCallback.md)

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
