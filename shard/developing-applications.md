## 9 Developing Applications for the Sharded Database

### Direct Routing to a Shard

Oracle clients and connections pools are able to recognize sharding keys specified in the connection string for high performance data dependent routing. A shard routing cache in the connection layer is used to route database requests directly to the shard where the data resides.

In direct, key-based, routing to a shard, a connection is established to a single, relevant shard which contains the data pertinent to the required transaction using a sharding key.

A sharding key is used to route database connection requests at a user session level during connection checkout. The composite sharding method requires both a sharding key and a super sharding key. Direct, key-based, routing requires the sharding key (or super sharding key) be passed as part of the connection. Based on this information, a connection is established to the relevant shard which contains the data pertinent to the given sharding key or super sharding key.

Once the session is established with a shard, all SQL queries and DMLs are supported and executed in the scope of the given shard. This routing is fast and is used for all OLTP workloads that perform intra-shard transactions. It is recommended that direct routing be employed for all OLTP workloads that require the highest performance and availability.

In support of Oracle Sharding, key enhancements have been made to Oracle connection pools and drivers. JDBC, Universal Connection Pool (UCP), OCI Session Pool (OCI), and Oracle Data Provider for .NET (ODP.NET) provide APIs to pass sharding keys during the connection creation. Apache Tomcat, IBM Websphere, Oracle WebLogic Server, and JBOSS can leverage JDBC/UCP support and use sharding. PHP, Python, Perl, and Node.js can leverage OCI support.

A shard topology cache is a mapping of the sharding key ranges to the shards. Oracle Integrated Connection Pools maintain this shard topology cache in their memory. Upon the first connection to a given shard (during pool initialization or when the pool connects to newer shards), the sharding key range mapping is collected from the shards to dynamically build the shard topology cache.

Caching the shard topology creates a fast path to the shards and expedites the process of creating a connection to a shard. When a connection request is made with a sharding key, the connection pool looks up the corresponding shard on which this particular sharding key exists (from its topology cache). If a matching connection is available in the pool then the pool returns a connection to the shard by applying its internal connection selection algorithm.

A database connection request for a given sharding key that is in any of the cached topology map, goes directly to the shard (that is, bypassing the shard director). Connection Pool also subscribes to RLB notifications from the SDB and dispenses the best connection based on runtime load balancing advisory. Once the connection is established, the client executes transactions directly on the shard. After all transactions for the given sharding key have been executed, the application must return the connection to the pool and obtain a connection for another key.

If a matching connection is not available in the pool, then a new connection is created by forwarding the connection request with the sharding key to the shard director.

Once the pools are initialized and the shard topology cache is built based on all shards, a shard director outage has no impact on direct routing.

### Sharding APIs Supporting Direct Routing

Oracle connection pools and drivers support Oracle Sharding.

JDBC, UCP, OCI, and Oracle Data Provider for .NET (ODP.NET) recognize sharding keys as part of the connection check. Apache Tomcat, Websphere, and WebLogic leverage UCP support for sharding and PHP, Python, Perl, and Node.js leverage OCI support.

#### Oracle JDBC APIs for Oracle Sharding

Oracle Java Database Connectivity (JDBC) provides APIs for connecting to database shards in an Oracle Sharding configuration.

The JDBC driver recognizes the specified sharding key and super sharding key and connects to the relevant shard that contains the data. Once the connection is established to a shard, then any database operations, such as DMLs, SQL queries and so on, are supported and executed in the usual way.

A shard-aware application gets a connection to a given shard by specifying the sharding key using the database sharding APIs.

- The `OracleShardingKey` interface indicates that the current object represents an Oracle sharding key that is to be used with Oracle sharded database.
- The `OracleShardingKeyBuilder` interface builds the compound sharding key with subkeys of various supported data types. This interface uses the new JDK 8 builder pattern for building a sharding key.
- The `OracleConnectionBuilder` interface builds connection objects with additional parameters other than user name and password.
- The `OracleDataSource` class provides database sharding support with the `createConnectionBuilder` and `createShardingKeyBulider` methods.
- The `OracleXADataSource` class provides database sharding support with the `createConnectionBuilder` method
- The `OracleConnection` class provides database sharding support with the `setShardingKeyIfValid` and `setShardingKey` methods.
- The `OracleXAConnection` class provides database sharding support with the `setShardingKeyIfValid` and `setShardingKey` methods.

See the Oracle Database JDBC Developer’s Guide for more information and examples.

Example 9-1 Sample Shard-Aware Application Code Using JDBC

The following code snippet shows how to use JDBC sharding APIs

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

**Related Topics**

