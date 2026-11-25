This section contains the following subsections:

- Overview of Connection Affinity

- Setting Up Connection Affinity

### 9.4.1 Overview of Connection Affinity

UCP JDBC connection pools leverage affinity functionality provided by an Oracle RAC database. Connection affinity requires the use of an Oracle JDBC driver and an Oracle RAC database version 11.1.0.6 or higher.

Connection affinity is a performance feature that enables a connection pool to select connections that are directed at a specific Oracle RAC instance. The pool uses run-time connection load balancing (if configured) to select an Oracle RAC instance to create the first connection and then subsequent connections are created with an affinity to the same instance.

**See Also:**

- "Strict Affinity Mode"

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/introduction-to-oracle-rac.md) for more information about setting up an Oracle RAC database.

UCP JDBC connection pools support the following three types of connection affinity:

- Transaction-Based Affinity

- Web Session Affinity

- Oracle RAC Data Affinity

#### 9.4.1.1 Transaction-Based Affinity

Transaction-based affinity is an affinity to an Oracle RAC instance that can be released by either the client application or a failure event. Applications typically use this type of affinity when long-lived affinity to an Oracle RAC instance is desired or when the cost (in terms of performance) of being redirected to a new Oracle RAC instance is high. Distributed transactions are a good example of transaction-based affinity. XA connections that are enlisted in a distributed transaction keep an affinity to the Oracle RAC instance for the duration of the transaction. In this case, an application would incur a significant performance cost if a connection is redirect to a different Oracle RAC instance during the distributed transaction.

#### 9.4.1.2 Web Session Affinity

Web session affinity is an affinity to an Oracle RAC instance that can be released by either the instance, a client application, or a failure event. The Oracle RAC instance uses a hint to communicate to a connection pool whether affinity has been enabled or disabled on the instance. An Oracle RAC instance may disable affinity based on many factors, such as performance or load. If an Oracle RAC instance can no longer support affinity, the connections in the pool are refreshed to use a new instance and affinity is established once again.

Applications typically use this type of affinity when short-lived affinity to an Oracle RAC instance is expected or if the cost (in terms of performance) of being redirected to a new Oracle RAC instance is minimal. For example, a mail client session might use Web session affinity to an Oracle RAC instance to increase performance and is relatively unaffected if a connection is redirected to a different instance.

#### 9.4.1.3 Oracle RAC Data Affinity

Data affinity describes the concept of ensuring that a group of related cache entries is contained within a single cache partition.

Starting from Oracle Database Release 18c, UCP supports Oracle RAC Data Affinity. When you enable Data Affinity on the Oracle RAC database, data on the affinitized tables are partitioned in such a way that a particular partition or subset of rows for a table is affinitized to a particular Oracle RAC database instance. The affinity leads to higher performance and scalability for the applications due to improved cache locality and reduced internode synchronization and block pings among the RAC instances.

**See Also:**

