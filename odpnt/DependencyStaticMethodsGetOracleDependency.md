This static method returns an `OracleDependency` instance based on the specified unique identifier.

### Declaration

    // C#
    public static OracleDependency GetOracleDependency(string guid)

### Parameters

- `guid`

  The string representation of the unique identifier of an `OracleDependency` instance.

### Exceptions

`ArgumentException` - The specified unique identifier cannot locate an `OracleDependency` instance.

### Return Value

An `OracleDependency` instance that has the specified `guid` parameter.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDependency Class](OracleDependencyClass.md)

- [OracleDependency Members](DependencyMembers.md)