- [JDBC Support for Database Sharding in Oracle Database JDBC Developer’s Guide](../jjdbc/database-sharding.md)

#### Oracle Call Interface for Oracle Sharding

Oracle Call Interface (OCI) provides an interface for connecting to database shards in an Oracle Sharding configuration.

To make requests that read from or write to a chunk, your application must be routed to the appropriate database (shard) that stores that chunk during the connection initiation step. This routing is accomplished by using a data key. The data key enables routing to the specific chunk by specifying its sharding key or to a group of chunks by specifying its super sharding key.

In order to get a connection to the correct shard containing the chunk you wish to operate on, you must specify a key in your application before getting a connection to a sharded Oracle database for either stand-alone connections or connections obtained from an OCI Session pool. For an OCI Session pool, you must specify a data key before you check out connections from the pool.

At a high-level, the following steps have to be followed to form sharding keys and shard group keys and get a session with an underlying connection:

1.  Allocate the sharding key descriptor by calling `OCIDescriptorAlloc()` and specifying the descriptor type parameter as `OCI_DTYPE_SHARDING_KEY` to form the sharding key.
2.  Allocate the shard group key descriptor by calling `OCIDescriptorAlloc()` and specifying the descriptor type parameter as `OCI_DTYPE_SHARDING_KEY` to form the shard group key.
3.  Call `OCISessionGet()` using the initialized authentication handle from the previous step containing the sharding key and shard group key information to get the database connection to the shard and chunk specified by the sharding key and group of chunks as specified by the shard group key.

See Oracle Call Interface Programmer's Guide for information about creating connections to OCI Session pools, stand-alone connections, and custom pool connections.

**Related Topics**

