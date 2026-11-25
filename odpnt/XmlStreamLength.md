Overrides `Stream`

This property indicates the number of bytes in the XML stream.

### Declaration

    // C#
    public override Int64 Length{get;}

### Property Value

An `Int64` value representing the number of bytes in the XML stream. An empty stream has a length of 0 bytes.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlStream Class](OracleXmlStreamClass.md)

- [OracleXmlStream Members](XmlStreamMembers.md)
