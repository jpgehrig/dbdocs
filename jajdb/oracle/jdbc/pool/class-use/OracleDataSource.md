Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleDataSource.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

## Uses of Class oracle.jdbc.pool.OracleDataSource

- **Packages that use [OracleDataSource](../OracleDataSource.md)**

  | Package            | Description                                                         |
  |--------------------|---------------------------------------------------------------------|
  | oracle.jdbc.pool   | A package of connection cache and pooling related classes.          |
  | oracle.jdbc.replay | Provides interfaces and factory methods for Application Continuity. |
  | oracle.jdbc.xa     | Provides classes that implement the JDBC XA APIs.                   |

- - ### Uses of [OracleDataSource](../OracleDataSource.md) in [oracle.jdbc.pool](../package-summary.md)

    **Subclasses of [OracleDataSource](../OracleDataSource.md) in [oracle.jdbc.pool](../package-summary.md)**

    | Modifier and Type | Class and Description                                                                                                                |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`OracleConnectionPoolDataSource`](../OracleConnectionPoolDataSource.md)<br>A DataSource object is a factory for Connection objects. |
    | `class `          | [`OracleOCIConnectionPool`](../OracleOCIConnectionPool.md)<br>A type-2 driver connection pool.                                       |

    **Methods in [oracle.jdbc.pool](../package-summary.md) with parameters of type [OracleDataSource](../OracleDataSource.md)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    |-------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected void`                                                                                | OracleDataSource.[`copy`](../OracleDataSource.md)`(`[`OracleDataSource`](../OracleDataSource.md)` ds)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `protected void`                                                                                | OracleDataSource.[`copy`](../OracleDataSource.md)`(`[`OracleDataSource`](../OracleDataSource.md)` ds)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | OracleConnectionCacheManager.[`createCache`](../OracleConnectionCacheManager.md)`(`[`OracleDataSource`](../OracleDataSource.md)` ods, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` cacheProperties)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Creates a connection cache using an auto-generated Connection Cache name, and the supplied Connection Cache Properties. The Connection Cache created is associated with the DataSource Object provided.                                                                                                |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | OracleConnectionCacheManager.[`createCache`](../OracleConnectionCacheManager.md)`(`[`OracleDataSource`](../OracleDataSource.md)` ods, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` cacheProperties)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Creates a connection cache using an auto-generated Connection Cache name, and the supplied Connection Cache Properties. The Connection Cache created is associated with the DataSource Object provided.                                                                                                |
    | `void`                                                                                          | OracleConnectionCacheManager.[`createCache`](../OracleConnectionCacheManager.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName, `[`OracleDataSource`](../OracleDataSource.md)` ods, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` cacheProperties)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Creates a connection cache using the supplied Connection Cache name, and the Connection Cache Properties. The Connection Cache created is associated with the DataSource Object provided. |
    | `void`                                                                                          | OracleConnectionCacheManager.[`createCache`](../OracleConnectionCacheManager.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` cacheName, `[`OracleDataSource`](../OracleDataSource.md)` ods, `[`Properties`](http://download.oracle.com/javase/8/docs/api/java/util/Properties.html?is-external=true)` cacheProperties)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. Creates a connection cache using the supplied Connection Cache name, and the Connection Cache Properties. The Connection Cache created is associated with the DataSource Object provided. |

  - ### Uses of [OracleDataSource](../OracleDataSource.md) in [oracle.jdbc.replay](../../replay/package-summary.md)

    **Fields in [oracle.jdbc.replay](../../replay/package-summary.md) declared as [OracleDataSource](../OracleDataSource.md)**

    | Modifier and Type                                        | Field and Description                                                            |
    |----------------------------------------------------------|----------------------------------------------------------------------------------|
    | `protected `[`OracleDataSource`](../OracleDataSource.md) | OracleDataSourceImpl.[`ods`](../../replay/OracleDataSourceImpl.md)               |
    | `protected `[`OracleDataSource`](../OracleDataSource.md) | OracleDataSourceImpl.[`ods`](../../replay/OracleDataSourceImpl.md)               |
    | `protected `[`OracleDataSource`](../OracleDataSource.md) | OracleDataSourceImpl.[`odsReconnectOnly`](../../replay/OracleDataSourceImpl.md)  |
    | `protected `[`OracleDataSource`](../OracleDataSource.md) | OracleDataSourceImpl.[`odsReconnectOnly`](../../replay/OracleDataSourceImpl.md)  |

  - ### Uses of [OracleDataSource](../OracleDataSource.md) in [oracle.jdbc.xa](../../xa/package-summary.md)

    **Subclasses of [OracleDataSource](../OracleDataSource.md) in [oracle.jdbc.xa](../../xa/package-summary.md)**

    | Modifier and Type | Class and Description                                                                         |
    |-------------------|-----------------------------------------------------------------------------------------------|
    | `class `          | [`OracleXADataSource`](../../xa/OracleXADataSource.md)<br>A factory for XAConnection objects. |

    **Methods in [oracle.jdbc.xa](../../xa/package-summary.md) with parameters of type [OracleDataSource](../OracleDataSource.md)**

    | Modifier and Type | Method and Description                                                                                            |
    |-------------------|-------------------------------------------------------------------------------------------------------------------|
    | `protected void`  | OracleXADataSource.[`copy`](../../xa/OracleXADataSource.md)`(`[`OracleDataSource`](../OracleDataSource.md)` ds)`  |
    | `protected void`  | OracleXADataSource.[`copy`](../../xa/OracleXADataSource.md)`(`[`OracleDataSource`](../OracleDataSource.md)` ds)`  |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleDataSource.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
