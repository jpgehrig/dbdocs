Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UniversalConnectionPoolAdapter.md)
- Use
- [Tree](../../../overview-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

## Uses of Interface oracle.ucp.UniversalConnectionPoolAdapter

- **Packages that use [UniversalConnectionPoolAdapter](../UniversalConnectionPoolAdapter.md)**

  | Package          | Description                                                                                                       |
  |------------------|-------------------------------------------------------------------------------------------------------------------|
  | oracle.ucp.admin | Defines interfaces for administering Universal Connection Pool instances, including JMX support.                  |
  | oracle.ucp.jdbc  | Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool. |

- - ### Uses of [UniversalConnectionPoolAdapter](../UniversalConnectionPoolAdapter.md) in [oracle.ucp.admin](../admin/package-summary.md)

    **Methods in [oracle.ucp.admin](../admin/package-summary.md) with parameters of type [UniversalConnectionPoolAdapter](../UniversalConnectionPoolAdapter.md)**

    | Modifier and Type                                                          | Method and Description                                                                                                                                                                                                                                                       |
    |----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                     | UniversalConnectionPoolManager.[`createConnectionPool`](../admin/UniversalConnectionPoolManager.md)`(`[`UniversalConnectionPoolAdapter`](../UniversalConnectionPoolAdapter.md)` ucpAdapter)`<br>Creates a connection pool instance based on specified UCP Adapter.           |
    | [`UniversalConnectionPoolMBean`](../admin/UniversalConnectionPoolMBean.md) | UniversalConnectionPoolManagerMBean.[`createConnectionPool`](../admin/UniversalConnectionPoolManagerMBean.md)`(`[`UniversalConnectionPoolAdapter`](../UniversalConnectionPoolAdapter.md)` ucpAdapter)`<br>Creates a connection pool instance based on specified UCP Adapter. |

  - ### Uses of [UniversalConnectionPoolAdapter](../UniversalConnectionPoolAdapter.md) in [oracle.ucp.jdbc](../jdbc/package-summary.md)

    **Classes in [oracle.ucp.jdbc](../jdbc/package-summary.md) that implement [UniversalConnectionPoolAdapter](../UniversalConnectionPoolAdapter.md)**

    | Modifier and Type | Class and Description                                                                             |
    |-------------------|---------------------------------------------------------------------------------------------------|
    | `class `          | [`PoolDataSourceImpl`](../jdbc/PoolDataSourceImpl.md)<br>A connection pool-aware data source.     |
    | `class `          | [`PoolXADataSourceImpl`](../jdbc/PoolXADataSourceImpl.md)<br>A connection pool-aware data source. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UniversalConnectionPoolAdapter.md)
- Use
- [Tree](../../../overview-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
