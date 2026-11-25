`OracleConnection` members are listed in the following tables.

### OracleConnection Constructors

`OracleConnection` constructors are listed in Table 6-38.

Table 6-38 OracleConnection Constructors

| Constructor                                         | Description                                                              |
|:----------------------------------------------------|:-------------------------------------------------------------------------|
| [OracleConnection Constructors](ConnectionCtors.md) | Instantiates a new instance of the `OracleConnection` class (Overloaded) |

### OracleConnection Static Properties

The `OracleConnection` static property is listed in Table 6-40.

Table 6-39 OracleConnection Static Property

| Property                                | Description                                                                    |
|:----------------------------------------|:-------------------------------------------------------------------------------|
| [IsAvailable](ConnectionIsAvailable.md) | Indicates whether or not the implicit database connection is available for use |

### OracleConnection Static Methods

The `OracleConnection` static methods are listed in Table 6-40.

Table 6-40 OracleConnection Static Methods

| Method                                      | Description                                                                                                                           |
|:--------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|
| `Equals`                                    | Inherited from `System.``Object` (Overloaded)                                                                                         |
| [ClearPool](ConnectionClearPoolCtor1.md)    | Clears the connection pool that is associated with the provided `OracleConnection` object<br>Not supported in a .NET stored procedure |
| [ClearAllPools](ConnectionClearAllPools.md) | Clears all connections from all the connection pools<br>Not supported in a .NET stored procedure                                      |

### OracleConnection Properties

`OracleConnection` properties are listed in Table 6-41.

Table 6-41 OracleConnection Properties

| Property                                                | Description                                                                                                                                                                                                                  |
|:--------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [ActionName](ConnectionActionName.md)                   | Specifies the action name for the connection                                                                                                                                                                                 |
| [ClientId](ConnectionClientId.md)                       | Specifies the client identifier for the connection                                                                                                                                                                           |
| [ClientInfo](ConnectionClientInfo.md)                   | Specifies the client information for the connection                                                                                                                                                                          |
| [ConnectionString](ConnectionConnectionString.md)       | Specifies connection information used to connect to an Oracle database                                                                                                                                                       |
| [ConnectionTimeout](ConnectionConnectionTimeout.md)     | Indicates the maximum amount of time that the `Open` method can take to obtain a pooled connection before the request is terminated                                                                                          |
| [ConnectionType](ConnectionConnectionType.md)           | Determines whether a particular connection object is associated with a TimesTen database connection, an Oracle database connection, or no physical connection<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core   |
| `Container`                                             | Inherited from `System.ComponentModel.Component`                                                                                                                                                                             |
| [Credential](ConnectionCredential.md)                   | Used to get or set an `OracleCredential` object on the connection                                                                                                                                                            |
| [Database](ConnectionDatabase.md)                       | Not Supported                                                                                                                                                                                                                |
| [DatabaseDomainName](ConnectionDatabaseDomainName.md)   | Specifies the name of the database domain to which the connection is set                                                                                                                                                     |
| [DatabaseEditionName](ConnectionDatabaseEditionName.md) | Sets or gets the edition name for the `OracleConnection` object                                                                                                                                                              |
| [DatabaseName](ConnectionDatabaseName.md)               | Specifies the name of the database to which the connection is set                                                                                                                                                            |
| [DataSource](ConnectionDatasource.md)                   | Specifies the Oracle Net Services Name, Connect Descriptor, or an easy connect naming that identifies the database to which to connect                                                                                       |
| [DRCPConnectionClass](ConnectionDRCPConnectionClass.md) | Specifies a logical name that identifies the DRCP connection pool that the ODP.NET connection will use                                                                                                                       |
| [DRCPPurity](ConnectionDRCPPurity.md)                   | Specifies whether an application can reuse a pooled session (`Pooled`) or must use a new session (`New`)                                                                                                                     |
| [HostName](ConnectionHostName.md)                       | Specifies the name of the host to which the connection is set                                                                                                                                                                |
| [InstanceName](ConnectionInstanceName.md)               | Specifies the name of the instance to which the connection is set                                                                                                                                                            |
| [ModuleName](ConnectionModuleName.md)                   | Specifies the module name for the connection                                                                                                                                                                                 |
| [PDBName](ConnectionPDBName.md)                         | Used to set and get the name of the pluggable database to which the session is connected to                                                                                                                                  |
| [ServerVersion](ConnectionServerVersion.md)             | Specifies the version number of the Oracle database to which the `OracleConnection` has established a connection                                                                                                             |
| [ServiceName](ConnectionServiceName.md)                 | Specifies the name of the service to which the connection is set                                                                                                                                                             |
| `Site`                                                  | Inherited from `System.ComponentModel.Component`                                                                                                                                                                             |
| [State](ConnectionState.md)                             | Specifies the current state of the connection                                                                                                                                                                                |
| [StatementCacheSize](ConnectionStatementCacheSize.md)   | Specifies the current size of the statement cache associated with this connection                                                                                                                                            |
| [SwitchedConnection](ConnectionSwitchedConnection.md)   | If the returned pooled connection changed its service name (`ServiceName`) or pluggable database (`PDBName`) in order to connect to the desired pluggable database, then this property will consider the connection switched |

