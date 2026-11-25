Overrides `Stream`

This property gets or sets the byte position within the stream.

### Declaration

    // C#
    public override Int64 Position{get; set;}

### Property Value

An `Int64` that indicates the current position in the stream.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

`ArgumentOutOfRangeException` - The `Position` is less than 0.

### Remarks

The beginning of the stream is represented by position `0`. Seeking to any location beyond the length of the stream is supported.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlStream Class](OracleXmlStreamClass.md)

- [OracleXmlStream Members](XmlStreamMembers.md)
