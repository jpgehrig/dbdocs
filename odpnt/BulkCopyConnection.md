This property specifies the `OracleConnection` object that the Oracle database uses to perform the bulk copy operation.

### Declaration

    // C#
    public OracleConnection Connection {get; }

### Property Value

The `OracleConnection` object used for the bulk copy operations.

### Remarks

This property gets the connection constructed by the `OracleBulkCopy`, if the `OracleBulkCopy` object is initialized using a connection string.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
