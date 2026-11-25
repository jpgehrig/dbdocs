This property specifies the number of rows to be sent as a batch to the database.

### Declaration

    // C#
    public int BatchSize {get; set;}

### Property Value

An integer value for the number of rows to be sent to the database as a batch.

### Exceptions

`ArgumentOutOfRangeException` - The batch size is less than zero.

### Remarks

The default value is zero, indicating that the rows are not sent to the database in batches. The entire set of rows are sent in one single batch.

A large batch size reduces database round trips, but it can also consume large amounts of client side memory. Excessive memory consumption slows down overall machine performance and leads to errors if the process runs out of accessible memory. It is recommended that client side memory is not consumed in excess. This can be done by reducing the batch size.

A batch is complete when `BatchSize` number of rows have been processed or there are no more rows to send to the database.

- If `BatchSize` `>` `0` and the `UseInternalTransaction` bulk copy option is specified, each batch of the bulk copy operation occurs within a transaction. If the connection used to perform the bulk copy operation is already part of a transaction, an `InvalidOperationException` exception is raised.

- If `BatchSize` `>` `0` and the `UseInternalTransaction` option is not specified, rows are sent to the database in batches of size `BatchSize`, but no transaction-related action is taken.

The `BatchSize` property can be set at any time. If a bulk copy is already in progress, the current batch size is determined by the previous batch size. Subsequent batches use the new batch size.

If the `BatchSize` property is initially zero and changes while a `WriteToServer` operation is in progress, that operation loads the data as a single batch. Any subsequent `WriteToServer` operations on the same `OracleBulkCopy` instance use the new `BatchSize`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleBulkCopy Class](OracleBulkCopyClass.md)

- [OracleBulkCopy Members](OracleBulkCopyMembers.md)

- "[OracleBulkCopyOptions Enumeration](OracleBulkCopyOptionsEnumeration.md)"
