The `OracleHAEventArgs` class provides event data for the `OracleConnection.HAEvent` event.

### Class Inheritance

`  System.Object`

`    System.EventArgs`

`      Oracle.DataAccess.Client.OracleHAEventArgs`

### Declaration

    // C#
    public sealed class OracleHAEventArgs

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

When any HA event occurs for a service, service member, host, node, or instance that an `OracleConnection` object is set to with `"ha events=true"`, the `OracleConnection.HAEvent` is triggered and passes an instance of `OracleHAEventArgs` to all the delegates that have registered with the event.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleHAEventArgs Members](HAEventArgsMembers.md)

- [OracleHAEventArgs Properties](HAEventArgsProperties.md)

- "[OracleConnection Class](OracleConnectionClass.md)"

- "[HAEvent](ConnectionHAEvent.md)"
