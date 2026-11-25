The `OracleConnectionOpenEventArgs` class provides connection information for the `OracleConnection.Open()` method. When a connection is opened, the callback registered using `ConnectionOpen` is triggered along with the `OracleConnectionOpenEventArgs` object.

### Class Inheritance

`System.Object`

`  System.EventArgs`

`    Oracle.DataAccess.Client.OracleConnectionOpenEventArgs`

### Declaration

    // C#
    public sealed class OracleConnectionOpenEventArgs

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnectionOpenEventArgs Members](ConnectionOpenEventArgsMembers.md)

- [OracleConnectionOpenEventArgs Properties](ConnectionOpenEventArgsProperties.md)
