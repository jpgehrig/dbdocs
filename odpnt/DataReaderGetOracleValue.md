This method returns the specified column value as an ODP.NET type.

### Declaration

    // C#
    public object GetOracleValue(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The value of the column as an ODP.NET type.

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

### Remarks

If the column is an Oracle object or Oracle collection column and a custom type mapping exists, then a custom type is returned.

If the column is an Oracle `REF` column, then an `OracleRef` is returned.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
