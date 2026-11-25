Stale connections are connections that remain either available or borrowed, but are no longer being used. Stale connections that remain borrowed may affect connection availability. In addition, stale connections may impact system resources that are otherwise wasted on maintaining unused connections for extended periods of time. The pool properties discussed in this section are used to control stale connections.

This section describes the following topics:

- What is Connection Reuse?

- Setting the Abandon Connection Timeout

- Setting the Time-To-Live Connection Timeout

- Setting the Connection Wait Timeout

- Setting the Inactive Connection Timeout

- Setting the Query Timeout

- Setting the Timeout Check Interval

**Note:**

It is good practice to close all connections that are no longer required by an application. Closing connections helps minimize the number of stale connections that remain borrowed.

### 4.4.1 What is Connection Reuse?

The connection reuse feature allows connections to be gracefully closed and removed from a connection pool after a specific amount of time or after the connection has been used a specific number of times. This feature saves system resources that are otherwise wasted on maintaining unusable connections.

#### 4.4.1.1 Setting the Maximum Connection Reuse Time

The maximum connection reuse time allows connections to be gracefully closed and removed from the pool after a connection has been in use for a specific amount of time. The timer for this property starts when a connection is physically created. Borrowed connections are closed only after they are returned to the pool and the reuse time is exceeded.

This feature is typically used when a firewall exists between the pool tier and the database tier and is setup to block connections based on time restrictions. The blocked connections remain in the pool even though they are unusable. In such scenarios, the connection reuse time is set to a smaller value than the firewall timeout policy.

**Note:**

The maximum connection reuse time is different from the time-to-live connection timeout. The time-to-live connection timeout starts when a connection is borrowed from the pool; while, the maximum connection reuse time starts when the connection is physically created. In addition, with a time-to-live timeout, a connection is closed and returned to the pool for reuse if the timeout expires during the borrowed period. With maximum connection reuse time, a connection is closed and discarded from the pool after the timeout expires.

The maximum connection reuse time value represents seconds. A value of `0` indicates that this feature is disabled. The default value is `0`. The following example demonstrates configuring a maximum connection reuse time:

    pds.setMaxConnectionReuseTime(300);

**Related Topics**

- Setting the Time-To-Live Connection Timeout

#### 4.4.1.2 Setting the Maximum Connection Reuse Count

The maximum connection reuse count allows connections to be gracefully closed and removed from the connection pool after a connection has been borrowed a specific number of times. This property is typically used to periodically recycle connections in order to eliminate issues such as memory leaks.

A value of `0` indicates that this feature is disabled. The default value is `0`. The following example demonstrates configuring a maximum connection reuse count:

    pds.setMaxConnectionReuseCount(100);

### 4.4.2 Setting the Connection Validation Timeout

The connection validation timeout specifies the duration within which a borrowed connection from the pool is validated. This is the maximum time for a connection validation operation. If the validation is not completed during this period, then the connection is treated as invalid.

The connection validation timeout value represents seconds. The default value is set to 15. The following example demonstrates configuring a connection validation timeout:

    pd.setConnectionValidationTimeout(55);

### 4.4.3 Setting the Abandon Connection Timeout

The abandoned connection timeout (ACT) enables borrowed connections to be reclaimed back into the connection pool after a connection has not been used for a specific amount of time. Abandonment is determined by monitoring calls to the database. This timeout feature helps maximize connection reuse and conserves system resources that are otherwise lost on maintaining borrowed connections that are no longer in use.

**Note:**

UCP either cancels or rolls back connections that have local transactions pending before reclaiming connections for reuse.

The ACT value represents seconds. A value of `0` indicates that the feature is disabled. The default value is set to `0`. The following example demonstrates configuring an abandoned connection timeout:

    pds.setAbandonedConnectionTimeout(10);

Every connection is reaped after a specific period of time. Either it is reaped when ACT expires, or, if it is immune from ACT, then it is reaped after the immunity expires. If you set ACT on a pool, then:

- If a statement is executed without calling the `Statement.setQueryTimeout` method on that statement, then the connection is reaped if ACT is exceeded, even though the connection is waiting for the server to respond to the query.

