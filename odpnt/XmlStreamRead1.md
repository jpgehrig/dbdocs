Overrides `Stream`

This method reads a specified amount of unicode bytes from the current instance, advances the position within the stream, and populates the byte array buffer.

### Declaration

    // C#
    public override int Read(byte[] buffer, int offset, int count);

### Parameters

- `buffer`

  The byte array buffer that is populated.

- `offset`

  The zero-based offset (in bytes) at which the buffer is populated.

- `count`

  The maximum amount of bytes to be read.

### Return Value

The number of unicode bytes read into the given `byte[]` buffer or `0` if the end of the stream has been reached.

### Remarks

This method reads a maximum of `count` bytes from the current stream and stores them in buffer beginning at `offset`. The current position within the stream is advanced by the number of bytes read. However, if an exception occurs, the current position within the stream remains unchanged.

The XML data is read starting from the position specified by the `Position` property.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlStream Class](OracleXmlStreamClass.md)

- [OracleXmlStream Members](XmlStreamMembers.md)
