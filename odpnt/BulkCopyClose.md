This method closes the `OracleBulkCopy` instance.

### Declaration

    // C#
    public void Close();

### Exceptions

`InvalidOperationException` - The `Close` method was called from a `OracleRowsCopied` event.

### Remarks

After the `Close` method is called on a `OracleBulkCopy` object, no other operation can succeed. Calls to the `WriteToServer` method throw an `InvalidOperationException`. The `Close` method closes the connection if the connection was opened by the `OracleBulkCopy` object, that is, if the `OracleBulkCopy` object was created by a constructor that takes a connection string.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