- If a statement is executed with calling the `Statement.setQueryTimeout` method, then the connection is reaped after the query timeout and ACT have expired. The connection is not reaped while waiting on the query timeout. The expiration of the query timeout is an event that resets the ACT timer. If the ACT expires while waiting for the `cancel` action that occurs at the expiration of the query time out, then the connection is reaped.

- If a connection has two statements: s1 with a query timeout and s2 without a query timeout, then ACT does not reap the connection while s1 waits for the query timeout, but reaps the connection if s2 hangs.

  Note that the two statements execute sequentially based on JDBC requirement.

### 4.4.4 Setting the Time-To-Live Connection Timeout

The time-to-live connection timeout enables borrowed connections to remain borrowed for a specific amount of time before the connection is reclaimed by the pool. This timeout feature helps maximize connection reuse and helps conserve systems resources that are otherwise lost on maintaining connections longer than their expected usage.

**Note:**

UCP either cancels or rolls back connections that have local transactions pending before reclaiming connections for reuse.

The time-to-live connection timeout value represents seconds. A value of `0` indicates that the feature is disabled. The default value is set to `0`. The following example demonstrates configuring a time-to-live connection timeout:

    pds.setTimeToLiveConnectionTimeout(18000)

### 4.4.5 Setting the Connection Wait Timeout

The connection wait timeout specifies how long an application request waits to obtain a connection if there are no longer any connections in the pool. A connection pool runs out of connections if all connections in the pool are being used (borrowed) and if the pool size has reached it's maximum connection capacity as specified by the maximum pool size property. The request receives an SQL exception if the timeout value is reached. The application can then retry getting a connection. This timeout feature improves overall application usability by minimizing the amount of time an application is blocked and provides the ability to implement a graceful recovery.

The connection wait timeout value represents seconds. A value of `0` indicates that the feature is disabled. The default value is set to `3` seconds. The following example demonstrates configuring a connection wait timeout:

    pds.setConnectionWaitTimeout(10);

### 4.4.6 Setting the Inactive Connection Timeout

The inactive connection timeout specifies how long an available connection can remain idle before it is closed and removed from the pool. This timeout property is only applicable to available connections and does not affect borrowed connections. This property helps conserve resources that are otherwise lost on maintaining connections that are no longer being used. The inactive connection timeout (together with the maximum pool size) allows a connection pool to grow and shrink as application load changes.

The inactive connection timeout value represents seconds. A value of `0` indicates that the feature is disabled. The default value is set to `0`. The following example demonstrates configuring an inactive connection timeout:

    pds.setInactiveConnectionTimeout(60);

### 4.4.7 Setting the Query Timeout

In Oracle Database 12c Release 2 (12.2.0.1), UCP introduced the `queryTimeout` property. This property specifies the number of seconds UCP waits for a `Statement` object to execute. If the limit is exceeded, then a `DatabaseException` is thrown. Use the `setQueryTimeout` method for setting this property in the following way:

    ...
    PoolDataSourceImpl pds = new PoolDataSourceImpl();
    pds.setConnectionFactoryClassName("oracle.jdbc.pool.OracleDataSource");
    pds.setURL(<url>);
    pds.setUser("scott");
    pds.setPassword(<password>);
    pds.setConnectionPoolName("my_pool");
    pds.setQueryTimeout(60); // 60 seconds to wait on query
    ...

### 4.4.8 Setting the Timeout Check Interval

The timeout check interval property controls how frequently the timeout properties (abandoned connection timeout, time-to-live connection timeout, and inactive connection timeout) are enforced. Connections that have timed-out are reclaimed when the timeout check cycle runs. This means that a connection may not actually be reclaimed by the pool at the moment that the connection times-out. The lag time between the connection timeout and actually reclaiming the connection may be considerable depending on the size of the timeout check interval.

The timeout check interval property represents seconds. The default value is set to `30`. The following example demonstrates configuring a property check interval:

    pds.setTimeoutCheckInterval(60);

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/introducing-oracle-net-services.md) for more information about Oracle Net Services
