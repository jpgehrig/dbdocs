An `OracleDependency` class represents a dependency between an application and an Oracle database, enabling the application to get notifications whenever the data of interest or the state of the Oracle database changes.

### Class Inheritance

`System.Object`

`  Oracle.DataAccess.Client.OracleDependency`

### Declaration

    // C#
    public sealed class OracleDependency

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

Not supported in a .NET stored procedure

### Thread Safety

All public static methods are thread-safe, although methods do not guarantee thread safety.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Members](DependencyMembers.md)

- [OracleDependency Constructors](DependencyConstructors.md)

- [OracleDependency Static Fields](DependencyStaticFields.md)

- [OracleDependency Static Methods](DependencyStaticMethods.md)

- [OracleDependency Methods](DependencyInstanceMethods.md)

- [OracleDependency Properties](DependencyInstanceProperties.md)

- [OracleDependency Events](DependencyEvents.md)
