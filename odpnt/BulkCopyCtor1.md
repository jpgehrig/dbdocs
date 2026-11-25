This constructor instantiates a new instance of `OracleBulkCopy` class using the specified connection and default `OracleBulkCopyOptions` enumeration values.

### Declaration

    // C#
    public OracleBulkCopy(OracleConnection connection);

### Parameters

- `connection`

  The open instance of `OracleConnection` that performs the bulk copy operation.

### Exceptions

`ArgumentNullException` - The connection parameter is null.

`InvalidOperationException` - The connection is not in the open state.

### Remarks

The connection object passed to this constructor must be open. It remains open after the `OracleBulkCopy` instance is closed.

This constructor uses the default enumeration value `OracleBulkCopyOptions.Default`.

The `Connection` property is set to the supplied connection.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)

- "[OracleBulkCopyOptions Enumeration](OracleBulkCopyOptionsEnumeration.md)"
