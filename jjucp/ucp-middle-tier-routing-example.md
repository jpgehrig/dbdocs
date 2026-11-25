The following example explains the usage of the middle-tier routing API of UCP.

Example 11-4 Example of Middle-Tier Routing Using UCP

    import java.sql.SQLException;
    import java.util.Properties;
    import java.util.Random;
    import java.util.Set;

    import oracle.jdbc.OracleShardingKey;
    import oracle.jdbc.OracleType;
    import oracle.ucp.UniversalConnectionPoolException;
    import oracle.ucp.routing.ShardInfo;
    import oracle.ucp.routing.oracle.OracleShardRoutingCache;

    /**
     * The code example illustrates the usage of the middle-tier routing feature of UCP.
     * The API accepts sharding key as input and returns the set of ShardInfo
     * instances mapped to the sharding key. The ShardInfo instance encapsulates
     * unique shard name and priority. The unique shard name then can be mapped
     * to a middle-tier server that connects to a specific shard.
     *
     */
    public class MidtierShardingExample {

      private static String user = "testuser1";
      private static String password = "testuser1";

      // catalog DB URL
      private static String url = "jdbc:oracle:thin:@//hostName:1521/catalogServiceName";
      private static String region = "regionName";

      public static void main(String args[]) throws Exception {
        testMidTierRouting();
      }

      static void testMidTierRouting() throws UniversalConnectionPoolException,
          SQLException {

        Properties dbConnectProperties = new Properties();
        dbConnectProperties.setProperty(OracleShardRoutingCache.USER, user);
        dbConnectProperties.setProperty(OracleShardRoutingCache.PASSWORD, password);
        // Mid-tier routing API accepts catalog DB URL
        dbConnectProperties.setProperty(OracleShardRoutingCache.URL, url);

        // Region name is required to get the ONS config string
        dbConnectProperties.setProperty(OracleShardRoutingCache.REGION, region);

        OracleShardRoutingCache routingCache = new OracleShardRoutingCache(
            dbConnectProperties);

        final int COUNT = 10;
        Random random = new Random();

        for (int i = 0; i < COUNT; i++) {
          int key = random.nextInt();
          OracleShardingKey shardKey = routingCache.getShardingKeyBuilder()
              .subkey(key, OracleType.NUMBER).build();
          OracleShardingKey superShardKey = null;

          Set<ShardInfo> shardInfoSet = routingCache.getShardInfoForKey(shardKey,
              superShardKey);

          for (ShardInfo shardInfo : shardInfoSet) {
            System.out.println("Sharding Key=" + key + " Shard Name="
                + shardInfo.getName() + " Priority=" + shardInfo.getPriority());
          }
        }

      }
    }
