This chapter describes the following interfaces:

- AbandonedConnectionTimeoutCallback Interface

- TimeToLiveConnectionTimeoutCallback Interface

### 6.1 AbandonedConnectionTimeoutCallback Interface

The `AbandonedConnectionTimeoutCallback` callback interface is used for the abandoned connection timeout feature. This feature enables applications to provide customized handling of abandoned connections.The callback object either uses one of its logical connection proxies or it is registered with each pooled connection. This enables applications to perform customized handling, when a particular connection is deemed abandoned by the pool. The `handleTimedOutConnection` method is invoked when a borrowed connection is deemed abandoned by the Universal Connection Pool. Applications can perform one of the following operations on the connection:

- Completely override the pool-handling process

- Invoke additional handling actions

- Assume the default pool-handling

The JDBC applications can invoke `cancel`, `close`, and `rollback` methods on the abandoned connection within the `handleTimedOutConnection` method.

**Note:**

If you try to register more than one `AbandonedConnectionTimeoutCallback` interface on the same connection, then it results in an exception. This exception can be a `UniversalConnectionPoolException` at the pool layer or a `java.sql.SQLException`, specific to the type of the UCP Adapter like JDBC, JCA and so on.

### 6.2 TimeToLiveConnectionTimeoutCallback Interface

The `TimeToLiveConnectionTimeoutCallback` callback interface used for the time-to-live (TTL) connection timeout feature. This enables applications to provide customized handling for TTL timed-out connections.

The callback object either uses one of its logical connection proxies or it is registered with each pooled connection. This enables applications to perform customized handling, when the TTL of the particular connection times out.

The `handleTimedOutConnection` method is invoked when a borrowed connection is found to be TTL timed-out by the Universal Connection Pool. Applications can perform one of the following operations on the connection:

- Completely override the pool-handling process

- Invoke additional handling actions

- Assume the default pool-handling

The JDBC applications can invoke `cancel`, `close`, and `rollback` methods on the abandoned connection within the `handleTimedOutConnection` method.

**Note:**

If you try to register more than one `TimeToLiveConnectionTimeoutCallback` interface on the same connection, then it results in an exception. This exception can be a `UniversalConnectionPoolException` at the pool layer or a `java.sql.SQLException`, specific to the type of the UCP Adapter like JDBC, JCA, and so on.
