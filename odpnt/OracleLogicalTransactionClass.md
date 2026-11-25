The `OracleLogicalTransaction` class provides detailed information about the logical transaction status. Applications can conclusively determine the outcome of the running transaction during the last database outage, then act accordingly to commit, complete, or rollback the transaction.

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    Oracle.DataAccess.Client.OracleLogicalTransaction`

### Declaration

    // C#
    public sealed class OracleLogicalTransaction

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleLogicalTransaction Members](LogicalTransactionMembers.md)

- [OracleLogicalTransaction Public Read-Only Properties](LogicalTransactionPublicProperties.md)

- [OracleLogicalTransaction Methods](LogicalTransactionMethods.md)
