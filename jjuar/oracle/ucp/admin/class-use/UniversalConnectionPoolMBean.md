Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UniversalConnectionPoolMBean.md)
- Use
- [Tree](../../../../overview-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-files/index-1.md)
- [Help](../../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

## Uses of Interface oracle.ucp.admin.UniversalConnectionPoolMBean

- **Packages that use [UniversalConnectionPoolMBean](../UniversalConnectionPoolMBean.md)**

  | Package          | Description                                                                                                       |
  |------------------|-------------------------------------------------------------------------------------------------------------------|
  | oracle.ucp       | Includes both required and optional callback interfaces that are used to implement connection pool features.      |
  | oracle.ucp.admin | Defines interfaces for administering Universal Connection Pool instances, including JMX support.                  |
  | oracle.ucp.jdbc  | Includes various interfaces and classes used by applications to work with JDBC connections and a connection pool. |

- - ### Uses of [UniversalConnectionPoolMBean](../UniversalConnectionPoolMBean.md) in [oracle.ucp](../../package-summary.md)

    **Methods in [oracle.ucp](../../package-summary.md) that return [UniversalConnectionPoolMBean](../UniversalConnectionPoolMBean.md)**

    | Modifier and Type                                                    | Method and Description                                                                                                                                                              |
    |----------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UniversalConnectionPoolMBean`](../UniversalConnectionPoolMBean.md) | UniversalConnectionPoolAdapter.[`createUniversalConnectionPoolMBean`](../../UniversalConnectionPoolAdapter.md)`()`<br>Creates a Universal Connection Pool MBean using this adapter. |

  - ### Uses of [UniversalConnectionPoolMBean](../UniversalConnectionPoolMBean.md) in [oracle.ucp.admin](../package-summary.md)

    **Methods in [oracle.ucp.admin](../package-summary.md) that return [UniversalConnectionPoolMBean](../UniversalConnectionPoolMBean.md)**

    | Modifier and Type                                                    | Method and Description                                                                                                                                                                                                                                                    |
    |----------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UniversalConnectionPoolMBean`](../UniversalConnectionPoolMBean.md) | UniversalConnectionPoolManagerMBean.[`createConnectionPool`](../UniversalConnectionPoolManagerMBean.md)`(`[`UniversalConnectionPoolAdapter`](../../UniversalConnectionPoolAdapter.md)` ucpAdapter)`<br>Creates a connection pool instance based on specified UCP Adapter. |

    **Methods in [oracle.ucp.admin](../package-summary.md) with parameters of type [UniversalConnectionPoolMBean](../UniversalConnectionPoolMBean.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                       |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | UniversalConnectionPoolManagerMBean.[`registerUniversalConnectionPoolMBean`](../UniversalConnectionPoolManagerMBean.md)`(`[`UniversalConnectionPoolMBean`](../UniversalConnectionPoolMBean.md)` poolMBean)`<br>Registers the Universal Connection Pool MBean instance with the MBean server. |

  - ### Uses of [UniversalConnectionPoolMBean](../UniversalConnectionPoolMBean.md) in [oracle.ucp.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.ucp.jdbc](../../jdbc/package-summary.md) that return [UniversalConnectionPoolMBean](../UniversalConnectionPoolMBean.md)**

    | Modifier and Type                                                    | Method and Description                                                                                                                                           |
    |----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UniversalConnectionPoolMBean`](../UniversalConnectionPoolMBean.md) | PoolDataSourceImpl.[`createUniversalConnectionPoolMBean`](../../jdbc/PoolDataSourceImpl.md)`()`<br>Creates a Universal Connection Pool MBean using this adapter. |

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UniversalConnectionPoolMBean.md)
- Use
- [Tree](../../../../overview-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-files/index-1.md)
- [Help](../../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev
- Next

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

Copyright © 2007, 2022, Oracle and/or its affiliates.
