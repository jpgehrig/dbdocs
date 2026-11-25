The `OracleHAEventStatus` enumeration indicates the status of the HA event source.

Table 8-4 lists all the `OracleHAEventStatus` enumeration values with a description of each enumerated value.

Table 8-4 OracleHAEventStatus Enumeration Values

| Member Name | Description                         |
|:------------|:------------------------------------|
| `Up`        | The source of the HA Event is up.   |
| `Down`      | The source of the HA Event is down. |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleHAEventArgs Class](OracleHAEventArgsClass.md)

- "[Status](HAEventArgsStatus.md)"
