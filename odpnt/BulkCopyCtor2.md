This constructor instantiates a new instance of the `OracleBulkCopy` class by first creating an `OracleConnection` object based on the supplied `connectionString` , then initializing the new `OracleBulkCopy` object with the `OracleConnection` object and `OracleBulkCopyOptions` default value.

### Declaration

    // C#
    public OracleBulkCopy(string connectionString);

### Parameters

- `connectionString`

  The connection information used to connect to the Oracle database and perform the bulk copy operation.

### Exception

`ArgumentNullException` - The `connectionString` parameter is null.

`ArgumentException` - The `connectionString` parameter is empty.

### Remarks

The `WriteToServer` method opens the connection, if it is not already opened. The connection is automatically closed when the `OracleBulkCopy` instance is closed.

This constructor uses the default enumeration value `OracleBulkCopyOptions.Default`.

The `Connection` property is set to the `OracleConnection` object initialized using the supplied `connectionString`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)

- "[OracleBulkCopyOptions Enumeration](OracleBulkCopyOptionsEnumeration.md)"
