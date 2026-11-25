Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolManager.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev Class
- [Next Class](UniversalConnectionPoolManagerImpl.md)

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

## Interface UniversalConnectionPoolManager

- All Known Implementing Classes:
  oracle.ucp.admin.UniversalConnectionPoolManagerBase, [UniversalConnectionPoolManagerImpl](UniversalConnectionPoolManagerImpl.md)

  ------------------------------------------------------------------------



      public interface UniversalConnectionPoolManager

  The UniversalConnectionPoolManager interface defines operations for creating and maintaining the Universal Connection Pool instances. A pool instance is registered with the pool manager every time a new pool is created. All the pool operations can be called by providing the pool name as a key. Operations for controlling the metric collection for individual Universal Connection Pool instances are also provided.
  The `jmxFlag` property on `UniversalConnectionPoolManager` determines the availability of JMX support. The default value for `jmxFlag` is `true`. The `jmxFlag` property is automatically set to `false` when the MBeanServer is not available.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                          | Method and Description                                                                                                                                                                     |
    |------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                     | `createConnectionPool``(`[`UniversalConnectionPoolAdapter`](../UniversalConnectionPoolAdapter.md)` ucpAdapter)`<br>Creates a connection pool instance based on specified UCP Adapter.      |
    | `void`                                                     | `destroyConnectionPool``(java.lang.String poolName)`<br>Destroys the connection pool.                                                                                                      |
    | [`UniversalConnectionPool`](../UniversalConnectionPool.md) | `getConnectionPool``(java.lang.String poolName)`<br>Gets the Universal Connection Pool instance from the Universal Connection Pool Manager.                                                |
    | `java.lang.String[]`                                       | `getConnectionPoolNames``()`<br>Gets all the pool names managed by the Universal Connection Pool Manager.                                                                                  |
    | `java.util.logging.Level`                                  | `getLogLevel``()`<br>Gets the log level for the logger.                                                                                                                                    |
    | `int`                                                      | `getMetricUpdateInterval``()`<br>Gets the metric update interval value.                                                                                                                    |
    | `boolean`                                                  | `isJmxEnabled``()`<br>Determines the JMX availability.                                                                                                                                     |
    | `void`                                                     | `purgeConnectionPool``(java.lang.String poolName)`<br>Purges the connection pool.                                                                                                          |
    | `void`                                                     | `reconfigureConnectionPool``(java.lang.String poolName, java.util.Properties configuration)`<br>Reconfigures the connection pool.                                                          |
    | `void`                                                     | `recycleConnectionPool``(java.lang.String poolName)`<br>Recycles the connection pool.                                                                                                      |
    | `void`                                                     | `refreshConnectionPool``(java.lang.String poolName)`<br>Refreshes the connection pool.                                                                                                     |
    | `void`                                                     | `setConnectionPool``(`[`UniversalConnectionPool`](../UniversalConnectionPool.md)` connectionPool)`<br>Sets the Universal Connection Pool with the `UniversalConnectionPoolManager` Object. |
    | `void`                                                     | `setJmxEnabled``(boolean jmxFlag)`<br>Sets the `jmxFlag` to either `true` or `false`.                                                                                                      |
    | `void`                                                     | `setLogLevel``(java.util.logging.Level newLogLevel)`<br>Sets the log level for the UCP logger.                                                                                             |
    | `void`                                                     | `setMetricUpdateInterval``(int interval)`<br>Sets the metric update interval value.                                                                                                        |
    | `void`                                                     | `startConnectionPool``(java.lang.String poolName)`<br>Starts the connection pool instance with the given name.                                                                             |
    | `void`                                                     | `startMetricsCollection``(java.lang.String poolName)`<br>Starts metric collection for the provided pool.                                                                                   |
    | `void`                                                     | `stopConnectionPool``(java.lang.String poolName)`<br>Stops the connection pool.                                                                                                            |
    | `void`                                                     | `stopMetricsCollection``(java.lang.String poolName)`<br>Stops metric collection for the provided pool.                                                                                     |

<!-- -->

