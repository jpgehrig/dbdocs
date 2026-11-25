This property specifies a value that enables or disables batch processing support, and specifies the number of SQL statements that can be executed in a single round-trip to the database.

### Declaration

    // C#
    public virtual int UpdateBatchSize {get; set;}

### Property Value

An integer that returns the batch size.

### Exceptions

`ArgumentOutOfRangeException` - The value is set to a number \< 0.

### Remarks

Update batches executed with large amounts of data may encounter an `"PLS-00123:` `Program` `too` `large"` error. To avoid this error, reduce the size of `UpdateBatchSize` to a smaller value.

For each row in the `DataSet` that has been modified, added, or deleted, one SQL statement will be executed on the database.

Values are as follows:

- Value = `0`

  The data adapter executes all the SQL statements in a single database round-trip

- Value = `1` - Default value

  This value disables batch updating and SQL statements are executed one at a time.

- Value = `n` where `n` \> `1`

  The data adapter updates `n` rows of data per database round-trip.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)

- "[Batch Processing](featOraCommand.md)"
