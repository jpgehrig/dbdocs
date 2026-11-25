Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleShardingKeyBuilder.md)
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

## Uses of Interface oracle.jdbc.OracleShardingKeyBuilder

- **Packages that use [OracleShardingKeyBuilder](../OracleShardingKeyBuilder.md)**

  | Package                | Description                                                                                                                   |
  |------------------------|-------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc            | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                             |
  | oracle.jdbc.datasource | Beginning in Oracle Release 12.2, some of the Oracle extensions to JDBC are captured in the package `oracle.jdbc.datasource`. |
  | oracle.jdbc.pool       | A package of connection cache and pooling related classes.                                                                    |

- - ### Uses of [OracleShardingKeyBuilder](../OracleShardingKeyBuilder.md) in [oracle.jdbc](../package-summary.md)

    **Methods in [oracle.jdbc](../package-summary.md) that return [OracleShardingKeyBuilder](../OracleShardingKeyBuilder.md)**

    | Modifier and Type                                            | Method and Description                                                                                                                                                                                                                                                                                                                                                           |
    |--------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleShardingKeyBuilder`](../OracleShardingKeyBuilder.md) | OracleShardingKeyBuilder.[`subkey`](../OracleShardingKeyBuilder.md)`(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` key, `[`SQLType`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true)` subkeyType)`<br>This method is called to include a subkey into a sharding Key object being built. |
    | [`OracleShardingKeyBuilder`](../OracleShardingKeyBuilder.md) | OracleShardingKeyBuilder.[`subkey`](../OracleShardingKeyBuilder.md)`(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` key, `[`SQLType`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLType.html?is-external=true)` subkeyType)`<br>This method is called to include a subkey into a sharding Key object being built. |

  - ### Uses of [OracleShardingKeyBuilder](../OracleShardingKeyBuilder.md) in [oracle.jdbc.datasource](../datasource/package-summary.md)

    **Methods in [oracle.jdbc.datasource](../datasource/package-summary.md) that return [OracleShardingKeyBuilder](../OracleShardingKeyBuilder.md)**

    | Modifier and Type                                                      | Method and Description                                                                                                                                 |
    |------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `default `[`OracleShardingKeyBuilder`](../OracleShardingKeyBuilder.md) | OracleCommonDataSource.[`createShardingKeyBuilder`](../datasource/OracleCommonDataSource.md)`()`<br>Creates a new `OracleShardingKeyBuilder` instance. |
    | `default `[`OracleShardingKeyBuilder`](../OracleShardingKeyBuilder.md) | OracleCommonDataSource.[`createShardingKeyBuilder`](../datasource/OracleCommonDataSource.md)`()`<br>Creates a new `OracleShardingKeyBuilder` instance. |

  - ### Uses of [OracleShardingKeyBuilder](../OracleShardingKeyBuilder.md) in [oracle.jdbc.pool](../pool/package-summary.md)

    **Classes in [oracle.jdbc.pool](../pool/package-summary.md) that implement [OracleShardingKeyBuilder](../OracleShardingKeyBuilder.md)**

    | Modifier and Type | Class and Description                                                      |
    |-------------------|----------------------------------------------------------------------------|
    | `class `          | [`OracleShardingKeyBuilderImpl`](../pool/OracleShardingKeyBuilderImpl.md)  |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleShardingKeyBuilder.md)
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
