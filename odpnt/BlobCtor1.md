This constructor creates an instance of the `OracleBlob` class bound to a temporary `BLOB` with an `OracleConnection` object.

### Declaration

    // C#
    public OracleBlob(OracleConnection con);

### Parameters

- `con`

  The `OracleConnection` object.

### Exceptions

`InvalidOperationException` - The `OracleConnection` is not opened.

### Remarks

The connection must be opened explicitly by the application. `OracleBlob` does not open the connection implicitly.

The temporary `BLOB` utilizes the provided connection to store `BLOB` data. Caching is not turned on by this constructor.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBlob Class](OracleBlobClass.md)

- [OracleBlob Members](BlobMembers.md)
