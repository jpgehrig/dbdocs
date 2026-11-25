This method releases any resources or memory allocated by the object.

### Declaration

    // C#
    public void Dispose();

### Implements

`IDisposable`

### Remarks

After the `Dispose` method is called on the `OracleBulkCopy` object, no other operation can succeed. The connection is closed if the connection was opened by the `OracleBulkCopy` object, that is, if a constructor that takes a connection string created the `OracleBulkCopy` object.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
