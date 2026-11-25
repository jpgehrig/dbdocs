Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../PoolDataSource.md)
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

## Uses of Interface oracle.ucp.jdbc.PoolDataSource

- **Packages that use [PoolDataSource](../PoolDataSource.md)**

  | Package         | Description                                                                                                       |
  |-----------------|-------------------------------------------------------------------------------------------------------------------|
  | oracle.ucp.jdbc | Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool. |

- - ### Uses of [PoolDataSource](../PoolDataSource.md) in [oracle.ucp.jdbc](../package-summary.md)

    **Subinterfaces of [PoolDataSource](../PoolDataSource.md) in [oracle.ucp.jdbc](../package-summary.md)**

    | Modifier and Type | Interface and Description                                                                           |
    |-------------------|-----------------------------------------------------------------------------------------------------|
    | `interface `      | [`PoolXADataSource`](../PoolXADataSource.md)<br>A Universal Connection Pool-enabled XA data source. |

    **Classes in [oracle.ucp.jdbc](../package-summary.md) that implement [PoolDataSource](../PoolDataSource.md)**

    | Modifier and Type | Class and Description                                                                        |
    |-------------------|----------------------------------------------------------------------------------------------|
    | `class `          | [`PoolDataSourceImpl`](../PoolDataSourceImpl.md)<br>A connection pool-aware data source.     |
    | `class `          | [`PoolXADataSourceImpl`](../PoolXADataSourceImpl.md)<br>A connection pool-aware data source. |

    **Methods in [oracle.ucp.jdbc](../package-summary.md) that return [PoolDataSource](../PoolDataSource.md)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                |
    |---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`PoolDataSource`](../PoolDataSource.md) | PoolDataSourceFactory.[`getPoolDataSource`](../PoolDataSourceFactory.md)`()`<br>Obtains a pool-enabled `PoolDataSource` instance.                                                     |
    | `static `[`PoolDataSource`](../PoolDataSource.md) | PoolDataSourceFactory.[`getPoolDataSource`](../PoolDataSourceFactory.md)`(java.util.Properties configuration)`<br>Creates and configures a new data source to a shared pool instance. |
    | `static `[`PoolDataSource`](../PoolDataSource.md) | PoolDataSourceFactory.[`getPoolDataSource`](../PoolDataSourceFactory.md)`(java.lang.String dataSourceName)`<br>Obtains a pool-enabled `PoolDataSource` instance.                      |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../PoolDataSource.md)
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
