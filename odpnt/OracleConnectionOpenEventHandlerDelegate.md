The `OracleConnectionOpenEventHandler` delegate represents the signature of the method that handles `OracleConnection.ConnectionOpen` event.

### Declaration

    // C#
    public delegate void OracleConnectionOpenEventHandler (OracleConnectionOpenEventArgs eventArgs);

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Parameters

- `eventArgs `

  The `OracleConnectionOpenEventArgs` object that contains the connection data.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [ConnectionOpen](ConnectionConnectionOpen.md)
