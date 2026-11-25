This instance method copies data from the current `OracleBlob` instance to the provided `OracleBlob` object with the specified destination offset.

### Declaration

    // C#
    public Int64 CopyTo(OracleBlob obj, Int64 dst_offset);

### Parameters

- `obj`

  The `OracleBlob` object to which the data is copied.

- `dst_offset`

  The offset (in bytes) at which the `OracleBlob` object is copied.

### Return Value

The return value is the amount copied.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`ArgumentOutOfRangeException` - The `dst_offset` is less than `0`.

`InvalidOperationException` - This exception is thrown if any of the following conditions exist:

- The `OracleConnection` is not open or has been closed during the lifetime of the object.

- The LOB object parameter has a different connection than the object.

### Remarks

If the `dst_offset` is beyond the end of the `OracleBlob` data, spaces are written into the `OracleBlob` until the `dst_offset` is met.

The offsets are `0`-based. No character conversion is performed by this operation.

The provided object and the current instance must be using the same connection; that is, the same `OracleConnection` object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBlob Class](OracleBlobClass.md)

- [OracleBlob Members](BlobMembers.md)
