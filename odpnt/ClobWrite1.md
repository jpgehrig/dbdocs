Overrides `Stream`

This instance method writes data from the provided byte array buffer into the `OracleClob`.

### Declaration

    // C#
    public override void Write(byte[ ] buffer, int offset, int count);

### Parameters

- `buffer`

  The byte array buffer that represents a Unicode string.

- `offset`

  The offset (in bytes) from which the `buffer` is read.

- `count`

  The amount of data (in bytes) from the buffer to be written into the `OracleClob`.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - This exception is thrown if any of the following conditions exist:

- The `offset` or the `count` is less than `0`.

- The `offset` is greater than or equal to the `buffer`.`Length`.

- The `offset` and the `count` together are greater than the `buffer`.`Length`.

- The `offset`, the `count`, or the `Position` is not even.

### Remarks

Both `offset` and `count` must be even numbers for `CLOB` and `NCLOB` because every two bytes represent a Unicode character.

The LOB data is read starting from the position specified by the `Position` property. The `Position` property must be an even number.

If necessary, proper data conversion is carried out from the client character set to the database character set.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
