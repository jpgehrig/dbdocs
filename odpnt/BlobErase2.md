This instance method erases a specified portion of data.

### Declaration

    // C#
    public Int64 Erase(Int64 offset, Int64 amount);

### Parameters

- `offset`

  The offset from which to erase.

- `amount`

  The quantity (in bytes) to erase.

### Return Value

The number of bytes erased.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - The `offset` or `amount` parameter is less than `0`.

### Remarks

Replaces the specified `amount` of data with zero-byte fillers.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBlob Class](OracleBlobClass.md)

- [OracleBlob Members](BlobMembers.md)
