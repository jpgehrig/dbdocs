The `OracleRowUpdatingEventArgs` class provides event data for the `OracleDataAdapter.RowUpdating` event.

### Class Inheritance

`System.Object`

`  System.EventArgs`

`    System.RowUpdatingEventArgs`

`      System.OracleRowUpdatingEventArgs`

### Declaration

    // C#
    public sealed class OracleRowUpdatingEventArgs : RowUpdatingEventArgs

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Example

The example for the `RowUpdated` event shows how to use `OracleRowUpdatingEventArgs`. See `RowUpdated` event "[Example](DataAdapterRowUpdated.md)".

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleRowUpdatingEventArgs Members](OracleRowUpdatingEventArgsmembers.md)

- [OracleRowUpdatingEventArgs Constructor](RowUpdatingEventArgsCtor.md)

- [OracleRowUpdatingEventArgs Static Methods](RowUpdatingEventArgsStaticMethods.md)

- [OracleRowUpdatingEventArgs Properties](RowUpdatingEventArgsProperties.md)

- [OracleRowUpdatingEventArgs Public Methods](RowUpdatingEventArgsPublicMethods.md)

- "[OracleDataAdapter Class](OracleDataAdapterClass.md)"
