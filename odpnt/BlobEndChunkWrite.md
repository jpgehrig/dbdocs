This instance method closes the `BLOB` referenced by the current `OracleBlob` instance.

### Declaration

    // C#
    public void EndChunkWrite();

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

Index updates occur immediately if there is write operation(s) deferred by the `BeginChunkWrite` method.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBlob Class](OracleBlobClass.md)

- [OracleBlob Members](BlobMembers.md)
