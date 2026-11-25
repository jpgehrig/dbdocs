This instance method removes the specified dependency between the application and the database. Once the registration of the dependency is removed from the database, the `OracleDependency` is no longer able to detect any changes that the database undergoes.

### Declaration

    // C#
    public void RemoveRegistration(OracleConnection con)

### Parameters

- `con`

  The connection associated with the `OracleDependency` instance.

### Exceptions

`InvalidOperationException` - The associated connection is not open.

### Remarks

The notification registration associated with the `OracleDependency` instance is removed from the database.

The `OracleConnection` parameter must be in an opened state. This instance method does not open the connection implicitly for the application.

An exception is thrown if the dependency is not valid.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)
