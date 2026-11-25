This method returns an OracleClob object of the specified CLOB column.

### Declaration

    // C#
    public OracleClob GetOracleClob(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The `OracleClob` value of the column.

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

- "[LOB Support](featLOBsupp.md)"
