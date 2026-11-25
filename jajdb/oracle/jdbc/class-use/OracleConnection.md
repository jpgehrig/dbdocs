Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleConnection.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

## Uses of Interface oracle.jdbc.OracleConnection

- **Packages that use [OracleConnection](../OracleConnection.md)**

  | Package          | Description                                                                                       |
  |------------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc      | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.jdbc.pool | A package of connection cache and pooling related classes.                                        |
  | oracle.sql       | A package of classes that represent java SQL types and Oracle specific SQL types.                 |

- - ### Uses of [OracleConnection](../OracleConnection.md) in [oracle.jdbc](../package-summary.md)

    **Classes in [oracle.jdbc](../package-summary.md) that implement [OracleConnection](../OracleConnection.md)**

    | Modifier and Type | Class and Description                                                                                                                           |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`OracleConnectionWrapper`](../OracleConnectionWrapper.md)<br>A simple implementation of a connection wrapper which may be nested to any depth. |

    **Fields in [oracle.jdbc](../package-summary.md) declared as [OracleConnection](../OracleConnection.md)**

    | Modifier and Type                                        | Field and Description                                                  |
    |----------------------------------------------------------|------------------------------------------------------------------------|
    | `protected `[`OracleConnection`](../OracleConnection.md) | OracleConnectionWrapper.[`connection`](../OracleConnectionWrapper.md)  |
    | `protected `[`OracleConnection`](../OracleConnection.md) | OracleConnectionWrapper.[`connection`](../OracleConnectionWrapper.md)  |

    **Methods in [oracle.jdbc](../package-summary.md) that return [OracleConnection](../OracleConnection.md)**

    | Modifier and Type                            | Method and Description                                                                                 |
    |----------------------------------------------|--------------------------------------------------------------------------------------------------------|
    | [`OracleConnection`](../OracleConnection.md) | OracleConnectionBuilder.[`build`](../OracleConnectionBuilder.md)`()`<br>Builds the connection object.  |
    | [`OracleConnection`](../OracleConnection.md) | OracleConnectionBuilder.[`build`](../OracleConnectionBuilder.md)`()`<br>Builds the connection object.  |
    | [`OracleConnection`](../OracleConnection.md) | OracleConnection.[`unwrap`](../OracleConnection.md)`()`<br>Return the wrapped object if any else null. |
    | [`OracleConnection`](../OracleConnection.md) | OracleConnectionWrapper.[`unwrap`](../OracleConnectionWrapper.md)`()`<br>Unwrap one level.             |
    | [`OracleConnection`](../OracleConnection.md) | OracleConnectionWrapper.[`unwrap`](../OracleConnectionWrapper.md)`()`<br>Unwrap one level.             |
    | [`OracleConnection`](../OracleConnection.md) | OracleConnection.[`unwrap`](../OracleConnection.md)`()`<br>Return the wrapped object if any else null. |

    **Methods in [oracle.jdbc](../package-summary.md) with parameters of type [OracleConnection](../OracleConnection.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                         |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OracleConnection.[`setWrapper`](../OracleConnection.md)`(`[`OracleConnection`](../OracleConnection.md)` wrapper)`<br>Set the wrapping object.                                                  |
    | `void`            | OracleConnectionWrapper.[`setWrapper`](../OracleConnectionWrapper.md)`(`[`OracleConnection`](../OracleConnection.md)` wrapper)`<br>Set a connection wrapper as the wrapper of this connection. |
    | `void`            | OracleConnectionWrapper.[`setWrapper`](../OracleConnectionWrapper.md)`(`[`OracleConnection`](../OracleConnection.md)` wrapper)`<br>Set a connection wrapper as the wrapper of this connection. |
    | `void`            | OracleConnection.[`setWrapper`](../OracleConnection.md)`(`[`OracleConnection`](../OracleConnection.md)` wrapper)`<br>Set the wrapping object.                                                  |

    **Constructors in [oracle.jdbc](../package-summary.md) with parameters of type [OracleConnection](../OracleConnection.md)**

    | Constructor and Description                                                                                                                                                                           |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleConnectionWrapper`](../OracleConnectionWrapper.md)`(`[`OracleConnection`](../OracleConnection.md)` toBeWrapped)`<br>Construct an instance which wraps the arguement                           |
    | [`OracleConnectionWrapper`](../OracleConnectionWrapper.md)`(`[`OracleConnection`](../OracleConnection.md)` toBeWrapped)`<br>Construct an instance which wraps the arguement                           |
    | [`OracleDatabaseMetaData`](../OracleDatabaseMetaData.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`<br>Deprecated. <br>-- Please use the factory method java.sql.Connection.getMetaData() |
    | [`OracleDatabaseMetaData`](../OracleDatabaseMetaData.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`<br>Deprecated. <br>-- Please use the factory method java.sql.Connection.getMetaData() |

  - ### Uses of [OracleConnection](../OracleConnection.md) in [oracle.jdbc.pool](../pool/package-summary.md)

    **Methods in [oracle.jdbc.pool](../pool/package-summary.md) that return [OracleConnection](../OracleConnection.md)**

    | Modifier and Type                                       | Method and Description                                                                                                               |
    |---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`OracleConnection`](../OracleConnection.md) | OracleConnectionBuilderImpl.[`build`](../pool/OracleConnectionBuilderImpl.md)`()`<br>Builds the connection of type OracleConnection. |
    | `abstract `[`OracleConnection`](../OracleConnection.md) | OracleConnectionBuilderImpl.[`build`](../pool/OracleConnectionBuilderImpl.md)`()`<br>Builds the connection of type OracleConnection. |

    **Methods in [oracle.jdbc.pool](../pool/package-summary.md) with parameters of type [OracleConnection](../OracleConnection.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                                      |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | OracleConnectionCacheCallback.[`handleAbandonedConnection`](../pool/OracleConnectionCacheCallback.md)`(`[`OracleConnection`](../OracleConnection.md)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` userObject)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. |
    | `boolean`         | OracleConnectionCacheCallback.[`handleAbandonedConnection`](../pool/OracleConnectionCacheCallback.md)`(`[`OracleConnection`](../OracleConnection.md)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` userObject)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead. |
    | `void`            | OracleConnectionCacheCallback.[`releaseConnection`](../pool/OracleConnectionCacheCallback.md)`(`[`OracleConnection`](../OracleConnection.md)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` userObject)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead.         |
    | `void`            | OracleConnectionCacheCallback.[`releaseConnection`](../pool/OracleConnectionCacheCallback.md)`(`[`OracleConnection`](../OracleConnection.md)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` userObject)`<br>Deprecated. <br>Use Oracle Universal Connection Pool instead.         |

  - ### Uses of [OracleConnection](../OracleConnection.md) in [oracle.sql](../../sql/package-summary.md)

    **Methods in [oracle.sql](../../sql/package-summary.md) that return [OracleConnection](../OracleConnection.md)**

    | Modifier and Type                                     | Method and Description                                                                                                                                  |
    |-------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleConnection`](../OracleConnection.md)          | DatumWithConnection.[`getOracleConnection`](../../sql/DatumWithConnection.md)`()`<br>Oracle extension.                                                  |
    | [`OracleConnection`](../OracleConnection.md)          | DatumWithConnection.[`getOracleConnection`](../../sql/DatumWithConnection.md)`()`<br>Oracle extension.                                                  |
    | `static `[`OracleConnection`](../OracleConnection.md) | ConcreteProxyUtil.[`getThinDriverReplayableConnectionDelegate`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`  |
    | `static `[`OracleConnection`](../OracleConnection.md) | ConcreteProxyUtil.[`getThinDriverReplayableConnectionDelegate`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`  |
    | `static `[`OracleConnection`](../OracleConnection.md) | ConcreteProxyUtil.[`unwrapConnectionProxy`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`                      |
    | `static `[`OracleConnection`](../OracleConnection.md) | ConcreteProxyUtil.[`unwrapConnectionProxy`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`                      |

    **Methods in [oracle.sql](../../sql/package-summary.md) with parameters of type [OracleConnection](../OracleConnection.md)**

    | Modifier and Type                                                                                        | Method and Description                                                                                                                                                                                                                                                                                                                                              |
    |----------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | ConcreteProxyUtil.[`checkAndGetACProxyConnection`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`<br>Check whether connection object from proxified or not.                                                                                                                                                                 |
    | `static `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | ConcreteProxyUtil.[`checkAndGetACProxyConnection`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`<br>Check whether connection object from proxified or not.                                                                                                                                                                 |
    | `static <T> T`                                                                                           | ConcreteProxyUtil.[`getProxyObject`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn, T delegate, `[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` proxyBaseClass, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` creator)`  |
    | `static <T> T`                                                                                           | ConcreteProxyUtil.[`getProxyObject`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn, T delegate, `[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` proxyBaseClass, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` creator)`  |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | TypeDescriptor.[`getSubtypeName`](../../sql/TypeDescriptor.md)`(`[`OracleConnection`](../OracleConnection.md)` conn, byte[] image, long offset)`                                                                                                                                                                                                                    |
    | `static `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | TypeDescriptor.[`getSubtypeName`](../../sql/TypeDescriptor.md)`(`[`OracleConnection`](../OracleConnection.md)` conn, byte[] image, long offset)`                                                                                                                                                                                                                    |
    | `static `[`OracleConnection`](../OracleConnection.md)                                                    | ConcreteProxyUtil.[`getThinDriverReplayableConnectionDelegate`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`                                                                                                                                                                                                              |
    | `static `[`OracleConnection`](../OracleConnection.md)                                                    | ConcreteProxyUtil.[`getThinDriverReplayableConnectionDelegate`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`                                                                                                                                                                                                              |
    | `static oracle.jdbc.replay.driver.TxnReplayableBase`                                                     | ConcreteProxyUtil.[`getTxnReplayableBaseOfConnection`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`                                                                                                                                                                                                                       |
    | `static oracle.jdbc.replay.driver.TxnReplayableBase`                                                     | ConcreteProxyUtil.[`getTxnReplayableBaseOfConnection`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`                                                                                                                                                                                                                       |
    | `static boolean`                                                                                         | ConcreteProxyUtil.[`isThinDriverReplayableConnection`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`                                                                                                                                                                                                                       |
    | `static boolean`                                                                                         | ConcreteProxyUtil.[`isThinDriverReplayableConnection`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`                                                                                                                                                                                                                       |
    | `static `[`OracleConnection`](../OracleConnection.md)                                                    | ConcreteProxyUtil.[`unwrapConnectionProxy`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`                                                                                                                                                                                                                                  |
    | `static `[`OracleConnection`](../OracleConnection.md)                                                    | ConcreteProxyUtil.[`unwrapConnectionProxy`](../../sql/ConcreteProxyUtil.md)`(`[`OracleConnection`](../OracleConnection.md)` conn)`                                                                                                                                                                                                                                  |

    **Constructors in [oracle.sql](../../sql/package-summary.md) with parameters of type [OracleConnection](../OracleConnection.md)**

    | Constructor and Description                                                                                                                  |
    |----------------------------------------------------------------------------------------------------------------------------------------------|
    | [`CLOB`](../../sql/CLOB.md)`(`[`OracleConnection`](../OracleConnection.md)` conn, byte[] lob_descriptor, short csform)`<br>Deprecated. <br>  |
    | [`CLOB`](../../sql/CLOB.md)`(`[`OracleConnection`](../OracleConnection.md)` conn, byte[] lob_descriptor, short csform)`<br>Deprecated. <br>  |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleConnection.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
