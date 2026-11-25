This property specifies the database partition that the data is loaded into.

### Declaration

    // C#
    public string DestinationPartitionName {get; set;}

### Property Value

A string value that identifies the destination partition name.

### Remarks

If `DestinationPartitionName` is modified while a `WriteToServer` operation is running, the change does not affect the current operation. The new `DestinationPartitionName` value is used the next time a `WriteToServer` method is called.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
