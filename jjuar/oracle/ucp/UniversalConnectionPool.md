Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPool.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](TimeToLiveConnectionTimeoutCallback.md)
- [Next Class](UniversalConnectionPoolAdapter.md)

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

## Interface UniversalConnectionPool

-

  ------------------------------------------------------------------------



      public interface UniversalConnectionPool

  A connection pool that pools any type of connection (called a physical connection).
  There are several key objects that make up the connection pool:

  - The physical pool itself
  - The connection factory adapter
  - The pooled connection
  - The connection retrieval info object

  *Physical Pool* The physical pool maintains pooled connections that can be borrowed from the pool, returned to the pool, or closed and not returned to the pool. The pool keeps track of the connections that are available (so that they can be borrowed) and connections that are in use (so they can be reaped if it is determined that they are no longer valid).

  *Connection Factory Adapter* The connection pool must rely on another entity to create and close connections because connection pools can pool any type of connection. This is the responsibility of the connection factory adapter. A connection factory adapter is tied to a specific resource (JDBC, JCA, LDAP, and so forth). When the connection pool needs to create a new connection, it asks the connection factory adapter to do so. The returned connection is placed inside a `UniversalPooledConnection` object that is then placed into the connection pool. When the connection pool closes a connection, it hands the connection to the connection factory adapter which then closes the connection.

  *Pooled Connections* Each pooled connection in the connection pool is an instance of `UniversalPooledConnection`. The pooled connection decorates a physical connection (created by the connection factory adapter) which can be borrowed.

  *Connection Retrieval Info* The connection retrieval info object is used by the connection factory adapter to create connections. It contains resource-specific information that the connection factory adapter uses to create connections. For example, the JDBC connection retrieval info object maintains the user and password that are used to create a connection from a JDBC resource. The JCA connection retrieval info object maintains the `Subject` and JCA `ConnectionRequestInfo object`.

  *Pool Properties* The pool provides some properties for users to customize the pool's behavior, such as:

  - *minPoolSize* The minimum number of connections that the pool maintains.
  - *maxPoolSize* The maximum number of connections that the pool maintains.
  - *initialPoolSize* The initial number of connections in the pool.

  *Statistics* The pool maintains some statistics such as:

  - The number of connections that are in use (borrowed) at any given time.
  - The number of connections that are available (not in use) at any given time.
  - The number of physical connections created by the resource.
  - The number of physical connections closed by the resource.

  *Lifecycle* A connection pool has a lifecycle. See `UniversalConnectionPoolLifeCycleState` for details. A connection pool is started by calling the `start()` method and stopped by calling the `stop()` method. Connections may not be borrowed until the connection pool has been started or after the pool has been stopped (unless the pool has been started again).

  See Also:
  [`UniversalPooledConnection`](UniversalPooledConnection.md), [`ConnectionFactoryAdapter`](ConnectionFactoryAdapter.md), [`ConnectionRetrievalInfo`](ConnectionRetrievalInfo.md), [`UniversalConnectionPoolStatistics`](UniversalConnectionPoolStatistics.md), [`UniversalConnectionPoolLifeCycleState`](UniversalConnectionPoolLifeCycleState.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                   | Method and Description                                                                                                                                                                                                                             |
    |-------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`UniversalPooledConnection`](UniversalPooledConnection.md)                         | `borrowConnection``(`[`ConnectionRetrievalInfo`](ConnectionRetrievalInfo.md)` connectionRetrievalInfo)`<br>Gets a connection from the connection pool.                                                                                             |
    | `void`                                                                              | `closeConnection``(`[`UniversalPooledConnection`](UniversalPooledConnection.md)` pooledConnection)`<br>Closes the pooled connection.                                                                                                               |
    | `int`                                                                               | `getAbandonedConnectionTimeout``()`<br>Gets the abandoned connection timeout value.                                                                                                                                                                |
    | `int`                                                                               | `getAvailableConnectionsCount``()`<br>Gets the number of connections that are available in the connection pool (that is, connections in the pool that are not currently in use by clients).                                                        |
    | `int`                                                                               | `getBorrowedConnectionsCount``()`<br>Gets the number of connections that are actively in use by clients.                                                                                                                                           |
    | `int`                                                                               | `getConnectionHarvestMaxCount``()`<br>Gets the maximum number of connections that may be harvested when the connection harvesting occurs.                                                                                                          |
    | `int`                                                                               | `getConnectionHarvestTriggerCount``()`<br>Gets the number of available connections below which the connection pool's connection harvesting occurs.                                                                                                 |
    | `int`                                                                               | `getConnectionLabelingHighCost``()`<br>Obtains the cost value which identifies a connection as "high-cost" for connection labeling.                                                                                                                |
    | `int`                                                                               | `getConnectionRepurposeThreshold``()`<br>Gets the connection repurpose threshold for the pool.                                                                                                                                                     |
    | [`ConnectionRetrievalInfo`](ConnectionRetrievalInfo.md)                             | `getConnectionRetrievalInfo``()`<br>Gets the `ConnectionRetrievalInfo` object which contains user and password information to create the connections.                                                                                              |
    | `int`                                                                               | `getConnectionValidationTimeout``()`<br>Connection validation timeout getter This property changes the allowed time for a connection valiadation.                                                                                                  |
    | `int`                                                                               | `getConnectionWaitTimeout``()`<br>Gets the amount of time to wait (in seconds) for a used connection to be released by a client.                                                                                                                   |
    | `int`                                                                               | `getHighCostConnectionReuseThreshold``()`<br>Obtains the high-cost connection reuse threshold property value for connection labeling.                                                                                                              |
    | `int`                                                                               | `getInactiveConnectionTimeout``()`<br>Gets the inactive connection timeout value.                                                                                                                                                                  |
    | `int`                                                                               | `getInitialPoolSize``()`<br>Gets the initial pool size.                                                                                                                                                                                            |
    | [`UniversalConnectionPoolLifeCycleState`](UniversalConnectionPoolLifeCycleState.md) | `getLifeCycleState``()`<br>Gets the life cycle state of the connection pool.                                                                                                                                                                       |
    | `int`                                                                               | `getLoginTimeout``()`<br>Gets the default maximum time in seconds that a driver will wait while attempting to connect to a database once the driver has been identified.                                                                           |
    | `int`                                                                               | `getMaxConnectionReuseCount``()`<br>Gets the maximum connection reuse count property value.                                                                                                                                                        |
    | `long`                                                                              | `getMaxConnectionReuseTime``()`<br>Gets the maximum connection reuse time property value.                                                                                                                                                          |
    | `int`                                                                               | `getMaxConnectionsPerService``()`<br>Gets the maximum number of connections that can be obtained to a particular service, in a shared pool.                                                                                                        |
    | `int`                                                                               | `getMaxPoolSize``()`<br>Gets the maximum number of connections that the connection pool maintains.                                                                                                                                                 |
    | `int`                                                                               | `getMinPoolSize``()`<br>Gets the minimum number of connections that the connection pool maintains.                                                                                                                                                 |
    | `java.lang.String`                                                                  | `getName``()`<br>Gets the name of the connection pool.                                                                                                                                                                                             |
    | `int`                                                                               | `getSecondsToTrustIdleConnection``()`<br>Gets the seconds To Trust Idle Connection value which determines whether or not connection validation on borrow should be skipped See property description in `setSecondsToTrustIdleConnection()`.        |
    | `boolean`                                                                           | `getShardingMode``()`<br>Returns the mode of UCP when UCP is using a Sharded Database.                                                                                                                                                             |
    | [`UniversalConnectionPoolStatistics`](UniversalConnectionPoolStatistics.md)         | `getStatistics``()`<br>Gets the statistics of the connection pool.                                                                                                                                                                                 |
    | `int`                                                                               | `getTimeoutCheckInterval``()`<br>Gets the frequency (in seconds) to enforce the timeout properties.                                                                                                                                                |
    | `int`                                                                               | `getTimeToLiveConnectionTimeout``()`<br>Gets the maximum time (in seconds) a connection may remain in-use.                                                                                                                                         |
    | `boolean`                                                                           | `getValidateConnectionOnBorrow``()`<br>Returns whether or not a connection being borrowed should first be validated.                                                                                                                               |
    | `boolean`                                                                           | `isShareable``()`<br>Returns whether the pool is shareable or not.                                                                                                                                                                                 |
    | `void`                                                                              | `purge``()`<br>Removes all connections from the connection pool.                                                                                                                                                                                   |
    | `void`                                                                              | `reconfigure``(java.util.Properties props)`<br>Allows a connection pool to be reconfigured gracefully with a different set of properties that specify the behavior of the connection pool at runtime.                                              |
    | `void`                                                                              | `recycle``()`<br>Allows only invalid available connections in the pool to be replaced with new/fresh connections.                                                                                                                                  |
    | `void`                                                                              | `refresh``()`<br>Allows connections in the pool, both borrowed and available ones, to be replaced with new/fresh connections.                                                                                                                      |
    | `void`                                                                              | `registerConnectionAffinityCallback``(`[`ConnectionAffinityCallback`](ConnectionAffinityCallback.md)` cbk)`<br>Registers a `ConnectionAffinityCallback` objet on the connection pool.                                                              |
    | `void`                                                                              | `registerConnectionLabelingCallback``(`[`ConnectionLabelingCallback`](ConnectionLabelingCallback.md)` cbk)`<br>Registers a `ConnectionLabelingCallback` object with this connection pool.                                                          |
    | `void`                                                                              | `removeConnectionAffinityCallback``()`<br>Removes the `ConnectionAffinityCallback` object registered on the connection pool.                                                                                                                       |
    | `void`                                                                              | `removeConnectionLabelingCallback``()`<br>Removes the `ConnectionLabelingCallback` object registered with this connection pool, if any.                                                                                                            |
    | `void`                                                                              | `returnConnection``(`[`UniversalPooledConnection`](UniversalPooledConnection.md)` pooledConnection)`<br>Returns a connection back into the connection pool.                                                                                        |
    | `void`                                                                              | `setAbandonedConnectionTimeout``(int abandonedConnectionTimeout)`<br>Sets the abandoned connection timeout.                                                                                                                                        |
    | `void`                                                                              | `setConnectionHarvestMaxCount``(int connectionHarvestMaxCount)`<br>Sets the maximum number of connections that may be harvested when the connection harvesting occurs.                                                                             |
    | `void`                                                                              | `setConnectionHarvestTriggerCount``(int connectionHarvestTriggerCount)`<br>Sets the number of available connections below which the connection pool's connection harvesting occurs.                                                                |
    | `void`                                                                              | `setConnectionLabelingHighCost``(int highCost)`<br>Sets the cost value which identifies a connection as "high-cost" for connection labeling.                                                                                                       |
    | `void`                                                                              | `setConnectionRepurposeThreshold``(java.lang.Integer threshold)`<br>Sets the connection repurpose threshold for the pool.                                                                                                                          |
    | `void`                                                                              | `setConnectionRetrievalInfo``(`[`ConnectionRetrievalInfo`](ConnectionRetrievalInfo.md)` cri)`<br>Sets the `ConnectionRetrievalInfo` for creating the initial connections (physical connections) in the pool based on the initialPoolSize property. |
    | `void`                                                                              | `setConnectionValidationTimeout``(int connectionValidationTimeout)`<br>Connection validation timeout setter This property changes the allowed time for a connection valiadation.                                                                   |
    | `void`                                                                              | `setConnectionWaitTimeout``(int waitTimeout)`<br>Sets the amount of time to wait (in seconds) for a used connection to be released by a client.                                                                                                    |
    | `void`                                                                              | `setHighCostConnectionReuseThreshold``(int threshold)`<br>Sets the high-cost connection reuse threshold for connection labeling.                                                                                                                   |
    | `void`                                                                              | `setInactiveConnectionTimeout``(int inactiveConnectionTimeout)`<br>Sets the inactive connection timeout.                                                                                                                                           |
    | `void`                                                                              | `setInitialPoolSize``(int initialPoolSize)`<br>Sets the initial pool size.                                                                                                                                                                         |
    | `void`                                                                              | `setLoginTimeout``(int seconds)`<br>Sets the default maximum time in seconds that a driver will wait while attempting to connect to a database once the driver has been identified.                                                                |
    | `void`                                                                              | `setMaxConnectionReuseCount``(int maxConnectionReuseCount)`<br>Sets the maximum connection reuse count property.                                                                                                                                   |
    | `void`                                                                              | `setMaxConnectionReuseTime``(long maxConnectionReuseTime)`<br>Sets the maximum connection reuse time property.                                                                                                                                     |
    | `void`                                                                              | `setMaxConnectionsPerService``(int maxConnectionsPerService)`<br>Sets the maximum number of connections that can be obtained to a particular service, in a shared pool.                                                                            |
    | `void`                                                                              | `setMaxPoolSize``(int maxPoolSize)`<br>Sets the maximum number of connections.                                                                                                                                                                     |
    | `void`                                                                              | `setMinPoolSize``(int minPoolSize)`<br>Sets the minimum number of connections.                                                                                                                                                                     |
    | `void`                                                                              | `setName``(java.lang.String name)`<br>Sets the name of the connection pool.                                                                                                                                                                        |
    | `void`                                                                              | `setSecondsToTrustIdleConnection``(int secondsToTrustIdleConnection)`<br>Sets the time in seconds to trust an idle connection to skip a validation test.                                                                                           |
    | `void`                                                                              | `setShardingMode``(boolean shardingMode)`<br>This API changes the mode of UCP when UCP is using a Sharded Database.                                                                                                                                |
    | `void`                                                                              | `setTimeoutCheckInterval``(int timeoutCheckInterval)`<br>Sets the frequency (in seconds) to enforce the timeout properties.                                                                                                                        |
    | `void`                                                                              | `setTimeToLiveConnectionTimeout``(int timeToLiveConnectionTimeout)`<br>Sets the maximum time (in seconds) a connection may remain in-use.                                                                                                          |
    | `void`                                                                              | `setValidateConnectionOnBorrow``(boolean validateConnectionOnBorrow)`<br>Sets whether or not a connection being borrowed should first be validated.                                                                                                |
    | `void`                                                                              | `start``()`<br>Starts the connection pool.                                                                                                                                                                                                         |
    | `void`                                                                              | `stop``()`<br>Stops the connection pool.                                                                                                                                                                                                           |

