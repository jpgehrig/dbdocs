This method returns an `OracleString` structure of the specified column.

### Declaration

    // C#
    public OracleString GetOracleString(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The `OracleString` value of the column.

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

`InvalidCastException` - The accessor method is invalid for this column type or the column value is `NULL`.

### Remarks

If the column is an Oracle `REF` column, the string returned is a hexadecimal value that represents the `REF` in the database.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