### OracleConnection Public Methods

`OracleConnection` public methods are listed in Table 6-42.

Table 6-42 OracleConnection Public Methods

| Public Method                                                                       | Description                                                                                                                                                     |
|:------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [BeginTransaction](ConnectionBeginTransactionOverloads.md)                          | Begins a local transaction (Overloaded)<br>Not supported in a .NET stored procedure for context connection                                                      |
| [ChangeDatabase](ConnectionChangeDatabase.md)                                       | Not Supported                                                                                                                                                   |
| [Clone](ConnectionClone.md)                                                         | Creates a copy of an `OracleConnection` object<br>Not supported in a .NET stored procedure                                                                      |
| [Close](ConnectionClose.md)                                                         | Closes the database connection                                                                                                                                  |
| [CreateCommand](ConnectionCreateCommand.md)                                         | Creates and returns an `OracleCommand` object associated with the `OracleConnection` object                                                                     |
| `CreateObjRef`                                                                      | Inherited from `System.MarshalByRefObject`                                                                                                                      |
| `Dispose`                                                                           | Inherited from `System.ComponentModel.Component`                                                                                                                |
| [EnlistDistributedTransaction](ConnectionEnlistDistributedTransaction.md)           | Enables applications to explicitly enlist in a specified distributed transaction<br>Not supported in a .NET stored procedure and .NET Core                      |
| [EnlistTransaction](ConnectionEnlistTransaction.md)                                 | Enables applications to enlist in a specified distributed transaction<br>Not supported in a .NET stored procedure                                               |
| `Equals`                                                                            | Inherited from `System.Object` (Overloaded)                                                                                                                     |
| [FlushCache](ConnectionFlushCache.md)                                               | Flushes all updates and deletes made through `REF` objects retrieved using this connection<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core         |
| `GetHashCode`                                                                       | Inherited from `System.``Object`                                                                                                                                |
| `GetLifetimeService`                                                                | Inherited from `System.MarshalByRefObject`                                                                                                                      |
| [GetSchema](ConnectionGetSchemaOverloads.md)                                        | Returns schema information for the data source of the `OracleConnection`                                                                                        |
| [GetSessionInfo](ConnectionGetSessionInfoOverloads.md)                              | Returns or refreshes the property values of the `OracleGlobalization` object that represents the globalization settings of the session (Overloaded)             |
| `GetType`                                                                           | Inherited from `System.Object`                                                                                                                                  |
| `InitializeLifetimeService`                                                         | Inherited from `System.MarshalByRefObject`                                                                                                                      |
| [Open](ConnectionOpen.md)                                                           | Opens a database connection with the property settings specified by the `ConnectionString`                                                                      |
| [OpenWithNewPassword](ConnectionOpenWithNewPassword.md)                             | Opens a new connection with the new password (Overloaded)<br>Not supported in a .NET stored procedure for context connection                                    |
| [PurgeStatementCache](ConnectionPurgeStatementCache.md)                             | Flushes the Statement Cache by closing all open cursors on the database, when statement caching is enabled                                                      |
| [SetSessionInfo](ConnectionSetSessionInfo.md)                                       | Alters the session's globalization settings with the property values provided by the `OracleGlobalization` object                                               |
| [SetShardingKey(OracleShardingKey, OracleShardingKey)](ConnectionSetShardingKey.md) | Enables applications to set the sharding key and super sharding key before requesting a connection<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core |
| `ToString`                                                                          | Inherited from `System.Object`                                                                                                                                  |

### OracleConnection Events

`OracleConnection` events are listed in Table 6-43.

Table 6-43 OracleConnection Events

| Event Name                                    | Description                                                                                                                                                        |
|:----------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [ConnectionOpen](ConnectionConnectionOpen.md) | This event is triggered upon the `OracleConnection.Open()` method                                                                                                  |
| `Disposed`                                    | Inherited from `System.ComponentModel.Component`                                                                                                                   |
| [Failover](ConnectionFailover.md)             | An event that is triggered when an Oracle failover occurs<br>Not supported in a .NET stored procedure<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core |
| [HAEvent](ConnectionHAEvent.md)               | An event that is triggered when an HA event occurs                                                                                                                 |
| [InfoMessage](ConnectionInfoMessage.md)       | An event that is triggered for any message or warning sent by the database                                                                                         |
| [StateChange](ConnectionStateChange.md)       | An event that is triggered when the connection state changes                                                                                                       |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)