<!-- -->

- - ### Method Detail

    - #### borrowConnection

          UniversalPooledConnection borrowConnection(ConnectionRetrievalInfo connectionRetrievalInfo)
                                              throws UniversalConnectionPoolException

      Gets a connection from the connection pool.
      Parameters:
      `connectionRetrievalInfo` - Info to use to get the connection.

      Returns:
      A UniversalPooledConnection for the specified connection retrieval info.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - if an error occurs getting a connection.

      [`NoAvailableConnectionsException`](NoAvailableConnectionsException.md) - if all of the connections are in use.

    <!-- -->

    - #### returnConnection

          void returnConnection(UniversalPooledConnection pooledConnection)
                         throws UniversalConnectionPoolException

      Returns a connection back into the connection pool. The pool can decide to close the underlying physical connection when necessary.
      Parameters:
      `pooledConnection` - The connection to return back into the pool.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### closeConnection

          void closeConnection(UniversalPooledConnection pooledConnection)
                        throws UniversalConnectionPoolException

      Closes the pooled connection. Do not put it back into the pool.
      Parameters:
      `pooledConnection` - The pooled connection to close.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - if an error occurs closing the connection.

    <!-- -->

    - #### refresh

          void refresh()
                throws UniversalConnectionPoolException

      Allows connections in the pool, both borrowed and available ones, to be replaced with new/fresh connections. All of the available connections are removed before replacing them with new connections. However, a borrowed connection is marked for removal. When such a borrowed connection is returned to the pool, it is closed and replaced with a new connection with the same user credentials.
      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### recycle

          void recycle()
                throws UniversalConnectionPoolException

      Allows only invalid available connections in the pool to be replaced with new/fresh connections.
      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### purge

          void purge()
              throws UniversalConnectionPoolException

      Removes all connections from the connection pool. The primary difference in behavior between this and `refresh()` is that the connection pool is left empty with no connections available after calling `purge()`. Some of the connection pool properties such as `minPoolSize` or `initialPoolSize` may not be honored when purging connections from the pool.
      Note that both borrowed and available connections are removed when this API is called. Any borrowed connections incur an exception after this API is called. The user is expected to retry and obtain a new connection from the pool.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### reconfigure

          void reconfigure(java.util.Properties props)
                    throws UniversalConnectionPoolException

      Allows a connection pool to be reconfigured gracefully with a different set of properties that specify the behavior of the connection pool at runtime. Reconfiguration of connection pool properties is always non-disruptive. If this operation cannot be completed right away, then the call returns and the enforcement of the properties continue to occur asynchronously.
      Parameters:
      `props` - Containing new set of pool properties for reconfiguration.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### start

          void start()
              throws UniversalConnectionPoolException

      Starts the connection pool.
      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If an error occurs during start.

    <!-- -->

    - #### stop

          void stop()
             throws UniversalConnectionPoolException

      Stops the connection pool.
      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getName

          java.lang.String getName()

      Gets the name of the connection pool.
      Returns:
      The name of the connection pool.

    <!-- -->

    - #### setName

          void setName(java.lang.String name)

      Sets the name of the connection pool.
      Parameters:
      `name` - The name of the connection pool.

    <!-- -->

    - #### getInitialPoolSize

          int getInitialPoolSize()

      Gets the initial pool size.
      Returns:
      the initial pool size.

    <!-- -->

    - #### setInitialPoolSize

          void setInitialPoolSize(int initialPoolSize)
                           throws UniversalConnectionPoolException

      Sets the initial pool size. This is the number of connections that are created and placed in the pool upon initialization.
      Parameters:
      `initialPoolSize` - the initial pool size.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getMinPoolSize

          int getMinPoolSize()

      Gets the minimum number of connections that the connection pool maintains.
      Returns:
      The minimum number of connections.

    <!-- -->

    - #### setMinPoolSize

          void setMinPoolSize(int minPoolSize)
                       throws UniversalConnectionPoolException

      Sets the minimum number of connections. If the number of available connections + the number of connections in use \< the minimum, then the connection is returned to the pool. Otherwise, the connection is closed.
      Parameters:
      `minPoolSize` - The minimum number of connections.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getMaxPoolSize

          int getMaxPoolSize()

      Gets the maximum number of connections that the connection pool maintains.
      Returns:
      The maximum number of connections.

    <!-- -->

    - #### setMaxPoolSize

          void setMaxPoolSize(int maxPoolSize)
                       throws UniversalConnectionPoolException

      Sets the maximum number of connections. The maximum number of connections includes the number of connections that are in use as well as the number of available connections.
      Parameters:
      `maxPoolSize` - The maximum number of connections.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getInactiveConnectionTimeout

          int getInactiveConnectionTimeout()

      Gets the inactive connection timeout value.
      Returns:
      The inactive connection timeout.

    <!-- -->

    - #### setInactiveConnectionTimeout

          void setInactiveConnectionTimeout(int inactiveConnectionTimeout)
                                     throws UniversalConnectionPoolException

      Sets the inactive connection timeout. This timeout determines how long an available connection remains in the connection pool before it is removed from the pool.
      Parameters:
      `inactiveConnectionTimeout` - The inactive connection timeout (in seconds).

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getAbandonedConnectionTimeout

          int getAbandonedConnectionTimeout()

      Gets the abandoned connection timeout value.
      Returns:
      The abandoned connection timeout.

    <!-- -->

    - #### setAbandonedConnectionTimeout

          void setAbandonedConnectionTimeout(int abandonedConnectionTimeout)
                                      throws UniversalConnectionPoolException

      Sets the abandoned connection timeout. This timeout determines how long a borrowed connection can remain unused before it is considered abandoned and reclaimed by the connection pool.
      Parameters:
      `abandonedConnectionTimeout` - The value of how long a connection has not been used before it is abandoned (in seconds).

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getConnectionWaitTimeout

          int getConnectionWaitTimeout()

      Gets the amount of time to wait (in seconds) for a used connection to be released by a client. This only applies when the maximum number of connections has been borrowed from the connection pool. When a client tries to borrow a connection from the pool and all connections are in use, the connection pool waits for a connection to be released back to the pool.
      Returns:
      The connection wait timeout.

    <!-- -->

    - #### setConnectionWaitTimeout

          void setConnectionWaitTimeout(int waitTimeout)
                                 throws UniversalConnectionPoolException

      Sets the amount of time to wait (in seconds) for a used connection to be released by a client.
      Parameters:
      `waitTimeout` - The amount of time to wait.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getTimeToLiveConnectionTimeout

          int getTimeToLiveConnectionTimeout()

      Gets the maximum time (in seconds) a connection may remain in-use. The used connection is unconditionally returned to the connection pool when this timeout expires. A value of 0 means that the feature is not enabled.
      Returns:
      The maximum time (in seconds) a used connection may be active.

    <!-- -->

    - #### setTimeToLiveConnectionTimeout

          void setTimeToLiveConnectionTimeout(int timeToLiveConnectionTimeout)
                                       throws UniversalConnectionPoolException

      Sets the maximum time (in seconds) a connection may remain in-use.
      Parameters:
      `timeToLiveConnectionTimeout` - The maximum time (in seconds) a used connection may be active.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getTimeoutCheckInterval

          int getTimeoutCheckInterval()

      Gets the frequency (in seconds) to enforce the timeout properties. It applies to all of the connection pool timeouts including `abandonedConnectionTimeout`, `inactiveConnectionTimeout`, and `timeToLiveConnectionTimeout`.
      Returns:
      The frequency (in seconds) to enforce the timeout properties.

    <!-- -->

    - #### setTimeoutCheckInterval

          void setTimeoutCheckInterval(int timeoutCheckInterval)
                                throws UniversalConnectionPoolException

      Sets the frequency (in seconds) to enforce the timeout properties.
      Parameters:
      `timeoutCheckInterval` - The frequency (in seconds) to enforce the timeout properties.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getValidateConnectionOnBorrow

          boolean getValidateConnectionOnBorrow()

      Returns whether or not a connection being borrowed should first be validated. When this property is set to `true`, connection validity is performed before returning the connection to the user.
      Returns:
      Whether or not a connection being borrowed should first be validated.

    <!-- -->

    - #### setValidateConnectionOnBorrow

          void setValidateConnectionOnBorrow(boolean validateConnectionOnBorrow)

      Sets whether or not a connection being borrowed should first be validated.
      Parameters:
      `validateConnectionOnBorrow` - Whether or not a connection being borrowed should first be validated.

    <!-- -->

    - #### getConnectionHarvestTriggerCount

          int getConnectionHarvestTriggerCount()

      Gets the number of available connections below which the connection pool's connection harvesting occurs. For example, if the value is set to 10, then connection harvesting occurs when the number of available connections drops to 10.
      Returns:
      The number of available connections below which the connection pool's connection harvesting occurs.

    <!-- -->

    - #### setConnectionHarvestTriggerCount

          void setConnectionHarvestTriggerCount(int connectionHarvestTriggerCount)
                                         throws UniversalConnectionPoolException

      Sets the number of available connections below which the connection pool's connection harvesting occurs.
      Parameters:
      `connectionHarvestTriggerCount` - The number of available connections below which the connection pool's connection harvesting occurs.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getConnectionHarvestMaxCount

          int getConnectionHarvestMaxCount()

      Gets the maximum number of connections that may be harvested when the connection harvesting occurs. Note that it is possible that the number of connections that are harvested may be anywhere from 0 to the `connectionHarvestMaxCount`.
      Returns:
      The maximum number of connections that may be harvested when the connection harvesting occurs.

    <!-- -->

    - #### setConnectionHarvestMaxCount

          void setConnectionHarvestMaxCount(int connectionHarvestMaxCount)
                                     throws UniversalConnectionPoolException

      Sets the maximum number of connections that may be harvested when the connection harvesting occurs.
      Parameters:
      `connectionHarvestMaxCount` - the maximum number of connections that may be harvested when the connection harvesting occurs.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getAvailableConnectionsCount

          int getAvailableConnectionsCount()

      Gets the number of connections that are available in the connection pool (that is, connections in the pool that are not currently in use by clients).
      Returns:
      The number of connections that are available in the connection pool.

    <!-- -->

    - #### getBorrowedConnectionsCount

          int getBorrowedConnectionsCount()

      Gets the number of connections that are actively in use by clients.
      Returns:
      The number of connections that are actively in use by clients.

    <!-- -->

    - #### getStatistics

          UniversalConnectionPoolStatistics getStatistics()

      Gets the statistics of the connection pool.
      Returns:
      The statistics of the connection pool.

    <!-- -->

    - #### getLifeCycleState

          UniversalConnectionPoolLifeCycleState getLifeCycleState()

      Gets the life cycle state of the connection pool.
      Returns:
      The life cycle state of the connection pool.

    <!-- -->

    - #### getConnectionRetrievalInfo

          ConnectionRetrievalInfo getConnectionRetrievalInfo()

      Gets the `ConnectionRetrievalInfo` object which contains user and password information to create the connections.
      Returns:
      `ConnectionRetrievalInfo` object which contains user and password information to create the connections.

    <!-- -->

    - #### setConnectionRetrievalInfo

          void setConnectionRetrievalInfo(ConnectionRetrievalInfo cri)

      Sets the `ConnectionRetrievalInfo` for creating the initial connections (physical connections) in the pool based on the initialPoolSize property.
      Parameters:
      `cri` - The `ConnectionRetrievalInfo` with user and password for creating the initial connections in the pool.

    <!-- -->

    - #### registerConnectionAffinityCallback

          void registerConnectionAffinityCallback(ConnectionAffinityCallback cbk)
                                           throws UniversalConnectionPoolException

      Registers a `ConnectionAffinityCallback` objet on the connection pool.
      Parameters:
      `cbk` - The affinity callback object to be registered

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If callback registration fails.

    <!-- -->

    - #### removeConnectionAffinityCallback

          void removeConnectionAffinityCallback()
                                         throws UniversalConnectionPoolException

      Removes the `ConnectionAffinityCallback` object registered on the connection pool.
      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If callback removal fails.

    <!-- -->

    - #### registerConnectionLabelingCallback

          void registerConnectionLabelingCallback(ConnectionLabelingCallback cbk)
                                           throws UniversalConnectionPoolException

      Registers a `ConnectionLabelingCallback` object with this connection pool.
      Parameters:
      `cbk` - The `ConnectionLabelingCallback` object to be registered.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If there is a callback already registered with this pool.

    <!-- -->

    - #### removeConnectionLabelingCallback

          void removeConnectionLabelingCallback()
                                         throws UniversalConnectionPoolException

      Removes the `ConnectionLabelingCallback` object registered with this connection pool, if any.
      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If callback removal fails.

    <!-- -->

    - #### getMaxConnectionReuseTime

          long getMaxConnectionReuseTime()

      Gets the maximum connection reuse time property value. See property description in `setMaxConnectionReuseTime()`.
      Returns:
      Maximum connection reuse time (in seconds)

    <!-- -->

    - #### setMaxConnectionReuseTime

          void setMaxConnectionReuseTime(long maxConnectionReuseTime)
                                  throws UniversalConnectionPoolException

      Sets the maximum connection reuse time property. This property specifies the maximum time any connection can potentially be reused after which the pool removes and closes a connection. The value is specified in seconds and must be greater than 0. For example, if the specified value is 3600 seconds, then when a connection is in existence for more than 3600 seconds, the connection is closed and removed from the pool. Connections are closed gracefully after they are returned to the pool and the specified property value has been exceeded. Default is 0, which means this feature is not enabled.
      Parameters:
      `maxConnectionReuseTime` - Maximum connection reuse time (in seconds).

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getMaxConnectionReuseCount

          int getMaxConnectionReuseCount()

      Gets the maximum connection reuse count property value. See property description in `setMaxConnectionReuseCount()`.
      Returns:
      Maximum connection reuse count.

    <!-- -->

    - #### setMaxConnectionReuseCount

          void setMaxConnectionReuseCount(int maxConnectionReuseCount)
                                   throws UniversalConnectionPoolException

      Sets the maximum connection reuse count property. This property specifies the maximum number of times any connection can be reused after which the pool removes and closes a connection. The value must be greater than 0 for this feature to be enabled. For example, if the specified value is 100, then when a connection is reused or borrowed 100 times from the pool, it is closed and removed from the pool. Connections are closed gracefully after they are returned to the pool and the property value has been exceeded. Default is 0, which means this feature is not enabled.
      Parameters:
      `maxConnectionReuseCount` - Maximum connection reuse count.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getSecondsToTrustIdleConnection

          int getSecondsToTrustIdleConnection()

      Gets the seconds To Trust Idle Connection value which determines whether or not connection validation on borrow should be skipped See property description in `setSecondsToTrustIdleConnection()`.
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
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md)

    <!-- -->

    - #### getConnectionLabelingHighCost

          int getConnectionLabelingHighCost()

      Obtains the cost value which identifies a connection as "high-cost" for connection labeling.
      Returns:
      The cost value that identifies a connection as "high-cost" for connection labeling.

      See Also:
      `setConnectionLabelingHighCost`

    <!-- -->

    - #### setConnectionLabelingHighCost

          void setConnectionLabelingHighCost(int highCost)
                                      throws UniversalConnectionPoolException

      Sets the cost value which identifies a connection as "high-cost" for connection labeling. Connection labeling uses the `cost(Properties, Properties)` method in ConnectionLabelingCallback to find a connection in the pool for a request. When this property is set, connections with a cost value equal to or greater than the property value are considered "high-cost" connections. The default value is Integer.MAX_VALUE.
      Parameters:
      `highCost` - The cost value that identifies a connection as "high-cost" for connection labeling.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If an exception occurs while setting the cost.

    <!-- -->

    - #### getHighCostConnectionReuseThreshold

          int getHighCostConnectionReuseThreshold()

      Obtains the high-cost connection reuse threshold property value for connection labeling.
      Returns:
      The high-cost connection reuse threshold property value currently set.

      See Also:
      `setConnectionLabelingHighCost`, `setHighCostConnectionReuseThreshold`

    <!-- -->

    - #### setHighCostConnectionReuseThreshold

          void setHighCostConnectionReuseThreshold(int threshold)
                                            throws UniversalConnectionPoolException

      Sets the high-cost connection reuse threshold for connection labeling. This property works together with the ConnectionLabelingHighCost property to determine when high-cost connections are reused for connection labeling. This property specifies a threshold of the number of total connections in the pool. If Connection Labeling finds all available connections are high-cost connections (i.e., the lowest cost value exceeds the ConnectionLabelingHighCost value), it checks this threshold to determine whether to reuse those connections. Only when this threshold is reached, Connection Labeling will try to reuse the high-cost connections in the pool to serve a labeled connection request. Otherwise, Connection Labeling picks a low-cost connection, a no-label connection available in the pool, or creates a brand-new physical connection to serve a labeled request. For example, if the property value is set to 10, Connection Labeling reuses high-cost connections when there are no low-cost connections available and the total connections reach 10. Note that any labeled connection with cost Integer.MAX_VALUE will not be reused. This is consistent with connection labeling behavior when this property and ConnectionLabelingHighCost are not set. A Connection Labeling callback must be registered at the same time for this property to take effect. The default value is 0, which is treated the same way as MinPoolSize.
      Parameters:
      `threshold` - The high-cost connection reuse threshold to set.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If any exception occurs while setting the threshold.

    <!-- -->

    - #### getMaxConnectionsPerService

          int getMaxConnectionsPerService()

      Gets the maximum number of connections that can be obtained to a particular service, in a shared pool.
      Returns:
      The maximum number of connections that can be obtained to a particular service.

    <!-- -->

    - #### setMaxConnectionsPerService

          void setMaxConnectionsPerService(int maxConnectionsPerService)
                                    throws UniversalConnectionPoolException

      Sets the maximum number of connections that can be obtained to a particular service, in a shared pool. An exception is thrown when setting a different maxConnectionsPerService value on a running pool instance.
      Parameters:
      `maxConnectionsPerService` - The maximum number of connections that can be obtained to a particular service.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If any exception occurs while setting the maxConnectionsPerService value.

    <!-- -->

    - #### getConnectionRepurposeThreshold

          int getConnectionRepurposeThreshold()

      Gets the connection repurpose threshold for the pool. This property is used in cases when the connection pool is shared by multiple datasources connecting to the same database but using different services.Only when this threshold is reached the pool will try to repurpose connections between different services before trying to create new connections. This property is applicable only for multi-tenant databases.
      Returns:
      connection repurpose threshold property value currently set.

    <!-- -->

    - #### setConnectionRepurposeThreshold

          void setConnectionRepurposeThreshold(java.lang.Integer threshold)
                                        throws UniversalConnectionPoolException

      Sets the connection repurpose threshold for the pool. This property is applicable only for multi-tenant databases.
      Parameters:
      `threshold` - connection repurpose threshold to set.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If any exception occurs while setting the threshold.

      See Also:
      `getConnectionRepurposeThreshold`

    <!-- -->

    - #### getLoginTimeout

          int getLoginTimeout()

      Gets the default maximum time in seconds that a driver will wait while attempting to connect to a database once the driver has been identified.
      Returns:
      timeout in seconds

    <!-- -->

    - #### setLoginTimeout

          void setLoginTimeout(int seconds)
                        throws UniversalConnectionPoolException

      Sets the default maximum time in seconds that a driver will wait while attempting to connect to a database once the driver has been identified.
      Parameters:
      `seconds` - timeout

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - in case of negative value

    <!-- -->

    - #### isShareable

          boolean isShareable()

      Returns whether the pool is shareable or not.
      Returns:
      Whether or not pool is shareable.

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

      Connection validation timeout setter This property changes the allowed time for a connection valiadation. If a connection validation operation lasts longer than this timeout, it is interrupted and a connection is considered to be invalid.
      Parameters:
      `connectionValidationTimeout` - validation timeout in seconds

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - gets thrown in case of negation timeout submitted

    <!-- -->

    - #### getConnectionValidationTimeout

          int getConnectionValidationTimeout()

      Connection validation timeout getter This property changes the allowed time for a connection valiadation. If a connection validation operation lasts longer than this timeout, it is interrupted and a connection is considered to be invalid.
      Returns:
      connection validation timeout in seconds

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalConnectionPool.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](TimeToLiveConnectionTimeoutCallback.md)
- [Next Class](UniversalConnectionPoolAdapter.md)

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
