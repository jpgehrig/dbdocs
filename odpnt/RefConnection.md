This instance property references the connection used by the `OracleRef`.

### Declaration

    // C#
    public OracleConnection Connection{get;}

### Property Value

An `OracleConnection` object associated with the `REF`.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

Once the `Dispose` method is invoked, this property is set to `null`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRef Class](OracleRefClass.md)

- [OracleRef Members](OracleRefMembers.md)
