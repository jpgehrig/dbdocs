### The OracleShardRoutingCache Class

This class extends the internal shard routing cache of UCP and makes the basic routing cache feature available to the WebLogic Server or middle-tier routers or load balancers.

`public class OracleShardRoutingCache extends ShardRoutingCache`

This class provides the `OracleShardRoutingCache(Properties dataSourceProps)` and `Set<ShardInfo> getShardInfoForKey(OracleShardingKey key, OracleShardingKey superKey)` methods.

### The ShardInfo Interface

The `ShardInfo` interface instances encapsulate unique shard name and priority. The unique shard name can then be mapped to a middle-tier server that connects to a specific shard.
