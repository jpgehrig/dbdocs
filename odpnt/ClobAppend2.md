This instance method appends data at the end of the `CLOB`, from the supplied byte array buffer, starting from offset (in bytes) of the supplied byte array buffer.

### Declaration

    // C#
    public int Append(byte[] buffer, int offset, int count);

### Parameters

- `buffer`

  An array of bytes, representing a Unicode string.

- `offset`

  The zero-based byte offset in the buffer from which data is read.

- `count`

  The number of bytes to be appended.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - Either the `offset` or the `count` parameter is not even.

### Remarks

Both `offset` and `count` must be even numbers for `CLOB` and `NCLOB` because every two bytes represent a Unicode character.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
