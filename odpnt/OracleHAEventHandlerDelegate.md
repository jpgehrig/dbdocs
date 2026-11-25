The `OracleHAEventHandler` delegate represents the signature of the method that handles the `OracleConnection.HAEvent` event.

### Declaration

    // C#
    public delegate void OracleHAEventHandler(OracleHAEventArgs eventArgs);

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Parameters

- `sender`

  The source of the event.

- `EventArgs`

  The `OracleHAEventArgs` object that contains the event data.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleHAEventArgs Class](OracleHAEventArgsClass.md)

- "[HAEvent](ConnectionHAEvent.md)"
