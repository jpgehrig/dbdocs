`OracleConnectionType `enumerated values specify whether a particular connection object is associated with an Oracle database connection, a TimesTen database connection, or no physical connection at all.

Table 6-172 lists all the `OracleConnectionType` enumeration values with a description of each enumerated value.

Table 6-172 OracleConnectionType Enumeration Values

| Member Name | Description                                                           |
|:------------|:----------------------------------------------------------------------|
| `Undefined` | No connection is associated with the `OracleConnection` object.       |
| `Oracle`    | The `OracleConnection` object is associated with an Oracle database.  |
| `TimesTen`  | The `OracleConnection` object is associated with a TimesTen database. |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[OracleConnection Class](OracleConnectionClass.md)"

- "[ConnectionType](ConnectionConnectionType.md)"
