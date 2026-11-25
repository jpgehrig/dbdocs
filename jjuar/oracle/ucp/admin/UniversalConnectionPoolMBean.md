Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolMBean.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolManagerMBean.md)
- Next Class

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

## Interface UniversalConnectionPoolMBean

-

  ------------------------------------------------------------------------



      public interface UniversalConnectionPoolMBean

  The Universal Connection Pool MBean defines operations and attributes for managing the Universal Connection Pool. The MBean is always associated with a pool instance. Remote users can get access to these operations and attributes using JMX operations.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                       | Method and Description                                                                                                                                                                                                  |
    |---------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                                   | `getAbandonedConnectionsCount``()`<br>Gets the number of abandoned connections that have been reclaimed.                                                                                                                |
    | `int`                                                   | `getAbandonedConnectionTimeout``()`<br>Gets the abandoned connection timeout of the Universal Connection Pool instance.                                                                                                 |
    | `int`                                                   | `getAvailableConnectionsCount``()`<br>Gets the available connections count of the Universal Connection Pool instance.                                                                                                   |
    | `int`                                                   | `getAverageBorrowedConnectionsCount``()`<br>Gets the average number of connections that are borrowed and actively in use by clients.                                                                                    |
    | `long`                                                  | `getAverageConnectionWaitTime``()`<br>Gets the average time (in milliseconds) a user thread has to wait before it could obtain a connection from the connection pool.                                                   |
    | `int`                                                   | `getBorrowedConnectionsCount``()`<br>Gets the borrowed connections count of the Universal Connection Pool instance.                                                                                                     |
    | `int`                                                   | `getConnectionHarvestMaxCount``()`<br>Gets the connection harvest maximum count of the Universal Connection Pool instance.                                                                                              |
    | `int`                                                   | `getConnectionHarvestTriggerCount``()`<br>Gets the connection harvest trigger count of the Universal Connection Pool instance.                                                                                          |
    | `long`                                                  | `getConnectionRepurposeCount``()`<br>Returns the number of connection repurposed in a shared pool for a mutitenant database, where connections can be reused across PDB's by switching their container and PDB service. |
    | `int`                                                   | `getConnectionsClosedCount``()`<br>Gets the number of connections closed by this connection pool.                                                                                                                       |
    | `int`                                                   | `getConnectionsCreatedCount``()`<br>Gets the number of connections created for this connection pool.                                                                                                                    |
    | `int`                                                   | `getConnectionValidationTimeout``()`<br>Connection validation timeout getter                                                                                                                                            |
    | `int`                                                   | `getConnectionWaitTimeout``()`<br>Gets the connection wait timeout of the Universal Connection Pool instance.                                                                                                           |
    | `long`                                                  | `getCumulativeConnectionBorrowedCount``()`<br>Gets the number of connections borrowed from the connection pool over the life of the pool.                                                                               |
    | `long`                                                  | `getCumulativeConnectionReturnedCount``()`<br>Gets the number of connections returned to the connection pool over the life of the pool.                                                                                 |
    | `long`                                                  | `getCumulativeConnectionUseTime``()`<br>Gets the cumulative time (in milliseconds) of connections that were borrowed from the pool and remained in use.                                                                 |
    | `long`                                                  | `getCumulativeConnectionWaitTime``()`<br>Gets the cumulative time (in milliseconds) that connection requests have waited for connections over the life of the connection pool.                                          |
    | `long`                                                  | `getCumulativeFailedConnectionWaitCount``()`<br>Gets the number of connection requests that waited unsuccessfully to borrow a connection from the pool.                                                                 |
    | `long`                                                  | `getCumulativeFailedConnectionWaitTime``()`<br>Gets the cumulative time (in milliseconds) that connection requests waited but failed to borrow a connection from the pool.                                              |
    | `long`                                                  | `getCumulativeSuccessfulConnectionWaitCount``()`<br>Gets the number of connection requests that waited successfully and borrowed a connection from the pool.                                                            |
    | `long`                                                  | `getCumulativeSuccessfulConnectionWaitTime``()`<br>Gets the cumulative time (in milliseconds) that connection requests waited successfully and borrowed a connection from the pool.                                     |
    | `long`                                                  | `getFailedAffinityBasedBorrowCount``()`<br>Gets the number of borrow requests that returned connections not matching the affinity contexts.                                                                             |
    | `long`                                                  | `getFailedRCLBBasedBorrowCount``()`<br>Gets the number of borrow requests failed using Runtime Connection Load-Balancing (RCLB) algorithms.                                                                             |
    | `java.lang.String`                                      | `getFcfProcessingInfo``()`<br>Gets the information of recent Fast Connection Failover (FCF) attempts, in the form of a String.                                                                                          |
    | `java.lang.String`                                      | `getFcfProcessingInfoProcessedOnly``()`                                                                                                                                                                                 |
    | `int`                                                   | `getInactiveConnectionTimeout``()`<br>Gets the inactive connection timeout of the Universal Connection Pool instance.                                                                                                   |
    | `int`                                                   | `getInitialPoolSize``()`<br>Gets the initial pool size of the Universal Connection Pool instance.                                                                                                                       |
    | `int`                                                   | `getLabeledConnectionsCount``()`<br>Gets the number of labeled connections in the connection pool.                                                                                                                      |
    | `java.lang.String`                                      | `getLifeCycleState``()`<br>Gets the lifecycle state of Universal Connection Pool instance.                                                                                                                              |
    | `int`                                                   | `getMaxConnectionReuseCount``()`<br>Gets the maximum connection reuse count of the Universal Connection Pool instance.                                                                                                  |
    | `long`                                                  | `getMaxConnectionReuseTime``()`<br>Gets the maximum connection reuse time of the Universal Connection Pool instance.                                                                                                    |
    | `int`                                                   | `getMaxPoolSize``()`<br>Gets the maximum pool size of the Universal Connection Pool instance.                                                                                                                           |
    | `javax.management.modelmbean.ModelMBeanInfo`            | `getMBeanInfo``(javax.management.ObjectName mbeanObjName, java.lang.String mbeanDisplayName)`<br>Builds `MBeanInfo` to define attributes, constructors, operations and notifications to expose to the remote users.     |
    | `int`                                                   | `getMinPoolSize``()`<br>Gets the minimum pool size of the Universal Connection Pool instance.                                                                                                                           |
    | `java.lang.String`                                      | `getName``()`<br>Gets the name of the Universal Connection Pool instance.                                                                                                                                               |
    | `int`                                                   | `getPeakConnectionsCount``()`<br>Gets the maximum number of connections that the connection pool has reached during the life of the pool.                                                                               |
    | `long`                                                  | `getPeakConnectionWaitTime``()`<br>Gets the longest wait (in milliseconds) a user request has to incur before obtaining a connection from the connection pool.                                                          |
    | `int`                                                   | `getPendingRequestsCount``()`<br>Gets the number of clients that are currently waiting to obtain a connection from the pool.                                                                                            |
    | `int`                                                   | `getRemainingPoolCapacityCount``()`<br>Gets the number of connections that may be added to the pool before it reaches `maxPoolSize`.                                                                                    |
    | `int`                                                   | `getSecondsToTrustIdleConnection``()`<br>Gets the seconds To Trust Idle Connection value.                                                                                                                               |
    | `boolean`                                               | `getShardingMode``()`<br>Returns the mode of UCP when UCP is using a Sharded Database.                                                                                                                                  |
    | `java.lang.String`                                      | `getStatistics``()`<br>Gets statistics for the Universal Connection Pool instance.                                                                                                                                      |
    | `long`                                                  | `getSuccessfulAffinityBasedBorrowCount``()`<br>Gets the number of borrow requests succeeded with matching affinity contexts.                                                                                            |
    | `long`                                                  | `getSuccessfulRCLBBasedBorrowCount``()`<br>Gets the number of borrow requests succeeded using Runtime Connection Load-Balancing (RCLB) algorithms.                                                                      |
    | `int`                                                   | `getTimeoutCheckInterval``()`<br>Gets the timeout check interval of the Universal Connection Pool instance.                                                                                                             |
    | `int`                                                   | `getTimeToLiveConnectionTimeout``()`<br>Gets the time to live connection timeout of the Universal Connection Pool instance.                                                                                             |
    | `int`                                                   | `getTotalConnectionsCount``()`<br>Gets the total number of connections (both available and borrowed) in the connection pool.                                                                                            |
    | `javax.management.modelmbean.ModelMBeanAttributeInfo[]` | `getUCPMBeanAttributes``()`<br>Builds the attribute information for the Universal Connection Pool MBean.                                                                                                                |
    | `javax.management.modelmbean.ModelMBeanOperationInfo[]` | `getUCPMBeanOperations``()`<br>Builds the operation information for the Universal Connection Pool MBean.                                                                                                                |
    | `boolean`                                               | `getValidateConnectionOnBorrow``()`<br>Gets the validate connection on borrow value of the Universal Connection Pool instance.                                                                                          |
    | `void`                                                  | `purge``()`<br>Purges the Universal Connection Pool instance.                                                                                                                                                           |
    | `void`                                                  | `recycle``()`<br>Recycles the Universal Connection Pool instance.                                                                                                                                                       |
    | `void`                                                  | `refresh``()`<br>Refreshes the Universal Connection Pool instance.                                                                                                                                                      |
    | `void`                                                  | `setAbandonedConnectionTimeout``(int abandonedConnectionTimeout)`<br>Sets the abandoned connection timeout of the Universal Connection Pool instance.                                                                   |
    | `void`                                                  | `setConnectionHarvestMaxCount``(int connectionHarvestMaxCount)`<br>Sets the connection harvest maximum count for the Universal Connection Pool instance.                                                                |
    | `void`                                                  | `setConnectionHarvestTriggerCount``(int connectionHarvestTriggerCount)`<br>Sets the connection harvest trigger count for the Universal Connection Pool instance.                                                        |
    | `void`                                                  | `setConnectionValidationTimeout``(int connectionValidationTimeout)`<br>Connection validation timeout setter                                                                                                             |
    | `void`                                                  | `setConnectionWaitTimeout``(int connectionWaitTimeout)`<br>Sets the connection wait timeout of the Universal Connection Pool instance.                                                                                  |
    | `void`                                                  | `setInactiveConnectionTimeout``(int inactiveConnectionTimeout)`<br>Sets the inactive connection timeout.                                                                                                                |
    | `void`                                                  | `setInitialPoolSize``(int initialPoolSize)`<br>Sets the initial pool size of the Universal Connection Pool instance.                                                                                                    |
    | `void`                                                  | `setMaxConnectionReuseCount``(int maxConnectionReuseCount)`<br>Sets the maximum connection reuse count for the Universal Connection Pool instance.                                                                      |
    | `void`                                                  | `setMaxConnectionReuseTime``(long maxConnectionReuseTime)`<br>Sets the maximum connection reuse time for the Universal Connection Pool instance.                                                                        |
    | `void`                                                  | `setMaxPoolSize``(int maxPoolSize)`<br>Sets the maximum pool size of the Universal Connection Pool instance.                                                                                                            |
    | `void`                                                  | `setMinPoolSize``(int minPoolSize)`<br>Sets the minimum pool size of the Universal Connection Pool instance.                                                                                                            |
    | `void`                                                  | `setName``(java.lang.String name)`<br>Sets the name of the Universal Connection Pool instance.                                                                                                                          |
    | `void`                                                  | `setSecondsToTrustIdleConnection``(int secondsToTrustIdleConnection)`<br>Sets the time in seconds to trust an idle connection to skip a validation test.                                                                |
    | `void`                                                  | `setShardingMode``(boolean shardingMode)`<br>This API changes the mode of UCP when UCP is using a Sharded Database.                                                                                                     |
    | `void`                                                  | `setTimeoutCheckInterval``(int timeoutCheckInterval)`<br>Sets the timeout check interval of the Universal Connection Pool instance.                                                                                     |
    | `void`                                                  | `setTimeToLiveConnectionTimeout``(int timeToLiveConnectionTimeout)`<br>Sets the time to live connection timeout of the Universal Connection Pool instance.                                                              |
    | `void`                                                  | `setValidateConnectionOnBorrow``(boolean validateConnectionOnBorrow)`<br>Sets the validate connection on borrow value for the Universal Connection Pool instance.                                                       |
    | `void`                                                  | `start``()`<br>Starts the Universal Connection Pool instance.                                                                                                                                                           |
    | `void`                                                  | `stop``()`<br>Stops the Universal Connection Pool instance.                                                                                                                                                             |
    | `void`                                                  | `useStrictWebSessionAffinity``(boolean strict)`<br>The knob for switching strict web session affinity                                                                                                                   |
    | `void`                                                  | `useStrictXAAffinity``(boolean strict)`                                                                                                                                                                                 |

