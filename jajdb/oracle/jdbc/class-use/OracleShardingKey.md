Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleShardingKey.md)
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

## Uses of Interface oracle.jdbc.OracleShardingKey

- **Packages that use [OracleShardingKey](../OracleShardingKey.md)**

  | Package                | Description                                                                                                                   |
  |------------------------|-------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc            | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                             |
  | oracle.jdbc.datasource | Beginning in Oracle Release 12.2, some of the Oracle extensions to JDBC are captured in the package `oracle.jdbc.datasource`. |
  | oracle.jdbc.pool       | A package of connection cache and pooling related classes.                                                                    |
  | oracle.jdbc.xa         | Provides classes that implement the JDBC XA APIs.                                                                             |

- - ### Uses of [OracleShardingKey](../OracleShardingKey.md) in [oracle.jdbc](../package-summary.md)

    **Methods in [oracle.jdbc](../package-summary.md) that return [OracleShardingKey](../OracleShardingKey.md)**

    | Modifier and Type                              | Method and Description                                                                             |
    |------------------------------------------------|----------------------------------------------------------------------------------------------------|
    | [`OracleShardingKey`](../OracleShardingKey.md) | OracleShardingKeyBuilder.[`build`](../OracleShardingKeyBuilder.md)`()`<br>Builds the Sharding key. |
    | [`OracleShardingKey`](../OracleShardingKey.md) | OracleShardingKeyBuilder.[`build`](../OracleShardingKeyBuilder.md)`()`<br>Builds the Sharding key. |

    **Methods in [oracle.jdbc](../package-summary.md) with parameters of type [OracleShardingKey](../OracleShardingKey.md)**

    | Modifier and Type                                                      | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                |
    |------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                 | OracleConnection.[`setShardingKey`](../OracleConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`<br>Sets the sharding key on this connection.                                                                                                                                                                                                                                              |
    | `void`                                                                 | OracleConnectionWrapper.[`setShardingKey`](../OracleConnectionWrapper.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                             |
    | `void`                                                                 | OracleConnectionWrapper.[`setShardingKey`](../OracleConnectionWrapper.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                             |
    | `void`                                                                 | OracleConnection.[`setShardingKey`](../OracleConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`<br>Sets the sharding key on this connection.                                                                                                                                                                                                                                              |
    | `void`                                                                 | OracleConnection.[`setShardingKey`](../OracleConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`<br>Sets the sharding key and the super sharding key on this connection.                                                                                                                                                |
    | `void`                                                                 | OracleConnectionWrapper.[`setShardingKey`](../OracleConnectionWrapper.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` key, `[`OracleShardingKey`](../OracleShardingKey.md)` superKey)`                                                                                                                                                                                                                          |
    | `void`                                                                 | OracleConnectionWrapper.[`setShardingKey`](../OracleConnectionWrapper.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` key, `[`OracleShardingKey`](../OracleShardingKey.md)` superKey)`                                                                                                                                                                                                                          |
    | `void`                                                                 | OracleConnection.[`setShardingKey`](../OracleConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`<br>Sets the sharding key and the super sharding key on this connection.                                                                                                                                                |
    | `boolean`                                                              | OracleConnection.[`setShardingKeyIfValid`](../OracleConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, int timeout)`<br>Checks the validity of the connection and also checks if the sharding key passed to this method is valid for the connection.If the sharding key is valid, it will be set on the connection.                                                                        |
    | `boolean`                                                              | OracleConnectionWrapper.[`setShardingKeyIfValid`](../OracleConnectionWrapper.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, int timeout)`                                                                                                                                                                                                                                                         |
    | `boolean`                                                              | OracleConnectionWrapper.[`setShardingKeyIfValid`](../OracleConnectionWrapper.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, int timeout)`                                                                                                                                                                                                                                                         |
    | `boolean`                                                              | OracleConnection.[`setShardingKeyIfValid`](../OracleConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, int timeout)`<br>Checks the validity of the connection and also checks if the sharding key passed to this method is valid for the connection.If the sharding key is valid, it will be set on the connection.                                                                        |
    | `boolean`                                                              | OracleConnection.[`setShardingKeyIfValid`](../OracleConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey, int timeout)`<br>Checks the validity of the connection and also checks if the sharding keys passed to this method are valid for the connection.If the sharding keys are valid, it will be set on the connection. |
    | `boolean`                                                              | OracleConnectionWrapper.[`setShardingKeyIfValid`](../OracleConnectionWrapper.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` key, `[`OracleShardingKey`](../OracleShardingKey.md)` superKey, int timeout)`                                                                                                                                                                                                      |
    | `boolean`                                                              | OracleConnectionWrapper.[`setShardingKeyIfValid`](../OracleConnectionWrapper.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` key, `[`OracleShardingKey`](../OracleShardingKey.md)` superKey, int timeout)`                                                                                                                                                                                                      |
    | `boolean`                                                              | OracleConnection.[`setShardingKeyIfValid`](../OracleConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey, int timeout)`<br>Checks the validity of the connection and also checks if the sharding keys passed to this method are valid for the connection.If the sharding keys are valid, it will be set on the connection. |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md)             | OracleConnectionBuilder.[`shardingKey`](../OracleConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`shardingKey`](../OraclePooledConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                    |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md)         | OracleXAConnectionBuilder.[`shardingKey`](../OracleXAConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                            |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md)         | OracleXAConnectionBuilder.[`shardingKey`](../OracleXAConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                            |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`shardingKey`](../OraclePooledConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                    |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md)             | OracleConnectionBuilder.[`shardingKey`](../OracleConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md)             | OracleConnectionBuilder.[`superShardingKey`](../OracleConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                      |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`superShardingKey`](../OraclePooledConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                          |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md)         | OracleXAConnectionBuilder.[`superShardingKey`](../OracleXAConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                  |
    | [`OracleXAConnectionBuilder`](../OracleXAConnectionBuilder.md)         | OracleXAConnectionBuilder.[`superShardingKey`](../OracleXAConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                  |
    | [`OraclePooledConnectionBuilder`](../OraclePooledConnectionBuilder.md) | OraclePooledConnectionBuilder.[`superShardingKey`](../OraclePooledConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                          |
    | [`OracleConnectionBuilder`](../OracleConnectionBuilder.md)             | OracleConnectionBuilder.[`superShardingKey`](../OracleConnectionBuilder.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                      |

  - ### Uses of [OracleShardingKey](../OracleShardingKey.md) in [oracle.jdbc.datasource](../datasource/package-summary.md)

    **Methods in [oracle.jdbc.datasource](../datasource/package-summary.md) with parameters of type [OracleShardingKey](../OracleShardingKey.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePooledConnection.[`setShardingKey`](../datasource/OraclePooledConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`<br>Sets the sharding key and the super sharding key on this connection.                                                                                                                                                |
    | `void`            | OraclePooledConnection.[`setShardingKey`](../datasource/OraclePooledConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`<br>Sets the sharding key and the super sharding key on this connection.                                                                                                                                                |
    | `boolean`         | OraclePooledConnection.[`setShardingKeyIfValid`](../datasource/OraclePooledConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey, int timeout)`<br>Checks the validity of the connection and also checks if the sharding keys passed to this method are valid for the connection.If the sharding keys are valid, it will be set on the connection. |
    | `boolean`         | OraclePooledConnection.[`setShardingKeyIfValid`](../datasource/OraclePooledConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey, int timeout)`<br>Checks the validity of the connection and also checks if the sharding keys passed to this method are valid for the connection.If the sharding keys are valid, it will be set on the connection. |

  - ### Uses of [OracleShardingKey](../OracleShardingKey.md) in [oracle.jdbc.pool](../pool/package-summary.md)

    **Classes in [oracle.jdbc.pool](../pool/package-summary.md) that implement [OracleShardingKey](../OracleShardingKey.md)**

    | Modifier and Type | Class and Description                                        |
    |-------------------|--------------------------------------------------------------|
    | `class `          | [`OracleShardingKeyImpl`](../pool/OracleShardingKeyImpl.md)  |

    **Fields in [oracle.jdbc.pool](../pool/package-summary.md) declared as [OracleShardingKey](../OracleShardingKey.md)**

    | Modifier and Type                                          | Field and Description                                                                                 |
    |------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md) | OracleConnectionBuilderImpl.[`shardingKey`](../pool/OracleConnectionBuilderImpl.md)                   |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md) | OraclePooledConnectionBuilderImpl.[`shardingKey`](../pool/OraclePooledConnectionBuilderImpl.md)       |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md) | OraclePooledConnectionBuilderImpl.[`shardingKey`](../pool/OraclePooledConnectionBuilderImpl.md)       |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md) | OracleConnectionBuilderImpl.[`shardingKey`](../pool/OracleConnectionBuilderImpl.md)                   |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md) | OracleConnectionBuilderImpl.[`superShardingKey`](../pool/OracleConnectionBuilderImpl.md)              |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md) | OraclePooledConnectionBuilderImpl.[`superShardingKey`](../pool/OraclePooledConnectionBuilderImpl.md)  |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md) | OraclePooledConnectionBuilderImpl.[`superShardingKey`](../pool/OraclePooledConnectionBuilderImpl.md)  |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md) | OracleConnectionBuilderImpl.[`superShardingKey`](../pool/OracleConnectionBuilderImpl.md)              |

    **Methods in [oracle.jdbc.pool](../pool/package-summary.md) with parameters of type [OracleShardingKey](../OracleShardingKey.md)**

    | Modifier and Type                                                                   | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                           |
    |-------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                                                               | OracleShardingKeyImpl.[`compareTo`](../pool/OracleShardingKeyImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` o)`<br>Used to compare two OracleShardingKey keys.                                                                                                                                                                                                                                                                       |
    | `int`                                                                               | OracleShardingKeyImpl.[`compareTo`](../pool/OracleShardingKeyImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` o)`<br>Used to compare two OracleShardingKey keys.                                                                                                                                                                                                                                                                       |
    | `void`                                                                              | OraclePooledConnection.[`setShardingKey`](../pool/OraclePooledConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`<br>Sets the sharding key and the super sharding key on this connection.                                                                                                                                                          |
    | `void`                                                                              | OraclePooledConnection.[`setShardingKey`](../pool/OraclePooledConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`<br>Sets the sharding key and the super sharding key on this connection.                                                                                                                                                          |
    | `boolean`                                                                           | OraclePooledConnection.[`setShardingKeyIfValid`](../pool/OraclePooledConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey, int timeout)`<br>Checks the validity of the connection and also checks if the sharding keys passed to this method are valid for the connection.If the sharding keys are valid, it will be set on the connection's session. |
    | `boolean`                                                                           | OraclePooledConnection.[`setShardingKeyIfValid`](../pool/OraclePooledConnection.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey, `[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey, int timeout)`<br>Checks the validity of the connection and also checks if the sharding keys passed to this method are valid for the connection.If the sharding keys are valid, it will be set on the connection's session. |
    | [`OracleConnectionBuilderImpl`](../pool/OracleConnectionBuilderImpl.md)             | OracleConnectionBuilderImpl.[`shardingKey`](../pool/OracleConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                              |
    | [`OraclePooledConnectionBuilderImpl`](../pool/OraclePooledConnectionBuilderImpl.md) | OraclePooledConnectionBuilderImpl.[`shardingKey`](../pool/OraclePooledConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                  |
    | [`OraclePooledConnectionBuilderImpl`](../pool/OraclePooledConnectionBuilderImpl.md) | OraclePooledConnectionBuilderImpl.[`shardingKey`](../pool/OraclePooledConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                  |
    | [`OracleConnectionBuilderImpl`](../pool/OracleConnectionBuilderImpl.md)             | OracleConnectionBuilderImpl.[`shardingKey`](../pool/OracleConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`                                                                                                                                                                                                                                                                                              |
    | [`OracleConnectionBuilderImpl`](../pool/OracleConnectionBuilderImpl.md)             | OracleConnectionBuilderImpl.[`superShardingKey`](../pool/OracleConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                                    |
    | [`OraclePooledConnectionBuilderImpl`](../pool/OraclePooledConnectionBuilderImpl.md) | OraclePooledConnectionBuilderImpl.[`superShardingKey`](../pool/OraclePooledConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                        |
    | [`OraclePooledConnectionBuilderImpl`](../pool/OraclePooledConnectionBuilderImpl.md) | OraclePooledConnectionBuilderImpl.[`superShardingKey`](../pool/OraclePooledConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                        |
    | [`OracleConnectionBuilderImpl`](../pool/OracleConnectionBuilderImpl.md)             | OracleConnectionBuilderImpl.[`superShardingKey`](../pool/OracleConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`                                                                                                                                                                                                                                                                                    |

  - ### Uses of [OracleShardingKey](../OracleShardingKey.md) in [oracle.jdbc.xa](../xa/package-summary.md)

    **Fields in [oracle.jdbc.xa](../xa/package-summary.md) declared as [OracleShardingKey](../OracleShardingKey.md)**

    | Modifier and Type                                          | Field and Description                                                                       |
    |------------------------------------------------------------|---------------------------------------------------------------------------------------------|
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md) | OracleXAConnectionBuilderImpl.[`shardingKey`](../xa/OracleXAConnectionBuilderImpl.md)       |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md) | OracleXAConnectionBuilderImpl.[`shardingKey`](../xa/OracleXAConnectionBuilderImpl.md)       |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md) | OracleXAConnectionBuilderImpl.[`superShardingKey`](../xa/OracleXAConnectionBuilderImpl.md)  |
    | `protected `[`OracleShardingKey`](../OracleShardingKey.md) | OracleXAConnectionBuilderImpl.[`superShardingKey`](../xa/OracleXAConnectionBuilderImpl.md)  |

    **Methods in [oracle.jdbc.xa](../xa/package-summary.md) with parameters of type [OracleShardingKey](../OracleShardingKey.md)**

    | Modifier and Type                                                         | Method and Description                                                                                                                                           |
    |---------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleXAConnectionBuilderImpl`](../xa/OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`shardingKey`](../xa/OracleXAConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`            |
    | [`OracleXAConnectionBuilderImpl`](../xa/OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`shardingKey`](../xa/OracleXAConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` shardingKey)`            |
    | [`OracleXAConnectionBuilderImpl`](../xa/OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`superShardingKey`](../xa/OracleXAConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`  |
    | [`OracleXAConnectionBuilderImpl`](../xa/OracleXAConnectionBuilderImpl.md) | OracleXAConnectionBuilderImpl.[`superShardingKey`](../xa/OracleXAConnectionBuilderImpl.md)`(`[`OracleShardingKey`](../OracleShardingKey.md)` superShardingKey)`  |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleShardingKey.md)
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
