The `OracleNullValueException` represents an exception that is thrown when trying to access an ODP.NET Types structure that has a null value.

### Class Inheritance

`System.Object`

`  System.Exception`

`    System.SystemException`

`      System.OracleTypeException`

`        Oracle.DataAccess.Types.OracleNullValueException`

### Declaration

    // C#
    public sealed class OracleNullValueException : OracleTypeException

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

- [OracleNullValueException Members](NullValueExceptionMembers.md)

- [OracleNullValueException Constructors](NullValueExceptionCtors.md)

- [OracleNullValueException Static Methods](NullValueExceptionStaticMethods.md)

- [OracleNullValueException Properties](NullValueExceptionProperties.md)

- [OracleNullValueException Methods](NullValueExceptionMethods.md)
