### Example

The following code snippet shows how to use UCP sharding APIs:

Example 11-3 UCP Sharding Example

          PoolDataSource pds = new PoolDataSourceImpl();
          pds.setURL(url);
          pds.setUser("system");
          pds.setPassword("manager");
          pds.setConnectionFactoryClassName("oracle.jdbc.pool.OracleDataSource");

          OracleShardingKey employeeNamekey =
              pds.createShardingKeyBuilder()
                 .subkey("Mary", JDBCType.VARCHAR)  // First Name
                 .subkey("Claire", JDBCType.VARCHAR)  // Last Name
                 .build();

          OracleShardingKey locationKey = pds.createShardingKeyBuilder()
                                             .subkey("US", JDBCType.VARCHAR)//Location
                                             .build();

           OracleConnection connection = pds.createConnectionBuilder()
                                           .shardingKey(employeeNamekey)
                                           .superShardingKey(locationKey)
                                           .build();
