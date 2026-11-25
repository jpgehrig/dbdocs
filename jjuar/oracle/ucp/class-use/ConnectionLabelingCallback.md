Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ConnectionLabelingCallback.md)
- Use
- [Tree](../../../overview-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

## Uses of Interface oracle.ucp.ConnectionLabelingCallback

- **Packages that use [ConnectionLabelingCallback](../ConnectionLabelingCallback.md)**

  | Package         | Description                                                                                                       |
  |-----------------|-------------------------------------------------------------------------------------------------------------------|
  | oracle.ucp      | Includes both required and optional callback interfaces that are used to implement connection pool features.      |
  | oracle.ucp.jdbc | Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool. |

- - ### Uses of [ConnectionLabelingCallback](../ConnectionLabelingCallback.md) in [oracle.ucp](../package-summary.md)

    **Methods in [oracle.ucp](../package-summary.md) with parameters of type [ConnectionLabelingCallback](../ConnectionLabelingCallback.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | UniversalConnectionPool.[`registerConnectionLabelingCallback`](../UniversalConnectionPool.md)`(`[`ConnectionLabelingCallback`](../ConnectionLabelingCallback.md)` cbk)`<br>Registers a `ConnectionLabelingCallback` object with this connection pool. |

  - ### Uses of [ConnectionLabelingCallback](../ConnectionLabelingCallback.md) in [oracle.ucp.jdbc](../jdbc/package-summary.md)

    **Subinterfaces of [ConnectionLabelingCallback](../ConnectionLabelingCallback.md) in [oracle.ucp.jdbc](../jdbc/package-summary.md)**

    | Modifier and Type | Interface and Description                                                                                                        |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------|
    | `interface `      | [`ConnectionLabelingCallback`](../jdbc/ConnectionLabelingCallback.md)<br>New callback interface for connection labeling support. |

    **Methods in [oracle.ucp.jdbc](../jdbc/package-summary.md) with parameters of type [ConnectionLabelingCallback](../ConnectionLabelingCallback.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                            |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | PoolDataSource.[`registerConnectionLabelingCallback`](../jdbc/PoolDataSource.md)`(`[`ConnectionLabelingCallback`](../ConnectionLabelingCallback.md)` cbk)`<br>Registers a connection labeling callback with the underlying connection pool.       |
    | `void`            | PoolDataSourceImpl.[`registerConnectionLabelingCallback`](../jdbc/PoolDataSourceImpl.md)`(`[`ConnectionLabelingCallback`](../ConnectionLabelingCallback.md)` cbk)`<br>Registers a ConnectionLabelingCallback with the underlying connection pool. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ConnectionLabelingCallback.md)
- Use
- [Tree](../../../overview-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
