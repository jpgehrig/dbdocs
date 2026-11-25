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

- [Prev Package](../package-summary.md)
- [Next Package](../jdbc/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.ucp.admin

Defines interfaces for administering Universal Connection Pool instances, including JMX support.

See: Description

- **Interface Summary**

  | Interface                                                                     | Description                                                                                                                           |
  |-------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
  | [UniversalConnectionPoolManager](UniversalConnectionPoolManager.md)           | The UniversalConnectionPoolManager interface defines operations for creating and maintaining the Universal Connection Pool instances. |
  | [UniversalConnectionPoolManagerMBean](UniversalConnectionPoolManagerMBean.md) | The Universal Connection Pool Manager MBean defines operations and attributes for managing pool instances.                            |
  | [UniversalConnectionPoolMBean](UniversalConnectionPoolMBean.md)               | The Universal Connection Pool MBean defines operations and attributes for managing the Universal Connection Pool.                     |

- **Class Summary**

  | Class                                                                       | Description                                                                                      |
  |-----------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|
  | [UniversalConnectionPoolManagerImpl](UniversalConnectionPoolManagerImpl.md) | The `UniversalConnectionPoolManagerImpl` class is the implementation class for the pool manager. |

## Package oracle.ucp.admin Description

Defines interfaces for administering Universal Connection Pool instances, including JMX support.

A pool instance is registered with the pool manager every time a new pool instance is created. All the pool operations can be called by providing the pool name as a key. Operations for controlling the metric collection for individual Universal Connection Pool instances are also provided.

Administration operations include:

- Starting and stopping the connection pool.
- Refreshing, recycling, purging, and destroying the connection pool.
- Starting and stopping metric collection for the provided connection pool.
- Setting and getting the metric update interval.
- Setting and getting the log level for the UCP logger.

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

- [Prev Package](../package-summary.md)
- [Next Package](../jdbc/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
