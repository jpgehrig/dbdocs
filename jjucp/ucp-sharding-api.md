### The UCPConnection Builder Class

The `UCPConnectionBuilder` class is used for building connection objects with additional parameters other than the `username`, `password`, and `label`. To use the builder, you must call the corresponding builder method for each parameter that needs to be a part of the connection request, followed by a `build` method. The order in which the builder methods are called is not important. However, if the same builder attribute is applied more than once, then only the most recent value is considered while building the connection.

### Syntax

    public abstract class UCPConnectionBuilder<S> implements OracleConnectionBuilder<UCPConnectionBuilder<S>,S>

The `UCPConnectionBuilder` class also provides the `validate` method and several constructors for setting the data for a specific user.

Example 11-2 Creating the Connection Builder

    PoolDataSource pds = PoolDataSourceFactory.getPoolDataSource();
    ..//set the required properties on the datasource
    ShardingKey superShardingKey = ds.createShardingKeyBuilder()
                                                                        .subkey("EASTERN_REGION", JDBCType.VARCHAR)
                                                                        .build();
    ShardingKey superShardingKey = ds.createShardingKeyBuilder()
                                                                        .subkey("PITTSBURGH_BRANCH", JDBCType.VARCHAR)
                                                                        .build();
    Connection conn = pds.createConnectionBuilder()
                                .shardingKey(superShardingKey)
                                .superShardingKey(superShardingKey)
                                .build();

### New Methods in PoolDataSource Interface

The following methods have been introduced in the `oracle.ucp.jdbc.PoolDataSource` interface:

    /**
     * Creates a new UCPConnectionBuilder instance.
     *
     * @param <S>
     * Connection type for this ConnectionBuilder
     * @param <B>
     * Builder type to use
     * @return The OracleConnectionBuilder instance that was created
     */
     public UCPConnectionBuilder createConnectionBuilder();

    /**
     * Creates a new OracleShardingKeyBuilder instance
     *
     * @return The OracleShardingKeyBuilder instance that was created
     */
     public default OracleShardingKeyBuilder createShardingKeyBuilder() {
     return new OracleShardingKeyBuilderImpl();
     }

### New Method in PoolXADataSource Interface

The following method has been introduced in the `oracle.ucp.admin.UniversalConnectionPoolManager` interface:

    /**
     * Creates a new XAConnectionBuilder instance.
     *
     * @return The XAConnectionBuilder instance that was created
     */
     public UCPXAConnectionBuilder createXAConnectionBuilder();
