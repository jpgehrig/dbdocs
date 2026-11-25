Overrides `Stream`.

This method sets the position within the current stream and returns the new position within the current stream.

### Declaration

    // C#
    public long Seek(long offset, SeekOrigin origin);

### Parameters

- `offset`

  A byte offset relative to origin.

  - If `offset` is negative, the new position precedes the position specified by `origin` by the number of bytes specified by `offset`.

  - If offset is zero, the new position is the position specified by `origin`.

  - If `offset` is positive, the new position follows the position specified by `origin` by the number of bytes specified by `offset`.

- `origin`

  A value of type `SeekOrigin` indicating the reference point used to obtain the new position.

### Return Value

` ` The new `Position` within the current stream.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object

### Remarks

Use the `CanSeek` property to determine whether or not the current instance supports seeking. Seeking to any location beyond the length of the stream is supported.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlStream Class](OracleXmlStreamClass.md)

- [OracleXmlStream Members](XmlStreamMembers.md)
