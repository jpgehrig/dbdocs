Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OraclePooledConnection.md)
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

## Uses of Interface oracle.jdbc.datasource.OraclePooledConnection

- **Packages that use [OraclePooledConnection](../OraclePooledConnection.md)**

  | Package                | Description                                                                                                                   |
  |------------------------|-------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc            | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                             |
  | oracle.jdbc.datasource | Beginning in Oracle Release 12.2, some of the Oracle extensions to JDBC are captured in the package `oracle.jdbc.datasource`. |
  | oracle.jdbc.pool       | A package of connection cache and pooling related classes.                                                                    |
  | oracle.jdbc.xa         | Provides classes that implement the JDBC XA APIs.                                                                             |
  | oracle.jdbc.xa.client  | Provides classes that implement the JDBC XA APIs.                                                                             |

- - ### Uses of [OraclePooledConnection](../OraclePooledConnection.md) in [oracle.jdbc](../../package-summary.md)

    **Methods in [oracle.jdbc](../../package-summary.md) that return [OraclePooledConnection](../OraclePooledConnection.md)**

    | Modifier and Type                                        | Method and Description                                                                                                            |
    |----------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
    | [`OraclePooledConnection`](../OraclePooledConnection.md) | OraclePooledConnectionBuilder.[`build`](../../OraclePooledConnectionBuilder.md)`()`<br>Builds the OraclePooledConnections object. |
    | [`OraclePooledConnection`](../OraclePooledConnection.md) | OraclePooledConnectionBuilder.[`build`](../../OraclePooledConnectionBuilder.md)`()`<br>Builds the OraclePooledConnections object. |

  - ### Uses of [OraclePooledConnection](../OraclePooledConnection.md) in [oracle.jdbc.datasource](../package-summary.md)

    **Subinterfaces of [OraclePooledConnection](../OraclePooledConnection.md) in [oracle.jdbc.datasource](../package-summary.md)**

    | Modifier and Type | Interface and Description                                                                                                                                                                                                                    |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `interface `      | [`OracleXAConnection`](../OracleXAConnection.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true). |

  - ### Uses of [OraclePooledConnection](../OraclePooledConnection.md) in [oracle.jdbc.pool](../../pool/package-summary.md)

    **Classes in [oracle.jdbc.pool](../../pool/package-summary.md) that implement [OraclePooledConnection](../OraclePooledConnection.md)**

    | Modifier and Type | Class and Description                                                                                                                                                           |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`OraclePooledConnection`](../../pool/OraclePooledConnection.md)<br>An OraclePooledConnection object is a connection object that provides hooks for connection pool management. |

    **Methods in [oracle.jdbc.pool](../../pool/package-summary.md) that return [OraclePooledConnection](../OraclePooledConnection.md)**

    | Modifier and Type                                                   | Method and Description                                                                                                                                    |
    |---------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract `[`OraclePooledConnection`](../OraclePooledConnection.md) | OraclePooledConnectionBuilderImpl.[`build`](../../pool/OraclePooledConnectionBuilderImpl.md)`()`<br>Builds the connection of type OraclePooledConnection. |
    | `abstract `[`OraclePooledConnection`](../OraclePooledConnection.md) | OraclePooledConnectionBuilderImpl.[`build`](../../pool/OraclePooledConnectionBuilderImpl.md)`()`<br>Builds the connection of type OraclePooledConnection. |

  - ### Uses of [OraclePooledConnection](../OraclePooledConnection.md) in [oracle.jdbc.xa](../../xa/package-summary.md)

    **Classes in [oracle.jdbc.xa](../../xa/package-summary.md) that implement [OraclePooledConnection](../OraclePooledConnection.md)**

    | Modifier and Type | Class and Description                                                                                                           |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`OracleXAConnection`](../../xa/OracleXAConnection.md)<br>An XAConnection object provides support for distributed transactions. |

  - ### Uses of [OraclePooledConnection](../OraclePooledConnection.md) in [oracle.jdbc.xa.client](../../xa/client/package-summary.md)

    **Classes in [oracle.jdbc.xa.client](../../xa/client/package-summary.md) that implement [OraclePooledConnection](../OraclePooledConnection.md)**

    | Modifier and Type | Class and Description                                                                                          |
    |-------------------|----------------------------------------------------------------------------------------------------------------|
    | `class `          | [`OracleXAHeteroConnection`](../../xa/client/OracleXAHeteroConnection.md)<br>A factory for Connection objects. |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OraclePooledConnection.md)
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
