This method populates the provided byte array with up to the maximum number of bytes, from the specified offset (in bytes) of the column.

### Declaration

    // C#
    public override long GetBytes(int index, long fieldOffset, byte[] buffer,
       int bufferOffset, int length);

### Parameters

- `index`

  The zero-based column index.

- `fieldOffset`

  The offset within the column from which reading begins (in bytes).

- `buffer`

  The byte array that the data is read into.

- `bufferOffset`

  The offset within the buffer to begin reading data into (in bytes).

- `length`

  The maximum number of bytes to read (in bytes).

### Return Value

The number of bytes read.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

`InvalidCastException` - The accessor method is invalid for this column type or the column value is `NULL`.

### Remarks

This method returns the number of bytes read into the buffer. This may be less than the actual length of the field if the method has been called previously for the same column.

If a null reference is passed for buffer, the length of the field in bytes is returned.

`IsDBNull` should be called to check for `NULL` values before calling this method.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
