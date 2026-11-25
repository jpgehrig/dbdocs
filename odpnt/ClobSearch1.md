This instance method searches for a character pattern, represented by the byte array, in the current instance of `OracleClob`.

### Declaration

    // C#
    public int Search(byte[] val, Int64 offset, Int64 nth);

### Parameters

- `val`

  A Unicode byte array.

- `offset`

  The `0`-based offset (in characters) starting from which the `OracleClob` is searched.

- `nth`

  The specific occurrence (`1`-based) of the match for which the absolute offset (in characters) is returned.

### Return Value

Returns the absolute `offset` of the start of the matched pattern (in bytes) for the `nth` occurrence of the match. Otherwise, `0` is returned.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - This exception is thrown if any of the following conditions exist:

- The `offset` is less than `0`.

- The `nth` is less than or equal to `0`.

- The `nth` is greater than or equal to `OracleClob.MaxSize`.

- The `offset` is greater than or equal to `OracleClob.MaxSize`.

### Remarks

The `byte[` `]` is converted to Unicode before the search is made.

The limit of the search pattern is 16383 bytes.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
