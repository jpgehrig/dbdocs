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

- [Prev Package](../pool/package-summary.md)
- [Next Package](../xa/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.jdbc.replay

Provides interfaces and factory methods for Application Continuity.

See: Description

- **Interface Summary**

  | Interface                                                               | Description                                                                                                                                                                         |
  |-------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [ConnectionInitializationCallback](ConnectionInitializationCallback.md) | This callback allows applications to re-establish session initial starting point after a failover and before replay starts.                                                         |
  | [OracleConnectionPoolDataSource](OracleConnectionPoolDataSource.md)     | A data source that supports transparent failover replay of JDBC operations.                                                                                                         |
  | [OracleDataSource](OracleDataSource.md)                                 | A data source that supports transparent failover replay of JDBC operations.                                                                                                         |
  | [OracleXADataSource](OracleXADataSource.md)                             | A data source that supports transparent failover replay of JDBC operations.                                                                                                         |
  | [ReplayableConnection](ReplayableConnection.md)                         |                                                                                                                                                                                     |
  | [ReplayStatistics](ReplayStatistics.md)                                 | Various runtime statistics about Application Continuity (AC), such as how many JDBC calls are affected by outages, how many replay attempts are made, how many replay succeed, etc. |

- **Class Summary**

  | Class                                                                       | Description                                                                                                                                                                    |
  |-----------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [OracleConnectionPoolDataSourceImpl](OracleConnectionPoolDataSourceImpl.md) |                                                                                                                                                                                |
  | [OracleDataSourceFactory](OracleDataSourceFactory.md)                       | Data source factory for creating instances of `OracleDataSource`, `OracleConnectionPoolDataSource`, and `OracleXADataSource` that provide transparent failover replay support. |
  | [OracleDataSourceImpl](OracleDataSourceImpl.md)                             | JDBC Data Source that supports transparent JDBC operation replay upon a failover.                                                                                              |
  | [OracleXADataSourceImpl](OracleXADataSourceImpl.md)                         |                                                                                                                                                                                |

- **Enum Summary**

  | Enum                                                                                      | Description             |
  |-------------------------------------------------------------------------------------------|-------------------------|
  | [ReplayableConnection.StatisticsReportType](ReplayableConnection.StatisticsReportType.md) | Statistics report type. |

## Package oracle.jdbc.replay Description

Provides interfaces and factory methods for Application Continuity.

Since:
12*c*

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

- [Prev Package](../pool/package-summary.md)
- [Next Package](../xa/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
