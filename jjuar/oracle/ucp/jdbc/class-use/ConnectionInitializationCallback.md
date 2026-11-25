Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ConnectionInitializationCallback.md)
- Use
- [Tree](../../../../overview-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-files/index-1.md)
- [Help](../../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

## Uses of Interface oracle.ucp.jdbc.ConnectionInitializationCallback

- **Packages that use [ConnectionInitializationCallback](../ConnectionInitializationCallback.md)**

  | Package         | Description                                                                                                       |
  |-----------------|-------------------------------------------------------------------------------------------------------------------|
  | oracle.ucp.jdbc | Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool. |

- - ### Uses of [ConnectionInitializationCallback](../ConnectionInitializationCallback.md) in [oracle.ucp.jdbc](../package-summary.md)

    **Methods in [oracle.ucp.jdbc](../package-summary.md) that return [ConnectionInitializationCallback](../ConnectionInitializationCallback.md)**

    | Modifier and Type                                                            | Method and Description                                                                                                                                         |
    |------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ConnectionInitializationCallback`](../ConnectionInitializationCallback.md) | PoolDataSource.[`getConnectionInitializationCallback`](../PoolDataSource.md)`()`<br>Obtains the registered connection initialization callback, if any.         |
    | [`ConnectionInitializationCallback`](../ConnectionInitializationCallback.md) | PoolDataSourceImpl.[`getConnectionInitializationCallback`](../PoolDataSourceImpl.md)`()`<br>Obtains the registered connection initialization callback, if any. |

    **Methods in [oracle.ucp.jdbc](../package-summary.md) with parameters of type [ConnectionInitializationCallback](../ConnectionInitializationCallback.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                             |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | PoolDataSource.[`registerConnectionInitializationCallback`](../PoolDataSource.md)`(`[`ConnectionInitializationCallback`](../ConnectionInitializationCallback.md)` cbk)`<br>Registers a connection initialization callback.         |
    | `void`            | PoolDataSourceImpl.[`registerConnectionInitializationCallback`](../PoolDataSourceImpl.md)`(`[`ConnectionInitializationCallback`](../ConnectionInitializationCallback.md)` cbk)`<br>Registers a connection initialization callback. |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ConnectionInitializationCallback.md)
- Use
- [Tree](../../../../overview-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-files/index-1.md)
- [Help](../../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
