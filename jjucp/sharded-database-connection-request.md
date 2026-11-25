The following sections describe how Universal Connection Pool (UCP) handles connection requests for a sharded database:

- [About Building the Sharding Key](../jjdbc/database-sharding.md)

- How to Checkout Connections from a Pool with a Known Sharding key

- About Checking Out Connections without Providing the Sharding Keys

- About Connecting to the Catalog Database for Cross Shard Queries

- About Configuring the Number of Connections Per Shard

- Pool Connection Selection Algorithm During Connection Checkout

- Failover or Resharding Event handling in UCP

### 11.2.1 About Building the Sharding Key

####

The shard aware applications must identify and build the sharding key and the super sharding key, which are required to establish a connection to the sharded database. For achieving this, the shard aware applications must use the `OracleShardingKey` and the `OracleShardingKeyBuilder` interfaces.

The `OracleShardingKeyBuilder` uses the following builder method for supporting compound keys with different data types:

    subkey(Object subkey, java.sql.SQLTYPE subkeyDataType)

There are multiple invocations of the `subkey` method on the builder for building a compound sharding key, where each subkey can be of different data types. The data type can be defined using the `oracle.jdbc.OracleType` enum or `java.sql.JDBCType`.

Example 11-1 Building a Sharding Key

The following example shows how to build a sharding key:

    import java.sql.Connection;
    import java.sql.Date;
    import java.sql.SQLException;
    import java.sql.Statement;

    import oracle.jdbc.OracleShardingKey;
    import oracle.jdbc.OracleType;
    import oracle.ucp.jdbc.PoolDataSource;
    import oracle.ucp.jdbc.PoolDataSourceFactory;

      public class ShardExample
      {
        public static void main(String[] args) throws SQLException
        {
          String url = "jdbc:oracle:thin:@(DESCRIPTION=(ADDRESS=(HOST=myhost)(PORT=3216)(PROTOCOL=tcp))(CONNECT_DATA=(SERVICE_NAME=myservice)(REGION=east)))";
          String user="testuser1";
          String pwd = "password";

          PoolDataSource pds = PoolDataSourceFactory.getPoolDataSource();
          pds.setURL(url);
          pds.setUser(user);
          pds.setPassword(pwd);
          pds.setConnectionFactoryClassName("oracle.jdbc.pool.OracleDataSource");
          pds.setInitialPoolSize(5);
          pds.setMinPoolSize(5);
          pds.setMaxPoolSize(20);

          // build the sharding key object
          Date shardingKeyVal = new java.sql.Date(0L);
          OracleShardingKey sdkey = pds.createShardingKeyBuilder()
                                       .subkey(shardingKeyVal, OracleType.DATE)
                                       .build();

          Connection conn = pds.createConnectionBuilder()
                                .shardingKey(sdkey)
                                .build();

          Statement stmt = conn.createStatement();
          stmt.execute("... SQL statement here ...");
          stmt.close();
          conn.close();
        }
      }

The following code snippet shows how to build a compound sharding key that consists of String and Date data types:

    ...
    Date shardingKeyVal = new java.sql.Date(0L);
    ...
    OracleShardingKey shardingKey = datasource.createShardingKeyBuilder()
                              .subkey("abc@xyz.com", JDBCType.VARCHAR)
                              .subkey(shardingKeyVal, OracleType.DATE)
                              .build();
    ...

**Note:**

- There is a fixed set of data types that are valid and supported. If any unsupported data types are used as keys, then exceptions are thrown. The following list specifies the supported data types:

  - `OracleType.VARCHAR2/JDBCType.VARCHAR`

  - `OracleType.CHAR/JDBCType.CHAR`

  - `OracleType.NVARCHAR/JDBCType.NVARCHAR`

  - `OracleType.NCHAR/JDBCType.NCHAR`

  - `OracleType.NUMBER/JDBCType.NUMERIC`

  - `OracleType.FLOAT/ JDBCType.FLOAT`

  - `OracleType.DATE/ JDBCType.DATE`

  - `OracleType.TIMESTAMP/JDBCType.TIMESTAMP`

  - `OracleType.TIMESTAMP_WITH_LOCAL_TIME_ZONE`

  - `OracleType.RAW`

