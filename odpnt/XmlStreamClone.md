This method creates a copy of an `OracleXmlStream` object.

### Declaration

    // C#
    public object Clone();

### Return Value

An `OracleXmlStream` object.

### Implements

`ICloneable`

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

### Remarks

The cloned object has the same property values as that of the object being cloned.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlStream Class](OracleXmlStreamClass.md)

- [OracleXmlStream Members](XmlStreamMembers.md)
