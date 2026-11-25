`OracleDRCPPurity` enumerated values specify the session purity.

Table 6-178 lists all the `OracleDRCPPurity` enumeration values with a description of each enumerated value.

Table 6-178 OracleDRCPPurity Enumeration Values

| Member Name | Description                                                                            |
|:------------|:---------------------------------------------------------------------------------------|
| `New`       | The application requires a session without any previously set session state.           |
| `Pooled`    | An application can reuse a pooled session (i.e. the session can have been used before) |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[OracleConnection Class](OracleConnectionClass.md)"

- [DRCPPurity](ConnectionDRCPPurity.md)
