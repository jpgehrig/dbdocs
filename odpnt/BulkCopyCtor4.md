This constructor instantiates a new instance of the `OracleBulkCopy` class by first creating an `OracleConnection` object based on the supplied `connectionString`, then initializing the new `OracleBulkCopy` object with the `OracleConnection` object and the supplied `OracleBulkCopyOptions` enumeration values.

### Declaration

    // C#
    public OracleBulkCopy(string connectionString, OracleBulkCopyOptions copyOptions);

### Parameters

- `connectionString`

  The connection information used to connect to the Oracle database to perform the bulk copy operation.

- `copyOptions`

  The combination of `OracleBulkCopyOptions` enumeration values that determine the behavior of the bulk copy operation.

### Exceptions

`ArgumentNullException` - The `connectionString` is null.

`ArgumentException` - The `connectionString` parameter is empty.

### Remarks

The constructor uses the new instance of the `OracleConnection` class to initialize a new instance of the `OracleBulkCopy` class. The `OracleBulkCopy` instance behaves according to options supplied in the `copyOptions` parameter.

The connection is automatically closed when the `OracleBulkCopy` instance is closed.

The `Connection` property is set to an `OracleConnection` object initialized using the supplied `connectionString`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)

- "[OracleBulkCopyOptions Enumeration](OracleBulkCopyOptionsEnumeration.md)"
