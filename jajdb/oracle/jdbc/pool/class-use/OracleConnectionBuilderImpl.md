Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleConnectionBuilderImpl.md)
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

## Uses of Class oracle.jdbc.pool.OracleConnectionBuilderImpl

- **Packages that use [OracleConnectionBuilderImpl](../OracleConnectionBuilderImpl.md)**

  | Package            | Description                                                         |
  |--------------------|---------------------------------------------------------------------|
  | oracle.jdbc.pool   | A package of connection cache and pooling related classes.          |
  | oracle.jdbc.replay | Provides interfaces and factory methods for Application Continuity. |
  | oracle.jdbc.xa     | Provides classes that implement the JDBC XA APIs.                   |

- - ### Uses of [OracleConnectionBuilderImpl](../OracleConnectionBuilderImpl.md) in [oracle.jdbc.pool](../package-summary.md)

    **Methods in [oracle.jdbc.pool](../package-summary.md) that return [OracleConnectionBuilderImpl](../OracleConnectionBuilderImpl.md)**

    | Modifier and Type                                                  | Method and Description                                                                                                                                                                                                                                                               |
    |--------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`accessToken`](../OracleConnectionBuilderImpl.md)`(`[`AccessToken`](../../AccessToken.md)` accessToken)`<br>Sets the [`accessToken(oracle.jdbc.AccessToken)`](../OracleConnectionBuilderImpl.md) field of this builder.                                 |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`accessToken`](../OracleConnectionBuilderImpl.md)`(`[`AccessToken`](../../AccessToken.md)` accessToken)`<br>Sets the [`accessToken(oracle.jdbc.AccessToken)`](../OracleConnectionBuilderImpl.md) field of this builder.                                 |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleDataSource.[`createConnectionBuilder`](../OracleDataSource.md)`()`<br>Creates a new instance                                                                                                                                                                                   |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleDataSource.[`createConnectionBuilder`](../OracleDataSource.md)`()`<br>Creates a new instance                                                                                                                                                                                   |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`gssCredential`](../OracleConnectionBuilderImpl.md)`(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection. |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`gssCredential`](../OracleConnectionBuilderImpl.md)`(`[`GSSCredential`](http://download.oracle.com/javase/8/docs/api/org/ietf/jgss/GSSCredential.html?is-external=true)` credential)`<br>Provide the GSSCredential used to authenticate the connection. |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`instanceName`](../OracleConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` instanceName)`                                                                                    |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`instanceName`](../OracleConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` instanceName)`                                                                                    |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`password`](../OracleConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                            |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`password`](../OracleConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` password)`                                                                                            |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`serviceName`](../OracleConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` serviceName)`                                                                                      |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`serviceName`](../OracleConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` serviceName)`                                                                                      |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`shardingKey`](../OracleConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../../OracleShardingKey.md)` shardingKey)`                                                                                                                                    |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`shardingKey`](../OracleConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../../OracleShardingKey.md)` shardingKey)`                                                                                                                                    |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`sslContext`](../OracleConnectionBuilderImpl.md)`(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Set the SSLContext on this builder.                                     |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`sslContext`](../OracleConnectionBuilderImpl.md)`(`[`SSLContext`](http://download.oracle.com/javase/8/docs/api/javax/net/ssl/SSLContext.html?is-external=true)` sslContext)`<br>Set the SSLContext on this builder.                                     |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`superShardingKey`](../OracleConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../../OracleShardingKey.md)` superShardingKey)`                                                                                                                          |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`superShardingKey`](../OracleConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../../OracleShardingKey.md)` superShardingKey)`                                                                                                                          |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`user`](../OracleConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                    |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleConnectionBuilderImpl.[`user`](../OracleConnectionBuilderImpl.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` user)`                                                                                                    |

    **Methods in [oracle.jdbc.pool](../package-summary.md) with parameters of type [OracleConnectionBuilderImpl](../OracleConnectionBuilderImpl.md)**

    | Modifier and Type                                                                                      | Method and Description                                                                                                                                                            |
    |--------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | OracleDataSource.[`getConnection`](../OracleDataSource.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` builder)`                                        |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | OracleDataSource.[`getConnection`](../OracleDataSource.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` builder)`                                        |
    | `protected `[`OraclePooledConnection`](../OraclePooledConnection.md)                                   | OracleConnectionPoolDataSource.[`getPooledConnection`](../OracleConnectionPoolDataSource.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBuilder)`  |
    | `protected `[`OraclePooledConnection`](../OraclePooledConnection.md)                                   | OracleConnectionPoolDataSource.[`getPooledConnection`](../OracleConnectionPoolDataSource.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBuilder)`  |

  - ### Uses of [OracleConnectionBuilderImpl](../OracleConnectionBuilderImpl.md) in [oracle.jdbc.replay](../../replay/package-summary.md)

    **Methods in [oracle.jdbc.replay](../../replay/package-summary.md) that return [OracleConnectionBuilderImpl](../OracleConnectionBuilderImpl.md)**

    | Modifier and Type                                                  | Method and Description                                                                                                                       |
    |--------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleDataSourceImpl.[`createConnectionBuilder`](../../replay/OracleDataSourceImpl.md)`()`<br>Creates a new OracleConnectionBuilder instance |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleDataSourceImpl.[`createConnectionBuilder`](../../replay/OracleDataSourceImpl.md)`()`<br>Creates a new OracleConnectionBuilder instance |

    **Methods in [oracle.jdbc.replay](../../replay/package-summary.md) with parameters of type [OracleConnectionBuilderImpl](../OracleConnectionBuilderImpl.md)**

    | Modifier and Type                                                                                                  | Method and Description                                                                                                                                                                                                                                                                           |
    |--------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | OracleDataSourceImpl.[`enableACAndProxifyIfNecessary`](../../replay/OracleDataSourceImpl.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBuilder)`  |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | OracleDataSourceImpl.[`enableACAndProxifyIfNecessary`](../../replay/OracleDataSourceImpl.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBuilder)`  |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | OracleDataSourceImpl.[`getConnection`](../../replay/OracleDataSourceImpl.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBldr)`                                                                                                                                    |
    | `protected `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true) | OracleDataSourceImpl.[`getConnection`](../../replay/OracleDataSourceImpl.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBldr)`                                                                                                                                    |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | OracleDataSourceImpl.[`getConnectionNoProxy`](../../replay/OracleDataSourceImpl.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBuilder)`                                                                                                                          |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)             | OracleDataSourceImpl.[`getConnectionNoProxy`](../../replay/OracleDataSourceImpl.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBuilder)`                                                                                                                          |
    | `protected `[`OraclePooledConnection`](../OraclePooledConnection.md)                                               | OracleConnectionPoolDataSourceImpl.[`getPooledConnection`](../../replay/OracleConnectionPoolDataSourceImpl.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBuilder)`                                                                                               |
    | `protected `[`OraclePooledConnection`](../OraclePooledConnection.md)                                               | OracleConnectionPoolDataSourceImpl.[`getPooledConnection`](../../replay/OracleConnectionPoolDataSourceImpl.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBuilder)`                                                                                               |

  - ### Uses of [OracleConnectionBuilderImpl](../OracleConnectionBuilderImpl.md) in [oracle.jdbc.xa](../../xa/package-summary.md)

    **Methods in [oracle.jdbc.xa](../../xa/package-summary.md) that return [OracleConnectionBuilderImpl](../OracleConnectionBuilderImpl.md)**

    | Modifier and Type                                                  | Method and Description                                                                                                                                                                                                                                                                                          |
    |--------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`getOracleConnectionBuilder`](../../xa/OracleXAConnectionBuilderImpl.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBldr)`<br>Utility method to set all the builder attributes on a Connection builder from this XA connection builder instance . |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`getOracleConnectionBuilder`](../../xa/OracleXAConnectionBuilderImpl.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBldr)`<br>Utility method to set all the builder attributes on a Connection builder from this XA connection builder instance . |

    **Methods in [oracle.jdbc.xa](../../xa/package-summary.md) with parameters of type [OracleConnectionBuilderImpl](../OracleConnectionBuilderImpl.md)**

    | Modifier and Type                                                  | Method and Description                                                                                                                                                                                                                                                                                          |
    |--------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`getOracleConnectionBuilder`](../../xa/OracleXAConnectionBuilderImpl.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBldr)`<br>Utility method to set all the builder attributes on a Connection builder from this XA connection builder instance . |
    | [`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`getOracleConnectionBuilder`](../../xa/OracleXAConnectionBuilderImpl.md)`(`[`OracleConnectionBuilderImpl`](../OracleConnectionBuilderImpl.md)` connBldr)`<br>Utility method to set all the builder attributes on a Connection builder from this XA connection builder instance . |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleConnectionBuilderImpl.md)
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
