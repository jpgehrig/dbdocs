Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UniversalConnectionPoolLifeCycleState.md)
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

## Uses of Class oracle.ucp.UniversalConnectionPoolLifeCycleState

- **Packages that use [UniversalConnectionPoolLifeCycleState](../UniversalConnectionPoolLifeCycleState.md)**

  | Package          | Description                                                                                                  |
  |------------------|--------------------------------------------------------------------------------------------------------------|
  | oracle.ucp       | Includes both required and optional callback interfaces that are used to implement connection pool features. |
  | oracle.ucp.admin | Defines interfaces for administering Universal Connection Pool instances, including JMX support.             |

- - ### Uses of [UniversalConnectionPoolLifeCycleState](../UniversalConnectionPoolLifeCycleState.md) in [oracle.ucp](../package-summary.md)

    **Fields in [oracle.ucp](../package-summary.md) declared as [UniversalConnectionPoolLifeCycleState](../UniversalConnectionPoolLifeCycleState.md)**

    | Modifier and Type                                                                               | Field and Description                                                                                                                                                 |
    |-------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`UniversalConnectionPoolLifeCycleState`](../UniversalConnectionPoolLifeCycleState.md) | UniversalConnectionPoolLifeCycleState.[`LIFE_CYCLE_FAILED`](../UniversalConnectionPoolLifeCycleState.md)<br>Connection pool has failed.                               |
    | `static `[`UniversalConnectionPoolLifeCycleState`](../UniversalConnectionPoolLifeCycleState.md) | UniversalConnectionPoolLifeCycleState.[`LIFE_CYCLE_RUNNING`](../UniversalConnectionPoolLifeCycleState.md)<br>Connection pool is started and can hand out connections. |
    | `static `[`UniversalConnectionPoolLifeCycleState`](../UniversalConnectionPoolLifeCycleState.md) | UniversalConnectionPoolLifeCycleState.[`LIFE_CYCLE_STARTING`](../UniversalConnectionPoolLifeCycleState.md)<br>Connection pool is starting up.                         |
    | `static `[`UniversalConnectionPoolLifeCycleState`](../UniversalConnectionPoolLifeCycleState.md) | UniversalConnectionPoolLifeCycleState.[`LIFE_CYCLE_STOPPED`](../UniversalConnectionPoolLifeCycleState.md)<br>Connection pool is stopped.                              |
    | `static `[`UniversalConnectionPoolLifeCycleState`](../UniversalConnectionPoolLifeCycleState.md) | UniversalConnectionPoolLifeCycleState.[`LIFE_CYCLE_STOPPING`](../UniversalConnectionPoolLifeCycleState.md)<br>Connection pool is stopping.                            |

    **Methods in [oracle.ucp](../package-summary.md) that return [UniversalConnectionPoolLifeCycleState](../UniversalConnectionPoolLifeCycleState.md)**

    | Modifier and Type                                                                      | Method and Description                                                                                                                |
    |----------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
    | [`UniversalConnectionPoolLifeCycleState`](../UniversalConnectionPoolLifeCycleState.md) | UniversalConnectionPool.[`getLifeCycleState`](../UniversalConnectionPool.md)`()`<br>Gets the life cycle state of the connection pool. |

  - ### Uses of [UniversalConnectionPoolLifeCycleState](../UniversalConnectionPoolLifeCycleState.md) in [oracle.ucp.admin](../admin/package-summary.md)

    **Methods in [oracle.ucp.admin](../admin/package-summary.md) that return [UniversalConnectionPoolLifeCycleState](../UniversalConnectionPoolLifeCycleState.md)**

    | Modifier and Type                                                                      | Method and Description                                                                                                                                                                                               |
    |----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UniversalConnectionPoolLifeCycleState`](../UniversalConnectionPoolLifeCycleState.md) | UniversalConnectionPoolManagerMBean.[`getConnectionPoolLifeCycleState`](../admin/UniversalConnectionPoolManagerMBean.md)`(java.lang.String poolName)`<br>Gets the life cycle state of the Universal Connection Pool. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../UniversalConnectionPoolLifeCycleState.md)
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
