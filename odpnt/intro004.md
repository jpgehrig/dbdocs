ODP.NET, Managed Driver, ODP.NET, Unmanaged Driver, and ODP.NET Core have a number of configuration setting differences.

Table 1-8 Application Programming Interfaces not supported in ODP.NET, Managed Driver and ODP.NET Core

| Namespace                         | Class/Enumeration/Interface                    | Unsupported Method/Property/Event                                                                                                       |
|:----------------------------------|:-----------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------|
| `Oracle.ManagedDataAccess.Client` | `FailoverEvent` enumeration                    | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `FailoverReturnCode` enumeration               | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `FailoverType` enumeration                     | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQAgent` class                          | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQDequeueuMode` enumeration             | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQDequeueOptions` class                 | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQEnqueueOptions` class                 | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQMessage` class                        | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQMessageAvailableEventArgs` class      | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQMessageAvailableEventHandler` class   | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQMessageDeliveryMode` enumeration      | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQMessageState` enumeration             | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQMessageType` enumeration              | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQNavigationMode` enumeration           | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQNotificationGroupingType` enumeration | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQNotificationType` enumeration         | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQQueue` class                          | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleAQVisibilityMode` enumeration           | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleBulkCopy` class                         | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleBulkCopyColumnMapping` class            | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleBulkCopyColumnMappingCollection` class  | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleBulkCopyOptions` class                  | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleClientFactory` class                    | Not supported in ODP.NET Core only                                                                                                      |
| `Oracle.ManagedDataAccess.Client` | `OracleCommand` class                          | `ArrayBindRowsAffected` property                                                                                                        |
| `Oracle.ManagedDataAccess.Client` | `OracleCommand` class                          | `ImplicitRefCursors` property                                                                                                           |
| `Oracle.ManagedDataAccess.Client` | `OracleConnection` class                       | `FlushCache()` method                                                                                                                   |
| `Oracle.ManagedDataAccess.Client` | `OracleConnection` class                       | `Failover` event                                                                                                                        |
| `Oracle.ManagedDataAccess.Client` | `OracleConnection` class                       | `ConnectionType` property                                                                                                               |
| `Oracle.ManagedDataAccess.Client` | `OracleConnection` class                       | `SetShardingKey` method                                                                                                                 |
| `Oracle.ManagedDataAccess.Client` | `OracleConnection` class                       | `EnlistDistributedTransaction(ITransaction)` method<br>Not supported in ODP.NET Core only                                               |
| `Oracle.ManagedDataAccess.Client` | `OracleConnectionType` enumeration             | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleDBShutdownMode` enumeration             | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleDBStartupMode` enumeration              | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleDataReader` class                       | `GetOracleRef()` method                                                                                                                 |
| `Oracle.ManagedDataAccess.Client` | `OracleDataReader` class                       | `GetOracleBlobForUpdate()` method<br>If the method is called, then a `NotSupportedException` is thrown.                                 |
| `Oracle.ManagedDataAccess.Client` | `OracleDataReader` class                       | `GetOracleClobForUpdate()` method<br>If the method is called, then a `NotSupportedException` is thrown.                                 |
| `Oracle.ManagedDataAccess.Client` | `OracleDataReader` class                       | `IsAutoIncrement` and `IdentityType` properties of the `GetSchemaTable`                                                                 |
| `Oracle.ManagedDataAccess.Client` | `OracleDataAdapter` class                      | `IdentityInsert` property                                                                                                               |
| `Oracle.ManagedDataAccess.Client` | `OracleDataAdapter` class                      | `IdentityUpdate` property                                                                                                               |
| `Oracle.ManagedDataAccess.Client` | `OracleDataAdapter` class                      | `SafeMapping` property                                                                                                                  |
| `Oracle.ManagedDataAccess.Client` | `OracleDatabase` class                         | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleDbType` enumeration                     | `Array`                                                                                                                                 |
| `Oracle.ManagedDataAccess.Client` | `OracleDbType` enumeration                     | `Object`                                                                                                                                |
| `Oracle.ManagedDataAccess.Client` | `OracleDbType` enumeration                     | `Ref`                                                                                                                                   |
| `Oracle.ManagedDataAccess.Client` | `OracleException` class                        | `IsRecoverable` property                                                                                                                |
| `Oracle.ManagedDataAccess.Client` | `OracleFailoverEventArgs` class                | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleFailoverEventHandler` class             | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleGlobalization` class                    | `ClientCharacterSet` property                                                                                                           |
| `Oracle.ManagedDataAccess.Client` | `OracleGlobalization` class                    | `GetClientInfo()` method                                                                                                                |
| `Oracle.ManagedDataAccess.Client` | `OracleGlobalization` class                    | `GetThreadInfo()` method                                                                                                                |
| `Oracle.ManagedDataAccess.Client` | `OracleGlobalization` class                    | `SetThreadInfo()` method                                                                                                                |
| `Oracle.ManagedDataAccess.Client` | `OracleIdentityType` enumeration               | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleNotificationRequest` class              | `GroupingInterval` property                                                                                                             |
| `Oracle.ManagedDataAccess.Client` | `OracleNotificationRequest` class              | `GroupingNotificationEnabled` property                                                                                                  |
| `Oracle.ManagedDataAccess.Client` | `OracleNotificationRequest` class              | `GroupingType` property                                                                                                                 |
| `Oracle.ManagedDataAccess.Client` | `OraclePermission` class                       | Not supported in ODP.NET Core only                                                                                                      |
| `Oracle.ManagedDataAccess.Client` | `OraclePermissionAttribute` class              | Not supported in ODP.NET Core only                                                                                                      |
| `Oracle.ManagedDataAccess.Client` | `OracleRowsCopiedEventArgs` class              | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Client` | `OracleRowsCopiedEventHandler` class           | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Types`  | `IOracleArrayTypeFactory` interface            | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Types`  | `IOracleCustomType` interface                  | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Types`  | `IOracleCustomTypeFactory` interface           | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Types`  | `OracleArrayMappingAttribute` class            | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Types`  | `OracleCustomTypeMappingAttribute` class       | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Types`  | `OracleObjectMappingAttribute` class           | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Types`  | `OracleRef` class                              | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Types`  | `OracleShardingKey` class                      | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Types`  | `OracleTimestampTZ` structure                  | `OracleTimeStampTZ(DateTime dt, string timeZone)` constructor. This constructor is supported but the `timeZone` must be an hour offset. |
| `Oracle.ManagedDataAccess.Types`  | `OracleUdt` class                              | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Types`  | `OracleUdtFetchOption` enumeration             | All                                                                                                                                     |
| `Oracle.ManagedDataAccess.Types`  | `OracleUdtStatus` enumeration                  | All                                                                                                                                     |

ODP.NET Core supports the `OracleConfiguration` , `OracleDataSourceCollection`, and `OracleOnsServerCollection` classes, which are not present in managed nor unmanaged ODP.NET.

**See Also:**

[Oracle Data Provider for .NET, Managed Driver Configuration](InstallManagedConfig.md) and [Configuration differences between ODP.NET, Managed Driver and ODP.NET, Unmanaged Driver](InstallConfigDiff.md) for more information about ODP.NET, Managed Driver .NET configuration settings.

[Distributed Transactions](InstallDistributedTransaction.md) for information about distributed transaction setup difference.

[Oracle Data Provider for .NET Core Configuration](InstallCoreConfiguration.md) for more information about configuring ODP.NET Core.
