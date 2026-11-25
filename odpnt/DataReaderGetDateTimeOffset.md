This method returns the `DateTimeOffset` value of a `TIMESTAMP WITH TIME ZONE` column. DateTimeOffset represents a point in time. It is generally expressed as a date and time relative to Coordinated Universal Time (UTC).

### Declaration

    // C#
    public override DateTimeOffset GetDateTimeOffset(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The `DateTimeOffset` value of the column.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

`InvalidCastException` - The accessor method is invalid for this column type or the column value is `NULL`.

### Remarks

- This method can be called only on a `TIMESTAMP WITH TIME ZONE` column.

- `IsDBNull` should be called to check for `NULL` values before calling this method.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