[Enabling a Custom Partition Assignment Strategy](https://docs.oracle.com/middleware/1212/coherence/COHDG/api_dataaffinity.htm#COHDG5577)

To use the Oracle RAC Data Affinity feature, the clients accessing the database through UCP must provide the data affinity key in their connection requests. UCP has the following capabilities when pooling connections for an affinity enabled RAC database:

1.  UCP learns the topology that contains the data affinity of the data partitions across Oracle RAC instances at pool start up.

2.  UCP connection requests that need to leverage the Oracle RAC Data Affinity feature provides the data affinity key using the sharding key builder and use the connection builder as follows:

          PoolDataSource pds = new PoolDataSourceImpl();
           // configure the datasource with the database connection properties

        /* Builds the RAC data affinity key using the sharding key builder API
        and gets a connection from the pool using UCP connection builder */
          OracleShardingKey dataAffinityKey =  pds.createShardingKeyBuilder()
                  .subkey(1000, OracleType.NUMBER)
                  .build();

          Connection connection = pds.createConnectionBuilder()
                  .shardingKey(dataAffinityKey)
                  .build();

    **Note:**

    You can still make connection requests to Oracle RAC Data Affinity-enabled without providing the data affinity key. However, in this case, you will not see the benefits of Oracle RAC Data Affinity feature.

3.  UCP determines the affinitized instance for the shard key provided in the request and checks if a connection for that instance exists in the pool. If the connection exists, then it is used to serve the request. If a matching connection does not exist in the pool, then a fallback to Run-Time Load Balancing chooses a connection for the request and serves it. If a new connection needs to be created to serve the request, then the request is routed to the affinitized instance corresponding to the provided shard (data affinity) key.

4.  UCP keeps its topology of the data partitions in sync with the server side when there are HA events or when there is a change in the affinity of data partitions on Oracle RAC.

### 9.4.2 Setting Up Connection Affinity

Perform the following steps to set up connection affinity:

- Enable FCF.

  **See Also:**

  "[About Fast Connection Failover](fast-connection-failover.md)"

- Enable run-time connection load balancing.

  **See Also:**

  "[About Run-Time Connection Load Balancing](run-time-connection-load-balancing.md)"

- Create a connection affinity callback.

- Register the callback.

**Note:**

Transaction-based affinity is strictly scoped between the application/middle-tier and UCP. Therefore, transaction-based affinity requires only the `setFastConnectionFailoverEnabled` property be set to `true` and does not require complete FCF configuration.

In addition, transaction-based affinity does not technically require run-time connection load balancing. However, it can help with performance and is usually enabled regardless. If run-time connection load balancing is not enabled, the connection pool randomly picks connections.

This section contains the following subsections:

- Creating a Connection Affinity Callback

- Registering a Connection Affinity Callback

- Removing a Connection Affinity Callback

#### 9.4.2.1 Creating a Connection Affinity Callback

Connection affinity requires the use of a callback. The callback is an implementation of the `ConnectionAffinityCallback` interface which is located in the `oracle.ucp` package. The callback is used by the connection pool to establish and retrieve a connection affinity context and is also used to set the affinity policy type (transaction-based or Web session).

The following example demonstrates setting an affinity policy in a callback implementation. The example also demonstrates manually setting an affinity context. typically, the connection pool sets the affinity context inside an application. However, the ability to manually set an affinity context is provided for applications that want to customize affinity behavior and control the affinity context directly.

    public class AffinityCallbackSample
       implements ConnectionAffinityCallback {

       Object appAffinityContext = null;
       ConnectionAffinityCallback.AffinityPolicy affinityPolicy =
       ConnectionAffinityCallback.AffinityPolicy.TRANSACTION_BASED_AFFINITY;

       //For Web session affinity, use WEBSESSION_BASED_AFFINITY;

       public void setAffinityPolicy(AffinityPolicy policy)
       {
          affinityPolicy = policy;
       }

       public AffinityPolicy getAffinityPolicy()
       {
          return affinityPolicy;
       }

       public boolean setConnectionAffinityContext(Object affCxt)
       {
          synchronized (lockObj)
          {
             appAffinityContext = affCxt;
          }
          return true;
       }

       public Object getConnectionAffinityContext()
       {
          synchronized (lockObj)
          {
             return appAffinityContext;
          }
       }
    }

#### 9.4.2.2 Registering a Connection Affinity Callback

A connection affinity callback is registered on a connection pool using the `registerConnectionAffinityCallback` method. The callback is registered when creating the connection pool. Only one callback can be registered per connection pool.

The following example demonstrates registering a connection affinity callback implementation:

    ConnectionAffinityCallback callback = new MyCallback();

    PoolDataSource  pds = PoolDataSourceFactory.getPoolDataSource();

    pds.setConnectionPoolName("AffinitySamplePool");
    pds.registerConnectionAffinityCallback(callback);
    ...

#### 9.4.2.3 Removing a Connection Affinity Callback

A connection affinity callback is removed from a connection pool using the `removeConnectionAffinityCallback` method. For example:

    PoolDataSource  pds = PoolDataSourceFactory.getPoolDataSource();

    pds.setConnectionPoolName("AffinitySamplePool");
    pds.removeConnectionAffinityCallback();
    ...

#### 9.4.2.4 Strict Affinity Mode

By default, affinity is only a hint. A connection pool selects a new Oracle RAC instance for connections if it does not find a connection on a desired instance. You can change this behavior by switching the strict affinity mode on. The strict affinity mode throws a UCP exception if a connection on a desired instance is not found.

Use the following pool properties to switch on the strict affinity mode:

- The `useStrictWebSessionAffinity` property

  Set the `useStrictWebSessionAffinity` property to `true` or `false` for switching the strict Web session affinity mode on or off respectively.

- The `useStrictXAAffinity` property

  Set the `useStrictXAAffinity` property to `true` or `false` for switching the strict transaction-based affinity mode on or off respectively.

These properties can be handled through the `UniversalConnectionPoolMBean`.

**Related Topics**

- [UniversalConnectionPoolMBean](jmx-based-management.md)
