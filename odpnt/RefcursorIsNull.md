This property indicates whether or not the `OracleRefCursor` is null.

### Declaration

    // C#
    public bool IsNull {get;}

### Property Value

Returns `true` if the `OracleRefCursor` represents a null value. Returns `false` otherwise.

### Exception

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRefCursor Class](OracleRefCursorClass.md)

- [OracleRefCursor Members](RefCursorMembers.md)
