This constructor creates an instance of the `OracleBlob` class bound to a temporary `BLOB` with an `OracleConnection` object and a boolean value for caching.

### Declaration

    // C#
    public OracleBlob(OracleConnection con, bool bCaching);

### Parameters

- `con`

  The `OracleConnection` object.

- `bCaching`

  A flag for enabling or disabling server-side caching.

### Exceptions

`InvalidOperationException` - The `OracleConnection` is not opened.

### Remarks

The connection must be opened explicitly by the application. `OracleBlob` does not open the connection implicitly.

The temporary `BLOB` uses the provided connection to store `BLOB` data. The `bCaching` input parameter determines whether or not server-side caching is used.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBlob Class](OracleBlobClass.md)

- [OracleBlob Members](BlobMembers.md)
