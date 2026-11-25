`OracleConnection` events are listed in Table 6-49.

Table 6-49 OracleConnection Events

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

- [OracleConnection Members](ConnectionMembers.md)
