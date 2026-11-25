Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ConnectionRetrievalInfo.md)
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

## Uses of Interface oracle.ucp.ConnectionRetrievalInfo

- **Packages that use [ConnectionRetrievalInfo](../ConnectionRetrievalInfo.md)**

  | Package    | Description                                                                                                  |
  |------------|--------------------------------------------------------------------------------------------------------------|
  | oracle.ucp | Includes both required and optional callback interfaces that are used to implement connection pool features. |

- - ### Uses of [ConnectionRetrievalInfo](../ConnectionRetrievalInfo.md) in [oracle.ucp](../package-summary.md)

    **Methods in [oracle.ucp](../package-summary.md) that return [ConnectionRetrievalInfo](../ConnectionRetrievalInfo.md)**

    | Modifier and Type                                          | Method and Description                                                                                                                                                                                         |
    |------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ConnectionRetrievalInfo`](../ConnectionRetrievalInfo.md) | UniversalConnectionPool.[`getConnectionRetrievalInfo`](../UniversalConnectionPool.md)`()`<br>Gets the `ConnectionRetrievalInfo` object which contains user and password information to create the connections. |
    | [`ConnectionRetrievalInfo`](../ConnectionRetrievalInfo.md) | UniversalPooledConnection.[`getConnectionRetrievalInfo`](../UniversalPooledConnection.md)`()`<br>Gets the connection retrieval info.                                                                           |
    | [`ConnectionRetrievalInfo`](../ConnectionRetrievalInfo.md) | ConnectionRetrievalInfo.[`getCopyWithNoLabels`](../ConnectionRetrievalInfo.md)`()`<br>Clones this connection retrieval object but removes all the connection labels associated.                                |

    **Methods in [oracle.ucp](../package-summary.md) with parameters of type [ConnectionRetrievalInfo](../ConnectionRetrievalInfo.md)**

    | Modifier and Type                                              | Method and Description                                                                                                                                                                                                                                                                                         |
    |----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UniversalPooledConnection`](../UniversalPooledConnection.md) | UniversalConnectionPool.[`borrowConnection`](../UniversalConnectionPool.md)`(`[`ConnectionRetrievalInfo`](../ConnectionRetrievalInfo.md)` connectionRetrievalInfo)`<br>Gets a connection from the connection pool.                                                                                             |
    | `java.lang.Object`                                             | ConnectionFactoryAdapter.[`createConnection`](../ConnectionFactoryAdapter.md)`(`[`ConnectionRetrievalInfo`](../ConnectionRetrievalInfo.md)` connectionRequestInfo)`<br>Creates a connection.                                                                                                                   |
    | [`UniversalPooledConnection`](../UniversalPooledConnection.md) | ConnectionFactoryAdapter.[`createPooledConnection`](../ConnectionFactoryAdapter.md)`(java.lang.Object connection, `[`ConnectionRetrievalInfo`](../ConnectionRetrievalInfo.md)` connectionRequestInfo)`<br>Creates a UniversalPooledConnection object.                                                          |
    | `boolean`                                                      | ConnectionRetrievalInfo.[`equalsIncludingPassword`](../ConnectionRetrievalInfo.md)`(`[`ConnectionRetrievalInfo`](../ConnectionRetrievalInfo.md)` cri)`<br>Checks whether this instance is equal to another.                                                                                                    |
    | `void`                                                         | UniversalConnectionPool.[`setConnectionRetrievalInfo`](../UniversalConnectionPool.md)`(`[`ConnectionRetrievalInfo`](../ConnectionRetrievalInfo.md)` cri)`<br>Sets the `ConnectionRetrievalInfo` for creating the initial connections (physical connections) in the pool based on the initialPoolSize property. |
    | `void`                                                         | UniversalPooledConnection.[`setConnectionRetrievalInfo`](../UniversalPooledConnection.md)`(`[`ConnectionRetrievalInfo`](../ConnectionRetrievalInfo.md)` cri)`<br>Sets the connection retrieval info on the connection.                                                                                         |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ConnectionRetrievalInfo.md)
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
