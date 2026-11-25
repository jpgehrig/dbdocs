Overrides `Stream`

This method reads a specified amount of characters from the current instance, advances the position within the stream, and populates the character array buffer.

### Declaration

    // C#
    public override int Read(char[] buffer, int offset, int count);

### Parameters

- `buffer`

  The character array buffer to be populated.

- `offset`

  The zero-based offset (in characters) in the buffer at which the buffer is populated.

- `count`

  The maximum amount of characters to be read from the stream.

### Return Value

The return value indicates the number of characters read from the stream or `0` if the end of the stream has been reached.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

This method requires that the `Position` on the stream instance be zero or an even number.

The XML data is read starting from the position specified by the `Position` property.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlStream Class](OracleXmlStreamClass.md)

- [OracleXmlStream Members](XmlStreamMembers.md)
