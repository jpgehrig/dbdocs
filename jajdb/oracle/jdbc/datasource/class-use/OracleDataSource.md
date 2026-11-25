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

## Uses of Interface oracle.jdbc.datasource.OracleDataSource

- **Packages that use [OracleDataSource](../OracleDataSource.md)**

  | Package            | Description                                                         |
  |--------------------|---------------------------------------------------------------------|
  | oracle.jdbc.pool   | A package of connection cache and pooling related classes.          |
  | oracle.jdbc.replay | Provides interfaces and factory methods for Application Continuity. |
  | oracle.jdbc.xa     | Provides classes that implement the JDBC XA APIs.                   |

- - ### Uses of [OracleDataSource](../OracleDataSource.md) in [oracle.jdbc.pool](../../pool/package-summary.md)

    **Classes in [oracle.jdbc.pool](../../pool/package-summary.md) that implement [OracleDataSource](../OracleDataSource.md)**

    | Modifier and Type | Class and Description                                                                                                                        |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`OracleConnectionPoolDataSource`](../../pool/OracleConnectionPoolDataSource.md)<br>A DataSource object is a factory for Connection objects. |
    | `class `          | [`OracleDataSource`](../../pool/OracleDataSource.md)<br>A DataSource object is a factory for Connection objects.                             |
    | `class `          | [`OracleOCIConnectionPool`](../../pool/OracleOCIConnectionPool.md)<br>A type-2 driver connection pool.                                       |

  - ### Uses of [OracleDataSource](../OracleDataSource.md) in [oracle.jdbc.replay](../../replay/package-summary.md)

    **Subinterfaces of [OracleDataSource](../OracleDataSource.md) in [oracle.jdbc.replay](../../replay/package-summary.md)**

    | Modifier and Type | Interface and Description                                                                                                                                         |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `interface `      | [`OracleConnectionPoolDataSource`](../../replay/OracleConnectionPoolDataSource.md)<br>A data source that supports transparent failover replay of JDBC operations. |
    | `interface `      | [`OracleDataSource`](../../replay/OracleDataSource.md)<br>A data source that supports transparent failover replay of JDBC operations.                             |
    | `interface `      | [`OracleXADataSource`](../../replay/OracleXADataSource.md)<br>A data source that supports transparent failover replay of JDBC operations.                         |

    **Classes in [oracle.jdbc.replay](../../replay/package-summary.md) that implement [OracleDataSource](../OracleDataSource.md)**

    | Modifier and Type | Class and Description                                                                                                                               |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`OracleConnectionPoolDataSourceImpl`](../../replay/OracleConnectionPoolDataSourceImpl.md)                                                          |
    | `class `          | [`OracleDataSourceImpl`](../../replay/OracleDataSourceImpl.md)<br>JDBC Data Source that supports transparent JDBC operation replay upon a failover. |
    | `class `          | [`OracleXADataSourceImpl`](../../replay/OracleXADataSourceImpl.md)                                                                                  |

  - ### Uses of [OracleDataSource](../OracleDataSource.md) in [oracle.jdbc.xa](../../xa/package-summary.md)

    **Classes in [oracle.jdbc.xa](../../xa/package-summary.md) that implement [OracleDataSource](../OracleDataSource.md)**

    | Modifier and Type | Class and Description                                                                         |
    |-------------------|-----------------------------------------------------------------------------------------------|
    | `class `          | [`OracleXADataSource`](../../xa/OracleXADataSource.md)<br>A factory for XAConnection objects. |

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
