This method returns the `Guid` value of the specified binary data column. A GUID is a Globally Unique Identifier.

### Declaration

    // C#
    public override Guid GetGuid(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

The `Guid` value of the column.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

`InvalidCastException` - The accessor method is invalid for this column type or the column value is `NULL`.

`System.ArgumentException` - Byte array for GUID must be exactly 16 bytes long.

### Remarks

- This method can be called on columns that contain binary data, such as `RAW` and `BLOB`.

- An exception will be thrown if the binary data of the column is not 16 bytes in length.

- `IsDBNull` should be called to check for `NULL` values before calling this method.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
