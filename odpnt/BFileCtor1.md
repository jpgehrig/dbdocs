This constructor creates an instance of the `OracleBFile` class with an `OracleConnection` object.

### Declaration

    // C#
    public OracleBFile(OracleConnection con);

### Parameters

- `con`

  The `OracleConnection` object.

### Exceptions

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

The connection must be opened explicitly by the application. `OracleBFile` does not open the connection implicitly.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBFile Class](OracleBFileClass.md)

- [OracleBFile Members](BFileMembers.md)
