Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionHarvestingCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionFactoryAdapter.md)
- [Next Class](ConnectionLabelingCallback.md)

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

## Interface ConnectionHarvestingCallback

-

  ------------------------------------------------------------------------



      public interface ConnectionHarvestingCallback

  The callback interface for the connection harvesting support. Applications using the connection harvesting feature can optionally provide an implementation of this interface.
  The callback object is registered with each harvestable pooled connection or using any of its logical connection proxies, allowing applications to perform customized cleanup tasks when this connection is harvested by the pool.

  The `cleanup(...)` method is invoked when a borrowed connection is harvested by the Universal Connection Pool. Applications using `java.sql.Connection`, for instance, can invoke the `close()` and `rollback()` methods on this Connection within a `cleanup()` implementation.

  It is an error to register more than one connection harvesting callback on the same connection. Any such attempt results in a `UniversalConnectionPoolException` at the pool layer or an exception specific to the type of a Universal Connection Pool Adapter (for example, JDBC, JCA, and so forth).

  See Also:
  [`UniversalConnectionPool`](UniversalConnectionPool.md), [`UniversalPooledConnection`](UniversalPooledConnection.md), [`PoolDataSource`](jdbc/PoolDataSource.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                            |
    |-------------------|-------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `cleanup``()`<br>Cleans up a connection being harvested before the connection is returned to the connection pool. |

<!-- -->

- - ### Method Detail

    - #### cleanup

          boolean cleanup()

      Cleans up a connection being harvested before the connection is returned to the connection pool. This method is called by the connection pool on the connection being harvested.
      Returns:
      If the cleanup is successful, return `true`; otherwise, return `false`.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/ConnectionHarvestingCallback.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](ConnectionFactoryAdapter.md)
- [Next Class](ConnectionLabelingCallback.md)

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
