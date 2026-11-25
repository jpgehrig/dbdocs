Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolManagerImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolManager.md)
- [Next Class](UniversalConnectionPoolManagerMBean.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.ucp.admin

## Class UniversalConnectionPoolManagerImpl

- java.lang.Object

- - oracle.ucp.admin.UniversalConnectionPoolManagerBase

  - - oracle.ucp.admin.UniversalConnectionPoolManagerImpl

<!-- -->

- All Implemented Interfaces:
  [UniversalConnectionPoolManager](UniversalConnectionPoolManager.md)

  ------------------------------------------------------------------------



      public class UniversalConnectionPoolManagerImpl
      extends oracle.ucp.admin.UniversalConnectionPoolManagerBase

  The `UniversalConnectionPoolManagerImpl` class is the implementation class for the pool manager. This is a singleton class and only one instance exists in a JVM.

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from class oracle.ucp.admin.UniversalConnectionPoolManagerBase

      `oracle.ucp.admin.UniversalConnectionPoolManagerBase.UCPMetric`

  <!-- -->

  - ### Field Summary

    - ### Fields inherited from class oracle.ucp.admin.UniversalConnectionPoolManagerBase

      `m_connPool, m_mappedPoolNames`

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                              | Method and Description                                                                                    |
    |--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
    | `static `[`UniversalConnectionPoolManager`](UniversalConnectionPoolManager.md) | `getUniversalConnectionPoolManager``()`<br>Returns the static Universal Connection Pool Manager instance. |

    - ### Methods inherited from class oracle.ucp.admin.UniversalConnectionPoolManagerBase

      `createConnectionPool, destroyConnectionPool, getConnectionPool, getConnectionPoolNames, getLogLevel, getManagerPoolID, getMetricUpdateInterval, getStateMetric, getTaskManager, getTimerManager, isJmxEnabled, purgeConnectionPool, reconfigureConnectionPool, recycleConnectionPool, refreshConnectionPool, setConnectionPool, setJmxEnabled, setLogLevel, setManagerPoolID, setMetricConsole, setMetricParentNoun, setMetricUpdateInterval, setTaskManager, setTimerManager, startConnectionPool, startMetricsCollection, stopConnectionPool, stopMetricsCollection`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getUniversalConnectionPoolManager

          public static UniversalConnectionPoolManager getUniversalConnectionPoolManager()
                                                                                  throws UniversalConnectionPoolException

      Returns the static Universal Connection Pool Manager instance. If necessary, a new instance is created and returned to the caller. This is a singleton object and there is only one `UniversalConnectionPoolManagerImpl` in a JVM.
      Returns:
      The UniversalConnectionPoolManager object.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while getting the `UniversalConnectionPoolManager` object.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolManagerImpl.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolManager.md)
- [Next Class](UniversalConnectionPoolManagerMBean.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
