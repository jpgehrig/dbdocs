Overrides `Stream`

This instance property indicates the current read or write position in the LOB stream in bytes.

### Declaration

    // C#
    public override Int64 Position{get; set;}

### Property Value

An `Int64` that indicates the read or write position.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - The `Position` is less than `0`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
