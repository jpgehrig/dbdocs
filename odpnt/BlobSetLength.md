Overrides `Stream`

This instance method trims or truncates the `BLOB` value to the specified length (in bytes).

### Declaration

    // C#
    public override void SetLength(Int64 newlen);

### Parameters

- `newlen`

  The desired length of the current stream in bytes.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - The `newlen` parameter is less than `0`.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBlob Class](OracleBlobClass.md)

- [OracleBlob Members](BlobMembers.md)