<!-- -->

- - ### Method Detail

    - #### refresh

          void refresh()
                throws UniversalConnectionPoolException

      Refreshes the Universal Connection Pool instance.
      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while refreshing the Universal Connection Pool instance.

    <!-- -->

    - #### recycle

          void recycle()
                throws UniversalConnectionPoolException

      Recycles the Universal Connection Pool instance.
      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while recycling the Universal Connection Pool instance.

    <!-- -->

    - #### purge

          void purge()
              throws UniversalConnectionPoolException

      Purges the Universal Connection Pool instance.
      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while purging the Universal Connection Pool instance.

    <!-- -->

    - #### start

          void start()
              throws UniversalConnectionPoolException

      Starts the Universal Connection Pool instance.
      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while starting the Universal Connection Pool instance.

    <!-- -->

    - #### stop

          void stop()
             throws UniversalConnectionPoolException

      Stops the Universal Connection Pool instance.
      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while stopping the Universal Connection Pool instance.

    <!-- -->

    - #### getName

          java.lang.String getName()

      Gets the name of the Universal Connection Pool instance.
      Returns:
      String Returns the name.

    <!-- -->

    - #### setName

          void setName(java.lang.String name)
                throws UniversalConnectionPoolException

      Sets the name of the Universal Connection Pool instance.
      Parameters:
      `name` - A new name for the Universal Connection Pool instance.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the name.

    <!-- -->

    - #### getInitialPoolSize

          int getInitialPoolSize()

      Gets the initial pool size of the Universal Connection Pool instance.
      Returns:
      The initial pool size.

    <!-- -->

    - #### setInitialPoolSize

          void setInitialPoolSize(int initialPoolSize)
                           throws UniversalConnectionPoolException

      Sets the initial pool size of the Universal Connection Pool instance.
      Parameters:
      `initialPoolSize` - New initial pool size.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the initial pool size.

    <!-- -->

    - #### getMinPoolSize

          int getMinPoolSize()

      Gets the minimum pool size of the Universal Connection Pool instance.
      Returns:
      The minimum pool size.

    <!-- -->

    - #### setMinPoolSize

          void setMinPoolSize(int minPoolSize)
                       throws UniversalConnectionPoolException

      Sets the minimum pool size of the Universal Connection Pool instance.
      Parameters:
      `minPoolSize` - New minimum pool size.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the minimum pool.

    <!-- -->

    - #### getMaxPoolSize

          int getMaxPoolSize()

      Gets the maximum pool size of the Universal Connection Pool instance.
      Returns:
      The maximum pool size.

    <!-- -->

    - #### setMaxPoolSize

          void setMaxPoolSize(int maxPoolSize)
                       throws UniversalConnectionPoolException

      Sets the maximum pool size of the Universal Connection Pool instance.
      Parameters:
      `maxPoolSize` - New maximum pool size.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the maximum pool size.

    <!-- -->

    - #### getInactiveConnectionTimeout

          int getInactiveConnectionTimeout()

      Gets the inactive connection timeout of the Universal Connection Pool instance.
      Returns:
      The inactive connection timeout.

    <!-- -->

    - #### setInactiveConnectionTimeout

          void setInactiveConnectionTimeout(int inactiveConnectionTimeout)
                                     throws UniversalConnectionPoolException

      Sets the inactive connection timeout.
      Parameters:
      `inactiveConnectionTimeout` - New inactive connection timeout.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the inactive connection timeout.

    <!-- -->

    - #### getAbandonedConnectionTimeout

          int getAbandonedConnectionTimeout()

      Gets the abandoned connection timeout of the Universal Connection Pool instance.
      Returns:
      The abandoned connection timeout.

    <!-- -->

    - #### setAbandonedConnectionTimeout

          void setAbandonedConnectionTimeout(int abandonedConnectionTimeout)
                                      throws UniversalConnectionPoolException

      Sets the abandoned connection timeout of the Universal Connection Pool instance.
      Parameters:
      `abandonedConnectionTimeout` - New abandoned connection timeout.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the abandoned connection timeout.

    <!-- -->

    - #### getConnectionWaitTimeout

          int getConnectionWaitTimeout()

      Gets the connection wait timeout of the Universal Connection Pool instance.
      Returns:
      The connection wait timeout.

    <!-- -->

    - #### setConnectionWaitTimeout

          void setConnectionWaitTimeout(int connectionWaitTimeout)
                                 throws UniversalConnectionPoolException

      Sets the connection wait timeout of the Universal Connection Pool instance.
      Parameters:
      `connectionWaitTimeout` - New connection wait timeout.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the connection wait timeout.

    <!-- -->

    - #### getTimeToLiveConnectionTimeout

          int getTimeToLiveConnectionTimeout()

      Gets the time to live connection timeout of the Universal Connection Pool instance.
      Returns:
      The time to live connection timeout.

    <!-- -->

    - #### setTimeToLiveConnectionTimeout

          void setTimeToLiveConnectionTimeout(int timeToLiveConnectionTimeout)
                                       throws UniversalConnectionPoolException

      Sets the time to live connection timeout of the Universal Connection Pool instance.
      Parameters:
      `timeToLiveConnectionTimeout` - New time to live connection timeout.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the time to live connection timeout.

    <!-- -->

    - #### getTimeoutCheckInterval

          int getTimeoutCheckInterval()

      Gets the timeout check interval of the Universal Connection Pool instance.
      Returns:
      The timeout check interval.

    <!-- -->

    - #### setTimeoutCheckInterval

          void setTimeoutCheckInterval(int timeoutCheckInterval)
                                throws UniversalConnectionPoolException

      Sets the timeout check interval of the Universal Connection Pool instance.
      Parameters:
      `timeoutCheckInterval` - New timeout check interval.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the timeout check interval.

    <!-- -->

    - #### getValidateConnectionOnBorrow

          boolean getValidateConnectionOnBorrow()

      Gets the validate connection on borrow value of the Universal Connection Pool instance.
      Returns:
      The validate connection on borrow value.

    <!-- -->

    - #### setValidateConnectionOnBorrow

          void setValidateConnectionOnBorrow(boolean validateConnectionOnBorrow)

      Sets the validate connection on borrow value for the Universal Connection Pool instance.
      Parameters:
      `validateConnectionOnBorrow` - New validate connection on borrow value.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the validate connection on borrow value.

    <!-- -->

    - #### getConnectionHarvestTriggerCount

          int getConnectionHarvestTriggerCount()

      Gets the connection harvest trigger count of the Universal Connection Pool instance.
      Returns:
      The connection harvest trigger count.

    <!-- -->

    - #### setConnectionHarvestTriggerCount

          void setConnectionHarvestTriggerCount(int connectionHarvestTriggerCount)
                                         throws UniversalConnectionPoolException

      Sets the connection harvest trigger count for the Universal Connection Pool instance.
      Parameters:
      `connectionHarvestTriggerCount` - New connection harvest trigger count.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the connection harvest trigger count.

    <!-- -->

    - #### getConnectionHarvestMaxCount

          int getConnectionHarvestMaxCount()

      Gets the connection harvest maximum count of the Universal Connection Pool instance.
      Returns:
      The connection harvest maximum count.

    <!-- -->

    - #### setConnectionHarvestMaxCount

          void setConnectionHarvestMaxCount(int connectionHarvestMaxCount)
                                     throws UniversalConnectionPoolException

      Sets the connection harvest maximum count for the Universal Connection Pool instance.
      Parameters:
      `connectionHarvestMaxCount` - New connection harvest maximum count.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the connection harvest maximum count.

    <!-- -->

    - #### getMaxConnectionReuseTime

          long getMaxConnectionReuseTime()

      Gets the maximum connection reuse time of the Universal Connection Pool instance.
      Returns:
      The maximum connection reuse time.

    <!-- -->

    - #### setMaxConnectionReuseTime

          void setMaxConnectionReuseTime(long maxConnectionReuseTime)
                                  throws UniversalConnectionPoolException

      Sets the maximum connection reuse time for the Universal Connection Pool instance.
      Parameters:
      `maxConnectionReuseTime` - New maximum connection reuse time (in seconds).

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the maximum connection reuse time.

    <!-- -->

    - #### getMaxConnectionReuseCount

          int getMaxConnectionReuseCount()

      Gets the maximum connection reuse count of the Universal Connection Pool instance.
      Returns:
      The maximum connection reuse count.

    <!-- -->

    - #### setMaxConnectionReuseCount

          void setMaxConnectionReuseCount(int maxConnectionReuseCount)
                                   throws UniversalConnectionPoolException

      Sets the maximum connection reuse count for the Universal Connection Pool instance.
      Parameters:
      `maxConnectionReuseCount` - New maximum connection reuse count.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while changing the maximum connection reuse count.

    <!-- -->

    - #### setShardingMode

          void setShardingMode(boolean shardingMode)

      This API changes the mode of UCP when UCP is using a Sharded Database. By default UCP requires the caller to provide a sharding key for every connection request. When switching off the sharding mode, UCP behaves like a regular connection pool and all the sharding features are disabled so that a caller can request a connection without providing any sharding key.
      Parameters:
      `shardingMode` - Mode of UCP when using a Sharded Database.

    <!-- -->

    - #### getShardingMode

          boolean getShardingMode()

      Returns the mode of UCP when UCP is using a Sharded Database. By default sharding mode is ON which means UCP requires the caller to provide a sharding key for every connection request.
      Returns:
      Mode of UCP when using a Sharded Database.

    <!-- -->

    - #### setConnectionValidationTimeout

          void setConnectionValidationTimeout(int connectionValidationTimeout)
                                       throws UniversalConnectionPoolException

      Connection validation timeout setter
      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md)

    <!-- -->

    - #### getConnectionValidationTimeout

          int getConnectionValidationTimeout()

      Connection validation timeout getter

    <!-- -->

    - #### getAvailableConnectionsCount

          int getAvailableConnectionsCount()

      Gets the available connections count of the Universal Connection Pool instance.
      Returns:
      The available connections count.

    <!-- -->

    - #### getBorrowedConnectionsCount

          int getBorrowedConnectionsCount()

      Gets the borrowed connections count of the Universal Connection Pool instance.
      Returns:
      The borrowed connections count.

    <!-- -->

    - #### getStatistics

          java.lang.String getStatistics()

      Gets statistics for the Universal Connection Pool instance.
      Returns:
      The statistics.

    <!-- -->

    - #### getLifeCycleState

          java.lang.String getLifeCycleState()

      Gets the lifecycle state of Universal Connection Pool instance.
      Returns:
      The lifecycle state.

    <!-- -->

    - #### getUCPMBeanAttributes

          javax.management.modelmbean.ModelMBeanAttributeInfo[] getUCPMBeanAttributes()
                                                                               throws UniversalConnectionPoolException

      Builds the attribute information for the Universal Connection Pool MBean.
      Returns:
      `ModelMBeanAttributeInfo[]`.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while getting `ModelMBeanAttributeInfo[]`.

    <!-- -->

    - #### getUCPMBeanOperations

          javax.management.modelmbean.ModelMBeanOperationInfo[] getUCPMBeanOperations()
                                                                               throws UniversalConnectionPoolException

      Builds the operation information for the Universal Connection Pool MBean.
      Returns:
      `ModelMBeanOperationInfo[]`.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while getting `ModelMBeanOperationInfo[]`.

    <!-- -->

    - #### getMBeanInfo

          javax.management.modelmbean.ModelMBeanInfo getMBeanInfo(javax.management.ObjectName mbeanObjName,
                                                                  java.lang.String mbeanDisplayName)
                                                           throws UniversalConnectionPoolException

      Builds `MBeanInfo` to define attributes, constructors, operations and notifications to expose to the remote users.
      Parameters:
      `mbeanObjName` - Unique name for the Universal Connection Pool MBean.

      `mbeanDisplayName` - Display name for the Universal Connection Pool MBean.

      Returns:
      `ModelMBeanInfo` for Universal Connection Pool MBean.

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md) - If an error occurs while getting `ModelMBeanInfo` for the Universal Connection Pool MBean.

    <!-- -->

    - #### useStrictWebSessionAffinity

          void useStrictWebSessionAffinity(boolean strict)

      The knob for switching strict web session affinity
      Parameters:
      `strict` - if strict, otherwise nonstrict

    <!-- -->

    - #### useStrictXAAffinity

          void useStrictXAAffinity(boolean strict)

    <!-- -->

    - #### getSecondsToTrustIdleConnection

          int getSecondsToTrustIdleConnection()

      Gets the seconds To Trust Idle Connection value. See property description in `setSecondsToTrustIdleConnection()`.
      Returns:
      Seconds To Trust Idle Connection value.

    <!-- -->

    - #### setSecondsToTrustIdleConnection

          void setSecondsToTrustIdleConnection(int secondsToTrustIdleConnection)
                                        throws UniversalConnectionPoolException

      Sets the time in seconds to trust an idle connection to skip a validation test. It works in conjunction with `setValidateConnectionOnBorrow(boolean)`. When set to any positive value, a connection validation during the checkout is skipped if the connection was successfully used and returned to the pool within the time specified for secondsToTrustIdleConnection. Default value is set to 0 seconds which means that the feature is disabled.
      Parameters:
      `secondsToTrustIdleConnection` - The value of how long a connection can be trusted to skip connectionValidationOnBorrow

      Throws:
      [`UniversalConnectionPoolException`](../UniversalConnectionPoolException.md)

    <!-- -->

    - #### getTotalConnectionsCount

          int getTotalConnectionsCount()

      Gets the total number of connections (both available and borrowed) in the connection pool.
      Returns:
      The total number of connections (both available and borrowed) in the connection pool.

    <!-- -->

    - #### getAverageBorrowedConnectionsCount

          int getAverageBorrowedConnectionsCount()

      Gets the average number of connections that are borrowed and actively in use by clients.
      Returns:
      The number of connections that are borrowed and actively in use by clients.

    <!-- -->

    - #### getPeakConnectionsCount

          int getPeakConnectionsCount()

      Gets the maximum number of connections that the connection pool has reached during the life of the pool.
      Returns:
      The maximum number of connections that the connection pool has reached during the life of the pool.

    <!-- -->

    - #### getRemainingPoolCapacityCount

          int getRemainingPoolCapacityCount()

      Gets the number of connections that may be added to the pool before it reaches `maxPoolSize`.
      Returns:
      The number of connections that may be added to the pool before it reaches `maxPoolSize`.

    <!-- -->

    - #### getLabeledConnectionsCount

          int getLabeledConnectionsCount()

      Gets the number of labeled connections in the connection pool.
      Returns:
      The number of labeled connections in the connection pool.

    <!-- -->

    - #### getConnectionsCreatedCount

          int getConnectionsCreatedCount()

      Gets the number of connections created for this connection pool.
      Returns:
      The number of connections created for this connection pool.

    <!-- -->

    - #### getConnectionsClosedCount

          int getConnectionsClosedCount()

      Gets the number of connections closed by this connection pool.
      Returns:
      The number of connections closed by this connection pool.

    <!-- -->

    - #### getAverageConnectionWaitTime

          long getAverageConnectionWaitTime()

      Gets the average time (in milliseconds) a user thread has to wait before it could obtain a connection from the connection pool.
      Returns:
      The average time (in milliseconds) a user thread has to wait before it could obtain a connection from the connection pool.

    <!-- -->

    - #### getPeakConnectionWaitTime

          long getPeakConnectionWaitTime()

      Gets the longest wait (in milliseconds) a user request has to incur before obtaining a connection from the connection pool. This includes threads that waited unsuccessfully for a connection.
      Returns:
      The longest wait (in milliseconds) a user request has to incur before obtaining a connection from the connection pool.

    <!-- -->

    - #### getAbandonedConnectionsCount

          int getAbandonedConnectionsCount()

      Gets the number of abandoned connections that have been reclaimed.
      Returns:
      The number of abandoned connections that have been reclaimed.

    <!-- -->

    - #### getPendingRequestsCount

          int getPendingRequestsCount()

      Gets the number of clients that are currently waiting to obtain a connection from the pool.
      Returns:
      The number of clients that are currently waiting to obtain a connection from the pool.

    <!-- -->

    - #### getCumulativeConnectionWaitTime

          long getCumulativeConnectionWaitTime()

      Gets the cumulative time (in milliseconds) that connection requests have waited for connections over the life of the connection pool. This includes the time connections waited successfully and obtained a connection from the pool and those that failed waiting for a connection.
      Returns:
      The cumulative time (in milliseconds) that connection requests have waited for connections over the life of the connection pool.

    <!-- -->

    - #### getCumulativeConnectionBorrowedCount

          long getCumulativeConnectionBorrowedCount()

      Gets the number of connections borrowed from the connection pool over the life of the pool. This count is incremented each time a connection is borrowed.
      Returns:
      The number of connections borrowed from the connection pool over the life of the pool.

    <!-- -->

    - #### getCumulativeConnectionUseTime

          long getCumulativeConnectionUseTime()

      Gets the cumulative time (in milliseconds) of connections that were borrowed from the pool and remained in use.
      Returns:
      The cumulative time (in milliseconds) of connections that were borrowed from the pool and remained in use.

    <!-- -->

    - #### getCumulativeConnectionReturnedCount

          long getCumulativeConnectionReturnedCount()

      Gets the number of connections returned to the connection pool over the life of the pool.
      Returns:
      The number of connections returned to the connection pool over the life of the pool.

    <!-- -->

    - #### getCumulativeSuccessfulConnectionWaitTime

          long getCumulativeSuccessfulConnectionWaitTime()

      Gets the cumulative time (in milliseconds) that connection requests waited successfully and borrowed a connection from the pool.
      Returns:
      The cumulative time (in milliseconds) that connection requests waited successfully and borrowed a connection from the pool.

    <!-- -->

    - #### getCumulativeSuccessfulConnectionWaitCount

          long getCumulativeSuccessfulConnectionWaitCount()

      Gets the number of connection requests that waited successfully and borrowed a connection from the pool.
      Returns:
      The number of connection requests that waited successfully and borrowed a connection from the pool.

    <!-- -->

    - #### getCumulativeFailedConnectionWaitTime

          long getCumulativeFailedConnectionWaitTime()

      Gets the cumulative time (in milliseconds) that connection requests waited but failed to borrow a connection from the pool.
      Returns:
      The cumulative time (in milliseconds) that connection requests waited but failed to borrow a connection from the pool.

    <!-- -->

    - #### getCumulativeFailedConnectionWaitCount

          long getCumulativeFailedConnectionWaitCount()

      Gets the number of connection requests that waited unsuccessfully to borrow a connection from the pool.
      Returns:
      The number of connection requests that waited unsuccessfully to borrow a connection from the pool.

    <!-- -->

    - #### getSuccessfulAffinityBasedBorrowCount

          long getSuccessfulAffinityBasedBorrowCount()

      Gets the number of borrow requests succeeded with matching affinity contexts.
      Returns:
      The number of borrow requests succeeded with matching affinity contexts.

    <!-- -->

    - #### getFailedAffinityBasedBorrowCount

          long getFailedAffinityBasedBorrowCount()

      Gets the number of borrow requests that returned connections not matching the affinity contexts.
      Returns:
      The number of borrow requests that returned connections not matching the affinity contexts.

    <!-- -->

    - #### getSuccessfulRCLBBasedBorrowCount

          long getSuccessfulRCLBBasedBorrowCount()

      Gets the number of borrow requests succeeded using Runtime Connection Load-Balancing (RCLB) algorithms.
      Returns:
      The number of borrow requests succeeded using Runtime Connection Load-Balancing (RCLB) algorithms.

    <!-- -->

    - #### getFailedRCLBBasedBorrowCount

          long getFailedRCLBBasedBorrowCount()

      Gets the number of borrow requests failed using Runtime Connection Load-Balancing (RCLB) algorithms.
      Returns:
      The number of borrow requests failed using Runtime Connection Load-Balancing (RCLB) algorithms.

    <!-- -->

    - #### getFcfProcessingInfo

          java.lang.String getFcfProcessingInfo()

      Gets the information of recent Fast Connection Failover (FCF) attempts, in the form of a String. The information returned is to help diagnosing FCF problems, and includes the outcome of each FCF attempt (successful or failed), the relevant RAC instances, the number of connections cleaned up, the exception that triggered the FCF attempt failure, etc.
      Returns:
      The information string for recent FCF attempts.

    <!-- -->

    - #### getFcfProcessingInfoProcessedOnly

          java.lang.String getFcfProcessingInfoProcessedOnly()

    <!-- -->

    - #### getConnectionRepurposeCount

          long getConnectionRepurposeCount()

      Returns the number of connection repurposed in a shared pool for a mutitenant database, where connections can be reused across PDB's by switching their container and PDB service.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPoolMBean.md)
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-files/index-1.md)
- [Help](../../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolManagerMBean.md)
- Next Class

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
