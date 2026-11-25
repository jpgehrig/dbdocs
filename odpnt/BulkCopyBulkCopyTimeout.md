This property specifies the number of seconds allowed for the bulk copy operation to complete before it is aborted.

### Declaration

    // C#
    public int BulkCopyTimeout {get; set;}

### Property Value

An integer value for the number of seconds after which the bulk copy operation times out.

### Exceptions

`ArgumentOutOfRangeException` - The timeout value is set to less than zero.

### Remarks

The default value is 30 seconds.

If `BatchSize``>0`, rows that were sent to the database in the previous batches remain committed. The rows that are processed in the current batch are not sent to the database. If `BatchSize=0`, no rows are sent to the database.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)
