Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolAdapter.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPool.md)
- [Next Class](UniversalConnectionPoolException.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.ucp

## Interface UniversalConnectionPoolAdapter

- All Known Implementing Classes:
  [PoolDataSourceImpl](jdbc/PoolDataSourceImpl.md), [PoolXADataSourceImpl](jdbc/PoolXADataSourceImpl.md)

  ------------------------------------------------------------------------



      public interface UniversalConnectionPoolAdapter

  Universal Connection Pool Adapter interface.
  A Universal Connection Pool Adapter extends Universal Connection Pool to provide resource-specific functionality. The Universal Connection Pool Adapter is tightly coupled with the connection factory adapter and provides resource-specific implementations of the pooled connections.

  This interface defines standard operations that a Universal Connection Pool Adapter supports.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                       | Method and Description                                                                                    |
    |-------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
    | [`UniversalConnectionPool`](UniversalConnectionPool.md)                 | `createUniversalConnectionPool``()`<br>Creates a Universal Connection Pool instance using this adapter.   |
    | [`UniversalConnectionPoolMBean`](admin/UniversalConnectionPoolMBean.md) | `createUniversalConnectionPoolMBean``()`<br>Creates a Universal Connection Pool MBean using this adapter. |

<!-- -->

- - ### Method Detail

    - #### createUniversalConnectionPool

          UniversalConnectionPool createUniversalConnectionPool()
                                                         throws java.lang.Exception

      Creates a Universal Connection Pool instance using this adapter. Pool and connection factory configuration properties should be set on this adapter prior to invoking this method.
      This method should not register the created pool instance with the Universal Connection Pool Manager. The `createConnectionPool` method on `UniversalConnectionPoolManager` is responsible for that.

      Returns:
      The created Universal Connection Pool instance.

      Throws:
      `java.lang.Exception` - If any error occurs during the process of connection pool creation.

      See Also:
      [`UniversalConnectionPoolManager`](admin/UniversalConnectionPoolManager.md)

    <!-- -->

    - #### createUniversalConnectionPoolMBean

          UniversalConnectionPoolMBean createUniversalConnectionPoolMBean()
                                                                   throws java.lang.Exception

      Creates a Universal Connection Pool MBean using this adapter. If a Universal Connection Pool instance is not yet created, this method must first create a pool instance, in which case pool and connection factory configuration properties should be set on this adapter prior to invoking this method.
      This method should not register the created pool MBean with the MBean server. The `createConnectionPool` operation on `UniversalConnectionPoolManagerMBean` is responsible for that.

      Returns:
      The created Universal Connection Pool MBean.

      Throws:
      `java.lang.Exception` - If any error occurs during the process of connection pool creation.

      See Also:
      [`UniversalConnectionPoolManagerMBean`](admin/UniversalConnectionPoolManagerMBean.md)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolAdapter.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPool.md)
- [Next Class](UniversalConnectionPoolException.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2022, Oracle and/or its affiliates.
