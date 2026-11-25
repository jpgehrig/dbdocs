An `OraclePermissionAttribute` object enables ODP.NET to enforce declarative security and helps ensure that a user has a security level adequate for accessing data.

### Class Inheritance

`  System.Object`

`    System.Attribute`

`      System.Security.Permissions.SecurityAttribute`

`        System.Security.Permissions.CodeAccessSecurityAttribute`

`          System.Data.Common.DBDataPermissionAttribute`

`            Oracle.DataAccess.Client.OraclePermissionAttribute`

### Declaration

    // C#
    [Serializable, AttributeUsage(AttributeTargets.Method |
    AttributeTargets.Constructor | AttributeTargets.Class | AttributeTargets.Struct |
    AttributeTargets.Assembly, AllowMultiple = true, Inherited = false)]
    public sealed class OraclePermissionAttribute: DBDataPermissionAttribute

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

- [OraclePermissionAttribute Members](PermissionAttributeMembers.md)

- [OraclePermissionAttribute Constructor](PermissionAttributeCtors.md)

- [OraclePermissionAttribute Static Methods](PermissionAttributeStaticMethods.md)

- [OraclePermissionAttribute Public Properties](PermissionAttributePublicProperties.md)

- [OraclePermissionAttribute Public Methods](PermissionAttributePublicMethods.md)
