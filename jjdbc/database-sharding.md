This chapter describes JDBC support for Database Sharding in the following sections:

- Overview of Database Sharding for JDBC Users

- About Building the Sharding Key

- APIs for Database Sharding Support

- JDBC Sharding Example

### 24.1 Overview of Database Sharding for JDBC Users

Modern web applications face new scalability challenges with huge volumes of data. A commonly accepted solution to this problem is sharding. Sharding is a data tier architecture, where data is horizontally partitioned across independent databases. Each database in such a configuration is called a shard. All shards together make up a single logical database, which is referred to as a sharded database (SDB). Sharding is a shared-nothing database architecture because shards do not share physical resources such as CPU, memory, or storage devices.

Sharding uses Global Data Services (GDS), where GDS routes a client request to an appropriate database based on parameters such as availability, load, network latency, and replication lag. A GDS pool is a set of replicated databases that offer the same global service. The databases in a GDS pool can be located in multiple data centers across different regions. A sharded GDS pool contains all shards of a sharded database and their replicas, and appears as a single sharded database to database clients.

Starting from Oracle Database 12c Release 2 (12.2.0.1), Oracle JDBC supports database sharding. The JDBC driver recognizes the specified sharding key and super sharding key and connects to the relevant shard that contains the data. Once the connection is established to a shard, then any database operations, such as DMLs, SQL queries and so on, are supported and executed in the usual way. The following section describes the sharding terminologies used in this guide:

**See Also:**

[Oracle Database Administrator’s Guide](../shard/sharding-overview.md)

#### Sharding, Shard, and Sharded Database

Sharding is a data tier architecture where data is horizontally partitioned across independent databases. Each database in such configuration is called a shard. All shards together make up a single logical database which is referred to as a sharded database (SDB).

#### Sharding Key, Composite Sharding Key, and Super Sharding Key

A sharding key is a partitioning key used in single-level sharding by range, list, or consistent hash. All sharding keys together are referred to as the composite sharding keys. A super-sharding key is the partitioning key used in composite sharding for the top-level sharding by range or list. Both the sharding key and the super sharding key can contain one or more columns that determine the shard where each row is stored. A sharding key can be of type VARCHAR2, CHAR, DATE, NUMBER, TIMESTAMP and so on.

