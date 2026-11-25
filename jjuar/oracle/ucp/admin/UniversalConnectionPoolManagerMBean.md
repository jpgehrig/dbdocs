Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolManagerMBean.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolManagerImpl.md)
- [Next Class](UniversalConnectionPoolMBean.md)

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

## Interface UniversalConnectionPoolManagerMBean

-

  ------------------------------------------------------------------------



      public interface UniversalConnectionPoolManagerMBean

  The Universal Connection Pool Manager MBean defines operations and attributes for managing pool instances. Remote users can get access to these operations and attributes using JMX operations. The MBean has access to the Universal Connection Pool Manager and gets the required pool object to start an operation.
  There is only one Universal Connection Pool Manager MBean for a JVM and this is registered with an MBeanServer.

  All the operations implemented on the pool manager MBean are called only when `jmxFlag` on the pool manager is set to `true`. Default value for `jmxFlag` is `true`. When the MBeanServer is not available, `jmxFlag` is automatically set to `false`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                      | Method and Description                                                                                                                                                                                   |
    |----------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UniversalConnectionPoolMBean`](UniversalConnectionPoolMBean.md)                      | `createConnectionPool``(`[`UniversalConnectionPoolAdapter`](../UniversalConnectionPoolAdapter.md)` ucpAdapter)`<br>Creates a connection pool instance based on specified UCP Adapter.                    |
    | `void`                                                                                 | `destroyConnectionPool``(java.lang.String poolName)`<br>Destroys the connection pool.                                                                                                                    |
    | [`UniversalConnectionPoolLifeCycleState`](../UniversalConnectionPoolLifeCycleState.md) | `getConnectionPoolLifeCycleState``(java.lang.String poolName)`<br>Gets the life cycle state of the Universal Connection Pool.                                                                            |
    | `java.lang.String[]`                                                                   | `getConnectionPoolNames``()`<br>Gets all the pool names managed by the Universal Connection Pool Manager.                                                                                                |
    | `java.util.logging.Level`                                                              | `getLogLevel``()`<br>Gets the log level for the logger.                                                                                                                                                  |
    | `java.lang.String`                                                                     | `getMBeanNameForConnectionPool``(java.lang.String connectionPoolName)`<br>Gets the MBean Name for the corresponding Universal Connection Pool MBean Object.                                              |
    | `int`                                                                                  | `getMetricUpdateInterval``()`<br>Gets the metric update interval value.                                                                                                                                  |
    | `void`                                                                                 | `purgeConnectionPool``(java.lang.String poolName)`<br>Purges the connection pool.                                                                                                                        |
    | `void`                                                                                 | `reconfigureConnectionPool``(java.lang.String poolName, java.util.Properties configuration)`<br>Reconfigures the connection pool.                                                                        |
    | `void`                                                                                 | `recycleConnectionPool``(java.lang.String poolName)`<br>Recycles the connection pool.                                                                                                                    |
    | `void`                                                                                 | `refreshConnectionPool``(java.lang.String poolName)`<br>Refreshes the connection pool.                                                                                                                   |
    | `void`                                                                                 | `registerUniversalConnectionPoolMBean``(`[`UniversalConnectionPoolMBean`](UniversalConnectionPoolMBean.md)` poolMBean)`<br>Registers the Universal Connection Pool MBean instance with the MBean server. |
    | `void`                                                                                 | `setLogLevel``(java.util.logging.Level newLogLevel)`<br>Sets the log level for the UCP logger.                                                                                                           |
    | `void`                                                                                 | `setMetricUpdateInterval``(int interval)`<br>Sets the metric update interval value.                                                                                                                      |
    | `void`                                                                                 | `startConnectionPool``(java.lang.String poolName)`<br>Starts the connection pool.                                                                                                                        |
    | `void`                                                                                 | `startMetricsCollection``(java.lang.String poolName)`<br>Starts metric collection for the provided pool.                                                                                                 |
    | `void`                                                                                 | `stopConnectionPool``(java.lang.String poolName)`<br>Stops the connection pool.                                                                                                                          |
    | `void`                                                                                 | `stopMetricsCollection``(java.lang.String poolName)`<br>Stops metric collection for the provided pool.                                                                                                   |
    | `void`                                                                                 | `unregisterUniversalConnectionPoolMBean``(java.lang.String poolName)`<br>Unregisters the Universal Connection Pool MBean from the MBean server.                                                          |

<!-- -->

- - ### Method Detail

    - #### startConnectionPool

          void startConnectionPool(java.lang.String poolName)
                            throws UniversalConnectionPoolException

      Starts the connection pool. A connection pool object is obtained from the manager by providing `poolname` as a key. Pool operation is called to start the connection pool.
      Starting the pool does not start metric collection for the pool. Operation `startMetricsCollection` needs to be called to start the metric collection for the pool.

      Parameters:
      `String` - Connection pool name to find the connection pool object from the pool manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while starting the connection pool.

    <!-- -->

    - #### stopConnectionPool

          void stopConnectionPool(java.lang.String poolName)
                           throws UniversalConnectionPoolException

      Stops the connection pool. Connection pool object is obtained from the manager by providing `poolname` as a key. Pool operation is called to stop the connection pool. Stops the metric collection if it is already started.
      Parameters:
      `String` - Connection pool name to find the connection pool object from the pool manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while stopping the connection pool.

    <!-- -->

    - #### refreshConnectionPool

          void refreshConnectionPool(java.lang.String poolName)
                              throws UniversalConnectionPoolException

      Refreshes the connection pool. Connection pool object is obtained from the manager by providing `poolname` as a key. Pool operation is called to refresh the connection pool.
      Parameters:
      `String` - Connection pool name to find the connection pool object from the pool manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while refreshing the connection pool.

    <!-- -->

    - #### recycleConnectionPool

          void recycleConnectionPool(java.lang.String poolName)
                              throws UniversalConnectionPoolException

      Recycles the connection pool. Connection pool object is obtained from the manager by providing `poolname` as a key. Pool operation is called to recycle the connection pool. This is similar to `refresh()`, but allows only invalid available connections in the pool to be replaced with new/fresh connections.
      Parameters:
      `String` - Connection pool name to find the connection pool object from the pool manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while recycling the connection pool.

    <!-- -->

    - #### purgeConnectionPool

          void purgeConnectionPool(java.lang.String poolName)
                            throws UniversalConnectionPoolException

      Purges the connection pool. Connection pool object is obtained from the manager by providing `poolname` as a key. Pool operation is called to purge the connection pool.
      Removes all connections from the connection pool. The primary difference in behavior between this and `refresh()` is that the connection pool is left empty with no connections available after calling `purge()`. Some of the connection pool properties such as `minPoolSize` or `initialPoolSize` may not be honored when purging connections from the pool.

      Parameters:
      `String` - Connection pool name to find the connection pool object from the pool manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while purging the connection pool.

    <!-- -->

    - #### createConnectionPool

          UniversalConnectionPoolMBean createConnectionPool(UniversalConnectionPoolAdapter ucpAdapter)
                                                     throws UniversalConnectionPoolException

      Creates a connection pool instance based on specified UCP Adapter. Pool and connection factory configuration properties should be set on the Adapter prior to invoking this method. The created pool instance will be added to this UCP manager.
      Parameters:
      `UniversalConnectionPoolAdapter` - The UCP Adapter for pool creation.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while creating the connection pool.

    <!-- -->

    - #### destroyConnectionPool

          void destroyConnectionPool(java.lang.String poolName)
                              throws UniversalConnectionPoolException

      Destroys the connection pool. Connection pool object is obtained from the manager by providing `poolname` as a key. Pool operation is called to stop the connection pool. The pool is stopped and removed from the manager.
      Parameters:
      `String` - Connection pool name to find the connection pool object from the pool manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while destroying the connection pool.

    <!-- -->

    - #### reconfigureConnectionPool

          void reconfigureConnectionPool(java.lang.String poolName,
                                         java.util.Properties configuration)
                                  throws UniversalConnectionPoolException

      Reconfigures the connection pool. The connection pool is obtained from the manager by providing `poolName` as key. The following properties are supported in the "configuration" parameter: `initialPoolSize`, `minPoolSize`, `maxPoolSize`, `fastConnectionFailoverEnabled`, `maxIdleTime`, `maxConnectionReuseCount`, `maxConnectionReuseTime`, `maxStatements`, `abandonedConnectionTimeout`, `connectionHarvestMaxCount`, `timeoutCheckInterval`, `connectionHarvestTriggerCount`, `inactiveConnectionTimeout`, `propertyCycle`, `connectionWaitTimeout`, `validateConnectionOnBorrow`, `onsConfiguration`, `sqlForValidateConnection`, `timeToLiveConnectionTimeout`, `loginTimeout`, `highCostConnectionReuseThreshold`, `connectionLabelingHighCost`, `connectionAffinityCallback`, `connectionInitializationCallback`, `connectionLabelingCallback`, `secondsToTrustIdleConnection`, `connectionRepurposeThreshold`.
      Parameters:
      `poolName` - Connection pool name registered with the universal connection pool manager.

      `configuration` - the configuration input as Properties

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while reconfiguring the connection pool.

    <!-- -->

    - #### getConnectionPoolNames

          java.lang.String[] getConnectionPoolNames()
                                             throws UniversalConnectionPoolException

      Gets all the pool names managed by the Universal Connection Pool Manager.
      Returns:
      String\[\] List of connection pool Names, returned as an Array.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while getting the pool names.

    <!-- -->

    - #### startMetricsCollection

          void startMetricsCollection(java.lang.String poolName)
                               throws UniversalConnectionPoolException

      Starts metric collection for the provided pool.
      Parameters:
      `String` - Connection pool name to find the connection pool object from the pool manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while starting metrics collection.

    <!-- -->

    - #### stopMetricsCollection

          void stopMetricsCollection(java.lang.String poolName)
                              throws UniversalConnectionPoolException

      Stops metric collection for the provided pool.
      Parameters:
      `String` - Connection pool name to find the connection pool object from the pool manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while stopping metrics collection.

    <!-- -->

    - #### setMetricUpdateInterval

          void setMetricUpdateInterval(int interval)
                                throws UniversalConnectionPoolException

      Sets the metric update interval value.
      Parameters:
      `int` - Value for metric update interval in seconds.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while updating metric interval.

    <!-- -->

    - #### getMetricUpdateInterval

          int getMetricUpdateInterval()

      Gets the metric update interval value.
      Returns:
      The metric update interval in seconds.

    <!-- -->

    - #### registerUniversalConnectionPoolMBean

          void registerUniversalConnectionPoolMBean(UniversalConnectionPoolMBean poolMBean)
                                             throws UniversalConnectionPoolException

      Registers the Universal Connection Pool MBean instance with the MBean server. One MBean is registered for every Universal Connection Pool instance. The MBean is created using the standard `RequiredModelMBean` class during the registration of the Model MBean.
      Parameters:
      `UniversalConnectionPoolMBean` - the MBean to register in the MBeanServer.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while registering the MBean.

    <!-- -->

    - #### unregisterUniversalConnectionPoolMBean

          void unregisterUniversalConnectionPoolMBean(java.lang.String poolName)
                                               throws UniversalConnectionPoolException

      Unregisters the Universal Connection Pool MBean from the MBean server. The MBean is created using the standard `RequiredModelMBean` class during the registration of the Model MBean.
      Parameters:
      `String` - Pool name to identify the MBean and to unregister it from the MBeanServer.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while unregistering the MBean.

    <!-- -->

    - #### getConnectionPoolLifeCycleState

          UniversalConnectionPoolLifeCycleState getConnectionPoolLifeCycleState(java.lang.String poolName)
                                                                         throws UniversalConnectionPoolException

      Gets the life cycle state of the Universal Connection Pool.
      Parameters:
      `String` - Connection pool name to find the connection pool object from Universal Connection Pool Manager.

      Returns:
      The life cycle state of the connection pool.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while getting the life cycle state.

    <!-- -->

    - #### setLogLevel

          void setLogLevel(java.util.logging.Level newLogLevel)

      Sets the log level for the UCP logger.
      Parameters:
      `newLogLevel` - The new log level to be set for UCP logger.

    <!-- -->

    - #### getLogLevel

          java.util.logging.Level getLogLevel()

      Gets the log level for the logger.
      Returns:
      Level Returns the Level object for the Logger.

    <!-- -->

    - #### getMBeanNameForConnectionPool

          java.lang.String getMBeanNameForConnectionPool(java.lang.String connectionPoolName)
                                                  throws UniversalConnectionPoolException

      Gets the MBean Name for the corresponding Universal Connection Pool MBean Object.
      Parameters:
      `String` - Connection Pool Name for which MBean Name is queried

      Returns:
      String Returns the MBean Name String

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolManagerMBean.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolManagerImpl.md)
- [Next Class](UniversalConnectionPoolMBean.md)

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
