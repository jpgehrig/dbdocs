The `OracleTruncateException` class represents an exception that is thrown when truncation in a ODP.NET Types class occurs.

### Class Inheritance

`System.Object`

`  System.Exception`

`    System.SystemException`

`      System.OracleTypeException`

`        Oracle.DataAccess.Types.OracleTruncateException`

### Declaration

    // C#
    public sealed class OracleTruncateException : OracleTypeException

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTruncateException Members](TruncateExceptionMembers.md)

- [OracleTruncateException Constructors](TruncateExceptionCtors.md)

- [OracleTruncateException Static Methods](TruncateExceptionStaticMethods.md)

- [OracleTruncateException Properties](TruncateExceptionProperties.md)

- [OracleTruncateException Methods](TruncateExceptionMethods.md)
