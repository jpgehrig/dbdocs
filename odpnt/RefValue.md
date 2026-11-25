This instance property returns a .NET representation of this Oracle `REF`.

### Declaration

    // C#
    public string Value{get;}

### Property Value

A .NET representation of the Oracle `REF`.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

This property returns a HEX string that represents the `REF`.

The returned string can be used to create a new `OracleRef` instance by using the `OracleRef(OracleConnection,` `string)` constructor.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRef Class](OracleRefClass.md)

- [OracleRef Members](OracleRefMembers.md)

- "[OracleRef(OracleConnection, string)](RefCtor1.md)"
