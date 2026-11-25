The `OracleRowsCopiedEventArgs` class represents the set of arguments passed as part of event data for the `OracleRowsCopied` event.

### Class Inheritance

`System.Object`

`  System.EventArgs`

`    System.OracleRowsCopiedEventArgs`

### Declaration

    // C#
    public class OracleRowsCopiedEventArgs : EventArgs

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

Each time the number of rows represented by the `OracleBulkCopy.NotifyAfter` property is processed, the `OracleBulkCopy.OracleRowsCopied` event is raised, providing an `OracleRowsCopiedEventArgs` object that stores the event data.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleRowsCopiedEventArgs Members](OracleRowsCopiedEventArgsMembers.md)

- [OracleRowsCopiedEventArgs Constructors](OracleRowsCopiedEventArgsConstructors.md)

- [OracleRowsCopiedEventArgs Properties](OracleRowsCopiedEventArgsProperties.md)
