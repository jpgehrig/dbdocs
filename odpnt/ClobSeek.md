Overrides `Stream`

This instance method sets the position on the current LOB stream.

### Declaration

    // C#
    public override Int64 Seek(Int64 offset, SeekOrigin origin);

### Parameters

- `offset`

  A byte offset relative to origin.

- `origin`

  A value of type `System.IO.SeekOrigin` indicating the reference point used to obtain the new position.

### Return Value

Returns an `Int64` that indicates the position.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

If `offset` is negative, the new position precedes the position specified by `origin` by the number of characters specified by `offset`.

If `offset` is zero, the new position is the position specified by `origin`.

If `offset` is positive, the new position follows the position specified by `origin` by the number of characters specified by `offset`.

`SeekOrigin.Begin` specifies the beginning of a stream.

`SeekOrigin.Current` specifies the current position within a stream.

`SeekOrigin.End` specifies the end of a stream.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleClob Class](OracleClobClass.md)

- [OracleClob Members](ClobMembers.md)
