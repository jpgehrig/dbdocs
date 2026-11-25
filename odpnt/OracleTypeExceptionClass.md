The `OracleTypeException` is the base exception class for handling exceptions that occur in the ODP.NET Types classes.

### Class Inheritance

`System.Object`

`  System.Exception`

`    System.SystemException`

`      Oracle.DataAccess.Types.OracleTypeException`

### Declaration

    // C#
    public class OracleTypeException : SystemException

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

- [OracleTypeException Members](TypeExceptionMembers.md)

- [OracleTypeException Constructors](TypeExceptionCtors.md)

- [OracleTypeException Static Methods](TypeExceptionStaticMethods.md)

- [OracleTypeException Properties](TypeExceptionProperties.md)

- [OracleTypeException Methods](TypeExceptionMethods.md)