- - ### Method Detail

    - #### startConnectionPool

          void startConnectionPool(java.lang.String poolName)
                            throws UniversalConnectionPoolException

      Starts the connection pool instance with the given name.
      Starting the pool does not start metric collection for the pool. Operation `startMetricsCollection` needs to be called to start the metric collection for the pool.

      Parameters:
      `String` - Connection pool name for identifying the pool instance registered with the pool manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while starting the connection pool.

    <!-- -->

    - #### stopConnectionPool

          void stopConnectionPool(java.lang.String poolName)
                           throws UniversalConnectionPoolException

      Stops the connection pool. Connection pool object is obtained from the manager by providing pool name as key. Pool operation is called to stop the connection pool. Stops the metric collection if it is already started.
      Parameters:
      `String` - Connection pool name to find the connection pool object from the pool manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while stopping the connection pool.

    <!-- -->

    - #### refreshConnectionPool

          void refreshConnectionPool(java.lang.String poolName)
                              throws UniversalConnectionPoolException

      Refreshes the connection pool. Connection pool object is obtained from the manager by providing `poolname` as key. Pool operation is called to refresh the connection pool.
      Parameters:
      `String` - Connection pool name to find the connection pool object from pool manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while refreshing the connection pool.

    <!-- -->

    - #### recycleConnectionPool

          void recycleConnectionPool(java.lang.String poolName)
                              throws UniversalConnectionPoolException

      Recycles the connection pool. Connection pool object is obtained from the manager by providing `poolname` as key. Pool operation is called to recycle the connection pool. This is similar to `refresh()`, but allows only invalid available connections in the pool to be replaced with new/fresh connections.
      Parameters:
      `String` - Connection pool name to find the connection pool object from pool manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while recycling the connection pool.

    <!-- -->

    - #### purgeConnectionPool

          void purgeConnectionPool(java.lang.String poolName)
                            throws UniversalConnectionPoolException

      Purges the connection pool. Connection pool object is obtained from the manager by providing `poolname` as key. Pool operation is called to purge the connection pool.
      Removes all connections from the connection pool. The primary difference in behavior between this and `refresh()` is that the connection pool is left empty with no connections available after calling `purge()`. Some of the connection pool properties such as `minPoolSize` or `initialPoolSize` may not be honored when purging connections from the pool.

      Parameters:
      `String` - Connection pool name to find the connection pool object from pool manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while purging the connection pool.

    <!-- -->

    - #### createConnectionPool

          void createConnectionPool(UniversalConnectionPoolAdapter ucpAdapter)
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

      Destroys the connection pool. The connection pool is obtained from the manager by providing `poolname` as key. Pool operation is called to stop the connection pool. Pool will be stopped and removed from the manager.
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

    - #### setConnectionPool

          void setConnectionPool(UniversalConnectionPool connectionPool)
                          throws UniversalConnectionPoolException

      Sets the Universal Connection Pool with the `UniversalConnectionPoolManager` Object. Once the pool is stored, it can be maintained with the operations provided on the pool manager.
      Parameters:
      `UniversalConnectionPool` - The `UniversalConnectionPool` object to be maintained by the Universal Connection Pool Manager.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while storing the `UniversalConnectionPool` object with the Universal Connection Pool Manager.

    <!-- -->

    - #### getConnectionPool

          UniversalConnectionPool getConnectionPool(java.lang.String poolName)
                                             throws UniversalConnectionPoolException

      Gets the Universal Connection Pool instance from the Universal Connection Pool Manager.
      Parameters:
      `String` - Connection pool name to get the Universal Connection Pool instance.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while getting the Universal Connection Pool instance.

    <!-- -->

    - #### getConnectionPoolNames

          java.lang.String[] getConnectionPoolNames()
                                             throws UniversalConnectionPoolException

      Gets all the pool names managed by the Universal Connection Pool Manager.
      Returns:
      String\[\] List of connection pool names, returned as an Array.

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

    - #### setJmxEnabled

          void setJmxEnabled(boolean jmxFlag)
                      throws UniversalConnectionPoolException

      Sets the `jmxFlag` to either `true` or `false`.
      Parameters:
      `boolean` - Flag indicating whether JMX is enabled or not.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while setting `jmxFlag`.

    <!-- -->

    - #### isJmxEnabled

          boolean isJmxEnabled()

      Determines the JMX availability.
      Returns:
      `true` if JMX is enabled; otherwise `false`.

    <!-- -->

    - #### setLogLevel

          void setLogLevel(java.util.logging.Level newLogLevel)

      Sets the log level for the UCP logger.
      Parameters:
      `Level` - The new log level to be set for UCP logger.

    <!-- -->

    - #### getLogLevel

          java.util.logging.Level getLogLevel()

      Gets the log level for the logger.
      Returns:
      Level Returns the Level object for the Logger.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolManager.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- Prev Class
- [Next Class](UniversalConnectionPoolManagerImpl.md)

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
