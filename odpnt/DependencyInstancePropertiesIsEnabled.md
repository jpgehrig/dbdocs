This property specifies whether or not the dependency is enabled between the application and the database.

### Declaration

    // C#
    public bool IsEnabled {get;}

### Property Value

A `bool` value that specifies whether or not dependency is enabled between the application and the database.

### Remarks

The dependency between the application and the database is not established when the `OracleDependency` instance is created. The dependency is established when the command that is associated with this dependency is executed, at which time the notification request is registered with the database. The dependency ends when the notification registration is removed from the database or when it times out.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)