For JDBC users, it is recommended that sharding keys and super sharding keys must be passed while obtaining connections from the database. However, Sharding Keys can be provided in the connection string as a separate attribute under `CONNECT_DATA`. Passing sharding key in the connection string restricts the connections only to one shard. So, it is not recommended to use this approach. Following code snippet shows how you can provide Sharding Keys as a separate attribute under `CONNECT_DATA` in the connection string:

    (DESCRIPTION=(…)(CONNECT_DATA=(SERVICE_NAME=ORCL (SHARDING_KEY=…) (SUPER_SHARDING_KEY=...)))

**Note:**

You must provide the sharding key compliant to the NLS formatting that is specified in the database.

#### Multi Shard Queries

Multi Shard Queries enable routing and processing of queries and transactions that access data stored on multiple shards. Multi Shard Queries are executed without a sharding key. Multi Shard Operations are used for simple aggregation of data and reporting across shards.

#### Shard Catalog

Shard Catalog is a special database that is used for storing sharded database and supporting multi shard queries. It also helps in centralized management of a sharded database.

#### Shard Director

A shard director is a specific implementation of a global service manager (GSM) that acts as a regional listener for clients that connect to an SDB and maintains a current topology map of the SDB. Based on the sharding key passed during a connection request, it routes the connections to the appropriate shard.

#### Shard Topology

Shard Topology is the sharding key range mappings stored in a particular shard. Universal Connection Pool (UCP) can cache shard topology, which enables it to bypass shard director while establishing connections to shards. So, applications that you built using UCP get fast path for shards.

**See Also:**

[Oracle Universal Connection Pool Developer’s Guide](../jjucp/intro.md)

#### Chunk

A chunk is a single partition from each table of a table family. It is a unit of data migration between shards.

#### Chunk Split

Chunk Split is a process that is required when chunks become too big or only part of a chunk needs to be migrated to another shard.

#### Chunk Migration

Chunk migration is the process of moving a chunk from one shard to another, when data or workload skew occurs without any change in the number of shards. It is initiated by DBA to eliminate hot spots.

#### Resharding

Resharding is the process of redistributing data between shards triggered by a change in the number of shards. Chunks are moved between shards for even distribution of chunks across shards. However, content of chunks does not change, that is, no rehashing takes place during Resharding.

### 24.2 About Building the Sharding Key

####

The shard aware applications must identify and build the sharding key and the super sharding key, which are required to establish a connection to the sharded database. For achieving this, the shard aware applications must use the `OracleShardingKey` and the `OracleShardingKeyBuilder` interfaces.

The `OracleShardingKeyBuilder` uses the following builder method for supporting compound keys with different data types:

    subkey(Object subkey, java.sql.SQLTYPE subkeyDataType)

There are multiple invocations of the `subkey` method on the builder for building a compound sharding key, where each subkey can be of different data types. The data type can be defined using the `oracle.jdbc.OracleType` enum or `java.sql.JDBCType`.

Example 24-1 Building a Sharding Key

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

### 24.3 APIs for Database Sharding Support

Oracle Database 12c Release 2 (12.2.0.1) introduced a set of APIs for implementing database sharding. The following sections discuss these APIs in details:

- The OracleShardingKey Interface

- The OracleShardingKeyBuilder Interface

- The OracleConnectionBuilder Interface

- Other New Classes and Methods for Database Sharding Support

#### 24.3.1 The OracleShardingKey Interface

#####

This interface indicates that the current object represents an Oracle sharding key that is to be used with Oracle sharded database.

##### Syntax

    public interface OracleShardingKey extends Comparable <OracleShardingKey>

#### 24.3.2 The OracleShardingKeyBuilder Interface

`OracleShardingKeyBuilder` provides the interface to build the compound sharding key with subkeys of various supported data types. This interface uses the new JDK 8 builder pattern for building a sharding key.

##### Syntax

    public interface OracleShardingKeyBuilder

Example 24-2 Creating the Sharding Key

    OracleDataSource ods = new OracleDataSource();
    ...
    //set datasource properties..
    ...
    OracleShardingKey shardingKey = ods.createShardingKeyBuilder()
                                       .subkey("Customer_Name_XYZ", JDBCType.VARCHAR)
                                       .subkey(94002, JDBCType.NUMERIC)
                                       .build();

#### 24.3.3 The OracleConnectionBuilder Interface

The `OracleConnectionBuilder` is used for building connection objects with additional parameters, other than user name and password. For creating a connection, the builder methods need to be called for each parameter that needs to be part of the connection request, followed by a `build()` method. The order in which the builder methods are called is not important. However, if the same builder attribute is applied more than once, then only the most recent value is considered while building the connection. The `build()` method of the builder can be called only once on a builder object.

##### Syntax

    public interface OracleConnectionBuilder

Example 24-3 Creating the Connection Builder

    ...
    OracleDataSource ods=new OracleDataSource();
    ...
    OracleConnection conn = ods.createConnectionBuilder()
                               .shardingKey(shardingKey)
                               .superShardingKey(superShardingKey)
                               .build();

#### 24.3.4 Other New Classes and Methods for Database Sharding Support

#####

This section describes the rest of the new classes and methods introduced for implementing database sharding support.

##### New Methods in OracleDataSource Class

The `createConnectionBuilder` and `createShardingKeyBulider` methods have been introduced in `OracleDataSource` class for database sharding support.

    OracleConnectionBuilder createConnectionBuilder() throws SQLException;
    OracleShardingKeyBuilder createShardingKeyBuilder()

##### New Methods in OracleXADataSource Class

The `createConnectionBuilder` method has been introduced in `OracleXADataSource` class for database sharding support.

    OracleConnectionBuilder createConnectionBuilder() throws SQLException;

##### New Methods in OracleConnection Class

The `setShardingKeyIfValid` and `setShardingKey` methods have been introduced in `OracleConnection` class for database sharding support.

    boolean setShardingKeyIfValid(OracleShardingKey shardingKey, OracleShardingKey superShardingKey, int timeout) throws SQLException;

    void setShardingKey(OracleShardingKey shardingKey, OracleShardingKey superShardingKey) throws SQLException;

##### New Methods in OracleXAConnection Class

The `setShardingKeyIfValid` and `setShardingKey` methods have been introduced in `OracleConnection` class for database sharding support.

    boolean setShardingKeyIfValid(OracleShardingKey shardingKey, OracleShardingKey superShardingKey, int timeout) throws SQLException;

    void setShardingKey(OracleShardingKey shardingKey, OracleShardingKey superShardingKey) throws SQLException;

### 24.4 JDBC Sharding Example

The following code snippet shows how to use JDBC sharding APIs:

Example 24-4 JDBC Sharding Example

          OracleDataSource ods = new OracleDataSource();
          ods.setURL("jdbc:oracle:thin:@(DESCRIPTION=(ADDRESS=(HOST=myhost)(PORT=1521)(PROTOCOL=tcp))(CONNECT_DATA=(SERVICE_NAME=myorcldbservicename)))");
          ods.setUser("hr");
          ods.setPassword("hr");

         // Employee name is the sharding Key in this example.
         // Build the Sharding Key using employee name as shown below.

          OracleShardingKey employeeNameShardKey = ods.createShardingKeyBuilder()
                                                      .subkey("Mary", JDBCType.VARCHAR)// First Name
                                                      .subkey("Claire", JDBCType.VARCHAR)// Last Name
                                                      .build();

          OracleShardingKey locationSuperShardKey = ods.createShardingKeyBuilder() // Building a super sharding key using location as the key
                                                       .subkey("US", JDBCType.VARCHAR)
                                                       .build();

          OracleConnection connection = ods.createConnectionBuilder()
                                           .shardingKey(employeeNameShardKey)
                                           .superShardingKey(locationSuperShardKey)
                                           .build();
