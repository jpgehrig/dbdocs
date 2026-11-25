`OracleConnectionStringBuilder` members are listed in the following tables.

### OracleConnectionStringBuilder Constructors

`OracleConnectionStringBuilder` constructors are listed in Table 6-52.

Table 6-52 OracleConnectionStringBuilder Constructors

| Constructor                                                                          | Description                                                                       |
|:-------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------|
| [OracleConnectionStringBuilder Constructors](ConnectionStringBuilderConstructors.md) | Instantiates a new instance of `OracleConnectionStringBuilder` class (Overloaded) |

### OracleConnectionStringBuilder Public Properties

`OracleConnectionStringBuilder` instance properties are listed in Table 6-53.

Table 6-53 OracleConnectionStringBuilder Public Properties

| Properties                                                               | Description                                                                                                                                                                                                 |
|:-------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `BrowsableConnectionString`                                              | Inherited from `System.Data.Common. DbConnectionStringBuilder`                                                                                                                                              |
| [ConnectionLifeTime](ConnectionStringBuilderConnectionLifeTime.md)       | Specifies the value corresponding to the `Connection` `Lifetime` attribute in the `ConnectionString` property                                                                                               |
| `ConnectionString`                                                       | Inherited from `System.Data.Common. DbConnectionStringBuilder`                                                                                                                                              |
| [ConnectionTimeout](ConnectionStringBuilderConnectionTimeout.md)         | Specifies the value corresponding to the `Connection` `Timeout` attribute in the `ConnectionString` property                                                                                                |
| [ContextConnection](ConnectionStringBuilderContextConnection.md)         | Specifies the value corresponding to the `Context` `Connection` attribute in the `ConnectionString` property                                                                                                |
| `Count`                                                                  | Inherited from `System.Data.Common.DbConnectionStringBuilder`                                                                                                                                               |
| [DataSource](ConnectionStringBuilderDataSource.md)                       | Specifies the value corresponding to the `Data` `Source` attribute in the `ConnectionString` property                                                                                                       |
| [DBAPrivilege](ConnectionStringBuilderDBAPrivilege.md)                   | Specifies the value corresponding to the `DBA` `Privilege` attribute in the `ConnectionString` property                                                                                                     |
| [DecrPoolSize](ConnectionStringBuilderDecrPoolSize.md)                   | Specifies the value corresponding to the `Decr` `Pool` `Size` attribute in the `ConnectionString` property                                                                                                  |
| [Enlist](ConnectionStringBuilderEnlist.md)                               | Specifies the value corresponding to the `Enlist` attribute in the `ConnectionString` property                                                                                                              |
| [HAEvents](ConnectionStringBuilderHAEvents.md)                           | Specifies the value corresponding to the `HA` `Events` attribute in the `ConnectionString` property                                                                                                         |
| [IncrPoolSize](ConnectionStringBuilderIncrPoolSize.md)                   | Specifies the value corresponding to the `Incr` `Pool` `Size` attribute in the `ConnectionString` property                                                                                                  |
| [IsFixedSize](ConnectionStringBuilderIsFixedSize.md)                     | Indicates whether or not the Connection String Builder has a fixed size                                                                                                                                     |
| `IsReadOnly`                                                             | Inherited from `System.Data.Common.DbConnectionStringBuilder`                                                                                                                                               |
| [Item](ConnectionStringBuilderItem.md)                                   | Specifies the value associated with the specified attribute                                                                                                                                                 |
| [Keys](ConnectionStringBuilderKeys.md)                                   | Specifies a collection of attributes contained in the Connection String Builder                                                                                                                             |
| [LoadBalancing](ConnectionStringBuilderLoadBalancing.md)                 | Specifies the value corresponding to the `Load` `Balancing` attribute in the `ConnectionString` property                                                                                                    |
| [MaxPoolSize](ConnectionStringBuilderMaxPoolSize.md)                     | Specifies the value corresponding to the `Max` `Pool` `Size` attribute in the `ConnectionString` property                                                                                                   |
| [MetadataPooling](ConnectionStringBuilderMetadataPooling.md)             | Specifies the value that corresponds to the `Metadata` `Pooling` attribute in the `ConnectionString` property                                                                                               |
| [MinPoolSize](ConnectionStringBuilderMinPoolSize.md)                     | Specifies the value corresponding to the `Min` `Pool` `Size` attribute in the `ConnectionString` property                                                                                                   |
| [Password](ConnectionStringBuilderPassword.md)                           | Specifies the value corresponding to the `Password` attribute in the `ConnectionString` property                                                                                                            |
| [PersistSecurityInfo](ConnectionStringBuilderPersistSecurityInfo.md)     | Specifies the value corresponding to the `Persist` `Security` `Info` attribute in the `ConnectionString` property                                                                                           |
| [Pooling](ConnectionStringBuilderPooling.md)                             | Specifies the value corresponding to the `Pooling` attribute in the `ConnectionString` property                                                                                                             |
| [PromotableTransaction](ConnectionStringBuilderPromotableTransaction.md) | Specifies the value corresponding to the `PromotableTransaction` attribute in the `ConnectionString` property<br>This property has been deprecated in 12.2.0.1. It will be desupported in a future release. |
| [ProxyPassword](ConnectionStringBuilderProxyPassword.md)                 | Specifies the value corresponding to the `Proxy` `User` `Id` attribute in the `ConnectionString` property                                                                                                   |
| [ProxyUserId](ConnectionStringBuilderProxyUserId.md)                     | Specifies the value corresponding to the `Proxy` `User` `Id` attribute in the `ConnectionString` property                                                                                                   |
| [SelfTuning](ConnectionStringBuilderSelfTuning.md)                       | Specifies the value corresponding to the `Self Tuning` attribute in the `ConnectionString` property                                                                                                         |
| [StatementCachePurge](ConnectionStringBuilderStatementCachePurge.md)     | Specifies the value corresponding to the `Statement` `Cache` `Purge` attribute in the `ConnectionString` property                                                                                           |
| [StatementCacheSize](ConnectionStringBuilderStatementCacheSize.md)       | Specifies the value corresponding to the `Statement` `Cache` `Size` attribute in the `ConnectionString` property                                                                                            |
| [UserID](ConnectionStringBuilderUserID.md)                               | Specifies the value corresponding to the `User` `Id` attribute in the `ConnectionString` property                                                                                                           |
| [ValidateConnection](ConnectionStringBuilderValidateConnection.md)       | Specifies the value corresponding to the `Validate` `Connection` attribute in the `ConnectionString` property                                                                                               |
| [Values](ConnectionStringBuilderValues.md)                               | Specifies a collection of values contained in the Connection String Builder                                                                                                                                 |

