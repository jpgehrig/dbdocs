This method returns the column value as a .NET type.

### Declaration

    // C#
    public override object GetValue(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The value of the column as a .NET type.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, all rows have been read, or no valid custom type mapping has been specified for the Oracle Object or Oracle Collection column.

`IndexOutOfRangeException` - The column index is invalid.

### Remarks

If the column is an Oracle Object or an Oracle Collection column, the .NET custom type corresponding to the custom type mapping is returned.

If the column is an Oracle `REF` column, a hexidecimal value is returned as a .NET string that represents the `REF` in the database.

If the UDT is `NULL`, `DBNull.Value` is returned

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
