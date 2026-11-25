`OracleConnection` public methods are listed in Table 6-48.

Table 6-48 OracleConnection Public Methods

| Public Method                                                                       | Description                                                                                                                                                     |
|:------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [BeginTransaction](ConnectionBeginTransactionOverloads.md)                          | Begins a local transaction (Overloaded)<br>Not supported in a .NET stored procedure for context connection                                                      |
| [ChangeDatabase](ConnectionChangeDatabase.md)                                       | Not Supported                                                                                                                                                   |
| [Clone](ConnectionClone.md)                                                         | Creates a copy of an `OracleConnection` object<br>Not supported in a .NET stored procedure                                                                      |
| [Close](ConnectionClose.md)                                                         | Closes the database connection                                                                                                                                  |
| [CreateCommand](ConnectionCreateCommand.md)                                         | Creates and returns an `OracleCommand` object associated with the `OracleConnection` object                                                                     |
| `CreateObjRef`                                                                      | Inherited from `System.MarshalByRefObject`                                                                                                                      |
| `Dispose`                                                                           | Inherited from `System.ComponentModel.Component`                                                                                                                |
| [EnlistDistributedTransaction](ConnectionEnlistDistributedTransaction.md)           | Enables applications to explicitly enlist in a specified distributed transaction<br>Not supported in a .NET stored procedure and ODP.NET Core                   |
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

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
