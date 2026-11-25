This method populates the provided character array with up to the maximum number of characters, from the specified offset (in characters) of the column.

### Declaration

    // C#
    public override long GetChars(int index, long fieldOffset, char[] buffer,
        int bufferOffset, int length);

### Parameters

- `index`

  The zero based column index.

- `fieldOffset`

  The index within the column from which to begin reading (in characters).

- `buffer`

  The character array that the data is read into.

- `bufferOffset`

  The index within the buffer to begin reading data into (in characters).

- `length`

  The maximum number of characters to read (in characters).

### Return Value

The number of characters read.

### Implements

`IDataRecord`

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

`InvalidCastException` - The accessor method is invalid for this column type or the column value is `NULL`.

### Remarks

This method returns the number of characters read into the buffer. This may be less than the actual length of the field, if the method has been called previously for the same column.

If a null reference is passed for buffer, the length of the field in characters is returned.

`IsDBNull` should be called to check for `NULL` values before calling this method.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)
