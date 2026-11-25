An `OraclePermission` object enables ODP.NET to enforce imperative security and helps ensure that a user has a security level adequate for accessing data.

### Class Inheritance

`  System.Object`

`    System.Security.CodeAccessPermission`

`      System.Data.Common.DBDataPermission`

`        Oracle.DataAccess.Client.OraclePermission`

### Declaration

    // C#
    public class OraclePermission: DBDataPermission

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           |
|:---------------|:---------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OraclePermission Members](PermissionMembers.md)

- [OraclePermission Constructor](PermissionCtor.md)

- [OraclePermission Static Methods](PermissionStaticMethods.md)

- [OraclePermission Public Properties](PermissionPublicProperties.md)

- [OraclePermission Public Methods](PermissionPublicMethods.md)
