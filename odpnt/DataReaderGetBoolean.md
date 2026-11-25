This method returns the bool value of the specified numeric column.

### Declaration

    // C#
    public override bool GetBoolean(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The bool value of the column.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

`InvalidCastException` - The accessor method is invalid for this column type.

### Remarks

- This method can be called on any numeric database type column (`NUMBER`, `BINARY_DOUBLE`, `BINARY_FLOAT`, and `FLOAT`).

- `FALSE` is returned if column value is `0`; `TRUE` otherwise.

- `IsDBNull` should be called to check for `NULL` values before calling this method.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
