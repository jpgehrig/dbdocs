This instance method copies data from the current `OracleClob` instance to the provided `OracleClob` object with the specified destination offset.

### Declaration

    // C#
    public Int64 CopyTo(OracleClob obj, Int64 dst_offset);

### Parameters

- `obj`

  The `OracleClob` object to which the data is copied.

- `dst_offset`

  The offset (in characters) at which the `OracleClob` object is copied.

### Return Value

The return value is the amount copied.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`ArgumentOutOfRangeException` - The `dst_offset` is less than `0`.

`InvalidOperationException` - This exception is thrown if any of the following conditions exist:

- The `OracleConnection` is not open or has been closed during the lifetime of the object.

- The LOB object parameter has a different connection than the object.

### Remarks

If the `dst_offset` is beyond the end of the `OracleClob` data, spaces are written into the `OracleClob` until the `dst_offset` is met.

The offsets are `0`-based. No character conversion is performed by this operation.

The provided object and the current instance must be using the same connection; that is, the same `OracleConnection` object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
