This instance method replaces the specified `amount` of data (in characters) starting from the specified `offset` with zero-byte fillers (in characters).

### Declaration

    // C#
    public Int64 Erase(Int64 offset, Int64 amount);

### Parameters

- `offset`

  The offset.

- `amount`

  The amount of data.

### Return Value

The actual number of characters erased.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - The `offset` or `amount` parameter is less than `0`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
