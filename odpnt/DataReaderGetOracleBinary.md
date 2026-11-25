This method returns an `OracleBinary` structure of the specified column.

### Declaration

    // C#
    public OracleBinary GetOracleBinary(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The `OracleBinary` value of the column.

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

`InvalidCastException` - The accessor method is invalid for this column type or the column value is `NULL`.

### Remarks

`IsDBNull` should be called to check for `NULL` values before calling this method.

`GetOracleBinary` is used on the following Oracle types:

- `BFILE`

- `BLOB`

- `LONG` `RAW`

- `RAW`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
