This instance method compares data referenced by the current instance and that of the supplied object.

### Declaration

    // C#
    public int Compare(Int64 src_offset, OracleBlob obj, Int64 dst_offset,
       Int64 amount);

### Parameters

- `src_offset`

  The comparison starting point (in bytes) for the current instance.

- `obj`

  The provided `OracleBlob` object.

- `dst_offset`

  The comparison starting point (in bytes) for the provided `OracleBlob`.

- `amount`

  The number of bytes to compare.

### Return Value

Returns a value that is:

- Less than zero: if the data referenced by the current instance is less than that of the supplied instance

- Zero: if both objects reference the same data

- Greater than zero: if the data referenced by the current instance is greater than that of the supplied instance

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The parameter has a different connection than the object, `OracleConnection` is not opened, or `OracleConnection` has been reopened.

`ArgumentOutOfRangeException` - The `src_offset`, the `dst_offset`, or the `amount` parameter is less than `0`.

### Remarks

The provided object and the current instance must be using the same connection, that is, the same `OracleConnection` object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBlob Class](OracleBlobClass.md)

- [OracleBlob Members](BlobMembers.md)
