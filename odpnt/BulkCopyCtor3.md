This constructor instantiates a new instance of `OracleBulkCopy` using the specified connection object and `OracleBulkCopyOptions` value.

### Declaration

    // C#
    public OracleBulkCopy(OracleConnection connection, OracleBulkCopyOptions      copyOptions);

### Parameters

- `connection`

  The open instance of an `OracleConnection` object that performs the bulk copy operation.

- `copyOptions`

  The combination of `OracleBulkCopyOptions` enumeration values that determine the behavior of the `OracleBulkCopy` object.

### Exceptions

`ArgumentNullException` - The `connection` parameter is null.

`InvalidOperationException` - The connection is not in the open state.

### Remarks

The connection passed to this constructor must be open. It remains open after the `OracleBulkCopy` instance is closed.

The `Connection` property is set to the supplied connection.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)

- "[OracleBulkCopyOptions Enumeration](OracleBulkCopyOptionsEnumeration.md)"
