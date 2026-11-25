Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleCommonDataSource.md)
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

## Uses of Interface oracle.jdbc.datasource.OracleCommonDataSource

- **Packages that use [OracleCommonDataSource](../OracleCommonDataSource.md)**

  | Package                | Description                                                                                                                   |
  |------------------------|-------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc.datasource | Beginning in Oracle Release 12.2, some of the Oracle extensions to JDBC are captured in the package `oracle.jdbc.datasource`. |
  | oracle.jdbc.pool       | A package of connection cache and pooling related classes.                                                                    |
  | oracle.jdbc.replay     | Provides interfaces and factory methods for Application Continuity.                                                           |
  | oracle.jdbc.xa         | Provides classes that implement the JDBC XA APIs.                                                                             |

- - ### Uses of [OracleCommonDataSource](../OracleCommonDataSource.md) in [oracle.jdbc.datasource](../package-summary.md)

    **Subinterfaces of [OracleCommonDataSource](../OracleCommonDataSource.md) in [oracle.jdbc.datasource](../package-summary.md)**

    | Modifier and Type | Interface and Description                                                                                                                                                                                                                                                                    |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `interface `      | [`OracleConnectionPoolDataSource`](../OracleConnectionPoolDataSource.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`ConnectionPoolDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true). |
    | `interface `      | [`OracleDataSource`](../OracleDataSource.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`DataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true).                                                         |
    | `interface `      | [`OracleXADataSource`](../OracleXADataSource.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`XADataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true).                                                 |

  - ### Uses of [OracleCommonDataSource](../OracleCommonDataSource.md) in [oracle.jdbc.pool](../../pool/package-summary.md)

    **Classes in [oracle.jdbc.pool](../../pool/package-summary.md) that implement [OracleCommonDataSource](../OracleCommonDataSource.md)**

    | Modifier and Type | Class and Description                                                                                                                        |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`OracleConnectionPoolDataSource`](../../pool/OracleConnectionPoolDataSource.md)<br>A DataSource object is a factory for Connection objects. |
    | `class `          | [`OracleDataSource`](../../pool/OracleDataSource.md)<br>A DataSource object is a factory for Connection objects.                             |
    | `class `          | [`OracleOCIConnectionPool`](../../pool/OracleOCIConnectionPool.md)<br>A type-2 driver connection pool.                                       |

  - ### Uses of [OracleCommonDataSource](../OracleCommonDataSource.md) in [oracle.jdbc.replay](../../replay/package-summary.md)

    **Classes in [oracle.jdbc.replay](../../replay/package-summary.md) that implement [OracleCommonDataSource](../OracleCommonDataSource.md)**

    | Modifier and Type | Class and Description                                                                                                                               |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`OracleConnectionPoolDataSourceImpl`](../../replay/OracleConnectionPoolDataSourceImpl.md)                                                          |
    | `class `          | [`OracleDataSourceImpl`](../../replay/OracleDataSourceImpl.md)<br>JDBC Data Source that supports transparent JDBC operation replay upon a failover. |
    | `class `          | [`OracleXADataSourceImpl`](../../replay/OracleXADataSourceImpl.md)                                                                                  |

  - ### Uses of [OracleCommonDataSource](../OracleCommonDataSource.md) in [oracle.jdbc.xa](../../xa/package-summary.md)

    **Classes in [oracle.jdbc.xa](../../xa/package-summary.md) that implement [OracleCommonDataSource](../OracleCommonDataSource.md)**

    | Modifier and Type | Class and Description                                                                         |
    |-------------------|-----------------------------------------------------------------------------------------------|
    | `class `          | [`OracleXADataSource`](../../xa/OracleXADataSource.md)<br>A factory for XAConnection objects. |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleCommonDataSource.md)
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