### OracleConnectionStringBuilder Public Methods

`OracleConnectionStringBuilder` instance methods are listed in Table 6-54.

Table 6-54 OracleConnectionStringBuilder Public Methods

| Methods                                              | Description                                                                                    |
|:-----------------------------------------------------|:-----------------------------------------------------------------------------------------------|
| `Add`                                                | Inherited from `System.Data.Common.DbConnectionStringBuilder`                                  |
| [Clear](ConnectionStringBuilderClear.md)             | Clears the connection string contents                                                          |
| [ContainsKey](ConnectionStringBuilderContainsKey.md) | Indicates whether or not a specific attribute in the connection string is supported by ODP.NET |
| `EquivalentTo`                                       | Inherited from `System.Data.Common.DbConnectionStringBuilder`                                  |
| [Remove](ConnectionStringBuilderRemove.md)           | Removes the entry corresponding to the specified attribute from the connection string          |
| `ShouldSerialize`                                    | Inherited from `System.Data.Common.DbConnectionStringBuilder`                                  |
| `ToString`                                           | Inherited from `System.Data.Common.DbConnectionStringBuilder`                                  |
| [TryGetValue](ConnectionStringBuilderTryGetValue.md) | Returns the value corresponding to the supplied attribute, as an output parameter              |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnectionStringBuilder Class](OracleConnectionStringBuilderClass.md)
