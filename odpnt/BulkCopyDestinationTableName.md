This property specifies the database table that the data is loaded into.

### Declaration

    // C#
    public string DestinationTableName {get; set;}

### Property Value

A string value that identifies the destination table name.

### Exceptions

`ArgumentNullException` - The destination table name set is null.

`ArgumentException` - The destination table name is empty.

### Remarks

If `DestinationTableName` is modified while a `WriteToServer` operation is running, the change does not affect the current operation. The new `DestinationTableName` value is used the next time a `WriteToServer` method is called.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
