Sharding is a data tier architecture, where data is horizontally partitioned across independent databases. Each database in such a configuration is called a shard. All shards together make up a single logical database, which is referred to as a sharded database. Sharding is a shared-nothing database architecture. The independent physical databases do not share CPU, memory, or storage devices. However, from the perspective of an application, the collection of physical databases looks like a single logical database.

Sharding uses Global Data Services (GDS), where GDS routes a client request to an appropriate database based on parameters such as availability, load, network latency, and replication lag. A GDS pool is a set of replicated databases that offers the same global service. The databases in a GDS pool can be located in multiple data centers across different regions. A sharded GDS pool contains all shards of a sharded database and their replicas, and appears as a single sharded database to database clients.

Applications can connect to multiple databases (shards) where data is partitioned based on one or more sharding strategies. The strategy can be hash based, range based, or list based. Each time a database operation is required, the application needs to determine which shard it must connect to.

A sharding key provides the partitioning key that determines in which shard a row of data is stored. A table can be partitioned using a sharding key.

A super sharding key is a collection of shard chunks, where only those chunks, which have a specific value of the super shard key identifier, are stored. A super sharding key is used for distributing data across database groups. Specifying super sharding keys are a way through which user-controlled data partitioning is possible.

### ODP.NET Sharding

Starting from version 12.2, ODP.NET and Oracle Database both support sharding.

**Note:**

ODP.NET, Managed Driver and ODP.NET Core do not support sharding.

ODP.NET applications must provide the sharding key and super sharding key information before opening the database connection for single shard queries. These sharding values cannot be set or changed after opening the connection. If any of the shard key values need to be modified, a new connection must be created with the new values and then opened.

If shard keys are set after the connection has been opened, the ODP.NET connection will not use these new shard key values until after the next `OracleConnection.Open()` call.

The `OracleShardingKey` object stores one or more key values. Multiple keys can be set to create a composite key. ODP.NET recognizes the sharding key(s) specified and connects to the correct shard and chunk.

Sharding is supported with or without connection pooling. The ODP.NET connection pool maintains connections to different shards and chunks of the sharded GDS database within the same shared pool.

The shard key (`SHARD_KEY`) and super sharding key (`GROUP_KEY`) can be specified in the TNS connect descriptor, rather than in the application code. The .NET developer then chooses the connect descriptor applicable to the shard that the application will use.

The data distribution across the shards and chunks in the database is transparent to the end user. ODP.NET minimizes the end user impact of chunk resharding within GDS.

To perform cross-shard queries, no ODP.NET shard APIs are used. Instead, applications connect to the GDS catalog service, allowing access to all the sharded databases. The SQL query is specifically constructed to iterate over all the necessary shards. For example, the non-shard database query `select count(*) from employees` is equivalent to the cross- shard query `select sum(c) from (Iterator(select count(*) c from employees(i))`.

#### ODP.NET Single Shard Query Example

    using System;
    using Oracle.DataAccess.Client;

    class Sharding
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection("user id=hr;password=hr;Data Source=orcl;");
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

**See Also:**

- [OracleShardingKey Class](OracleShardingKeyClass.md)

- [SetShardingKey(OracleShardingKey, OracleShardingKey)](ConnectionSetShardingKey.md)