- You must provide a sharding key that is compliant to the NLS formatting specified in the database.

### 11.2.2 How to Checkout Connections from a Pool with a Sharding Key

When a connection is borrowed from UCP, then the shard aware application can provide the sharding key and the super sharding key using the new connection builder present in the `PoolDataSource` class. If sharding keys do not exist or do not map to the data types specified by the database metadata, then an `IllegalArgumentException` is thrown. The following code snippet shows how to checkout a connection with sharding keys:

    PoolDataSource pds = PoolDataSourceFactory.getPoolDataSource();
    ...
    Connection conn = pds.createConnectionBuilder()
    // Establish a connection using sharding key and super sharding key
                 .shardingKey(shardingKey)
                 .superShardingKey(superShardingKey)
                 .build();

    OracleShardingKey shardKey = pds.createShardingKeyBuilder()
    // Build a compound sharding key with email address and customer ID as the two sharding keys
                    .subkey(<email>, OracleType.VARCHAR2)
                    .subkey(<custid>, OracleType.NUMBER)
                    .build();

    OracleShardingKey superShardKey = pds.createShardingKeyBuilder()
    // Build a super sharding key with the customer region
                         .subkey(<cust_region>, OracleType.VARCHAR2)
                         .build();

**Note:**

You must specify a sharding key during the connection checkout. Otherwise, an error or exception is thrown back to the application. Race condition also results in exception during connection usage.

### 11.2.3 About Checking Out Connections without Providing the Sharding Keys

Providing sharding keys in a connection request through connection builder API is mandatory when you use UCP data source for connecting to a sharded database. If you do not provide the sharding key, then an exception is thrown back to the user.

### 11.2.4 About Connecting to the Shard Catalog or Co-ordinator for Multi Shard Queries

When connecting to the Shard Catalog or Co-ordinator for running multi shard queries, it is recommended that a separate pool be created using a new `PoolDataSource` instance. You can run multi shard queries on connections retrieved from a data source that is created on the coordinator service. The connection request for the coordinator should not have sharding keys in the connection builder API.

### 11.2.5 About Configuring the Number of Connections Per Shard

When UCP is used to pool connections for a sharded database, the pool contains connections to different shards. So, when connections are pulled, to ensure a fair usage of the pool capacity across all shards connected, UCP uses the `MaxConnectionsPerShard` parameter. This is a global parameter, which applies to every shard in the sharded database, and is used to limit the total number of connections to any shard below the specified limit.

The following table describes the APIs for setting and retrieving this parameter:

| Method                                                                        | Description                                                                                                       |
|:------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------|
| `poolDatasource.setMaxConnectionsPerShard(<max_connections_per_shard_limit>)` | Sets the maximum number of connections per shard.                                                                 |
| `poolDatasource.getMaxConnectionsPerShard()`                                  | Retrieves the value that was set using the `setMaxConnectionsPerShard(<max_connections_per_shard_limit>)` method. |

**Note:**

You cannot use the `MaxConnectionsPerShard` parameter in a sharded database with Oracle Golden Gate configuration.

### 11.2.6 Pool Connection Selection Algorithm During Connection Checkout

Whenever new connections are created through UCP to different shards in the sharded database, the pool incrementally learns and builds a shard routing cache internally.

The routing cache maps the sharding keys to the respective shards, on which the keys exist. While looking up connections in the pool for a connection request with specific sharding keys, UCP uses the cache to redirect the request to the correct shard. This feature, called Fast Path Connection Borrow, enables efficient reuse of connections in the pool, based on the requested sharding keys. This feature also helps in avoiding going to the sharded database for routing the requests.

### 11.2.7 Failover or Resharding Event Handling in UCP

After a resharding or failover event, an attempt is made to keep the UCP shard routing cache in sync with the data on the server. The cache is kept up-to-date by subscribing to the ONS notification for various changes on the database.
