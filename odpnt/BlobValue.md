This instance property returns the data, starting from the first byte in the `BLOB`, as a byte array.

### Declaration

    // C#
    public Byte[] Value{get;}

### Property Value

A byte array.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - The `Value` is less than `0`.

### Remarks

The value of `Position` is not used or changed by using this property. 2 GB is the maximum byte array length that can be returned by this property.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBlob Class](OracleBlobClass.md)

- [OracleBlob Members](BlobMembers.md)
