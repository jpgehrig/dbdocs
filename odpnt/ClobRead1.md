Overrides `Stream`

This instance method reads a specified amount of bytes from the current instance and populates the byte array `buffer`.

### Declaration

    // C#
    public override int Read(byte [] buffer, int offset, int count);

### Parameters

- `buffer`

  The byte array buffer that is populated.

- `offset`

  The offset (in bytes) at which the buffer is populated.

- `count`

  The amount of bytes to be read.

### Return Value

The number of bytes read from the `CLOB`.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

Both `offset` and `count` must be even numbers for `CLOB` and `NCLOB` because every two bytes represent a Unicode character.

The LOB data is read starting from the position specified by the `Position` property, which must also be an even number.

`OracleClob` is free to return fewer bytes than requested, even if the end of the stream has not been reached.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
