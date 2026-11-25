Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ConnectionAffinityCallback.md)
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

## Uses of Interface oracle.ucp.ConnectionAffinityCallback

- **Packages that use [ConnectionAffinityCallback](../ConnectionAffinityCallback.md)**

  | Package         | Description                                                                                                       |
  |-----------------|-------------------------------------------------------------------------------------------------------------------|
  | oracle.ucp      | Includes both required and optional callback interfaces that are used to implement connection pool features.      |
  | oracle.ucp.jdbc | Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool. |

- - ### Uses of [ConnectionAffinityCallback](../ConnectionAffinityCallback.md) in [oracle.ucp](../package-summary.md)

    **Methods in [oracle.ucp](../package-summary.md) with parameters of type [ConnectionAffinityCallback](../ConnectionAffinityCallback.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                            |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | UniversalConnectionPool.[`registerConnectionAffinityCallback`](../UniversalConnectionPool.md)`(`[`ConnectionAffinityCallback`](../ConnectionAffinityCallback.md)` cbk)`<br>Registers a `ConnectionAffinityCallback` objet on the connection pool. |

  - ### Uses of [ConnectionAffinityCallback](../ConnectionAffinityCallback.md) in [oracle.ucp.jdbc](../jdbc/package-summary.md)

    **Methods in [oracle.ucp.jdbc](../jdbc/package-summary.md) with parameters of type [ConnectionAffinityCallback](../ConnectionAffinityCallback.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                               |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | PoolDataSource.[`registerConnectionAffinityCallback`](../jdbc/PoolDataSource.md)`(`[`ConnectionAffinityCallback`](../ConnectionAffinityCallback.md)` cbk)`<br>Registers a connection affinity callback on the connection pool.       |
    | `void`            | PoolDataSourceImpl.[`registerConnectionAffinityCallback`](../jdbc/PoolDataSourceImpl.md)`(`[`ConnectionAffinityCallback`](../ConnectionAffinityCallback.md)` cbk)`<br>Registers a ConnectionAffinityCallback on the connection pool. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ConnectionAffinityCallback.md)
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
