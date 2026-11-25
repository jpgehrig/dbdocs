`FailoverType` enumerated values are used to indicate the type of failover event that was raised.

Table 11-9 lists all the `FailoverType` enumeration values with a description of each enumerated value.

Table 11-9 FailoverType Enumeration Values

| Member Names           | Description                                                        |
|:-----------------------|:-------------------------------------------------------------------|
| `FailoverType.Session` | Indicates that the user has requested only session failover.       |
| `FailoverType.Select`  | Indicates that the user has requested select and session failover. |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

**See Also:**

- [FailoverEvent Enumeration](FailoverEventEnumeration.md)

- "[OracleFailoverEventArgs Class](OracleFailoverEventArgsClass.md)"

- "[FailoverType](FailoverEventArgsFailoverType.md)"

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/workload-management-with-dynamic-database-services.md)

- [Oracle Database Net Services Reference](../netrf/index.md)
