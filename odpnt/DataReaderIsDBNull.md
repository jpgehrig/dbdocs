This method indicates whether or not the column value is `NULL`.

### Declaration

    // C#
    public override bool IsDBNull(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

Returns `true` if the column is a `NULL` value; otherwise, returns `false`.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

### Remarks

This method should be called to check for `NULL` values before calling the other accessor methods.

### Example

The code example for the `OracleDataReader` class includes the `IsDBNull` method. See "[Example](OracleDataReaderClass.md)".

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
