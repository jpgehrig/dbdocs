Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- [Tree](package-tree.md)
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

# Uses of Package oracle.jdbc.datasource

- **Packages that use [oracle.jdbc.datasource](package-summary.md)**

  | Package                | Description                                                                                                                   |
  |------------------------|-------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc            | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                             |
  | oracle.jdbc.datasource | Beginning in Oracle Release 12.2, some of the Oracle extensions to JDBC are captured in the package `oracle.jdbc.datasource`. |
  | oracle.jdbc.pool       | A package of connection cache and pooling related classes.                                                                    |
  | oracle.jdbc.replay     | Provides interfaces and factory methods for Application Continuity.                                                           |
  | oracle.jdbc.xa         | Provides classes that implement the JDBC XA APIs.                                                                             |
  | oracle.jdbc.xa.client  | Provides classes that implement the JDBC XA APIs.                                                                             |

- **Classes in [oracle.jdbc.datasource](package-summary.md) used by [oracle.jdbc](../package-summary.md)**

  | Class and Description                                                                                                                                                                                                                                             |
  |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [OraclePooledConnection](class-use/OraclePooledConnection.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true). |
  | [OracleXAConnection](class-use/OracleXAConnection.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true).                 |

- **Classes in [oracle.jdbc.datasource](package-summary.md) used by [oracle.jdbc.datasource](package-summary.md)**

  | Class and Description                                                                                                                                                                                                                                                                                                                                                                            |
  |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [OracleCommonDataSource](class-use/OracleCommonDataSource.md)<br>Interface that defines the methods which are common between `OracleDataSource`, `OracleXADataSource` and `OracleConnectionPoolDataSource` and defines the Oracle extensions to the standard JDBC interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true). |
  | [OraclePooledConnection](class-use/OraclePooledConnection.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true).                                                                                                                                |

- **Classes in [oracle.jdbc.datasource](package-summary.md) used by [oracle.jdbc.pool](../pool/package-summary.md)**

  | Class and Description                                                                                                                                                                                                                                                                                                                                                                            |
  |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [OracleCommonDataSource](class-use/OracleCommonDataSource.md)<br>Interface that defines the methods which are common between `OracleDataSource`, `OracleXADataSource` and `OracleConnectionPoolDataSource` and defines the Oracle extensions to the standard JDBC interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true). |
  | [OracleDataSource](class-use/OracleDataSource.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`DataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true).                                                                                                                                                        |
  | [OraclePooledConnection](class-use/OraclePooledConnection.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true).                                                                                                                                |

- **Classes in [oracle.jdbc.datasource](package-summary.md) used by [oracle.jdbc.replay](../replay/package-summary.md)**

  | Class and Description                                                                                                                                                                                                                                                                                                                                                                            |
  |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [OracleCommonDataSource](class-use/OracleCommonDataSource.md)<br>Interface that defines the methods which are common between `OracleDataSource`, `OracleXADataSource` and `OracleConnectionPoolDataSource` and defines the Oracle extensions to the standard JDBC interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true). |
  | [OracleConnectionPoolDataSource](class-use/OracleConnectionPoolDataSource.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`ConnectionPoolDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true).                                                                                                |
  | [OracleDataSource](class-use/OracleDataSource.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`DataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true).                                                                                                                                                        |
  | [OracleXADataSource](class-use/OracleXADataSource.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`XADataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true).                                                                                                                                                |

- **Classes in [oracle.jdbc.datasource](package-summary.md) used by [oracle.jdbc.xa](../xa/package-summary.md)**

  | Class and Description                                                                                                                                                                                                                             |
  |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [OracleXAConnection](class-use/OracleXAConnection.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true). |

- **Classes in [oracle.jdbc.datasource](package-summary.md) used by [oracle.jdbc.xa.client](../xa/client/package-summary.md)**

  | Class and Description                                                                                                                                                                                                                                             |
  |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [OraclePooledConnection](class-use/OraclePooledConnection.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true). |
  | [OracleXAConnection](class-use/OracleXAConnection.md)<br>This interface defines the Oracle extensions to the standard JDBC interface [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true).                 |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Use
- [Tree](package-tree.md)
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
