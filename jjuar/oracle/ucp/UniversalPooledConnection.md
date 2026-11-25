Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalPooledConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolStatistics.md)
- [Next Class](UniversalPooledConnectionStatus.md)

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

## Interface UniversalPooledConnection

- All Superinterfaces:
  java.lang.AutoCloseable, java.io.Closeable

  ------------------------------------------------------------------------



      public interface UniversalPooledConnection
      extends java.io.Closeable

  The `UniversalPooledConnection` is the actual object that is pooled by the connection pool. A `UniversalPooledConnection` decorates a physical connection that is produced by a resource (JDBC is an example of a resource).
  `UniversalPooledConnection` object's are borrowed from, and returned to, a connection pool. A `UniversalPooledConnection` can also be closed which means that it is not returned to the connection pool and its associated physical connection is closed.

  The `heartbeat()` method is used to update this object so that the abandoned connection processing works properly. It is up to the client of the connection pool to call the `heartbeat()` method appropriately.

  The Connection Labeling mechanism is application-driven. Labels can be applied on, and removed from, a borrowed connection. Each connection label is defined as a key/value pair. Connection labels are used for connection-matching purposes. Any number of connection labels may be applied on a borrowed connection. It is also possible to obtain all the labels currently applied on a borrowed connection, as well as all the unmatched labels within application-requested labels for each connection-borrowing request.

  See Also:
  [`UniversalConnectionPool`](UniversalConnectionPool.md), [`UniversalPooledConnectionStatus`](UniversalPooledConnectionStatus.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                               | Method and Description                                                                                                                                                                                               |
    |---------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                          | `abort``()`<br>TODO document abort connection                                                                                                                                                                        |
    | `void`                                                                          | `applyConnectionLabel``(java.lang.String key, java.lang.String value)`<br>Applies a connection label on a borrowed connection.                                                                                       |
    | `void`                                                                          | `close``()`<br>TODO document close connection                                                                                                                                                                        |
    | [`AbandonedConnectionTimeoutCallback`](AbandonedConnectionTimeoutCallback.md)   | `getAbandonedConnectionTimeoutCallback``()`<br>Obtains the `AbandonedConnectionTimeoutCallback` registered with this connection.                                                                                     |
    | `long`                                                                          | `getAvailableStartTime``()`<br>Gets the timestamp that this pooled connection became available.                                                                                                                      |
    | `long`                                                                          | `getBorrowedStartTime``()`<br>Gets the timestamp that this pooled connection became borrowed.                                                                                                                        |
    | [`ConnectionHarvestingCallback`](ConnectionHarvestingCallback.md)               | `getConnectionHarvestingCallback``()`<br>Obtains the `ConnectionHarvestingCallback` registered with this connection.                                                                                                 |
    | `java.util.Properties`                                                          | `getConnectionLabels``()`<br>Retrieves all the connection labels applied on this connection.                                                                                                                         |
    | [`ConnectionRetrievalInfo`](ConnectionRetrievalInfo.md)                         | `getConnectionRetrievalInfo``()`<br>Gets the connection retrieval info.                                                                                                                                              |
    | `java.util.Properties`                                                          | `getDatabaseConnectionProperties``()`<br>Fetches the connection properties.                                                                                                                                          |
    | `oracle.ucp.common.CoreConnection`                                              | `getDelegator``()`                                                                                                                                                                                                   |
    | `long`                                                                          | `getLastAccessedTime``()`<br>Gets the last time (in milliseconds) that this pooled connection was used by the client.                                                                                                |
    | `long`                                                                          | `getLastConnectionValidationTime``()`<br>Gets the time that this pooled connection was last validated.                                                                                                               |
    | `long`                                                                          | `getLastNetworkAccessTime``()`<br>Gets the time (in milliseconds) when the underlying connection last accessed the network.                                                                                          |
    | `java.lang.Object`                                                              | `getPhysicalConnection``()`<br>Gets the physical connection that this `UniversalPooledConnection` decorates.                                                                                                         |
    | [`UniversalPooledConnectionStatus`](UniversalPooledConnectionStatus.md)         | `getStatus``()`<br>Gets the status of the pooled connection.                                                                                                                                                         |
    | [`TimeToLiveConnectionTimeoutCallback`](TimeToLiveConnectionTimeoutCallback.md) | `getTimeToLiveConnectionTimeoutCallback``()`<br>Obtains the `TimeToLiveConnectionTimeoutCallback` registered with this connection.                                                                                   |
    | `java.util.Properties`                                                          | `getUnmatchedConnectionLabels``(java.util.Properties requestedLabels)`<br>Obtains all the requested labels that did not match the applied labels on this connection when this connection was borrowed from the pool. |
    | `void`                                                                          | `handleTimeout``()`<br>TODO document handle timeouts on connection                                                                                                                                                   |
    | `void`                                                                          | `heartbeat``()`<br>Indicates that the pooled connection is alive and being used.                                                                                                                                     |
    | `boolean`                                                                       | `isAvailable``()`<br>check whether a connection is "available" or not                                                                                                                                                |
    | `boolean`                                                                       | `isConnectionHarvestable``()`<br>Whether this connection is currently harvestable.                                                                                                                                   |
    | `boolean`                                                                       | `isOracle``()`<br>Is this connection an Oracle connection?                                                                                                                                                           |
    | `boolean`                                                                       | `isReusable``()`<br>check whether a connection is "reusable" or not                                                                                                                                                  |
    | `boolean`                                                                       | `isSqlWithQueryTimeoutInProgress``()`<br>Checks whether or not the connection currently performing timed-out SQL operation                                                                                           |
    | `boolean`                                                                       | `isValid``()`<br>Checks whether or not the connection is valid.                                                                                                                                                      |
    | `int`                                                                           | `labelingCost``(java.util.Properties label)`<br>TODO document - costs are now here!                                                                                                                                  |
    | `void`                                                                          | `plugDelegator``(oracle.ucp.common.CoreConnection delegator)`                                                                                                                                                        |
    | `void`                                                                          | `registerAbandonedConnectionTimeoutCallback``(`[`AbandonedConnectionTimeoutCallback`](AbandonedConnectionTimeoutCallback.md)` cbk)`<br>Registers an `AbandonedConnectionTimeoutCallback` with this connection.       |
    | `void`                                                                          | `registerConnectionHarvestingCallback``(`[`ConnectionHarvestingCallback`](ConnectionHarvestingCallback.md)` cbk)`<br>Registers a `ConnectionHarvestingCallback` with this connection.                                |
    | `void`                                                                          | `registerTimeToLiveConnectionTimeoutCallback``(`[`TimeToLiveConnectionTimeoutCallback`](TimeToLiveConnectionTimeoutCallback.md)` cbk)`<br>Registers a `TimeToLiveConnectionTimeoutCallback` with this connection.    |
    | `void`                                                                          | `removeAbandonedConnectionTimeoutCallback``()`<br>Removes the `AbandonedConnectionTimeoutCallback` object registered with this connection, if any.                                                                   |
    | `void`                                                                          | `removeConnectionHarvestingCallback``()`<br>Removes the `ConnectionHarvestingCallback` object registered with this connection, if any.                                                                               |
    | `void`                                                                          | `removeConnectionLabel``(java.lang.String key)`<br>Removes the connection label with the given key from the connection labels applied on this connection.                                                            |
    | `void`                                                                          | `removeTimeToLiveConnectionTimeoutCallback``()`<br>Removes the `TimeToLiveConnectionTimeoutCallback` object registered with this connection, if any.                                                                 |
    | `boolean`                                                                       | `setAvailable``()`<br>mark connection as "available"                                                                                                                                                                 |
    | `void`                                                                          | `setAvailableStartTime``()`<br>Sets the time that this pooled connection became available to be the current system time.                                                                                             |
    | `boolean`                                                                       | `setBorrowed``()`<br>mark connection as "borrowed"                                                                                                                                                                   |
    | `void`                                                                          | `setBorrowedStartTime``()`<br>Sets the time that this pooled connection became borrowed to be the current system time.                                                                                               |
    | `void`                                                                          | `setConnectionHarvestable``(boolean isConnectionHarvestable)`<br>Specifies whether this connection is harvestable.                                                                                                   |
    | `void`                                                                          | `setConnectionRetrievalInfo``(`[`ConnectionRetrievalInfo`](ConnectionRetrievalInfo.md)` cri)`<br>Sets the connection retrieval info on the connection.                                                               |
    | `void`                                                                          | `setLastConnectionValidationTime``(long lastConnectionValidationTime)`<br>Sets or resets the time that this pooled connection was last validated.                                                                    |
    | `void`                                                                          | `setSqlWithQueryTimeoutInProgress``(boolean inProgress)`<br>Marks connection currently performing timed-out SQL operation                                                                                            |
    | `void`                                                                          | `setStatus``(`[`UniversalPooledConnectionStatus`](UniversalPooledConnectionStatus.md)` status)`<br>Sets the status of the pooled connection.                                                                         |
    | `void`                                                                          | `validate``()`<br>Validates this connection and sets corresponding status on this connection.                                                                                                                        |

<!-- -->

- - ### Method Detail

    - #### getPhysicalConnection

          java.lang.Object getPhysicalConnection()

      Gets the physical connection that this `UniversalPooledConnection` decorates.
      Returns:
      The physical connection. Never `null`.

    <!-- -->

    - #### getConnectionRetrievalInfo

          ConnectionRetrievalInfo getConnectionRetrievalInfo()

      Gets the connection retrieval info.
      Returns:
      The connection retrieval info. Never `null`.

    <!-- -->

    - #### setConnectionRetrievalInfo

          void setConnectionRetrievalInfo(ConnectionRetrievalInfo cri)

      Sets the connection retrieval info on the connection.
      Parameters:
      `cri` - -new CRI to be used for this connection

    <!-- -->

    - #### heartbeat

          void heartbeat()

      Indicates that the pooled connection is alive and being used.

    <!-- -->

    - #### setSqlWithQueryTimeoutInProgress

          void setSqlWithQueryTimeoutInProgress(boolean inProgress)

      Marks connection currently performing timed-out SQL operation
      Parameters:
      `set` - true, if timed-out SQL operation is in progress

    <!-- -->

    - #### isSqlWithQueryTimeoutInProgress

          boolean isSqlWithQueryTimeoutInProgress()

      Checks whether or not the connection currently performing timed-out SQL operation
      Returns:
      true if timed-out SQL operation is in progress

    <!-- -->

    - #### isValid

          boolean isValid()

      Checks whether or not the connection is valid.
      Returns:
      `true` if connection is valid; `false` otherwise.

    <!-- -->

    - #### validate

          void validate()

      Validates this connection and sets corresponding status on this connection. Possibly incurs a round-trip to the resource.

    <!-- -->

    - #### getLastAccessedTime

          long getLastAccessedTime()

      Gets the last time (in milliseconds) that this pooled connection was used by the client. This time is updated when the heartbeat method is called.
      Returns:
      The last time (in milliseconds) that this pooled connection was used by the client.

    <!-- -->

    - #### getLastNetworkAccessTime

          long getLastNetworkAccessTime()

      Gets the time (in milliseconds) when the underlying connection last accessed the network.
      Returns:
      The time (in milliseconds) when the underlying connection last accessed the network.

    <!-- -->

    - #### getStatus

          UniversalPooledConnectionStatus getStatus()

      Gets the status of the pooled connection.
      Returns:
      The status of the pooled connection.

    <!-- -->

    - #### setStatus

          void setStatus(UniversalPooledConnectionStatus status)
                  throws UniversalConnectionPoolException

      Sets the status of the pooled connection.
      Parameters:
      `status` - The status of the pooled connection.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - if an error occurs setting the status.

    <!-- -->

    - #### setAvailableStartTime

          void setAvailableStartTime()

      Sets the time that this pooled connection became available to be the current system time.

    <!-- -->

    - #### getAvailableStartTime

          long getAvailableStartTime()

      Gets the timestamp that this pooled connection became available.
      Returns:
      The time that this pooled connection became available.

    <!-- -->

    - #### setBorrowedStartTime

          void setBorrowedStartTime()

      Sets the time that this pooled connection became borrowed to be the current system time.

    <!-- -->

    - #### getBorrowedStartTime

          long getBorrowedStartTime()

      Gets the timestamp that this pooled connection became borrowed.
      Returns:
      The time that this pooled connection became available.

    <!-- -->

    - #### getLastConnectionValidationTime

          long getLastConnectionValidationTime()

      Gets the time that this pooled connection was last validated.
      Returns:
      The time that this pooled connection was last validated.

    <!-- -->

    - #### setLastConnectionValidationTime

          void setLastConnectionValidationTime(long lastConnectionValidationTime)

      Sets or resets the time that this pooled connection was last validated.

    <!-- -->

    - #### applyConnectionLabel

          void applyConnectionLabel(java.lang.String key,
                                    java.lang.String value)
                             throws UniversalConnectionPoolException

      Applies a connection label on a borrowed connection. Connection labels are cumulative. Each time this method is called, the supplied key/value pair is added to those connection labels already applied. However, for each particular label key, only the last applied value is retained. Applying connection labels on a closed connection throws `UniversalConnectionPoolException`.
      Parameters:
      `key` - The key of the connection label to be applied. Cannot be `null` or an empty string.

      `value` - The value of the connection label to be applied. Can be `null` or an empty string.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If this connection was closed or the key is `null` or an empty string.

    <!-- -->

    - #### removeConnectionLabel

          void removeConnectionLabel(java.lang.String key)
                              throws UniversalConnectionPoolException

      Removes the connection label with the given key from the connection labels applied on this connection. This method does nothing if there is no applied label with the specified key.
      Parameters:
      `key` - The key of the connection label to be removed. Cannot be `null` or an empty string.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If this connection was closed or the key is `null` or an empty string.

    <!-- -->

    - #### getConnectionLabels

          java.util.Properties getConnectionLabels()
                                            throws UniversalConnectionPoolException

      Retrieves all the connection labels applied on this connection. Any change to the result Properties object does not affect the labels applied to this connection.
      Returns:
      A `java.util.Properties` object storing all the applied labels as key/value pairs. Returns `null` if there are no applied labels on this connection.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If this connection was closed.

    <!-- -->

    - #### getUnmatchedConnectionLabels

          java.util.Properties getUnmatchedConnectionLabels(java.util.Properties requestedLabels)
                                                     throws UniversalConnectionPoolException

      Obtains all the requested labels that did not match the applied labels on this connection when this connection was borrowed from the pool.
      This method is typically used to verify, after a labeled connection is borrowed from the pool, which ones in the requested labels are matched and which ones are not.

      Parameters:
      `requestedLabels` - The requested labels that borrowed this connection from the pool.

      Returns:
      A java.util.Properties object storing all the requested labels that did not match the labels applied on this connection. Returns `null` if there are none.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If this connection was closed.

    <!-- -->

    - #### setConnectionHarvestable

          void setConnectionHarvestable(boolean isConnectionHarvestable)
                                 throws UniversalConnectionPoolException

      Specifies whether this connection is harvestable.
      Parameters:
      `isConnectionHarvestable` - Whether this connection is harvestable.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If this connection was closed.

    <!-- -->

    - #### isConnectionHarvestable

          boolean isConnectionHarvestable()

      Whether this connection is currently harvestable.
      Returns:
      A boolean indicating whether this connection is harvestable. `true` if so and `false` otherwise.

    <!-- -->

    - #### registerConnectionHarvestingCallback

          void registerConnectionHarvestingCallback(ConnectionHarvestingCallback cbk)
                                             throws UniversalConnectionPoolException

      Registers a `ConnectionHarvestingCallback` with this connection.
      Parameters:
      `cbk` - The `ConnectionHarvestingCallback` object to be registered.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If there is a callback already registered with the connection.

    <!-- -->

    - #### removeConnectionHarvestingCallback

          void removeConnectionHarvestingCallback()
                                           throws UniversalConnectionPoolException

      Removes the `ConnectionHarvestingCallback` object registered with this connection, if any.
      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If callback removal fails.

    <!-- -->

    - #### getConnectionHarvestingCallback

          ConnectionHarvestingCallback getConnectionHarvestingCallback()
                                                                throws UniversalConnectionPoolException

      Obtains the `ConnectionHarvestingCallback` registered with this connection.
      Returns:
      The `ConnectionHarvestingCallback` object registered. `null` if none.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If an error occurs.

    <!-- -->

    - #### registerAbandonedConnectionTimeoutCallback

          void registerAbandonedConnectionTimeoutCallback(AbandonedConnectionTimeoutCallback cbk)
                                                   throws UniversalConnectionPoolException

      Registers an `AbandonedConnectionTimeoutCallback` with this connection.
      Parameters:
      `cbk` - The `AbandonedConnectionTimeoutCallback` object to be registered.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If there is a callback already registered with the connection.

    <!-- -->

    - #### removeAbandonedConnectionTimeoutCallback

          void removeAbandonedConnectionTimeoutCallback()
                                                 throws UniversalConnectionPoolException

      Removes the `AbandonedConnectionTimeoutCallback` object registered with this connection, if any.
      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If callback removal fails.

    <!-- -->

    - #### getAbandonedConnectionTimeoutCallback

          AbandonedConnectionTimeoutCallback getAbandonedConnectionTimeoutCallback()
                                                                            throws UniversalConnectionPoolException

      Obtains the `AbandonedConnectionTimeoutCallback` registered with this connection.
      Returns:
      The `AbandonedConnectionTimeoutCallback` object registered. `null` if none.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If an error occurs.

    <!-- -->

    - #### registerTimeToLiveConnectionTimeoutCallback

          void registerTimeToLiveConnectionTimeoutCallback(TimeToLiveConnectionTimeoutCallback cbk)
                                                    throws UniversalConnectionPoolException

      Registers a `TimeToLiveConnectionTimeoutCallback` with this connection.
      Parameters:
      `cbk` - The `TimeToLiveConnectionTimeoutCallback` object to be registered.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If there is a callback already registered with the connection.

    <!-- -->

    - #### removeTimeToLiveConnectionTimeoutCallback

          void removeTimeToLiveConnectionTimeoutCallback()
                                                  throws UniversalConnectionPoolException

      Removes the `TimeToLiveConnectionTimeoutCallback` object registered with this connection, if any.
      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If callback removal fails.

    <!-- -->

    - #### getTimeToLiveConnectionTimeoutCallback

          TimeToLiveConnectionTimeoutCallback getTimeToLiveConnectionTimeoutCallback()
                                                                              throws UniversalConnectionPoolException

      Obtains the `TimeToLiveConnectionTimeoutCallback` registered with this connection.
      Returns:
      The `TimeToLiveConnectionTimeoutCallback` object registered.`null` if none.

      Throws:
      [`UniversalConnectionPoolException`](UniversalConnectionPoolException.md) - If an error occurs.

    <!-- -->

    - #### close

          void close()

      TODO document close connection
      Specified by:
      `close` in interface `java.lang.AutoCloseable`

      Specified by:
      `close` in interface `java.io.Closeable`

    <!-- -->

    - #### abort

          void abort()

      TODO document abort connection

    <!-- -->

    - #### handleTimeout

          void handleTimeout()

      TODO document handle timeouts on connection

    <!-- -->

    - #### isAvailable

          boolean isAvailable()

      check whether a connection is "available" or not
      Returns:
      true, if it is "available", false otherwise

    <!-- -->

    - #### setAvailable

          boolean setAvailable()

      mark connection as "available"
      Returns:
      true, if it was previously "borrowed", false otherwise

    <!-- -->

    - #### setBorrowed

          boolean setBorrowed()

      mark connection as "borrowed"
      Returns:
      true, if it was previously "available", false otherwise

    <!-- -->

    - #### isReusable

          boolean isReusable()

      check whether a connection is "reusable" or not
      Returns:
      true, if it is "reusable", false otherwise

    <!-- -->

    - #### labelingCost

          int labelingCost(java.util.Properties label)

      TODO document - costs are now here!

    <!-- -->

    - #### plugDelegator

          void plugDelegator(oracle.ucp.common.CoreConnection delegator)

    <!-- -->

    - #### getDelegator

          oracle.ucp.common.CoreConnection getDelegator()

    <!-- -->

    - #### getDatabaseConnectionProperties

          java.util.Properties getDatabaseConnectionProperties()

      Fetches the connection properties.

    <!-- -->

    - #### isOracle

          boolean isOracle()

      Is this connection an Oracle connection?
      Returns:
      true, if Oracle connection, otherwise (for non-oracle data sources) returns false

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/UniversalPooledConnection.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-files/index-1.md)
- [Help](../../help-doc.md)

**Oracle® Universal Connection Pool Java API Reference
19c Release**
E96461-04

- [Prev Class](UniversalConnectionPoolStatistics.md)
- [Next Class](UniversalPooledConnectionStatus.md)

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
