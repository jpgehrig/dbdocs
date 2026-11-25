Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Package](../babelfish/package-summary.md)
- [Next Package](../dcn/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.jdbc.datasource

Beginning in Oracle Release 12.2, some of the Oracle extensions to JDBC are captured in the package `oracle.jdbc.datasource`.

See: Description

- **Interface Summary**

  | Interface                                                           | Description                                                                                                                                                                                                                                                                                                                     |
  |---------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [OracleCommonDataSource](OracleCommonDataSource.md)                 | Interface that defines the methods which are common between `OracleDataSource`, `OracleXADataSource` and `OracleConnectionPoolDataSource` and defines the Oracle extensions to the standard JDBC interface [`CommonDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/CommonDataSource.html?is-external=true). |
  | [OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md) | This interface defines the Oracle extensions to the standard JDBC interface [`ConnectionPoolDataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/ConnectionPoolDataSource.html?is-external=true).                                                                                                                |
  | [OracleDataSource](OracleDataSource.md)                             | This interface defines the Oracle extensions to the standard JDBC interface [`DataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/DataSource.html?is-external=true).                                                                                                                                            |
  | [OraclePooledConnection](OraclePooledConnection.md)                 | This interface defines the Oracle extensions to the standard JDBC interface [`PooledConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/PooledConnection.html?is-external=true).                                                                                                                                |
  | [OracleXAConnection](OracleXAConnection.md)                         | This interface defines the Oracle extensions to the standard JDBC interface [`XAConnection`](http://download.oracle.com/javase/8/docs/api/javax/sql/XAConnection.html?is-external=true).                                                                                                                                        |
  | [OracleXADataSource](OracleXADataSource.md)                         | This interface defines the Oracle extensions to the standard JDBC interface [`XADataSource`](http://download.oracle.com/javase/8/docs/api/javax/sql/XADataSource.html?is-external=true).                                                                                                                                        |

## Package oracle.jdbc.datasource Description

Beginning in Oracle Release 12.2, some of the Oracle extensions to JDBC are captured in the package `oracle.jdbc.datasource`.

The interfaces have been placed in the package to avoid package conflicts with implementations classes of the same name in existing packages like `oracle.jdbc.pool`.

Since:
12.2

Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Package](../babelfish/package-summary.md)
- [Next Package](../dcn/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
