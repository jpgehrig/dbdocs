Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UniversalConnectionPool.md)
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

## Uses of Interface oracle.ucp.UniversalConnectionPool

- **Packages that use [UniversalConnectionPool](../UniversalConnectionPool.md)**

  | Package          | Description                                                                                                       |
  |------------------|-------------------------------------------------------------------------------------------------------------------|
  | oracle.ucp       | Includes both required and optional callback interfaces that are used to implement connection pool features.      |
  | oracle.ucp.admin | Defines interfaces for administering Universal Connection Pool instances, including JMX support.                  |
  | oracle.ucp.jdbc  | Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool. |

- - ### Uses of [UniversalConnectionPool](../UniversalConnectionPool.md) in [oracle.ucp](../package-summary.md)

    **Methods in [oracle.ucp](../package-summary.md) that return [UniversalConnectionPool](../UniversalConnectionPool.md)**

    | Modifier and Type                                          | Method and Description                                                                                                                                                         |
    |------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UniversalConnectionPool`](../UniversalConnectionPool.md) | UniversalConnectionPoolAdapter.[`createUniversalConnectionPool`](../UniversalConnectionPoolAdapter.md)`()`<br>Creates a Universal Connection Pool instance using this adapter. |

    **Methods in [oracle.ucp](../package-summary.md) with parameters of type [UniversalConnectionPool](../UniversalConnectionPool.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                  |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | ConnectionFactoryAdapter.[`setUniversalConnectionPool`](../ConnectionFactoryAdapter.md)`(`[`UniversalConnectionPool`](../UniversalConnectionPool.md)` connectionPool)`<br>Sets the connection pool that interacts with this connection factory adapter. |

  - ### Uses of [UniversalConnectionPool](../UniversalConnectionPool.md) in [oracle.ucp.admin](../admin/package-summary.md)

    **Methods in [oracle.ucp.admin](../admin/package-summary.md) that return [UniversalConnectionPool](../UniversalConnectionPool.md)**

    | Modifier and Type                                          | Method and Description                                                                                                                                                                                                   |
    |------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UniversalConnectionPool`](../UniversalConnectionPool.md) | UniversalConnectionPoolManager.[`getConnectionPool`](../admin/UniversalConnectionPoolManager.md)`(java.lang.String poolName)`<br>Gets the Universal Connection Pool instance from the Universal Connection Pool Manager. |

    **Methods in [oracle.ucp.admin](../admin/package-summary.md) with parameters of type [UniversalConnectionPool](../UniversalConnectionPool.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                  |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | UniversalConnectionPoolManager.[`setConnectionPool`](../admin/UniversalConnectionPoolManager.md)`(`[`UniversalConnectionPool`](../UniversalConnectionPool.md)` connectionPool)`<br>Sets the Universal Connection Pool with the `UniversalConnectionPoolManager` Object. |

  - ### Uses of [UniversalConnectionPool](../UniversalConnectionPool.md) in [oracle.ucp.jdbc](../jdbc/package-summary.md)

    **Methods in [oracle.ucp.jdbc](../jdbc/package-summary.md) that return [UniversalConnectionPool](../UniversalConnectionPool.md)**

    | Modifier and Type                                          | Method and Description                                                                                                                                      |
    |------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UniversalConnectionPool`](../UniversalConnectionPool.md) | PoolDataSourceImpl.[`createUniversalConnectionPool`](../jdbc/PoolDataSourceImpl.md)`()`<br>Creates a Universal Connection Pool instance using this adapter. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UniversalConnectionPool.md)
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
