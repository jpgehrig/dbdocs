Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Package](../admin/package-summary.md)
- [Next Package](oracle/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.ucp.jdbc

Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool.

See: Description

- **Interface Summary**

  | Interface                                                               | Description                                                                                                                                                                                                      |
  |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [ConnectionInitializationCallback](ConnectionInitializationCallback.md) | This callback allows applications and frameworks to initialize connections retrieved from Universal Connection Pool using common actions, before the connections are put to use.                                 |
  | [ConnectionLabelingCallback](ConnectionLabelingCallback.md)             | New callback interface for connection labeling support.                                                                                                                                                          |
  | [ConnectionWithAbandonedTimeout](ConnectionWithAbandonedTimeout.md)     | Interface supporting abandoned connection timeout handling for JDBC `java.sql.Connections`.                                                                                                                      |
  | [ConnectionWithTimeToLiveTimeout](ConnectionWithTimeToLiveTimeout.md)   | Interface supporting time-to-live connection timeout handling for JDBC `java.sql.Connections`.                                                                                                                   |
  | [HarvestableConnection](HarvestableConnection.md)                       | Interface supporting Connection Harvesting for JDBC `java.sql.Connections`.                                                                                                                                      |
  | [JDBCConnectionPoolStatistics](JDBCConnectionPoolStatistics.md)         | Various runtime statistics for the Universal Connection Pool that are specific to JDBC resources.                                                                                                                |
  | [LabelableConnection](LabelableConnection.md)                           | Interface supporting Connection Labeling for JDBC `java.sql.Connections`.                                                                                                                                        |
  | [PoolDataSource](PoolDataSource.md)                                     | A connection pool-aware data source interface.                                                                                                                                                                   |
  | [PoolXADataSource](PoolXADataSource.md)                                 | A Universal Connection Pool-enabled XA data source.                                                                                                                                                              |
  | [UCPConnectionBuilder](UCPConnectionBuilder.md)                         | A builder created from a `PoolDataSource` object, used to get a connection to the database that the `PoolDataSource` object represents.                                                                          |
  | [UCPXAConnectionBuilder](UCPXAConnectionBuilder.md)                     | A builder created from a `PoolXADataSource` object, used to get a connection to the database that the `PoolXADataSource` object represents.                                                                      |
  | [ValidConnection](ValidConnection.md)                                   | This interface allows JDBC applications to easily and quickly determine the usability of a `java.sql.Connection` object and to identify connection objects that should no longer be used for connection pooling. |

- **Class Summary**

  | Class                                             | Description                                                                                                                                                             |
  |---------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [PoolDataSourceFactory](PoolDataSourceFactory.md) | Data source factory for creating instances of the pool-enabled `PoolDataSource` or `PoolXADataSource` that provide access to Universal Connection Pool functionalities. |
  | [PoolDataSourceImpl](PoolDataSourceImpl.md)       | A connection pool-aware data source.                                                                                                                                    |
  | [PoolXADataSourceImpl](PoolXADataSourceImpl.md)   | A connection pool-aware data source.                                                                                                                                    |

## Package oracle.ucp.jdbc Description

Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool.

Among the interfaces found in this package, the `PoolDataSource` and `PoolXADataSource` data source interfaces are used by an application to get connections as well as getting and setting connection pool properties. Data source instances implementing these two interfaces automatically create a connection pool.

Allows query-only operations on all available Universal Connection Pool statistics specific to JDBC resources.

## Related Documentation

For overviews, tutorials, examples, guides, and tool documentation, see:

- Oracle Universal Connection Pool for JDBC Developer's Guide



Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Use](package-use.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Package](../admin/package-summary.md)
- [Next Package](oracle/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