- [OCI Interface for Using Shards in Oracle Call Interface Programmer's Guide](../lnoci/oci-interface-for-using-shards.md)

#### Oracle Universal Connection Pool APIs for Oracle Sharding

Oracle Universal Connection Pool (UCP) provides APIs for connecting to database shards in an Oracle Sharding configuration.

A shard-aware application gets a connection to a given shard by specifying the sharding key using the enhanced sharding API calls `createShardingKeyBuilder` and `createConnectionBuilder`.

At a high-level, the following steps have to be followed in making an application work with a sharded database:

1.  Update the URL to reflect the shard directors and global service.

2.  Set the following pool parameters at the pool level and the shard level.

    - `setInitialPoolSize` sets the initial number of connections to be created when UCP is started

    - `setMinPoolSize` sets the minimum number of connections maintained by pool at runtime

    - `setMaxPoolSize` sets maximum number of connections allowed on connection pool

    - `setMaxConnectionsPerShard` sets max connections per shard

3.  Build a sharding key object with `createShardingKeyBuilder`.

4.  Establish a connection using `createConnectionBuilder`.

5.  Execute transactions within the scope of the given shard.

Example 9-2 Establishing a Connection Using UCP Sharding API

The following is a code fragment which illustrates how the sharding keys are built and connections established using UCP Sharding API calls.

    ...

    PoolDataSource pds =
         PoolDataSourceFactory.getPoolDataSource();

      // Set Connection Pool properties
    pds.setURL(DB_URL);
    pds.setUser("hr");
    pds.setPassword("****");
    pds.setInitialPoolSize(10);
    pds.setMinPoolSize(20);
    pds.setMaxPoolSize(30);

    // build the sharding key object

    OracleShardingKey shardingKey =
        pds.createShardingKeyBuilder()
          .subkey("mary.smith@example.com", OracleType.VARCHAR2)
          .build();

      // Get an UCP connection for a shard
    Connection conn =
        pds.createConnectionBuilder()
         .shardingKey(shardingKey)
         .build();
    ...

Example 9-3 Sample Shard-Aware Application Code Using UCP Connection Pool

In this example the pool settings are defined at the pool level and at the shard level.

    import java.sql.Connection;
    import java.sql.ResultSet;
    import java.sql.SQLException;
    import java.sql.Statement;

    import oracle.jdbc.OracleShardingKey;
    import oracle.jdbc.OracleType;
    import oracle.jdbc.pool.OracleDataSource;
    import oracle.ucp.jdbc.PoolDataSource;
    import oracle.ucp.jdbc.PoolDataSourceFactory;

    public class MaxConnPerShard
    {
      public static void main(String[] args) throws SQLException
      {
        String url = "jdbc:oracle:thin:@(DESCRIPTION=(ADDRESS=(HOST=shard-dir1)(PORT=3216)
     (PROTOCOL=tcp))(CONNECT_DATA=(SERVICE_NAME=shsvc.shpool.oradbcloud)(REGION=east)))";
        String user="testuser1", pwd = "testuser1";

        int maxPerShard = 100, initPoolSize = 20;

        PoolDataSource pds = PoolDataSourceFactory.getPoolDataSource();
        pds.setConnectionFactoryClassName(OracleDataSource.class.getName());
        pds.setURL(url);
        pds.setUser(user);
        pds.setPassword(pwd);
        pds.setConnectionPoolName("testpool");
        pds.setInitialPoolSize(initPoolSize);

        // set max connection per shard
        pds.setMaxConnectionsPerShard(maxPerShard);
        System.out.println("Max-connections per shard is: "+pds.getMaxConnectionsPerShard());

        // build the sharding key object
        int shardingKeyVal = 123;
        OracleShardingKey sdkey = pds.createShardingKeyBuilder()
            .subkey(shardingKeyVal, OracleType.NUMBER)
            .build();

        // try to build maxPerShard connections with the sharding key
        Connection[] conns = new Connection[maxPerShard];
        for (int i=0; i<maxPerShard; i++)
        {
          conns[i] = pds.createConnectionBuilder()
              .shardingKey(sdkey)
              .build();

    Statement stmt = conns[i].createStatement();
          ResultSet rs = stmt.executeQuery("select sys_context('userenv', 'instance_name'),
           sys_context('userenv', 'chunk_id') from dual");
          while (rs.next()) {
            System.out.println((i+1)+" - inst:"+rs.getString(1)+", chunk:"+rs.getString(2));
          }
          rs.close();
          stmt.close();
        }

        System.out.println("Try to build "+(maxPerShard+1)+" connection ...");
        try {
          Connection conn = pds.createConnectionBuilder()
              .shardingKey(sdkey)
              .build();

          Statement stmt = conn.createStatement();
          ResultSet rs = stmt.executeQuery("select sys_context('userenv', 'instance_name'),
           sys_context('userenv', 'chunk_id') from dual");
          while (rs.next()) {
            System.out.println((maxPerShard+1)+" - inst:"+rs.getString(1)+",
             chunk:"+rs.getString(2));
          }
          rs.close();
          stmt.close();

          System.out.println("Problem!!! could not build connection as max-connections per
            shard exceeded");
          conn.close();
        } catch (SQLException e) {
          System.out.println("Max-connections per shard met, could not build connection
            any more, expected exception: "+e.getMessage());
        }
        for (int i=0; i<conns.length; i++)
        {
          conns[i].close();
        }
      }
    }

**Related Topics**

- [UCP APIs for Database Sharding Support in Oracle Universal Connection Pool Developer’s Guide](../jjucp/ucp-sharding-api.md)

#### Oracle Data Provider for .NET APIs for Oracle Sharding

Oracle Data Provider for .NET (ODP.NET) provides APIs for connecting to database shards in an Oracle Sharding configuration.

Using ODP.NET APIs, a shard-aware application gets a connection to a given shard by specifying the sharding key and super sharding key with APIs such as the `SetShardingKey(OracleShardingKey shardingKey, OracleShardingKey superShardingKey)` instance method in the `OracleConnection` class.

At a high level, the following steps are necessary for a .NET application to work with a sharded database:

1.  Use ODP.NET, Unmanaged Driver.

    Sharding is supported with or without ODP.NET connection pooling. Each pool can maintain connections to different shards of the sharded database.

2.  Use an `OracleShardingKey` class to set the sharding key and another instance for the super sharding key.

3.   Invoke the `OracleConnection.SetShardingKey()` method prior to calling `OracleConnection.Open()` so that ODP.NET can return a connection with the specified sharding key and super sharding key.

    These keys must be set while the `OracleConnection` is in a Closed state, otherwise an exception is thrown.

Example 9-4 Sample Shard-Aware Application Code Using ODP.NET

    using System;
    using Oracle.DataAccess.Client;

    class Sharding
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection
          ("user id=hr;password=hr;Data Source=orcl;");
        //Setting a shard key
        OracleShardingKey shardingKey = new OracleShardingKey(OracleDbType.Int32, 123);
        //Setting a second shard key value for a composite key
        shardingKey.SetShardingKey(OracleDbType.Varchar2, "gold");
        //Creating and setting the super shard key
        OracleShardingKey superShardingKey = new OracleShardingKey();
        superShardingKey.SetShardingKey(OracleDbType.Int32, 1000);

        //Setting super sharding key and sharding key on the connection
        con.SetShardingKey(shardingKey, superShardingKey);
        con.Open();

        //perform SQL query
      }
    }

**Related Topics**

- [Database Sharding in Oracle Data Provider for .NET Developer's Guide for Microsoft Windows](../odpnt/featDataSharding.md)
