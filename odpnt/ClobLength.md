Overrides `Stream`

This instance property indicates the size of the `CLOB` data in bytes.

### Declaration

    // C#
    public override Int64 Length {get;}

### Property Value

An `Int64` that indicates the size of the `CLOB` in bytes.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
