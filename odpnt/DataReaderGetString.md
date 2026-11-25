This method returns the `string` value of the specified column.

### Declaration

    // C#
    public override string GetString(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The `string` value of the column.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

`InvalidCastException` - The accessor method is invalid for this column type or the column value is `NULL`.

### Remarks

Call the `IsDBNull` method to check for null values before calling this method.

If the column is an Oracle `REF` column, the string returned is a hexadecimal string that represents the `REF` in the database.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
