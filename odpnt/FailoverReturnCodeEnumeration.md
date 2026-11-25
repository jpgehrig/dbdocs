`FailoverReturnCode` enumerated values are passed back by the application to the ODP.NET provider to request a retry in case of a failover error, or to continue in case of a successful failover.

Table 11-8 lists the `FailoverReturnCode` enumeration values with a description of each enumerated value.

Table 11-8 FailoverReturnCode Enumeration Values

| Member Names                 | Description                                                                                   |
|:-----------------------------|:----------------------------------------------------------------------------------------------|
| `FailoverReturnCode.Retry`   | Requests ODP.NET to retry failover in case `FailoverEvent.Error` is passed to the application |
| `FailoverReturnCode.Success` | Requests ODP.NET to proceed so that the application receive more notifications, if any        |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

**See Also:**

- [FailoverEvent Enumeration](FailoverEventEnumeration.md)

- "[OracleFailoverEventArgs Class](OracleFailoverEventArgsClass.md)"

- "[FailoverEvent](FailoverEventArgsFailoverEvent.md)"

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/workload-management-with-dynamic-database-services.md)

- [Oracle Database Net Services Reference](../netrf/index.md)
