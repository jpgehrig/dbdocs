This method returns an `OracleRef` object of the specified `REF` column.

### Declaration

    // C#
    public OracleRef GetOracleRef(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The `OracleRef` object of the specified column.

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, the `Read` method has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

`InvalidCastException` - The accessor method is invalid for this column type.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
