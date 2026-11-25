This constructor creates an instance of the `OracleClob` class that is bound to a temporary `CLOB`, with an `OracleConnection` object, a boolean value for caching, and a boolean value for `NCLOB`.

### Declaration

    // C#
    public OracleClob(OracleConnection con, bool bCaching, bool bNCLOB);

### Parameters

- `con`

  The `OracleConnection` object connection.

- `bCaching`

  A flag that indicates whether or not server-side caching is enabled.

- `bNCLOB`

  A flag that is set to `true` if the instance is a `NCLOB` or `false` if it is a `CLOB`.

### Exceptions

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

The connection must be opened explicitly by the application. `OracleClob` does not open the connection implicitly. The temporary `CLOB` or `NCLOB` uses the provided connection to store `CLOB` data.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
