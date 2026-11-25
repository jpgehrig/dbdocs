`FailoverEvent` enumerated values are used to specify the state of the failover.

Table 11-7 lists all the `FailoverEvent` enumeration values with a description of each enumerated value.

Table 11-7 FailoverEvent Enumeration Values

| Member Names            | Description                                                                                                                                                                                                                                                                                                                                                                                |
|:------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `FailoverEvent.Begin `  | Indicates that failover has detected a lost connection and that failover is starting.                                                                                                                                                                                                                                                                                                      |
| `FailoverEvent.End `    | Indicates successful completion of failover.                                                                                                                                                                                                                                                                                                                                               |
| `FailoverEvent.Abort `  | Indicates that failover was unsuccessful, and there is no option of retrying.                                                                                                                                                                                                                                                                                                              |
| `FailoverEvent.Error `  | Indicates that failover was unsuccessful, and it gives the application the opportunity to handle the error and retry failover. The application can retry failover by returning `FailoverReturnCode.Retry` for the event notification.                                                                                                                                                      |
| `FailoverEvent.Reauth ` | Indicates that a user handle has been reauthenticated. This applies to the situation where a client has multiple user sessions on a single server connection. During the initial failover, only the active user session is failed over. Other sessions are failed over when the application tries to use them. This is the value passed to the callback during these subsequent failovers. |

No significant database operation should occur immediately after a `FailoverEvent.Begin` event. SQL and major database operations should wait until the `FailoverEvent.End` event. `FailoverEvent.Begin` is primarily used to reject failover or to trace it. `FailoverEvent.Begin` can also be used for non-database application operations, such as informing the end user a failover is in progress and to wait until it completes before proceeding. Transactions can be used in the `FailoverEvent.End` callback phase, such as to file fault tickets or audit. These transactions must be committed before the callback completes.

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

**See Also:**

- FailoverEvent Enumeration

- "[OracleFailoverEventArgs Class](OracleFailoverEventArgsClass.md)"

- "[FailoverEvent](FailoverEventArgsFailoverEvent.md)"

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/ensuring-application-continuity.md)

- [Oracle Database Net Services Reference](../netrf/index.md)
