This method reads the next row in the result set.

### Declaration

    // C#
    public override  bool Read();

### Return Value

Returns `true` if another row exists; otherwise, returns `false`.

### Implements

`IDataReader`

### Exceptions

`InvalidOperationException` - The connection is closed or the reader is closed.

### Remarks

The initial position of the data reader is before the first row. Therefore, the `Read` method must be called to fetch the first row. The row that was just read is considered the current row. If the `OracleDataReader` has no more rows to read, it returns `false`.

### Example

The code example for the `OracleDataReader` class includes the `Read` method. See "[Example](OracleDataReaderClass.md)".

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
