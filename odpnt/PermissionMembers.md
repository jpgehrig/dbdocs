`OraclePermission` members are listed in the following tables.

### OraclePermission Constructors

The `OraclePermission` constructor is listed in Table 6-135.

Table 6-135 OraclePermission Constructor

| Constructor                                       | Description                                                  |
|:--------------------------------------------------|:-------------------------------------------------------------|
| [OraclePermission Constructor](PermissionCtor.md) | Instantiates a new instance of the `OraclePermission` class. |

### OraclePermission Static Methods

The `OraclePermission` static methods are listed in Table 6-136.

Table 6-136 OraclePermission Static Methods

| Static Method      | Description                           |
|:-------------------|:--------------------------------------|
| `Equals`           | Inherited from `System.Object`        |
| `ReferenceEquals`  | Inherited from `System.Object`        |
| `RevertAll`        | Inherited from `CodeAccessPermission` |
| `RevertAssert`     | Inherited from `CodeAccessPermission` |
| `RevertDeny`       | Inherited from `CodeAccessPermission` |
| `RevertPermitOnly` | Inherited from `CodeAccessPermission` |

### OraclePermission Public Properties

The `OraclePermission` public methods are listed in [Table 6-140](PermissionPublicProperties.md).

Table 6-137 OraclePermission Public Properties

| Public Properties    | Description                                                                             |
|:---------------------|:----------------------------------------------------------------------------------------|
| `AllowBlankPassword` | Inherited from `DBDataPermission`<br>`OraclePermission` does not support this property. |

### OraclePermission Public Methods

The `OraclePermission` public methods are listed in Table 6-138.

Table 6-138 OraclePermission Public Methods

| Public Method                         | Description                                                                                                       |
|:--------------------------------------|:------------------------------------------------------------------------------------------------------------------|
| [Add](PermissionAdd.md)               | Adds a new connection string fragment and a list of restricted keywords to the `OraclePermission` object          |
| `Assert`                              | Inherited from `CodeAccessPermission`                                                                             |
| [Copy](PermissionCopy.md)             | Returns a copy of the current permission object                                                                   |
| `Demand`                              | Inherited from `CodeAccessPermission`                                                                             |
| `Deny`                                | Inherited from `CodeAccessPermission`                                                                             |
| `Equals`                              | Inherited from `CodeAccessPermission`                                                                             |
| `FromXml`                             | Inherited from `DBDataPermission`                                                                                 |
| `GetHashCode`                         | Inherited from `CodeAccessPermission`                                                                             |
| `GetType`                             | Inherited from `System.Object`                                                                                    |
| `Intersect`                           | Inherited from `DBDataPermission`                                                                                 |
| [IsSubsetOf](PermissionIsSubsetOf.md) | Returns a boolean value that indicates whether or not the current permission is a subset of the target permission |
| `IsUnrestricted`                      | Inherited from `DBDataPermission`                                                                                 |
| `PermitOnly`                          | Inherited from `CodeAccessPermission`                                                                             |
| `ToString`                            | Inherited from `CodeAccessPermission`                                                                             |
| `ToXml`                               | Inherited from `DBDataPermission`                                                                                 |
| `Union`                               | Inherited from `DBDataPermission`                                                                                 |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OraclePermission Class](OraclePermissionClass.md)
