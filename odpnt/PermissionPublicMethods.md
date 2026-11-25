The `OraclePermission` public methods are listed in Table 6-141.

Table 6-141 OraclePermission Public Methods

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

- [OraclePermission Members](PermissionMembers.md)
