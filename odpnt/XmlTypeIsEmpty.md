This property indicates whether or not the `OracleXmlType` is empty.

### Declaration

    // C#
    public bool IsEmpty {get;}

### Property Value

Returns `true` if the `OracleXmlType` represents an empty XML document. Returns `false` otherwise.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

`InvalidOperationException` - The `OracleConnection` is not open or has been closed during the lifetime of the object.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleXmlType Class](OracleXmlTypeClass.md)

- [OracleXmlType Members](XmlTypeMembers.md)
