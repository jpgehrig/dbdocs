This method returns the `Int32` value of the specified `NUMBER` column.

**Note:**

`int` is equivalent to `Int32`.

### Declaration

    // C#
    public override int GetInt32(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The `Int32` value of the column.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

`InvalidCastException` - The accessor method is invalid for this column type or the column value is `NULL`.

### Remarks

`IsDBNull` should be called to check for `NULL` values before calling this method.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
